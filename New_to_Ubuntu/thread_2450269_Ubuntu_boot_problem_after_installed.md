---
title: "Ubuntu boot problem after installed"
date: 2020-09-10
forum: New to Ubuntu
---

### Post by ayarmukh on 2020-09-10
Hi Community,

Could you please help me with the following issue:

I have installed Ubuntu alongside windows 10 with manual partition, but it is not started after I start my machine (I only have windows option and after pressing ESC I got options of Windows or BIOS).

I tried boot repair tool (when I choose "Try Ubuntu"), but it did not help. Have not even seen option "Recommended repairs", only "Create BootInfo summary"

URL: [https://paste.ubuntu.com/p/FGnXQNM6xw](https://paste.ubuntu.com/p/FGnXQNM6xw)

Thanks
Andrey

---

### Post by CelticWarrior on 2020-09-10
Welcome.

Have you installed Windows yourself? Why did you install in Legacy mode?

---

### Post by ayarmukh on 2020-09-10
Hi, 

The windows was pre-installed. Do you mean that I have installed ubuntu in legacy or windows?

Thanks

---

### Post by CelticWarrior on 2020-09-10
Sorry, my mistake. I was reading the wrong information.

Please open UEFI settings > Boot menu and change the boot order to have "Ubuntu" first.

---

### Post by oldfred on 2020-09-10
You have a Windows UEFI boot  entry, so it must be UEFI. But Ubuntu entry in UEFI is not a typical UEFI boot entry. Perhaps BIOS boot, but NVMe drives not fully shown. They show as md which may be Intel RST related. Before you could not even see a RST drive, but now you can, but still not functional.
But you show bitlocker. 
And is then nvme0n1 just for Windows fast startup and is Intel RST? More like a swap partition just for Windows boot.

What brand/model system?
What video card/chip?

You need to make sure UEFI fast boot is off, and UEFI is set to AHCI for drives, not Intel RST. But need to install Windows AHCI driver first or Windows will not boot ( you can turn it back on temporarily to add AHCI driver, but then Ubuntu will not work).
Often easier to install if UEFI Secure Boot off, but if no proprietary drivers required it should just work. If you need proprietary drivers for video or Wi-Fi then you need to set your own Secure Boot keys.

Windows AHCI instructions - some have found safeboot method better
[https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571](https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571) & 
[https://askubuntu.com/questions/1233623/workaround-to-install-ubuntu-20-04-with-intel-rst-systems](https://askubuntu.com/questions/1233623/workaround-to-install-ubuntu-20-04-with-intel-rst-systems) & 
[https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347](https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347)
AHCI enable - May have to unlock bitlocker if used
[https://www.tenforums.com/drivers-hardware/15006-attn-ssd-owners-enabling-ahci-mode-after-windows-10-installation.html#post332243](https://www.tenforums.com/drivers-hardware/15006-attn-ssd-owners-enabling-ahci-mode-after-windows-10-installation.html#post332243)
Dual boot with Bitlocker works
[https://askubuntu.com/questions/1135654/how-to-install-ubuntu-alongside-bitlocker-encrypted-windows10](https://askubuntu.com/questions/1135654/how-to-install-ubuntu-alongside-bitlocker-encrypted-windows10)

---

### Post by ayarmukh on 2020-09-10
Ubuntu option is not in the Boot menu of BIOS.

---

### Post by ayarmukh on 2020-09-10
My laptop is ASUS VivoBook (X413FA-EK591T). Video card is Intel(R) UHD Graphics (sorry I might be wrong here).

[COLOR=#000000]And is then nvme0n1 just for Windows fast startup and is Intel RST? - I do not really know. How can I check? There is only one drive on my machine.[/COLOR]

---

### Post by oldfred on 2020-09-10
You should have setting in UEFI for drives that is RAID, Intel RST or AHCI. You want AHCI.
I think then your second small NVMe drive will not be used.

Before Microsoft required vendor to speed boot as Windows boots so slow, so they added a tiny SSD to system just for booting. Some of those SSD were large enough for / (root) and users just installed Ubuntu into that with /home and/or data on HDD. Then very fast Ubuntu, at price of slower boot Windows. But SSD did not help Windows except for booting.

---

### Post by ayarmukh on 2020-09-10
Thanks for you reply. Could you please advise which section in the article is relevant? All this is new for me and the article seems to be huge.

---

### Post by CelticWarrior on 2020-09-10
The article is for learning about UEFI. Nothing there is specific to your case. What you were suggested to change in UEFI settings depends on your specific hardware.

---

### Post by ayarmukh on 2020-09-10
Thanks a lot everyone. After switching to [COLOR=#000000]AHCI I got it working.[/COLOR]

---

