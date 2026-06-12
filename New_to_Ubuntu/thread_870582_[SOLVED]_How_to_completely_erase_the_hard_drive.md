---
title: "[SOLVED] How to completely erase the hard drive"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by mczonie on 2008-07-26
I recently installed Ubuntu and have been having some problems, so I want to completely erase my hard drive and start over. I read somewhere else that I can do this by opening a terminal and entering 

```
# shred -vfz -n 100 /dev/hda
```

Is this correct?

---

### Post by arpanaut on 2008-07-26
[http://www.dban.org/](http://www.dban.org/)

---

### Post by Tim Sharitt on 2008-07-26
First, I don't know about that command so I won't comment on it. However, if you are reinstalling, the partitioner in the installer should have an option to erase the entire disk and start with a new partition layout.

---

### Post by rzrgenesys187 on 2008-07-26
If you don't want it securely erased you can just reformat the drive during a new Ubuntu or Windows installation otherwise the method arpanaut suggeted sounds good, in fact I downloaded that earlier today

---

### Post by mczonie on 2008-07-26
> **Tim Sharitt said:**
> However, if you are reinstalling, the partitioner in the installer should have an option to erase the entire disk and start with a new partition layout.

How do I reinstall? Just put the CD in and then restart the computer?

---

### Post by wrtpeeps on 2008-07-26
> **mczonie said:**
> How do I reinstall? Just put the CD in and then restart the computer?

Yea.

The exact same thing you did to install the first time.

---

### Post by mczonie on 2008-07-26
> **wrtpeeps said:**
> Yea.

The exact same thing you did to install the first time.

OK, thanks.

---

### Post by mbsullivan on 2008-07-26
> # shred -vfz -n 100 /dev/hda

First off, you'd better be running from a CD or other harddrive (don't try to nuke the drive you're running from).

Other than that, this will work fine if you're prepared to wait 200 years for it to finish. Shred overwrites data with random bits, which are taken from the very slow /dev/urandom device.

If you don't need the erase to be super secure, you could always just replace the entire device with zeros:

```
dd if=/dev/zero of=/dev/sda bs=4k conv=notrunc
```

If you want to make sure:

```
dd if=/dev/sda | hexdump -C | grep [^00]
```

I don't see anything wrong with DBAN, either.

> I recently installed Ubuntu and have been having some problems, so I want to completely erase my hard drive and start over

Oh, yeah just put the CD back in and reboot (make sure it's top in BIOS for boot priority)... I thought this was some sort of security issue.

Mike

---

### Post by mczonie on 2008-07-26
> **mbsullivan said:**
> make sure it's top in BIOS for boot priority

How do I do that?

---

### Post by mbsullivan on 2008-07-26
> How do I do that?

Well, if it worked the first time, then it probably already is. 

If you want to check, though, it's different for every machine. In general the procedure goes like this:

(1) Enter the BIOS immediately following reboot.
[INDENT]- The key to press is different on every machine.[/INDENT]
[INDENT]- Typically using [del] or [F1].[/INDENT]
[INDENT]- It should say on your machine's flash screen (look for "BIOS" or "SETUP").[/INDENT]

(2) Find something like "Boot priority" or "startup order" that lists a bunch of devices (floppy disk, CD-ROM drive, Different Harddrives). It may be under a submenu (typically something like "Basic Configuration" or "Peripherals").

(3) Set the CD-ROM drive to be above the harddrive, such that you're not trapped booting to the broken installation when you want to boot to the CD to reinstall Ubuntu.

Mike

---

### Post by rzrgenesys187 on 2008-07-26
> **mczonie said:**
> How do I do that?

When your computer starts up it should give you a screen and somewhere it will say "press * for setup" and possibly "press # for boot selection"

* -> in my case it's F2
# -> in my case it's F12 

In setup go to the boot menu and instructions will tell you how.  In the boot selection menu highlight the cdrom drive and hit enter.  If you've never done this and manged to install before I'm assuming cdrom is set to first priority

P.S. setup menu will change the boot priority for good whereas boot selection is a one time change

---

### Post by mczonie on 2008-07-26
> **rzrgenesys187 said:**
> When your computer starts up it should give you a screen and somewhere it will say "press * for setup" and possibly "press # for boot selection"

* -> in my case it's F2
# -> in my case it's F12 

In setup go to the boot menu and instructions will tell you how.  In the boot selection menu highlight the cdrom drive and hit enter.  If you've never done this and manged to install before I'm assuming cdrom is set to first priority

P.S. setup menu will change the boot priority for good whereas boot selection is a one time change

I was running windows before. When I installed Ubuntu, I just put the CD in and followed the instructions.

---

### Post by mbsullivan on 2008-07-26
> I was running windows before. When I installed Ubuntu, I just put the CD in and followed the instructions.

Yeah, that should work again. If it doesn't, then worry about the boot priority. It's not a big deal.

Mike

---

