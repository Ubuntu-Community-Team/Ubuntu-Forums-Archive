---
title: "New to ubuntu and getting install error, i686"
date: 2015-04-12
forum: New to Ubuntu
---

### Post by forwheeler2000 on 2015-04-12
I have a Dell inspiron 6000 laptop and want to install xbuntu. I downloaded the 32 bit version and created a bootable usb flash drive.
I get an error:[h=1][SIZE=2][Kernel requires an x86-64 CPU, but only detected an i686 CPU]("http://askubuntu.com/questions/128657/kernel-requires-an-x86-64-cpu-but-only-detected-an-i686-cpu-how-can-i-install")[/SIZE][/h]
I went into the bios and looked for virtualization options since that is what I have read that fixes the issue but I can't find an option like that.
Has anyone installed xubuntu on this model laptop?

---

### Post by grahammechanical on 2015-04-12
Double check that you did indeed download the 32 bit version of Xubuntu. It should say  i386 .iso and not amd64.iso

I ask because a 32 bit version of Ubuntu/Xubuntu will run on both 32 bit and 64 bit CPUs. But a 64 bit version of Ubuntu/Xubuntu will only run on a 64 bit CPU. That error message seems to be saying the The Linux kernel in Xbuntu is 64 bit but the CPU is not. The CPU in the Inspiron 6000 is listed as 32 bit with Physical Address Extensions (PAE). 

Regards.

---

### Post by forwheeler2000 on 2015-04-12
The file is named xubuntu-14.04.2-desktop-i386.iso.torrent and I downloaded it from [http://xubuntu.org/getxubuntu](http://xubuntu.org/getxubuntu). I selected the 32 bit download from that page so it looks like the correct file.

---

### Post by Dennis N on 2015-04-12
> **forwheeler2000 said:**
> The file is named xubuntu-14.04.2-desktop-i386.iso.torrent and I downloaded it from [http://xubuntu.org/getxubuntu](http://xubuntu.org/getxubuntu). I selected the 32 bit download from that page so it looks like the correct file.

Yes, I have Xubuntu 14.04 intalled on a Dell 6000. That model had lots of processor options available, but all are 32 bit so you want a 32 bit version of the OS. The file you mention ( xubuntu-14.04.2-desktop-i386.iso.torrent ) is not an iso file, but a torrent file to be used in a bittorrent client to get the correct iso file. Look further down the page at "Mirror Downloads" to get the iso for the installer directly, either **xubuntu-14.04.1-desktop-i386.iso** or  **xubuntu-14.04.2-desktop-i386.iso**

If you want to use a bittorrent client, that will work too.

---

### Post by forwheeler2000 on 2015-04-12
Yes I have a torrent client installed and have the ISO file. I created a bootable flash drive and included the ISO file. If you have it installed then I assume that I should be able to get it installed too. I just need to figure out what I need to do to get past this error. I may have the other processor however.

---

### Post by Dennis N on 2015-04-12
Well, there were more than 2 processors  - I just corrected that. Looked at the original product brochure (I count 15 offered) and they are either Pentium M 7xx or Celeron M 3xx (xx replaced by various numbers). All Pentium M are 32 bit, however (according to Wikipedia). So were the Celeron M.

---

### Post by forwheeler2000 on 2015-04-12
So do you think that xubuntu is not compatible with that hardware?

---

### Post by Dennis N on 2015-04-12
> **forwheeler2000 said:**
> So do you think that xubuntu is not compatible with that hardware?

I would guess yours is compatable since my Dell 6000 is. The error you get suggests to me that the installer is intended for 64 bit systems. You are not using virtualization, so that doesn't seem to apply. I would use the direct download of the 32 bit installer and try that.

---

### Post by forwheeler2000 on 2015-04-12
Okay thanks

---

### Post by forwheeler2000 on 2015-04-14
I was able to download the iso instead of the torrent version and it works. Thanks.
I get unknown filesystem now after trying a dual boot setup so I ran the boot repair and got this result. [http://paste.ubuntu.com/10824748/](http://paste.ubuntu.com/10824748/)

If I need to start a new thread let me know.

---

### Post by yancek on 2015-04-14
How do you get the unknown filesystem?  When you boot Xubuntu, windows?  Are you able to boot Xubuntu?  Have you changed the BIOS to boot from the hard drive?

---

### Post by forwheeler2000 on 2015-04-15
I get the error when I start the laptop after installing Xubuntu. Yes it is booting to the hard drive. When you search for this error on the internet it seems to be a common error and I tried the boot repair tool that is commonly suggested. When you use that tool you get a response which I posted in my last post.

---

### Post by forwheeler2000 on 2015-04-16
I just wiped the drive and only installed xubuntu and it works of course without windows.

---

### Post by mastablasta on 2015-04-17
no install windows on another part of the drive and then update GRUB with boot repair tool should work.

---

