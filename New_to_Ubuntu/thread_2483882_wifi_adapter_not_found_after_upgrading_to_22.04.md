---
title: "wifi adapter not found after upgrading to 22.04"
date: 2023-02-11
forum: New to Ubuntu
---

### Post by atheroshelp on 2023-02-11
Hi,

I just upgrades my os from Ubuntu 18.04 to 22.04 using the default software updater app. 

When it finished I was unable to connect to wifi. Going to the wifi tab in settings displayed "no wifi adapter found". 

When running lspci -nnk I get "Network controller [0280] Qualcomm atheros qca6174 wireless network adapter".

I have tried several methods suggested online, but nothing seems to be working.

---

### Post by ActionParsnip on 2023-02-12
What is the output of
```

sudo lshw -C network; lsusb; dmesg | grep -i firm

```

Thanks

---

### Post by atheroshelp on 2023-02-12
*-network UNCLAIMED
   Description: Network controller
   Product: QCA6174 802.11ac wireless network adapter
   Vendor: Qualcomm atheros
...

[   0.204781] ACPI: [firmware bug]: BIOS_OSI(Linux) query ignored

lsusb prints the Linux root hub, card reader controller, touch screen, etc but nothing about the network controller.

Hope this helps, thanks.

---

### Post by jeremy31 on 2023-02-12
Try this in terminal ```
sudo modprobe -v ath10k_pci
```

---

### Post by atheroshelp on 2023-02-12
I get:
modprobe: FATAL: module ath10k_pci not found in directory /lib/modules/5.4.0-1091-gke

---

### Post by jeremy31 on 2023-02-12
Are you sure the upgrade completed?  You should have a 5.15 kernel

---

### Post by atheroshelp on 2023-02-12
When I opened the software updater, I asked it to upgrade to the latest version.

However, running lsb_release -a confirms that I apparently only upgraded to 20.04.5.

I apologize for this. Is there any fix for this issue on 20.04 that doesn't apply to 22.04?

Thanks, sorry for the confusion.

---

### Post by jeremy31 on 2023-02-13
You will likely need to boot into an older kernel from Grub, Advanced options for Ubuntu, then if wireless works do ```
sudo apt install linux-modules-extra-5.4.0-1091-gke
```
Then reboot and see if it works with current kernel

---

### Post by ActionParsnip on 2023-02-13
GKE appears to be Google Kubernetes. Does their config allow updates to the next LTS? Is that supported?

---

### Post by atheroshelp on 2023-02-13
Running apt install requires accessing the internet. How do I do this when the computer can't connect to wifi in the first place?

---

### Post by atheroshelp on 2023-02-13
Nvm jeremy31 was correct. For anyone in the future, the grub menu is the one that comes up when restarting. I selected the oldest available kernel, ran the command, and the new kernel works just fine. It even fixed my TouchPad, which also broke during the upgrade.

Thank you!

---

