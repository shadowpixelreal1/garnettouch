# GarnetTouch

A from-scratch Windows touchscreen driver for the Xiaomi Redmi Note 13 Pro 5G
(codename **garnet**, Snapdragon 7s Gen 2 / SM7435) running Windows 11 on ARM.

This repo hosts the project's showcase page (`index.html`). It's a static site —
open the file locally, or enable **GitHub Pages** (Settings → Pages → deploy from
the default branch) to serve it at `https://<user>.github.io/<repo>/`.

## Status

| Component     | State        |
|---------------|--------------|
| Touchscreen   | Working — 10-finger multitouch |
| Volume keys   | Built, on-device test pending |
| Wi-Fi         | In progress (co-processor bring-up) |

## How touch works

Goodix GT9916R → SPI (QUP1 SE3, GSI) → GPI DMA (GPII 0) → APPS SMMU → Windows HID (VHF).
A small UEFI driver powers the controller and opens the SMMU before Windows boots;
a WDM kernel driver owns the DMA engine and speaks the Goodix "Berlin" protocol,
reporting up to 10 contacts at ~100 Hz.

## Notes

Personal hobby build on a bootloader-unlocked phone. Built on the Mu-Silicium UEFI
port; hardware details mapped from the phone's own device tree.

Not affiliated with Xiaomi, Qualcomm, Goodix or Microsoft. Product and device names
are used only to describe the hardware.
