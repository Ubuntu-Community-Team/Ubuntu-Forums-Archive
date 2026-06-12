---
title: "Ubuntu won't boot anymore"
date: 2014-05-21
forum: New to Ubuntu
---

### Post by evy2 on 2014-05-21
Hi everyone, 

So here's the deal, yesterday I closed my laptop while he was still running as regularly. Today I opened my laptop again and didn't automatically start up again, so I figured my battery was empty.
However, he won't boot anymore and I get a black screen with a whole lot of text and nothing more (see included image, I took a picture of my screen). Please can you help me? 

[https://www.dropbox.com/s/oxtfik5b8hgtl7j/DSC_0177.jpg](https://www.dropbox.com/s/oxtfik5b8hgtl7j/DSC_0177.jpg)

---

### Post by LastDino on 2014-05-21
hmm shot in the dark and not the solution, but can you successfully access/boot it by advanced options from grub menu? It should appear if you hit left shift continuously while booting up.

Also, think back, have you installed/uninstalled anything during last session or updated the system?

---

### Post by evy2 on 2014-05-21
Thanks so much for your reply! 

Nope, it won't boot from the grub menu either.

And I haven't installed/uninstalled anything I can remember. Sometimes I do get a notification for new updates and just click yes, maybe that happened yesterday, but I can't imagine why a simple update would cause that he simply won't boot anymore.

---

### Post by newbie2244 on 2014-05-21
Before any adequate answer can be provided, please specify your system brand and its configuration - e.g., HP, Dell, how much RAM, which drivers, etc. ALso pls specify which version of Ubuntu you have installed and what you use the sysstem for.

---

### Post by Foxy_Land on 2014-05-22
I had (almost the) same problem several weeks ago with 12.04. What I did was I downloaded boot repair disk from [http://sourceforge.net/p/boot-repair-cd/home/Home/](http://sourceforge.net/p/boot-repair-cd/home/Home/) , put it on usb flash disk with unetbootin, boot with the flash disk, and let the repair did its magic.

hope this helps,
Foxy

---

### Post by LastDino on 2014-05-22
> **Foxy_Land said:**
> I had (almost the) same problem several weeks ago with 12.04. What I did was I downloaded boot repair disk from [http://sourceforge.net/p/boot-repair-cd/home/Home/](http://sourceforge.net/p/boot-repair-cd/home/Home/) , put it on usb flash disk with unetbootin, boot with the flash disk, and let the repair did its magic.

hope this helps,
Foxy

+1 to this, try this and lets see if it works for you or not.

---

### Post by evy2 on 2014-05-22
Thanks so much. I'll try this out. By the way, my laptop is a Dell Latitude E6530, Intel Core i5-3360 M CPU @ 2.80GHz, 6GB RAM, 64-bit operating system, with Ubuntu in main partition and unfortunately windows in the little partition

---

### Post by evy2 on 2014-05-22
Unfortunately it didn't work. Everything seemed ok, then I rebooted the system and I still get the same screen

---

### Post by coldcritter64 on 2014-05-22
> **evy2 said:**
> ...**Everything seemed ok,** then I rebooted the system and I still get the same screen

Does that mean you had a successful boot the first go after using the boot repair disc ?

I note the picture you posted is saying "Init tainted", if you can get in after using the repair disc I'd try removing initramfs and then create a new one. I have no real idea if this will work so I'll wait for others to consider the idea before posting any codes. Let us know if I'm reading that quote from your last post correctly and we can go from there.

I really don't know fully the meaning of "Init tainted" but I'm suspecting that somehow your initramfs is corrupted by suspending or hibernating the laptop by closing the lid that way, some laptops do have those sort of problems at times. A couple of update-initramfs commands with the right options one after another _*may possibly*_ help this.

---

