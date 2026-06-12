---
title: "Install advice needed"
date: 2016-11-19
forum: New to Ubuntu
---

### Post by GiuHei3u on 2016-11-19
[COLOR=#000000]Finding it difficult explaining something which I know little of! For starters I was copying 12.04 onto the usb drive. Not aware that it had to be installed onto the drive. That took some time. It now is installed on the usb and now have the option to try Ubuntu or Install. Wanting to install on an External Drive I proceeded with that step until I arrived at the "Installation Type".This is a critical step for me and a mistake could be costly. There are a couple of options I have, one is for an installation to my internal drive and another is various partitions inside Windows. [/COLOR]

[COLOR=#000000]There is an option to choose the "Device for the Boot Loader Installation" and my external drive comes up as "Toshiba Ext USB 3.0 (1TB)". Would this be the correct choice to have the full installation of 12.04 on this External Drive and not on Windows?[/COLOR]



[COLOR=#000000]Thank You.[/COLOR]

---

### Post by ian-weisser on 2016-11-19
You may find it easier and safer to install Ubuntu to a guest VM on a Windows host.

Er, also 12.04 is four years old. I would suggest 16.04 instead.
You should obtain current, safe versions of Ubuntu from downloads.ubuntu.com

---

### Post by GiuHei3u on 2016-11-19
Hello Ian. Well the 16.04 only comes in 64 bit right? Running 32 bit here. Have no idea what a Guest VM on windows host is and don't want to partition my internal drive at this point. So my question remains.

---

### Post by ian-weisser on 2016-11-19
All flavors of Ubuntu 16.04 are available in 32-bit. See [https://www.ubuntu.com/download/alternative-downloads](https://www.ubuntu.com/download/alternative-downloads)

Ubuntu's default Unity Desktop can be sluggish for some 32-bit users. If so, a different flavor like Xubuntu or Lubuntu may work better on lower-spec 32-bit machines.
While awaiting install advice, I suggest trying one of more of those 16.04 32-bit flavors.

---

### Post by oldfred on 2016-11-19
Is this an install to your Asus motherboard? That shows UEFI "BIOS" which is then 64 bit.

And with Ubuntu only the 64 bit versions can be installed in UEFI boot mode.

Only systems over 10 years old or a few very lightweight laptops/tablets are 32 bit. So few systems are 32 bit and those systems do not have video support for Unity that Ubuntu is planning to discontinue 32 bit desktop. Server & lightweight flavors will probably maintain 32 bit for several more years. Or if less than 2GB of RAM you may then want 32 bit lightweight version like Lubuntu or Xubuntu.

       Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)

---

### Post by ajgreeny on 2016-11-19
If you are trying to carry out a full install to an external disk **it is essential that you use "Something Else"** in order to put grub, the Ubuntu boot-loader on to the external disk and not the internal disk, which is where it will go if you do not choose "Something Else".  You would then be able to boot the computer only when the external disk is attached.  Without the external disk you would just get a grub rescue prompt and not boot even to Windows.

---

### Post by GiuHei3u on 2016-11-19
Do have a 64 bit operating system. Windows 7 is 32 bit. Basic terms such as GRUB are foreign to me so I am immersing myself reading the documentation before I present any more questions to the forum. Appreciate your reply and links. Later next week I will be updating my processor and going to a solid state internal drive.

---

### Post by GiuHei3u on 2016-11-19
> **ajgreeny said:**
> If you are trying to carry out a full install to an external disk **it is essential that you use "Something Else"** in order to put grub, the Ubuntu boot-loader on to the external disk and not the internal disk, which is where it will go if you do not choose "Something Else".  You would then be able to boot the computer only when the external disk is attached.  Without the external disk you would just get a grub rescue prompt and not boot even to Windows.

Got it! Thanks.

---

### Post by oldfred on 2016-11-19
It is not whether Windows version you have is 32 bit or 64 bit, but whether your hardware is 64 bit. And most systems in last 10 years are 64 bit.

From live installer in terminal mode, you can run this to see modes.

lscpu

---

