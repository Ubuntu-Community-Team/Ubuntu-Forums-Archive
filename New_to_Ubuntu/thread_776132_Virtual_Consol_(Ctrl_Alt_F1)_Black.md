---
title: "Virtual Consol (Ctrl Alt F1) Black"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by optimusmedia on 2008-04-30
[SOLVED] (new forum won't let me edit the title.)

I am having a small handful of issues with Hardy. All are visual issues, so I want to blame my video card (NVidia GeForce 6150 rev a2).  This worked before upgrading. I'm going to list them as separate posts (or post to open threads that may apply) to avoid confusion.

My problem:  When attempting to switch to Virtual Consol (Ctrl Alt F1) I get a black screen.  It's working - I just can't see.   I can switch back (Ctrl Alt f7) and all is well again.

Info: 
```
lspci | grep VGA
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev a2)
```

[side note: I am sure I am not posting enough info, but as a newb, I'm not sure what commands/results you may need.]

---

### Post by mano cazalet on 2008-04-30
hello

i remember having this issue  with gutsy once.
could you check your /boot/grub/menu.lst 
is there any vga=xxx value at the kernel line?

---

### Post by optimusmedia on 2008-04-30
> **mano cazalet said:**
> could you check your /boot/grub/menu.lst 
is there any vga=xxx value at the kernel line?

Checked. There is none.

---

### Post by mano cazalet on 2008-04-30
now i remember
 in gutsy i had to add vga=792 in the first kernel line just after splash
but if you try this make sure to backup your menu.lst before.

Also found this [thread]("http://ubuntuforums.org/showthread.php?t=585454"), maybe it helps

---

### Post by optimusmedia on 2008-04-30
> **mano cazalet said:**
> now i remember
 in gutsy i had to add vga=792 in the first kernel line just after splash
but if you try this make sure to backup your menu.lst before.

Also found this [thread]("http://ubuntuforums.org/showthread.php?t=585454"), maybe it helps

VGA=792 didn't help, but the link did.  Specifically [this post]("http://ubuntuforums.org/showpost.php?p=4552837&postcount=13").  I then used this info to reload my Nvidia driver with [EnvyNG]("http://albertomilone.com/wordpress/?p=163") and use the 96.43.05 driver and it worked!

Thanks!

---

### Post by optimusmedia on 2008-05-01
This also fixed an issue I had with the screen going black after power management kicked in. My work around was to go try and go to Virtual Console (which didn't work until this fix) and then back with Ctrl Alt F7

---

### Post by kshtjsnghl on 2008-05-01
hey i have got the following hardware 
 
 kshitij@kshitij-laptop:~$ lspci|grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
kshitij@kshitij-laptop:~$ 

And i am getting the same problem. As soon as i press Alt+CTRl+F1, the screen goes blank and nothing shows up and then returns to the previous state as i press alt+ctrl+f7.
 
 What should i do??

---

### Post by mano cazalet on 2008-05-01
hi optimus, glad to hear you managed to solve 2 issues, that's great :)

kshtjsnghl

did you take a look at the thread I linked ^ 
as we saw it could be caused be graphics driver, 
or resolution settings at the kernel line in /etc/grub/menu.lst
or issues with initframs-tools

(just make sure to backup before changing any settings)

---

