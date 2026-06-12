---
title: "usb-imagewriter"
date: 2014-03-29
forum: New to Ubuntu
---

### Post by blueskychipita on 2014-03-29
In Linux Mint 16 Cinnamon, Mate and xfce editions the very useful tool "usb-imagewriter" (also usb-imageformatter) is included.  I cannot find it (either writer or formatter) in Ubuntu 13.10 or 14.04 final beta.  Any ideas as to how to add it is much appreciated.  It is much easier to use than unetbootin.  Thanks.

---

### Post by NM5TF on 2014-03-29
in Ubuntu 14.04 it is called "startup Disk Creator"....basically works the same as Mint's usb-imagewriter...

look in the dash/hud/whatever it's called now...

tommy

---

### Post by edeneen on 2014-03-29
I personally used unetbootin and it did NOT work, I used "start up disk creator" in Ubuntu and it worked fine with  CDs, DVDs, and flash drive.

---

### Post by blueskychipita on 2014-03-30
I have tried to use "startup-disk-creator" in Ubuntu 13.10 and 14.04 final beta, but I get an erase error for my usb stick and can never get to "create startup disc", it is grayed out.  I will try again with a different usb stick.  Thanks for the replies.

---

### Post by NM5TF on 2014-03-31
> **blueskychipita said:**
> I have tried to use "startup-disk-creator" in Ubuntu 13.10 and 14.04 final beta, but I get an erase error for my usb stick and can never get to "create startup disc", it is grayed out.  I will try again with a different usb stick.  Thanks for the replies.

just to make things a little more interesting....today I tried to make a bootable usb stick
using "starup-disk creator" for a new *nix distro...

I downloaded the .iso file correctly, but the app could not read it....:mad:

I then tried unetbootin to make the bootable stick & it DID work as I could boot the live image...:p

YMMV

tommy

---

### Post by sudodus on 2014-03-31
***Startup Disk Creator*** in Trusty has a bug that makes it fail if you try to erase the drive. Otherwise it works well for me and several other people. See this bug report

[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/915626](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/915626)

I wrote comment #61
>                         I tested usb-creator-gtk  in an updated/dist-upgraded  Lubuntu 13.10 i386 installation. I created persistence and the whole  process was much nicer than before. It works without any segfaults :-)

 But I can confirm that it  crashed when I tried to erase disk. The disk was not erased. The  partition is still there, and the files are still there. Is this another  bug? Should it be reported to Launchpad?
 Fortunately there is gparted, so we don't really need the erase disk function of usb-creator-gtk.

[B][I]
Unetbootin[/I][/B] works well in most cases. See this link

[Paul Sutton's Unetbootin how to]("http://zleap.net/unetbootln-usb-how_to/")

Both these tools rewrite the boot iso file made for a CD/DVD with the ISO 9660 file system into a FAT32 file system. And this process does not always work. In such cases it is possible to clone or flash the iso file as it is directly to a USB pendrive, provided it is a hybrid iso file. All current Ubuntu family iso files are hybrid iso files. There is a shell-script tool to make this process safe and convenient, ***mkusb***. See this link

[Ubuntu Forums tutorial "Howto make USB boot drives"]("http://ubuntuforums.org/showthread.php?t=1958073")

---

### Post by NM5TF on 2014-04-01
@sududus....thanx for link to mkusb.....will have to try that next time...

tommy

---

### Post by sudodus on 2014-04-01
> **NM5TF said:**
> @sududus....thanx for link to mkusb.....will have to try that next time...

tommy

You are welcome, and good luck :-)

---

