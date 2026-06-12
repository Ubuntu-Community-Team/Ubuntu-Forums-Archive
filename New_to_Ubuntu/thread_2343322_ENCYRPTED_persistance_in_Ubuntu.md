---
title: "ENCYRPTED persistance in Ubuntu"
date: 2016-11-15
forum: New to Ubuntu
---

### Post by michaellee8 on 2016-11-15
I am making a Ubuntu live boot USB for my own project, which contains many private coding, so I need to make my persistence partition encrypted. Just like the one in [Kali Linux, LUKS and persistence]("http://docs.kali.org/downloading/kali-linux-live-usb-persistence") preventing any information being stolen. However, I have no luck on both Google and forum at this moment.

Q&As:
[LIST=1]
[*]Why don't you install Ubuntu in the USB directly? This USB is going to be used in many places like school computers, which is may not compatible greatly if I do a direct install, also It takes so much space for a direct one.
[*]Why need encyrpted? Not just private codes, also something private like photos can also be stored there.
[*]Why don't you use Kali? I am also a user of it but I want to separate those hacking files and hacking configuration from my own code.
[/LIST]

Will be so happy if I can receive some help here. Ubuntu is truly wonderful if encrypted persistence exists.

---

### Post by C.S.Cameron on 2016-11-16
Kali is the only applicable encryption solution I can find using my memory and Google.

---

### Post by sudodus on 2016-11-16
*Easy:* You can use two Kali systems (in two different drives). That is an easy way to keep different data sets apart.

*More difficult but should be possible for you:* Create a persistent live drive with Ubuntu. Boot into it and create a new user with encrypted home (ecryptfs). Maybe not as secure as LUKS, but probably good enough. You can use [mkusb](https://help.ubuntu.com/community/mkusb) to create the persistent live drive, but you have to create the new user manually. It helps to install the package **gnome-system-tools**, which lets you use the program ***users-admin***

---

### Post by michaellee8 on 2016-11-16
Well I know these solution already, but I am here looking for a solution that provide a LUKS-encyrpted partition on my USB. You may assume that the reason that I need this level of safety is my data there is highly sensetive and confidential, so I need the very most safety method to do so, just like the one used in kali.

Any way to solve the problem will be appreciated :D

---

### Post by sudodus on 2016-11-16
Use two USB drives with Kali, one for each purpose and set of data. This is by far the easiest solution, and should provide the Kali level of security for both sets of data.

---

### Post by michaellee8 on 2016-11-16
I know that I can use kali and I am already using it. However I want to switch thing to Ubuntu also because of its nice UI (Unity) and hardware supports. I hope that the suggestion given can comply with below 2 conditions: 
1. Use the newest version of Ubuntu
2. Encrypt with the LUKS format with whole partition encyrption

Any solution will be appreciated. Big thanks if someone can help :D

I have saw these links so far, could be helpful but I just don't understand what are they talking about: 
1. [https://archimedesden.wordpress.com/2013/09/12/encrypted-persistent-storage-on-ubuntu-livecd/](https://archimedesden.wordpress.com/2013/09/12/encrypted-persistent-storage-on-ubuntu-livecd/)
2. [https://ubuntuforums.org/showthread.php?t=2147295](https://ubuntuforums.org/showthread.php?t=2147295)
3. [https://ubuntuforums.org/showthread.php?t=2270681](https://ubuntuforums.org/showthread.php?t=2270681)
4. [https://launchpadlibrarian.net/148175781/luks-persistent-img.ubuntu.patch](https://launchpadlibrarian.net/148175781/luks-persistent-img.ubuntu.patch)

---

### Post by sudodus on 2016-11-16
1. Have you tested the portability of an installed system in a USB 3 pendrive? I use such systems, and when I avoid proprietary drivers, they are very portable (except of course, when you need proprietary drivers). It might work in all the computers, where you want to use it. If you need to boot in both UEFI and BIOS mode, it is possible. You can make [something like this](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS), but you have to make it yourself, create the encrypted partition (and set the passphrase).

2. Another alternative is to have an unencrypted persistent live system, and in that system install VirtualBox (or another tool for virtualization). Create an installed Ubuntu system with LUKS encryption in the virtual machine.

*. You should consider the risk with creating your own system with encryption. There are many small details, that you must get right to avoid security holes.

---

### Post by michaellee8 on 2016-11-16
Thank you for your suggestion. Well how to make a encrypted installation then?

May be we should move this thread into "Installation and Upgrades".

---

### Post by sudodus on 2016-11-16
First of all, it is best to remove (or at least disconnect) the internal drive, when you install into an external drive.

Then you can use the following method (made for testers, but valid in general for all versions, and not only for standard Ubuntu but for the community flavours too),

[Install (entire disk with lvm and encryption) in Ubuntu Desktop amd64 in Xenial Daily](http://iso.qa.ubuntu.com/qatracker/milestones/351/builds/135575/testcases/1451/results)

Following this manual will install in either UEFI or BIOS mode, and you need the tweaks described in a previous post by me ([something like this](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)) to make it bootable in both UEFI and BIOS mode.

---

### Post by arbiel-perlacremaz on 2016-11-17
Hi
To install on a USB stick
- prepare your partitions (gparted or LVM) as you prefer, setting apart what you want to protect from what may be left clear
- cryptsetup the partitions or logical volumes you want to protect (crypting /root is probably not useful, and too cumbersome)
- restart your PC booting from the installation tool of your choice (iso file, so called Live USB or CD/DVD)
- uncrypt the crypted partition by a command line (sudo cryptsetup open …)
- install using "Other choice" (not sure of the precise label, as I am not an english speaking user) and select by hand where to locate the directories (/boot, /root, /home, …)
- install grub on the MBR of your stick.

As the installer has not been advertised that any partition or logical volume volume is crypted, you will have to create, or at least to modify /etc/crypttab file and to modify the /home line of your /etc/fstab file, both files of your USB stick /root partition.

Then you perform a bootinfo report, which you post inside your response to this post, so we can explain you what to do next.

---

### Post by crass on 2017-02-11
> **michaellee8 said:**
> I am making a Ubuntu live boot USB for my own project, which contains many private coding, so I need to make my persistence partition encrypted.
...
Will be so happy if I can receive some help here. Ubuntu is truly wonderful if encrypted persistence exists.

I've been adding encryption to ubuntu's live persistence file for some time.  Why they refuse to accept/use the patches I've given them is beyond me (see this bug I created with [patches for saucy]("https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1215504")).  I've recently updated the patches for yakkety and write a [blog post]("https://archimedesden.wordpress.com/2017/01/09/encrypted-persistent-ubuntu-livecd-16-10-redux/") about it.  Right now the changes are only for yakkety, but its fairly easy to update them for a different iso.  Just apply the xdelta to the yakkety iso, and you'll have an iso that you can **loopback** mount with grub2 with encrypted persistence!

Note that with this method the encrypted persistence must be a file on a FAT filesystem (see initrd/scripts/casper-helpers function find_cow_device).  So this comes with the 4GB max filesize of FAT volumes.  You could edit your etc/fstab and etc/crypttab to add other encrypted filesystems, so the 4GB limit isn't a huge deal, more of an annoyance.  The problem with having a generic iso that uses a LUKS encrypted partition is, how does the initrd know what LUKS device to choose from if there are multiple?  You could have it try all of them till it finds one that works, but that's a big pain if there are a lot of encrypted partitions.  A workable solution is to have the initrd check for a specially named partition (call it "casper-rw", just like what it currently looks for with persistence files).  However, the common MSDOS partition label does not allow partition names (although GPT does).  I may add that in the future, but my patches do not currently do that.

---

### Post by kyknos12 on 2017-02-11
There's a unorthodox way but it works, You can use centos live gnome lib modules and initrd.img ready scripts and created custom encrypt live ubuntu iso,I have made 2 customs encrypted distributions slackware and ubuntu with success, defined and a sample,
anyone interested can post tutorial

---

