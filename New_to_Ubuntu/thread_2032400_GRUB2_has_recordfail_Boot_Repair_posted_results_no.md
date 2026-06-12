---
title: "GRUB2 has recordfail Boot Repair posted results noob needs help"
date: 2012-07-23
forum: New to Ubuntu
---

### Post by dynosis on 2012-07-23
i tried a lot of places did a lot of suggestions i am at wits end.
i managed to get boot repair please see output . any help greatly appreciated.
go to: [http://paste.ubuntu.com/1107467/](http://paste.ubuntu.com/1107467/).
thanks again

---

### Post by G4dget on 2012-07-23
Maybe I'm noob enough to not fully understand what your problem is. Knowing what Grub isn't doing may be helpful. Are you able to boot into any of the OS that you have by either grub or pointing your bios to a different hard drive to load from?

---

### Post by dynosis on 2012-07-23
yeah sorry grub2 is not booting updated kernel i.e 3.2.0.27

but am able to boot into previous versions i.e. 3.2.0.26

 thank s for your time 
did you check out the pastebin for further info

---

### Post by G4dget on 2012-07-23
Yes I did look at the pastebin but now knowing the problem didn't know what to look for. My guess is it is more of an issue with kernel 3.0.0.27 and not grub but I could be wrong. 

Someone had suggested I try Boot-Repair ([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)) but i got my issue fixed with needing it and don't know if it will help in your situation. 

Is 3.0.0-27 the only thing that fails to load?

---

### Post by dynosis on 2012-07-23
yes i tried boot repair several times
thanks for for suggestions i really don't want to reinstall again

p.s. do you believe the guy above ( [muthietbinh11a]("http://ubuntuforums.org/member.php?u=1706678")) trying to spam he should be banned, he's gone now
i am leaving too tried will try again tomorrow

---

### Post by NikTh on 2012-07-23
Hi , 
big mess my friend. Big mess. I hope someone with a lot of experience could help you for now , but even correct your problem (for now) you will face similar situation in future.. (IMO)

In pastebin , i can see.. Custom kernel (3.3.4) , "one million" entries , and of course menu.lst  that leads to grub legacy. 
Also i can see Neonsmart technologies.. did you mattered something from within windows ? Did you installed a  program called EasyBCD  and played with entries ? 

You can test something .. 
boot from ubuntu working kernel .. 3.2.0-26 and open a terminal.. do this
```
sudo update-initramfs -c -v -k 3.2.0-27-generic
```and give the results here. 
**Put the results inside [CODE] tags , by highlighting the text and click # symbol on top of message pane.**
Thanks

---

### Post by oldfred on 2012-07-24
Post info suggested by NikTh. Did you have any upgrade errors? Does the install have to incorporate proprietary video drivers, or if you manually installed a kernel did you incorporate the proprietary video driver (I do not know how.)?

To keep things straight and make it a bit more reliable, I like to have the boot loader on the same drive as the install. Then it another drive fails it does not prevent booting or if boot drive fails, the boot from another drive should work.

You also have flexnet. This is used by Windows software to implement DRM. It used to interfer with grub2, but grub created a work around. But if you have multiple drives, best to keep Windows boot loader in the drive with flexnet to avoid issues.
> Sector 53 is already in use by FlexNetYou may want to house clean some older kernels and clean up boot menus. I like to keep one older kernel but delete all the others. I also turn off os-prober and use my own entries in 40_custom to limit number to entries. And/or chainload to another grub legacy installed to a partition.

I do not know about Neosmarts EasyBCD.

HOWTO: Grub Customizer Updated for grub 1.99
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)
[http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html](http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html)
The Grub 2 Guide - drs305 also link to grub customizer
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober

I copy only the entries I want into 40_custom.

gksudo gedit /etc/grub.d/40_custom
Then do:
sudo update-grub

---

### Post by dynosis on 2012-07-24
i got so fustrated i deleted all my os's. I want to know how to remove all grub2 instances,so when i do a fresh install ,no more problems. but i don't know to remove all these diff instances all over of grub2 being on every disk. i was doing a fresh install of 12.04 and rifht then there was a prob with grub2 please help thank you

---

### Post by Bufeu on 2012-07-24
> **dynosis said:**
> i got so fustrated i deleted all my os's. I want to know how to remove all grub2 instances,so when i do a fresh install ,no more problems. but i don't know to remove all these diff instances all over of grub2 being on every disk. i was doing a fresh install of 12.04 and rifht then there was a prob with grub2 please help thank youYou might fins this interesting: [http://forums.fedoraforum.org/showthread.php?t=271243](http://forums.fedoraforum.org/showthread.php?t=271243).

---

### Post by oldfred on 2012-07-24
You do not normally delete the MBR, but just install the new version you want. MBR should have something in it to boot from

You can use your Boot_repair to install a Windows like boot loader to the Windows drive and it will let you choose what to install where.

---

### Post by dynosis on 2012-07-24
thank you very much for your assistance.
i like ubuntu or for that fact linux, you learn something everyday. even if it gets me fustrated.

---

