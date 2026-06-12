---
title: "Install Troubles"
date: 2012-04-07
forum: New to Ubuntu
---

### Post by Hacked N Nacked on 2012-04-07
Hi well my problem is... I installed 1104 and 10 04
in dual boot after rebooting there was four different boot options just for the older ubuntu
two are recovery I should only have one 
and now in disk info it says there is a 700mb whole disk USB device auto mounting at/root it won't let me delete it or format it and after rebooting again there is also zram dsk 0 running as solid state disk speed So how do I remove this hacker/dodgy two drives. Any help most grateful thanks. Even After formatimg full drive it still there I think advanced Linux user has took over my comp how IF possible can I delete them ?
THANKS

---

### Post by Bucky Ball on 2012-04-07
Four is correct. Always keep the kernel (and recovery) of the last working kernel in case you can't get into the one you're using (update kills it, tweaking breaks it). You can then choose the previous kernel to get in and fix the problem (hopefully). 

Thus, if you have 10.04 and 11.04 you would have eight; the current 10.04 and the previous working (or not) kernel and same for 11.04.

You can omit these from the list with Grub Customizer, a handy little app:

[http://www.webupd8.org/2010/10/grub-customizer-lets-you-reorder-add-or.html](http://www.webupd8.org/2010/10/grub-customizer-lets-you-reorder-add-or.html)

You can then hide the previous kernels (but they are still there if you need to boot to one).

---

### Post by Hacked N Nacked on 2012-04-07
Thanks for quick reply !
But I mean 1 kernal 1 recovery for 1104 and two kernals and two recovery for 1004
also do u no anything about those iffy USB\firewire drives SSD 288mb, and
700Mb the other it says I don't own them so can't format or delete them
Thanks again!

---

### Post by Bucky Ball on 2012-04-07
Your second question should be asked in a new thread. 

I presume you had 10.04 installed first and it has had a kernel update since. What you have is correct. I presume you then installed 11.04 (recently) and therefore it hasn't had a kernel update and has one entry (one entry would be the kernel and its recovery kernel). Normal.

As suggested, you can hide the unwanted ones with Grub Customizer or by editing the file and placing a hash (#) in front of the kernels you do not want to appear. ;)

PS: I think Ubuntu Tweak can also do this job and that can be found in the repositories (Software Centre or Synaptics).

---

