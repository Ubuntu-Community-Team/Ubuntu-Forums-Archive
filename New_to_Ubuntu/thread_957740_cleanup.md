---
title: "cleanup"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by caymahallesi on 2008-10-24
Hi guys,

I guess, I am the absolute ubuntu user ever. My question; how to cleanup ubuntu?

I have been installing open source programs, doing updates etc. but knowing from microcrash 's winxp pro, we have to delete temp files once and a while. 

Is the ubuntu have the same problem?

thanks

---

### Post by paul101 on 2008-10-24
nope; you dont have to do anything!


edit: if you really must do some clean-up, you could empty your trash can :)

---

### Post by kartoshka on 2008-10-24
If you've been installing and updating through synaptic, then you shouldn't have anything to worry about

---

### Post by northern lights on 2008-10-24
In GNU/Linux /tmp is cleared at every reboot.

Still, some dead files can occur, for instance when removing apps and not removing their now obsolete dependencies.

Run```
sudo apt-get autoremove
```to remove hypothetical (Synaptic, gnome-app-install will clear unused dependencies also) obsolete packages.

Further,```
sudo apt-get autoclean
```clears out the local repository of retrieved package files that can no longer be downloaded, and are largely useless.

---

### Post by caymahallesi on 2008-10-24
Ok, how about this, after all the updates done to my ubuntu box, at the startup menu (durring boot) now I have at least thre different version ubuntu boot option. how do I eliminate older version from that list?

---

### Post by paul101 on 2008-10-24
this is normal :)

---

### Post by northern lights on 2008-10-24
> **caymahallesi said:**
> Ok, how about this, after all the updates done to my ubuntu box, at the startup menu (durring boot) now I have at least thre different version ubuntu boot option. how do I eliminate older version from that list?

> **paul101 said:**
> this is normal :)

This is default.

It makes sense to alter that though.

The versions are not exactly of Ubuntu - a new entry is added to the GRUB menu everytime a more recent version of the Linux kernel is added to the Ubuntu repositories.

It is quite sensible to keep more than one for fallback options in case the newest kernel does somehow not work well with your hardware (most applicable for very recent or very old hardware).

I'd keep two or three.

They can be deleted from the menu by editing */boot/grub/menu.lst*```
gksu gedit /boot/grub/menu.list
```It's pretty much a self-explanatory file. You can manually delete obsolete menu entries as well as set the default number of entries to keep.

This however, just edits the menu, the kernels still reside on your system. The kernel packages are labeled *linux-image-running.number-type* for most hardware, the type is "generic". The current kernel series is 2.6. The most recent kernel in the Ubuntu repositories is *linux-image-2.6.24-21-generic*.

If you for instance want to keep -21, -19 and -18 but have -17 installed also, run ```
sudo apt-get autoremove linux-image-2.6.24-17-generic
```

---

### Post by bodhi.zazen on 2008-10-24
> **caymahallesi said:**
> Ok, how about this, after all the updates done to my ubuntu box, at the startup menu (durring boot) now I have at least thre different version ubuntu boot option. how do I eliminate older version from that list?

Remove the old kernels with apt-get or snyaptic.

See these threads as well :


[http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)

    [http://ubuntuforums.org/showthread.php?&t=140920](http://ubuntuforums.org/showthread.php?&t=140920)

    [http://ubuntu-tutorials.blogspot.com/2007/01/cleaning-up-ubuntu-gnulinux-system.html](http://ubuntu-tutorials.blogspot.com/2007/01/cleaning-up-ubuntu-gnulinux-system.html)

---

