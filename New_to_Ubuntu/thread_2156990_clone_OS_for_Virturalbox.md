---
title: "clone OS for Virturalbox"
date: 2013-06-23
forum: New to Ubuntu
---

### Post by crip720 on 2013-06-23
I am trying to get a friend to try Lubuntu[or Ubuntu] on a older computer[6yrs].  She is using XP right now, with a accounting program.  I know you can load an OS iso in to virturalbox[like XP], but I was wondering if you could clone/copy  your OS[ if not to big] that you are using now into Virturalbox or similar program.  This would be manily to saved the work of redoing the accounting program data.  Thank you.  Colin.

---

### Post by dshgna on 2013-06-24
Hi!

So, what you want is to get the current operating system to run on Virtualbox, am I right?

I'm not an expert, but just for my two cents ... What you need is to create an image of your current working system.

1. First you need to boot from a separate partition than the one currently in use. You could use a bootable Linux live usb/cd for this. 
2. Then from the new bootable medium, use a program like Clonezilla to create an ISO image of the system.[http://clonezilla.org/](http://clonezilla.org/)
3. This ISO image can be used in Virtualbox.

Hope this helps or you come up with an even better solution! I remember reading about a method to boot up a physical hard drive through virtualbox but unfortunately I can't seem to find the link. But I think that you don't want the existing system anymore, so creating an iso file would be the solution.

Cheers!

---

### Post by cub on 2013-06-24
As much as I urge people to switch to GNU/linux I must ask why you want to change the OS on her computer? Is something not working or missing? Otherwise, why not leave it alone since it might be tricky to get the accounting program to work?

---

### Post by monkeybrain2012 on 2013-06-24
No sure if you can clone and existence Windows installation and run in on VB. Isn't VB considered  a different machine and installing Windows on a different machine would require a new license from my understanding.

---

### Post by crip720 on 2013-06-24
She is using Windows XP right now, that will become unsupported next year.  So she should upgrade to another OS.

---

### Post by crip720 on 2013-06-24
Thanks dshgna, will look in to it.

---

### Post by monkeybrain2012 on 2013-06-24
> **cub said:**
> As much as I urge people to switch to GNU/linux I must ask why you want to change the OS on her computer? Is something not working or missing? Otherwise, why not leave it alone since it might be tricky to get the accounting program to work?

I suppose OP would test the VM first before wiping Windows. :) But even in the worst case scenario where he wipes Windows then finds out VM doesn't work she can still restore the image to the original machine.

@OP, if she tries to run the clone in vm she has to re-activate Windows, that can be tricky depending on her license, You may want to look at this

[http://techblog.tv/virtualbox-clone-windows-activation/](http://techblog.tv/virtualbox-clone-windows-activation/)

Also the accounting software may stop working because of change of hardware. Some expensive proprietary software requires a new license for a different machine configuration, sometimes changing the partition of your hard drive is enough to make them stop working.

---

