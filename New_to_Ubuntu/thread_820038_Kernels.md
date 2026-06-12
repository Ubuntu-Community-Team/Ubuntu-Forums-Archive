---
title: "Kernels"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by Terrigal on 2008-06-05
Hear is my problem.  When installing Ubuntu I had three goes before I could get 7.1 up and running. Now on my boot menu I have a clutter of kernels to choose from.  (I also have xp installed)I would like to clean up mu Boot Menu. I have read from other posts that it can be done with Synaptic. Here I can see "remove unwanted boot options". How do I know that I am not removing the ubuntu that I have open?  Does this make sense
James

---

### Post by bumanie on 2008-06-05
Rather than removing the kernels, it is preferable to keep them in case you need them one day, ie if an update makes your computer unbootable, you can then boot from an old kernel. You can 'uncomment' them in /boot/grub/menu.lst so that they don't appear on the start-up list.
> sudo gedit /boot/grub/menu.lst find the kernels you don't want listed and  place a # in front of the entries pertaining to that kernel version.

---

### Post by drs305 on 2008-06-05
Here is a newbie guide for what you might like to know about the kernel display. Options range from very simple to a bit harder. I wrote it yesterday ;-)

[HOWTO: Grub Menu Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by Promaster91 on 2008-06-05
If you want to remove any old kernels and save some space on your hard drive, go to Synaptic Package Manger and search for linux-generic. There you can remove any old kernels that are not needed. Watch out that you don't remove the kernel that you are currently using!! The grub boot loader will automatically update to the changes made.

---

