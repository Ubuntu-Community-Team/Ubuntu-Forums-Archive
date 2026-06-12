---
title: "V/v: Ubuntu setup"
date: 2021-05-18
forum: New to Ubuntu
---

### Post by bietduoc on 2021-05-18
I am using Dell Vostro laptop, ubuntu recommended.So where can I download the installer?Thank you

---

### Post by Impavidus on 2021-05-18
Read the full instructions here: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by tea for one on 2021-05-18
Here is a link to create a bootable usb device using Windows.

Within the overview, there is another link to finding the Ubuntu ISO

[s][https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview](https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview)[/s]

_Edit_

The link above is not up-to-date because in section 4, the following text appears:-

> The default selections for Partition scheme (MBR) and Target system (BIOS (or UEFI-CSM)) are appropriate (and are the only options available).

It is misleading not to mention GPT and UEFI.

Therefore, please ignore link.

---

### Post by ActionParsnip on 2021-05-18
[https://ubuntu.com/download](https://ubuntu.com/download)

---

### Post by ajgreeny on 2021-05-18
You should also read through all the information at [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) to make sure you fully understand about the differences between UEFI and MBR/BIOS.

I have no idea if that machine uses UEFI or BIOS by default but if UEFI is available make sure that you use it.
You will have to use gpt formatting for best use and will either have to create an ESP/EFI partition (about 200-500M) using fat32 with the ESP flag set, or allow the installer to use the whole disk and create the default partitions automatically as it installs.

---

### Post by oldfred on 2021-05-18
What model Dell Vostro laptop?
Older BIOS/MBR or newer UEFI/gpt?
Instructions considerably different depending on boot mode.

---

