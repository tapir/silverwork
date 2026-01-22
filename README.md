# SilverWork &nbsp; [![bluebuild build badge](https://github.com/tapir/silverwork/actions/workflows/build.yml/badge.svg)](https://github.com/tapir/silverwork/actions/workflows/build.yml)

A `BlueBuild` image based on their `fedora-silverblue` image. It mainly adds the `CachyOS ThinLTO` kernel.
Kernel and the modules are signed with my MOK key which will be automatically enrolled after the first boot. Use password `scachy` when asked.

## Changes

- Remove:
  - `firefox`
  - `firefox-langpacks`
  - `htop`
  - `nvtop`
  - `gnome-software`
  - `gnome-tour`
  - `ptyxis`
  - `gnome-system-monitor`
  - `malcontent-control`
  - `gnome-disk-utility`
  - `gnome-color-manager`
  - `yelp`
  - `pipewire-config-raop`
- Install:
  - `Bazaar` flatpak (App Store)
  - `Ptyxis` flatpak (Terminal)
  - `kernel-cachyos-lto` kernel
  - `cachyos-settings`
  - `scx-scheds`
  - `scx-tools`
  - `adw-gtk3-theme`

## Installation

- Disable `secureboot` from BIOS and boot to an atomic distro
- Switch to the latest image
  ```
  bootc switch ghcr.io/tapir/silverwork:latest
  systemctl reboot
  ```
- Accept MOK key enrollment with password `scachy`
- Enable `secureboot` back

The `latest` tag will automatically point to the latest build. That build will still always use the Fedora version specified in `recipe.yml`, so you won't get accidentally updated to the next major version.

## Verification

These images are signed with [Sigstore](https://www.sigstore.dev/)'s [cosign](https://github.com/sigstore/cosign). You can verify the signature by downloading the `cosign.pub` file from this repo and running the following command:

```bash
cosign verify --key cosign.pub ghcr.io/tapir/silverwork
```
