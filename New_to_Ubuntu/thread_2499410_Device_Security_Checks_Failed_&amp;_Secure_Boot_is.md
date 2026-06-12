---
title: "Device Security Checks Failed &amp; Secure Boot is Off"
date: 2024-07-25
forum: New to Ubuntu
---

### Post by ginoel on 2024-07-25
I'm new to Linux & installed Ubuntu 24.04 LTS  on my Microsoft Surface Book 2 but I have the following issues...
1. Under Settings/Privacy & Security/Device Security, I see:[INDENT]**Checks Failed **Hardware does not pass checks.
**Secure Boot is Off** No protection when the device is started.
**Security Events** Intel Management Engine Manufacturing Mode (this is listed 11 times - 6 times with a red X & 5 times with a green check mark.[/INDENT]
2. Under Camera and in Google Meet in Firefox, my built-in camera cannot be found -- but both the built-in front & back cameras work in Cheese.

I really don't know much about tech, but in reading different threads I haven't been able to find anything to resolve any of these issues. Here's more detail on my laptop:
# System Details Report
---

## Report details
- **Date generated:**                              2024-07-25 20:33:37

## Hardware Information:
- **Hardware Model:**                              Microsoft Corporation Surface Book 2
- **Memory:**                                      16.0 GiB
- **Processor:**                                   Intel® Core™ i7-8650U × 8
- **Graphics:**                                    Intel® UHD Graphics 620 (KBL GT2)
- **Graphics 1:**                                  NVIDIA GeForce GTX 1060
- **Disk Capacity:**                               (null)

## Software Information:
- **Firmware Version:**                            394.779.768
- **OS Name:**                                     Ubuntu 24.04 LTS
- **OS Build:**                                    (null)
- **OS Type:**                                     64-bit
- **GNOME Version:**                               46
- **Windowing System:**                            X11
- **Kernel Version:**                              Linux 6.9.3-surface-2

---

### Post by currentshaft on 2024-07-25
For the first part, secure boot can be enabled in BIOS settings.

For the second part, try installing the non-snap version of Firefox. OMGUbuntu has an article on how to do it.

---

### Post by ginoel on 2024-07-29
1. When I enabled secure boot in BIOS, the laptop wouldn't boot up  the text was so small, I couldn't read it. 

2. I followed the steps to install the non-snap version of Firefox from here: [https://askubuntu.com/questions/1399383/how-to-install-firefox-as-a-traditional-deb-package-without-snap-in-ubuntu-22/](https://askubuntu.com/questions/1399383/how-to-install-firefox-as-a-traditional-deb-package-without-snap-in-ubuntu-22/) and the camera is still not recognized.

---

