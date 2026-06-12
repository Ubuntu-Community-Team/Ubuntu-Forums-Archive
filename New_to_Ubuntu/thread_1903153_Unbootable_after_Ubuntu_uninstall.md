---
title: "Unbootable after Ubuntu uninstall"
date: 2012-01-01
forum: New to Ubuntu
---

### Post by Orbetrexx on 2012-01-01
I have a dell computer (older) with two 75GB Harddrives. Windows xp home, and until recently ubuntu. I did anewb thing and uninstalled ubuntu without fixing my MBR. Unfortunately now I'm unbootable with no Live CD or Windows recovery disk. Now I made a windowsxp install disk on a bootable usb. (mounted and wrote the iso with power iso) and plugged it in and restarted. The boot menu shows hard drive removable media and cd rom but when any are selected it automatically proceeds to grub rescue prompt. What I need is the EXACT commands I woukd need to enter to boot my windows xp up. Its still there.. I cant get to it. Remember, no live cd or windows cds.

---

### Post by 73ckn797 on 2012-01-01
See if this info can help: [https://help.ubuntu.com/community/RecoveringWindows](https://help.ubuntu.com/community/RecoveringWindows)

If the USB XP does boot to the install screen, the section on "Reinstating Windows' may help.

---

### Post by Mark Phelps on 2012-01-02
IF you have a way to burn a CD, then look into using Boot-Repair:

[http://ubuntuforums.org/showthread.php?t=1769482&highlight=boot-repair]("http://ubuntuforums.org/showthread.php?t=1769482&highlight=boot-repair")

---

### Post by saneearth on 2012-01-02
run: cmd

then: fixmbr

---

### Post by Orbetrexx on 2012-01-02
None work, except maybe the boot from cd thing.. But I have no way to get a disc right now... O was mainly wondering if there was any way to accomplish this without it. Because its going to take some work getting adisc for a machine I made out of about three. I can only get to two separate screens. One, choose which device to boot from and two, grub rescue prompt. Obviously I didn't mount this usb right or out would be booting from that.... So until I get adisc, is there any way to start windows from grub rescue? It lists both hard drives with a msdos1 partition.. If that means anything. Appreciate the help regardless of the outcome.

---

### Post by oldfred on 2012-01-02
If you have two hard drives have you tried booting from the second drive? Is your system new enough ( about 5 years or less) to boot from USB?

If you get grub rescue, you may be able to just boot into the Windows PBR - partition boot sector. It says the chain  command is available, but in most places with grub in menus, it is chainload?

Try
Manual boot:
grub rescue:
ls # Do you see (hd0), (hd0,1) ? If so, run the next command. If you see  (hd0,2), use that instead of (hd0,2) in the next command.

set root=(hd0,1)
chain +1
boot

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt 
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)

You can easily install a Windows like boot loader from the Ubuntu liveCD to the MBR.


Restore basic windows boot loader - universe enabled
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

---

### Post by Orbetrexx on 2012-01-02
Okay, when I "ls" the partitions and drives, I get (hd0) (hd0,msdos1)(hd1)(hd1,msdos1) (hd2)(hd2,msdos1) (fd0)
I tried the set root. And it doesn't recognize the chain, or chainload command. Its older... Not sure on years... 1.6ghz pentium and 256ram is what it originally came on it. So I'm thinking probably older.

*also.... I installed the second drive myself strictly for ubuntu. But I then, after successfully partitioning the drive and installing ubuntu, I deleted, uninstalled ubuntu, and deleted all partitions on the second drive. So basically its empty. The first hard drive however has a full windows install and over forty gigs of media. Basically I just forgot to restore the mbr before I restarted. And here w are.only thing I have close to a recovery or boot disk is the usb recovery iso I mounted. Unfortunately it looks like I can't boot from it on my older system. :(

---

### Post by oldfred on 2012-01-02
Deleting partitions does not delete MBR, but it is unlikely that the MBR on the empty disk is useful.

If the system is that old it does not boot from a USB. You can use plop to make a bootable USB.

Boot USB or PCMCIA (new)
[http://www.plop.at/en/home.html](http://www.plop.at/en/home.html)

Otherwise you can boot from CD or floppy? Or temporarily install drive to another PC and copy the data using that system.

---

### Post by Orbetrexx on 2012-01-02
Well I deleted all partitions after uninstalling and formatted the drive.. So I also doubt anything on drive 2 is useful. The usb, I made by using poweriso and following the directions for making a bootable usb. The image mounted was windows xp home sp 2 install. I'm not worried about losing my media anymore... I just want a clean install... Our to just get to windows. I can boot from acd and floppy, the problem is, I have no way of obtaining something to b boot from. As far as another system, I don't have one. The other one I had I disassembled and added to the one I have now. Lol... So from the research I've done on the site and forums.. Added with your answers.. I'm guessing I can't do anything but obtain a bootable disc to do the repairs... Or atleast get to the command prompt to use the fixmbr command?

---

### Post by oldfred on 2012-01-02
If system is old enough not to boot from USB, then you need to keep several working liveCDs. I used to have current verisions of gparted, system repair, Supergrub, as well as my Ubuntu install and after several installs older Ubuntu installs on CDs. Since I was reinstalling every 6 months I went though a lot of CDs.:) But my systems are both about 6 years old and both boot USB. When flash drives dropped in price, I now just download ISOs and put them on the flash drive to avoid burning all the CDs. Nice that they are reusable. 

If you do not know anyone with a working Windows or Linux, your best bet may be just to go to the local large computer store and buy a Linux magazine with several Linux liveCD systems. You may want an older one if possible or something with Lubuntu, Puppy or Knoppix. The newest Ubuntu needs 512MB to install.

If there is a Linux group in your area they would be able to give you a CD also.

---

### Post by Orbetrexx on 2012-01-02
I guess I'll just have to wait for a chance to get a disc. Lol thank you very much for the attention and h help. Didn't expect to even get a response.

---

