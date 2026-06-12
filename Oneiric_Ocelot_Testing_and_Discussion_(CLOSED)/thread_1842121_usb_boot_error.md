---
title: "usb boot error"
date: 2011-09-10
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by ngsupb on 2011-09-10
Hi,

I got a few questions:

1) does booting from usb work for you? I  downloaded 11.10 and installed from unetbootin to my usb flash. I get the error "Boot error" when I try to boot. I tried Startup Disk creator with the same result.  

Is it a known issue ?


2) Someone knows why this section for the upcoming release isn't located under the 
"Development & Programming" section as it was before for the previous releases? and why it is called Ubuntu +1?

---

### Post by jerrylamos on 2011-09-10
Could well depend on your hardware??  How is the bios set up?

I've booted Oneiric Ocelot on my tower, netbook, notebook three different ways.

1. Startup disk creator on 11.04 or 10.10 or 10.04.  Works, cranky, I don't much like it.  Note I use Gparted to format the usb to ext3 beforehand.

2. If you're good at command line, taking a usb flash with everything deleted on it and using dd to copy the .iso to the usb.  That's also cranky but works.  The Oneiric Ocelot images are in an iso hybrid format that will either boot that way or from a CD (if it fits) or DVD.

3.  What I usually use is to have a usb drive formatted to ext3.  I then use a standard cp command to copy the .iso.  Note you should do a sudo chmod 644 *.iso since the .iso downloads with only root permissions.

Do a df to see if your usb drive is /dev/sdc or whatever.  Adjust following code appropriately.

In my running ubuntu I add the following to /etc/grub.d/40_custom
```

menuentry "Ocelot ISO sdc1" {
set isofile="/oneiric-desktop-i386.iso"
loopback loop (hd2,1)$isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
}

```

then sudo update-grub
if necessary do sudo grub-install /dev/sda

Reboot and select your new entry from the Grub2 menu.

I use zsync to update the .iso on the hard drive and then when I want I recopy the file to the usb stick.

Good luck, Jerry

---

### Post by Blasphemist on 2011-09-10
The only thing I can see that Jerry didn't answer was whether or not unetbootin works. The answer is yes, I use it frequently and it never fails for me. Lately I don't even get rid of the iso on it before I use it.

---

### Post by cariboo on 2011-09-10
I've been using the Startup Disk creation tool, with no problems since the start of development. The only time I've run into a problem, is when I used dd incorrectly. :)

---

### Post by vishalrao on 2011-09-11
I also get this "boot error" message when trying to boot a USB stick with 11.10 after writing it from startup-disk-creator on 11.04 :) Same problem if I dd the image too.

I've got an Intel DP35DP motherboard which has been able to boot previous images (pre 11.10) just fine.

---

### Post by ngsupb on 2011-09-11
got it installed on other notebook.  Appears to be something hardware related. ...but I was able to install 11.04 before there.

Anyway has already started to test it and reporting bugs.

---

### Post by Denver Dave on 2011-09-11
Pardon this basic question.  I'm running the DVD from "The Official ubuntu Book" on my (previously) Windows PC. I basically know nothing about Ubuntu or Linux, let alone how to use various utilities.   From what I'm running, is there a way to recognize a usb stick and install ubuntu to the USB drive so that I can load it from there, without using various utilities mentioned that I don't know anything about.

I'd like to load a little faster than from the DVD and be able to save files and install the adobe flash player so I can test Youtube videos, but I'm not ready to change the hard drive on my windows PC.

Next step?

Thanks.

---

### Post by effenberg0x0 on 2011-09-11
Download Universal USB Installer. 

It will download Ubuntu, format your USB, burn Ubuntu to the USB and prepare the USB for boot.
You can use this USB to either test (Live Session) or install Ubuntu.

[http://www.pendrivelinux.com/downloads/Universal-USB-Installer/Universal-USB-Installer.exe](http://www.pendrivelinux.com/downloads/Universal-USB-Installer/Universal-USB-Installer.exe)

You have the option to create some space in the USB to store your files, install programs, etc. (its called persistence. See [http://www.pendrivelinux.com/what-is-persistent-linux/](http://www.pendrivelinux.com/what-is-persistent-linux/))

Regards,
Effenberg

---

### Post by cariboo on 2011-09-11
> **Denver Dave said:**
> Pardon this basic question.  I'm running the DVD from "The Official ubuntu Book" on my (previously) Windows PC. I basically know nothing about Ubuntu or Linux, let alone how to use various utilities.   From what I'm running, is there a way to recognize a usb stick and install ubuntu to the USB drive so that I can load it from there, without using various utilities mentioned that I don't know anything about.

I'd like to load a little faster than from the DVD and be able to save files and install the adobe flash player so I can test Youtube videos, but I'm not ready to change the hard drive on my windows PC.

Next step?

Thanks.

This is the wrong place for your post, as this sub-forum is about testing the next release of Ubuntu. It would be better asked in [ABT]("http://ubuntuforums.org/forumdisplay.php?f=326").

To answer your question though, you can install Ubuntu to a USB thumb drive, just the same way you would install it to a hard drive. You didn't say what version the DVD is, but when you are running the installer, once you reach the partitioning section, choose manual partitioning, and select the usb drive to install to. Be aware that Linux uses different device labeling than Windows, depending on how many hard drives you have in your system, it could be labeled /dev/sdb for only one drive,  on my server which has 7 hard drives my usb drive has a device label of /dev/sdh.

Again depending on which version you are installing, your usb device should be a minimum of 4GiB in size. I have a couple of installs on 8GiB thumb drives and SD cards.

---

