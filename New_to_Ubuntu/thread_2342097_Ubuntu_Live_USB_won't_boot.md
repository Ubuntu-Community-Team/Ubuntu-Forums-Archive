---
title: "Ubuntu Live USB won't boot"
date: 2016-11-03
forum: New to Ubuntu
---

### Post by sashko.taylor on 2016-11-03
Hello to the community.

I am trying to install Ubuntu 16.04 LTS on my home desktop. 
I created a Live USB stick (formatted in FAT32), changed the boot priority to USB, but the computer just won't progress with booting from it. 
There are no boot logo or text nor any mistake messages.

I tried 2 different USB sticks, same thing. When trying them on another computer, they boot alright and allow to try 16.04 before installing it.
I also tried inserting a hard drive with Ubuntu 14.04 installed, and it works perfectly well.

Seems like this computer just refuses to boot from USB (but some time ago this was possible, I can remember). Any advice?

---

### Post by RobGoss on 2016-11-04
Hello and welcome,  Have you try changing to a different USB port? there might be something wrong with the one you're trying to boot from

I'm not sure how old this machine is your using but some older machines may not recognized the USB drive I know you mentioned it use to boot from it so I'm wondering why not now

You may also want to try booting from a DVD and see if it will boot

---

### Post by sashko.taylor on 2016-11-04
Yes, the USB ports are fine, I tried several of them. Moreover, the computer sees the USB drive(s), but won't boot from them. 
The hardware is not too old, it's from about 2012.

I think I will try booting from a DVD, once I get a chance to burn one. 
Still, now I am challenged to find a reason why it won't boot from a USB drive, while **it should**.:)

---

### Post by Geoffrey_Arndt on 2016-11-04
Are you running a dual-boot . . . with a version of Windows that has secure boot turned on?

If that's not the case, use a better usb flash-stick tool such as etcher:   [https://etcher.io/](https://etcher.io/)

---

### Post by RobGoss on 2016-11-04
> **sashko.taylor said:**
> Yes, the USB ports are fine, I tried several of them. Moreover, the computer sees the USB drive(s), but won't boot from them. 
The hardware is not too old, it's from about 2012.

I think I will try booting from a DVD, once I get a chance to burn one. 
Still, now I am challenged to find a reason why it won't boot from a USB drive, while **it should**.:)

I think it would help if you provided the specs for your machine like **Brand**, **Ram**, **Processor**, **Motherboard **and so on maybe we can figure out why it's not recognizing your USB stick

How old is this machine?

---

### Post by Geoffrey_Arndt on 2016-11-04
Yes - good advice from Rob . . !  But I suspect it's the usb creation tool.   Have had best results from Etcher . . . worth a try . . . let us know yea/nay.

---

### Post by RobGoss on 2016-11-04
Geoffrey_Arndt I've never used that tool but as you suggested might be a good idea to gave it a try. Personally I think it's something not correct in the BIOS

---

### Post by Geoffrey_Arndt on 2016-11-05
Yea Rob,  I think you're right.   On some systems, the uefi/bios or legacy/bios can be hard to manipulate so usb boot is supported.   often it's more than re-arranging boot device order.   These systems often have hidden menus/screens . . like going down a rabbit hole with multiple tunnels and chambers.   Too bad a bios hasn't been implemented that makes use of a mind map structure - fully decomposed so you can see the whole thing.

---

### Post by sashko.taylor on 2016-11-05
> **Geoffrey_Arndt said:**
>  use a better usb flash-stick tool such as etcher:   [https://etcher.io/](https://etcher.io/)

Etcher worked perfectly fine. 
Before, I tried creating the USB with Rufus and Unetbootin, both failed. But Etcher did the job.

Thanks Geoffrey_Arndt and RobGoss.

---

### Post by RobGoss on 2016-11-05
Your very welcome glad you resolved your issue if you don't mind can you mark this thread as solved, you can do this by using the **Thread Tool** at the top of this post.

Thanks so much

---

### Post by g33zr on 2016-11-27
@ Geoffrey_Arndt: Many thanks for suggesting Etcher. I'm not a Unetbootin fan and wanted something more reliable to install Linux distros on my old iMac test machine. (I previously burned the iso images to DVDs, but the CD/DVD drive bit the dust.) Etcher is the best usb tool I've used yet. However, I'm surprised that it's not included in Synaptic Package Manager or Ubuntu Software whereas Unetbootin is.

---

### Post by Geoffrey_Arndt on 2016-11-28
Isn't the Sable an awesome machine?   I love it . . . er . . . I should say my wife loves it (it's become her PC! . . . ).

Re Etcher, it's pretty new.    It is open-source and available via GitHub . . . (Apache License).

---

