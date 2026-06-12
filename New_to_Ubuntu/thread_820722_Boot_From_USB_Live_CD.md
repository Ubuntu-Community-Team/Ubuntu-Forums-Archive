---
title: "Boot From USB Live CD?"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by yurikoster1 on 2008-06-06
Hello all,
This is my 1st post and i hope it's in the right place, if not i apologize and ask that it be moved to an appropriate location.

i have installed ubuntu on a USB HD and have been running it succefully on several computers. unfortunately my computer at home does not have USB boot support on bios, so i searched extensively and found this 

[https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)

which i don't fully comprehend. i was wandering if there was an easy way to do this on hardy with UCK (ubuntu customization kit) [http://uck.sourceforge.net/](http://uck.sourceforge.net/)

also i was wandering if the persistent mode was fixed on the livecd iso we can download from ubuntu official site, and if i can also add the persisten mode option to my custom live cd with usb boot support.

thanks in advance,

Yuri Koster

---

### Post by Hospadar on 2008-06-06
I think you can achieve what you want to do with a grub boot floppy or cd and follow the directions on the page you linked (the "Booting Via Grub" section)

I've never actuall done this, but I think the super grub disk will let you do what you need to do here
[http://www.supergrubdisk.org/index.php?pid=5](http://www.supergrubdisk.org/index.php?pid=5)

Try burning yourself a copy and pop it in and see what happens.

Let us know if it dies horribly or is totally the wrong thing

---

### Post by yurikoster1 on 2008-06-06
thank u for your help

I tried using the super grub disk , but no luck. i tried every option available in the cd (many many options :P) but it was unable to boot from my USB HD. since the super grub website seems to be offline, i can't help but wonder is there any "special" thing i must do to make super grub boot my USB HD?

i am going to try the link in my previous message again and c if it works ill keep posting my results

---

### Post by adrian15 on 2008-06-10
> **yurikoster1 said:**
> i tried every option available in the cd (many many options :P) but it was unable to boot from my USB HD. since the super grub website seems to be offline, i can't help but wonder is there any "special" thing i must do to make super grub boot my USB HD?


I have managed to bring Super Grub Disk site back to life.
Here there is the [Super Grub Disk wiki page about usb boot](http://www.supergrubdisk.org/wiki/USB_Boot).

adrian15

---

