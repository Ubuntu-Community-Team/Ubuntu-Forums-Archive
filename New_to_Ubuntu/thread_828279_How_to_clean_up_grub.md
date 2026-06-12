---
title: "How to clean up grub"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by Julian Lewis on 2008-06-13
Hi,
  I have noticed that each new kernel installation causes another entry in the list grub presents at boot up time.
I have a couple of questions ...

1) Does this mean that my disc is cluttered up with old kernel related zombies I no longer need ?

2) Is there some inbuilt feature that keeps a limited number of past updates or can this list grow indefinably.
(Although I hardly ever need MSWindows anymore, it would be nice, if on the occasions when I can't avoid using it, that I don't haver to scroll over a pile of zombies to use it). Hence how can I clean up without seriously risking breaking grub and no longer being able to boot)

I found this ...

[http://www.go2linux.org/clean-linux-kernel-images-grub-menu](http://www.go2linux.org/clean-linux-kernel-images-grub-menu)

I also found this ...

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

but it looks like cleaning up grub is a very risky process. 

Is there an easy safe way ?

Cheer Julian

---

### Post by drs305 on 2008-06-13
I think this will answer your questions (and more). There is very little risk in using StartUp-Manager, which is described in the link below.

[HOWTO: Grub Menu Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by gr4nf on 2008-06-13
As long as you make a backup, it can't be very dangerous.

---

### Post by Hospadar on 2008-06-13
Howdy, I believe if you just uninstall the old kernels in synaptic they will automatically remove themselves from the boot menu (if they don't, you can always just edit you /boot/grub/menu.lst file and remove them manually, after making a backup of course)

Just be sure you don't remove the most recent linux kernel (cause it's sort of important =P)  If you search by name in synaptic for "linux" they'll be the linux-image-<bunch o' #'s>-generic packages (or something like that).  When you mark them for uninstallation, it will also mark any old kernel header and extension packages you have installed, which is ok.  Again, just make sure you arn't removing the most recent kernel, so take a look at the grub menu when you boot up, right down the number of the one you are booting into, and don't remove that one.

---

### Post by ukripper on 2008-06-13
> **Julian Lewis said:**
> Hi,
  I have noticed that each new kernel installation causes another entry in the list grub presents at boot up time.
I have a couple of questions ...

1) Does this mean that my disc is cluttered up with old kernel related zombies I no longer need ?

2) Is there some inbuilt feature that keeps a limited number of past updates or can this list grow indefinably.
(Although I hardly ever need MSWindows anymore, it would be nice, if on the occasions when I can't avoid using it, that I don't haver to scroll over a pile of zombies to use it). Hence how can I clean up without seriously risking breaking grub and no longer being able to boot)

I found this ...

[http://www.go2linux.org/clean-linux-kernel-images-grub-menu](http://www.go2linux.org/clean-linux-kernel-images-grub-menu)

I also found this ...

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

but it looks like cleaning up grub is a very risky process. 

Is there an easy safe way ?

Cheer Julian

easiest way to remove zombie kernels is go to 
system-->administration-->synaptic package manager
search for linux-image 
and find kernel images you dont need and mark for removal.

and then go to terminal and type:
```
sudo update-grub
```
this will update your grub with remaining entries.


Alternate method , you can amend an option in grub menu.lst
```
#howmany=all
```
change this to 
> #howmany=3

save and exit 

then do ```
sudo update-grub
```
reboot
depending on how many kernels you need listed in your grub menu.

---

### Post by kansasnoob on 2008-06-13
Using startupmanager is very simple and totally safe and it can just be installed from synaptic.

---

### Post by Mentem on 2008-06-13
I'll give another vote for startup-manager.

---

### Post by Julian Lewis on 2008-06-13
> **drs305 said:**
> I think this will answer your questions (and more). There is very little risk in using StartUp-Manager, which is described in the link below.

[HOWTO: Grub Menu Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")

Thanks for that, I installed startup manager, and set it to keep 2 kernel versions as recommended. That worked a treat. I will keep 3 kernels on my system just in case. (Anyway disk space is cheap these days, and a kernel isn't eating much space.)
Cheers Julian

---

### Post by Smbrandes on 2008-07-16
Removing three prior kernals gaine almost 400mb of space. That is certainly not inconsequential.

---

