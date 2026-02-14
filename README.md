# Video2X Qt6

## Building AppImage

### Enable AppImage Build

Add to CMake configuration:
```bash
cmake -DVIDEO2X_BUILD_APPIMAGE=ON ..
cmake --build . --target appimage -j$(nproc)
```

### LinuxDeploy Tools

The build system will auto-download `linuxdeploy` and `linuxdeploy-plugin-qt`, but this may fail occasionally.

You can specify local paths instead:
```bash
cmake \
  -DLINUXDEPLOY_LOCAL=/path/to/linuxdeploy-x86_64.AppImage \
  -DLINUXDEPLOY_QT_LOCAL=/path/to/linuxdeploy-plugin-qt-x86_64.AppImage \
  ..
```

### libtiff5 Dependency (Qt 6.10.2+ on Kubuntu 24.04)

Kubuntu 24.04 ships with `libtiff6`, but Qt 6.10.2+ may require `libtiff5`. 

**Option 1: Auto-download (recommended)**
The build system will automatically download and extract libtiff5 if needed.

**Option 2: Manual setup**
```bash
# Download libtiff5 package
wget -O libtiff5.deb https://security.ubuntu.com/ubuntu/pool/main/t/tiff/libtiff5_4.3.0-6ubuntu0.12_amd64.deb

# Extract to local directory
mkdir -p libtiff5
dpkg-deb -x libtiff5.deb libtiff5

# Specify path in CMake
cmake -LIBTIFF5_LIB_PATH=/path/to/libtiff5/usr/lib/x86_64-linux-gnu/ ..
```

> [!IMPORTANT]
> Please create issues in the [Video2X repo](https://github.com/k4yt3x/video2x) for centralized issue-tracking.

The Qt6 graphical user interface for [Video2X](https://github.com/k4yt3x/video2x). You can download the releases on Video2X's [releases page](https://github.com/k4yt3x/video2x/releases). Build instructions and usages are available on the [documentation site](https://docs.video2x.org/).

![6.3.0-screenshot](https://github.com/user-attachments/assets/c5442f84-5ffc-4476-915f-a0fc188a2cb3)

## Translations

Special thanks to:

- [@reindex-ot](https://github.com/reindex-ot) for providing the Japanese (Japan) translation.
- [@ruiramalhoofc](https://github.com/ruiramalhoofc) for providing the Portuguese (Portugal) translation.
- [@GautDlpr](https://github.com/GautDlpr) for providing the French (France) translation.
- [@Pete4K](https://github.com/Pete4K) for providing the German (Germany) translation.

## License

This project is licensed under the [ISC license](LICENSE).\
Copyright (C) 2024-2025 K4YT3X.
