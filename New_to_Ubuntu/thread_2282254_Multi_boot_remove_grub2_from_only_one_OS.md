---
title: "Multi boot remove grub2 from only one OS"
date: 2015-06-12
forum: New to Ubuntu
---

### Post by crip720 on 2015-06-12
I have a multi-boot setup, mainly Ubuntu and Ubuntu types, and when I install an OS I let it do what it wants.  I would like to remove/uninstall grub2 from the Linux Lite partition because it tends to add every kernal under the sun to grub. this happens during install and grub2 updates.  I use boot repair so I can see what OS I want boot into.  I only want to remove grub from Linux Lite, not the OS it self,and use grub2 on the other OSs to boot from.  Can I do this safely and permanently?  I am thinking of using synpathic in Linux Lite or something else.  Thank you, Colin.

---

### Post by Bashing-om on 2015-06-12
crip720; Hello;

There can be but one controlling boot authority; and to make sure that the authority I want maintains that control I turn off 30_os-prober -from within - all other installs.
```

sudo chmod -x /etc/grub.d/30_os-prober

```

Re-install grub for the primary, 
In the primary install run:
```

sudo update-grub

```
That will pick up the other installs for the primary grub boot menu and will not have a recursive effect .

[INDENT][INDENT]recursivness, at an end
 [/INDENT][/INDENT]

---

### Post by crip720 on 2015-06-12
Thank you for your answer, just to be sure, the code you gave is copy and paste, no changes due to my setup? [-x]  If so I will boot into Linux Lite and do it.  Linux Lite12.04 seems like a nice OS, but it's grub makes a mess that I do not like to update it.  Colin.

---

### Post by Bashing-om on 2015-06-13
crip720; Yepper;

You have the right of it, just copy and paste from within the install that you want to remove the e(x)acutable bit.
What I do suggest is after disabling 30_os-prober in linux light, that now you (re-install) A new grub - this new grub will not have other systems in it.
THEN reinstall grub in ubuntu and there will be no doubling up of boot code. IF you should have more than the 2 operating systems installed I do recommend that 30_os-proper only be enabled in that primary system ubuntu.
Once grubs are straight then in the primary operating system pick up and chainload those other systems:
```

sudo update-grub

```


[INDENT]it's a thing
[INDENT][INDENT][INDENT]but it is only a thing
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bucky Ball on 2015-06-13
I don't know if it is compatible with Linux Lite, or if any of the advice here is as Linux Lite is based on the Ubuntu kernel but it is not Ubuntu or officially supported here so no idea about the differences, but you could also use [Grub Customizer]("http://ubuntuhandbook.org/index.php/2014/04/install-grub-customizer-ubuntu-1404/") to customise what you see in your grub screen at boot.

---

### Post by crip720 on 2015-06-13
Thank you Bashing-om, I am on Linux lite now and did what you said.  Linux Lite has been updated and rebooted and grub is looking good.  I do not know what Linux Lite does to grub, since I have tried quite a few other Linux OSs and they did only added the new OS with the names of the older OSs.  Linux Lite seems to list at lease three very long lines for each kernel, and I had trouble trying to boot any of them, except for the first line for Linux Lite and the Windows line.  This seems to be solved.  Colin.

---

### Post by Bashing-om on 2015-06-13
crip720; Great !

Pleased that worked it out for you. I too multi-boot and it took the longest for this to penetrate my thick skull. Recursion in the booting of /boot/grub/cfg(s). Stop the secondary operating systems from probing others and only the primary listing all the other systems .

[INDENT][INDENT]works for my use-case
[/INDENT][/INDENT]

---

