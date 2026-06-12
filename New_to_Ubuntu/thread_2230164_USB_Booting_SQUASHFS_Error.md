---
title: "USB Booting SQUASHFS Error"
date: 2014-06-17
forum: New to Ubuntu
---

### Post by MLUbuntu on 2014-06-17
Hello,

I know this has been answered extensively but I haven't been able to fix my problem, so I have decided to write a post about it. Yes, I'm a total newbie.

I'm trying to install Ubuntu 14.04 on my Toshiba Satellite nb10t-a-101 laptop. Currently there is no OS present, only the BIOS (UEFI).

I boot from the USB, I get on to the grub menu where I can Try, Install (etc). When I press on Try, I get the Ubuntu splash screen for a few seconds (with the little orange dots) then the screen goes black and starts showing lots of SQUASHFS Errors.

I have read other posts about it and I know it is supposed to be a HW error. I have tried the following:

I have redownloaded the .iso file and done a md5 checksum. Says no error.
I have "burned" the .iso file into a usb using Universal USB Installer and also through Terminal on OS X.
I bought a brand new USB today and tried it a few times. Still shows the same error. (There is no CD Reader on the laptop so I can't try with CDs
Fearing the worst, I thought it may be bad memory modules. I used memtest86 and it showed no errors after several runs

I don't know what else to do and I can't get past this point.

I wanted to try the "[COLOR=#333333][FONT=Ubuntu]Successful boot was achieved by adding "all_generic_ide" to the grub boot line for the live CD. " workaround but I really don't know how to do it. I press 'e' but I don't know how to correctly add the lines. 

[/FONT][/COLOR]Ah, also secure boot and fast boot are disabled, I have checked all the UEFI settings available.
[COLOR=#333333][FONT=Ubuntu]
So there's not much more I can do.

Thank you! I really want to use Ubuntu! :([/FONT][/COLOR]

---

### Post by negora on 2014-09-19
Hello:

I've an old laptop, a Toshiba Satellite A60. And I've been facing this problem with the installer for a long, long, long time :/ . I've tried everything:

  * DVD.
  * USB booted with Plop Boot Manager.
  * ISO stored in an USB device and booted with GRUB2.

What I did in the end was to create a virtual machine in another computer, using VirtualBox. I created a virtual hard drive with the smallest possible size for the install (8-9 GB). Once it was installed, I booted the virtual machine with a Clonezilla LiveCD and made an image of the disk. Finally, I restored that image in my Satellite A60. Because the Linux kernel configures almost all hardware at boot time automatically, I had no problem and it worked flawless.

I made a small virtual disk because the destination hard drive must be at least as big as this one. This way you ensure that you can restore the disk image anywhere, even in computers with a small hard drive.

When you use Clonezilla to make the disk image, I recommend you to create it into another virtual hard drive created for this task specifically. Don't create it in an USB device directly. For me it was extraordinarily slow. When the task has finished, use the own Ubuntu installed in the virtual machine to copy the disk image from the virtual disk to the host (using a shared folder), and then to an USB.

Finally, when you've restored the image in the destination, use GParted to resize the disk partitions as you want.

Cheers.

---

### Post by NM5TF on 2014-09-19
@MLUbuntu....

did you by chance use UNetbootin to make your USB iso ???

if so, there is a bug as it will overwrite the squashfs files...

google it, or search the forums for a work around...I have seen it before, but don't remember where it is...

tommy

---

