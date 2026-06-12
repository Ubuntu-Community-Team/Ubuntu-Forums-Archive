---
title: "Multiboot with Vista, XP and any Linux"
date: 2007-04-22
forum: Other OS Talk
---

### Post by yoshida on 2007-04-22
EDIT: Move, plz. Looks like I posted in the wrong section.

Today I have created a multiboot with XP, Vista and Ubuntu. When I boot my PC the Vista Bootloader is giving me these options:

Windows XP Professional
Windows Vista Business
Ubuntu 7.04 AMD64

That's right, the VISTA bootloader. Leave the grub out of this... partially.

Here's how I've done it:
The order in which the OS'es are installed is not important. AS LONG AS THE GRUB IS NOT INSTALLED IN THE MBR! Vista needs it's bootloader to be there. That's why I'm giving this sucker right of way. Instead install the GRUB on the same partition as your Linux distro.

It's been possible for a long time to implement Linux with your boot.ini using [Bootpart](http://www.winimage.com/bootpart.htm). All you need to do is tell Bootpart on which partition Linux is installed, and it will create a binary. This binary will be started with your XP's Boot.ini. The secret is that Vista's bootloader uses the same settings as your boot.ini, so once it is updated and you reboot your system... Linux will be right there in the Vista bootloader.

Once done you can remove all folders from your XP partition and resize it to a few MB for all I care, as long as boot.ini and the binary file will be there. The downside to this is that you'll have to use three bootloaders to get into Linux: Vista's (which will have to reside in the MBR), XP's (which calls the binary) and the Grub (which will eventually boot Linux). But you can ofcourse change the timeout of XP's boot.ini and the Grub to zero, so you can choose Linux and boot uninterrupted.


Use whatever's in this post anyway you like, but at your **own** risk.

---

### Post by edgecoug71 on 2007-05-04
Not bad, I got it working for me, but I know from some others I have talked to they have GRUB and it is not seeing Vista....I haven't had a chance to mess around with GRUB and Vista, but just wanted to post and say thanks for tips for using windows bootloader....

---

