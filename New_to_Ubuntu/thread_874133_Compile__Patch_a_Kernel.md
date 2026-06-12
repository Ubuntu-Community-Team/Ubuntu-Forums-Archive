---
title: "Compile / Patch a Kernel"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by BGFG on 2008-07-29
Hi,
How does one do this ?
Don't worry I DO know this can break my system but:
-Ubuntu is stored on it's own physical drive
-I dual boot so i have a backup system
-I still have the -18 and -19 kernels
-Grub is initiated from my vista bootloader so i can still get to the    forums if it hits the fan.
(yeah i have vista. for now)

Any instructions.... links ? i already checked this but the date.... :

[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

---

### Post by sdennie on 2008-07-29
That guide is old but still good.  It's what I used when I was learning to compile the kernel the Ubuntu way and it should work just fine.

---

### Post by BGFG on 2008-07-29
Thanks a lot then Vor. will try it. I have the 'patch-2.6.26.bz2' sitting on my desktop.

---

### Post by sdennie on 2008-07-29
You probably don't want the patch but the full version.  To get that click on the "F" link on the line of the kernel you want from kernel.org.

---

### Post by logos34 on 2008-07-30
> **vor said:**
> You probably don't want the patch but the full version.  To get that click on the "F" link on the line of the kernel you want from kernel.org.

oh, so you don't have to add the patch-2.6.26.bz2 to the full version ('linux-2.6.26.bz2')?

not that it matters in my case, I can't figure out a way to build a graphics driver kernel module against my existing 2.6.24 kernel, let alone the 2.6.26...:(

---

### Post by sdennie on 2008-07-30
> **logos34 said:**
> oh, so you don't have to add the patch-2.6.26.bz2 to the full version ('linux-2.6.26.bz2')?

not that it matters in my case, I can't figure out a way to build a graphics driver kernel module against my existing 2.6.24 kernel, let alone the 2.6.26...:(

The user interface to kernel.org is a bit non-intuitive at first.  There is a small legend at the bottom of the kernel listing that says what each link does.  But, no, as far as I'm aware, you shouldn't need to patch 2.6.26 until 2.6.26.1 comes out.

(I posted in your other thread about your driver problem. :) )

---

### Post by BGFG on 2008-07-30
Hi VOR,
What do you think of this ? on another note,
I know that Ubuntu is already debian based but debian is the only other OS that has sparked any major interest in me. I don't seem compelled to try any RED HAT based systems. 

[http://www.debian.org/releases/stable/amd64/ch08s06.html.en](http://www.debian.org/releases/stable/amd64/ch08s06.html.en)

---

### Post by PmDematagoda on 2008-07-30
> The user interface to kernel.org is a bit non-intuitive at first. There is a small legend at the bottom of the kernel listing that says what each link does. But, no, as far as I'm aware, you shouldn't need to patch 2.6.26 until 2.6.26.1 comes out.

Unless you intend on running 2.6.27.rc1 which came out yesterday:).

---

