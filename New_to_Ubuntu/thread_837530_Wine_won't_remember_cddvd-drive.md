---
title: "Wine won't remember cd/dvd-drive"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by tstack77 on 2008-06-22
I just installed imgburn and got the error 'No devices detected'. I opened up wine configuration-->drives, and noticed that no cdrom drive was detected under Drive Mapping. Auto detect found the drive, I clicked Apply, but when I opened up imgburn again the problem remained.

I went back into wine config and the drive was gone again!?

I autodetected the drive again then went into the advanced tab. I cannot select 'Autodetect from Device' because the selection below was grayed out. In 'Manually Assign' the label displays as Drive D, but I have no idea what to put under Serial (displays 0).

Any ideas?

---

### Post by uclalinux on 2008-06-22
I am not sure, maybe you are doing it wrong. Wine can be tricky

But what is this ImgBurn Software?  

For burning CD,DVD, and .iso I would recommend **K3B** it is very easy to use

For making a iso i would use the **DD command** (it is one of the most powerful commands i think Linux has, and it is what made me switch to the Linux operating system for good) You can read about the dd command here, ([http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/))

If copying and burning DVD movies is what your looking for then I get a program called **K9copy**, it will that the 8 GB dvd movie and compress it to 4.3GB so that it can be burnt to a normal dvd 

All of these programs can be found in the synaptic package manager

---

### Post by cariboo on 2008-06-22
For those the are terminal challenged here is a link to Linux Man Pages:

[http://www.linuxmanpages.com/](http://www.linuxmanpages.com/)

Jim

---

### Post by tstack77 on 2008-06-22
Imgburn is a great piece of software which unfortunately has no linux equal. If there is something else that I can do in wine, please help me out with a check list to get the cdrom drive recognized automatically.

Jim, I'm not sure what I'm to do with the linuxmanpages. How does your site have anything to do with my cdrom problem in wine?

---

### Post by tstack77 on 2008-06-23
Bump

---

### Post by mc4man on 2008-06-24
what version of wine are you using?
just saw in a thread where the same thing was happening about the auto detect. I was going to suggest upgrading the ver., but the issue was 'resolved' (he was using 0.9.59)
ck. here and post back - anyone you wants to use imgburn certainly should get chance
[http://ubuntuforums.org/showthread.php?p=5246038#post5246038](http://ubuntuforums.org/showthread.php?p=5246038#post5246038)

---

