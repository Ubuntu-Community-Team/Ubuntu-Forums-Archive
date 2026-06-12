---
title: "How hard is it to develop a kernel driver?"
date: 2010-11-27
forum: Programming Talk
---

### Post by fallenshadow on 2010-11-27
I am asking how hard because im presuming its gonna be hard. :D

So does anyone know how hard it would be to develop one? Has anyone got experience of developing one here?

If so how much code is involved?

---

### Post by worksofcraft on 2010-11-27
> **fallenshadow said:**
> I am asking how hard because im presuming its gonna be hard. :D

So does anyone know how hard it would be to develop one? Has anyone got experience of developing one here?

If so how much code is involved?

This recent thread about a [character device driver]("http://ubuntuforums.org/showthread.php?t=1575088") shows it's actually quite easy.

---

### Post by fallenshadow on 2010-11-27
Wow looks kinda easy but you would really need to know what you are doing though.

How does a person test their code?

---

### Post by ziekfiguur on 2010-11-27
> **fallenshadow said:**
> 
How does a person test their code?
On a disposable computer? I think you can write output to logfiles.

---

### Post by fallenshadow on 2010-11-28
Ah I don't have a disposable computer... guess I will have to forget about this. :D

---

### Post by eeperson on 2010-11-28
> **fallenshadow said:**
> Ah I don't have a disposable computer... guess I will have to forget about this. :D
You can also use virtual machine.  This doesn't require an extra physical computer.

---

### Post by fallenshadow on 2010-12-05
I don't understand how you could use a virtual machine when you are developing a hardware driver. Surely the virtual machine will just be using its own virtual drivers.

Ok I doubt I would have a chance at developing my own driver but is there any place to go and request the development of one? :D

---

### Post by dwhitney67 on 2010-12-05
> **fallenshadow said:**
> I don't understand how you could use a virtual machine when you are developing a hardware driver. Surely the virtual machine will just be using its own virtual drivers.

:confused:

> **fallenshadow said:**
> 
Ok I doubt I would have a chance at developing my own driver but is there any place to go and request the development of one? :D
Do you have a specialized piece of h/w that you want to connect to your computer?  Or are you just floating your thoughts?

Unless someone does something really dumb, there is no harm in developing a kernel driver and installing it into your current OS.  If the driver does not meet your expectations, then you can remove it.  In the worst case, you would need to reboot your system.

The most basic of kernel drivers is probably one that prints a message to the kernel log when it is loaded, and then another message when it is unloaded.

If you have a particular h/w device that sits on the PCI bus or the USB bus, then of course you will have to put forth more effort to detect, and then access the registers/memory on that device.  The main question is whether you would know how to do this?  If not, then I would suggest that you study other kernel drivers, and in during the course of your studies, attempt to develop your own that performs the basics (ie logging to the kernel log).

---

### Post by fallenshadow on 2010-12-06
Well my problem is I have a disk drive, which should work for everything up as far as DVD-RW disks.

However it seems it can only work with CD-R and CD-RW disks. Im thinking if I could just look at a disk driver that supports DVD-Rs and DVD-RWs I could take some of that code and implement it into the current driver for my disk drive.

Ive been using Ubuntu for about 3 years and still I can't burn a DVD!! I would hope I could just ask some kernel dudes to sort this out but sometimes if you wanna get something done you have to do it yourself!

Can somebody confirm or deny if its possible to do testing in a virtual machine?

---

### Post by dwhitney67 on 2010-12-06
For that case, of course you can use a virtual machine.  But at the same token, there's no reason why you should be able to use your host OS too.

You've indicated that you have a DVD-RW drive; is that what is stated on the drive itself?  Typically the logo is present on the drive's faceplate.

Also, what drive do you have, and what driver is being loaded for such?  What tool(s) have you attempted to use to write a DVD image to the drive?

These are all questions you should answer before flinging yourself into the direction of developing a kernel driver.  I suspect that you are not the only person in the world with the same optical drive that is running some variant of Linux.

---

### Post by fallenshadow on 2010-12-06
My disk drive is:

LG - DVD-RAM GSA-H20L

Hardware supported types: (as listed by cnet.com)

DVD+R , DVD+RW , DVD-RAM , DVD+R DL , DVD-R DL , DVD-R , CD-RW , CD-R , DVD-RW , CD-ROM , DVD-ROM

Obviously somebody else out there would have the same drive but its still a pretty exotic drive.

I can't attempt to burn an image to the disc or anything because the disc isn't even recognized.

How do I know what driver is being loaded?

---

