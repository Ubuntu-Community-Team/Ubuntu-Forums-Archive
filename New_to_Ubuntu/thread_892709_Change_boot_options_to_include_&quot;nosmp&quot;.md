---
title: "Change boot options to include &quot;nosmp&quot;?"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by Tibco on 2008-08-17
> Supposedly adding "nosmp" as a boot option, disabling Sync To Vblank in Beryl, and if you edit the /etc/default/acpi-support and set POST_VIDEO=false, suspend and hibernate
should work better.
Iam having some trouble with my suspend, and i checked a dv9000 thread, which is related to my laptop and found this advice. I have diabled vblank, and set post_video to false, can someone tell me how to set "nosmp" as a boot option?

---

### Post by Tibco on 2008-08-17
can some help me? it seems a simple enough question...

---

### Post by nicedude on 2008-08-17
The boot option you are asking about is simply nosmp added to boot parameters, you could also try noapic to turn off some power management that sometimes screws up boot, I have to do this as well as tap the power key at a certain point it stops to get my laptop to boot the live CD. But after install everything is OK so I wouldn't worry much you will just have to struggle through the install.

hope this helps

---

### Post by Tibco on 2008-08-17
> **nicedude said:**
> The boot option you are asking about is simply nosmp added to boot parameters, you could also try noapic to turn off some power management that sometimes screws up boot, I have to do this as well as tap the power key at a certain point it stops to get my laptop to boot the live CD. But after install everything is OK so I wouldn't worry much you will just have to struggle through the install.

hope this helps

Can you tell me _how _to add nosmp to the boot parameters in a step by step please? like do i have do edit grub? what do i have to *do*?

---

### Post by carandraug on 2008-08-17
I think you have to do it in the file /boot/grub/menu.lst

Search for the line you use to boot (probably the first after ## ## End Default Options ##). Look for something that look like this
```
## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-15-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-15-generic root=UUID=c1d433db-a62a-4321-83bd-32a7e26410b0 ro quiet splash
initrd          /boot/initrd.img-2.6.22-15-generic
quiet

``` and add the option at the end of the line that starts with "kernel"

---

### Post by Tibco on 2008-08-17
> **carandraug said:**
> I think you have to do it in the file /boot/grub/menu.lst

Search for the line you use to boot (probably the first after ## ## End Default Options ##). Look for something that look like this
```
## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-15-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-15-generic root=UUID=c1d433db-a62a-4321-83bd-32a7e26410b0 ro quiet splash
initrd          /boot/initrd.img-2.6.22-15-generic
quiet

``` and add the option at the end of the line that starts with "kernel"

Hmm when i did that, grub let ubuntu go to the splash screen but the loading bar just went back and forth and didn't actually start to load. So i used a diff kernel to get back in and change it back to normal, if anyone is interested in the instructions im following, go here: [http://ubuntuforums.org/showthread.php?t=512059](http://ubuntuforums.org/showthread.php?t=512059)
press cntrl+f and then type suspend and it should be right under there.

---

