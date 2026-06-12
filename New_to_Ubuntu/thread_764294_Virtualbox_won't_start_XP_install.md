---
title: "Virtualbox won't start XP install"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by ecs_pf5 on 2008-04-23
Installed Virtualbox on Kubuntu via Adept, went fine.

Setup an XP VM with 512Mb ram &10gb dynamic disk, that went ok.

Inserted XP install disk, clicked 'finish', and instead of proceeding with XP install, it gave me:

> 

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel and execute '/etc/init.d/vboxdrv start' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}


How do I install the virtualbox-ose-modules package for my kernel (and how can I identify my kernel, I installed Kubuntu about 3 months (?) ago but didn't write down the exact details :mad:

[edit] on reflection my sig probably does have the correct details for my current install.

Thanks for any suggestions.

---

### Post by rlogan on 2008-04-23
Hi

I had the same issue when I first attempted using VirtualBox. What I found that when I checked Synaptic to see if the OSE module was installed was that it was. So check this out first, presuming that this is fine then jump to the next bit.

Now you have to make sure that your user is part of the vboxusers group, check this via System -> Admin -> Users and Groups. You may need to enter you password at this point or hit the unlock button if running Hardy Heron. Then click on the vboxusers group and make sure your user has the checkbox selected.

If you have upgraded to Hardy and its stopped working, make sure you have the correct ose modules loaded for your current kernel. I had this one last night when I went to boot XP VM.

My kernel version is listed on the grub menu, well I am sure theres another way, but that works for me 

Hope this helps

Cheers

---

### Post by ecs_pf5 on 2008-04-23
Couldn't figure out how to tell if virtualbox-ose-modules was installed because I couldn't find Synaptic on Kubuntu.. the Add/Remove (Adept?) that I could find, doesn't seem quite as comprehensive as Synaptic at showing what's installed.

So I went ahead anyway & tried 

```

sudo /etc/init.d/vboxdrv start

```

That worked.. so I guess I must have the ose things.

I found I could add myself into the vboxusers group in Kubuntu using System Settings > User Management, thanks for that tip, that seemed to be the final thing needed.

XP's now installing. I wanted it like this so I could finally dispense with my Microsoft partition yet still have the capability to run the odd Windows app - I'd found Wine not well suited for some of the few Windows apps I still need to run.

Many thanks :)

---

### Post by rlogan on 2008-04-23
Sorry didn't pick up on the Kubuntu bit, I know when I installed VB initially it did install the ose by default.

Good to see its heading in the right direction, just watch when you do the upgrade to Heron as had to upgrade OSE module. Just one to remember !!

I tried Wine briefly, but I still have dula boot on both machines.

All the best

---

