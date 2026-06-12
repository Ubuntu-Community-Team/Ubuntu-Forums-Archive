---
title: "Lubuntu slower with each update"
date: 2012-11-21
forum: New to Ubuntu
---

### Post by elfuego on 2012-11-21
Hi!

I've been using lubuntu on Asus eeepc 901 since July and I've noticed that it gets progressively slower after each update. Right now, it has gotten so painfully slow that even scrolling in web browser (both chromium and firefox) has at least a .5sec lag, even on javascript and flash-free websites (such as vanilla php-bb forums). Javascript-filled websites (for example yahoo mail service) are almost unusable. 

Back in July, right after installation - the system was happy and snappy. I have installed exactly 0 new programs ever since. 

I get the feeling that somehow, CPU speed locked down to 800Mhz again [(link to original problem)]("http://ubuntuforums.org/showthread.php?t=2034269"). :(

Any ideas what went wrong, or how do I check what is wrong? :confused:

---

### Post by snowpine on 2012-11-21
You can try booting to the old kernel under which you had good performance. (choose it from GRUB menu at boot)

Does your EEE have a SSD drive? If so you might want to check its health (not an SSD user myself so I can't walk you through it) and also that it is not getting full. :)

---

### Post by kalehrl on 2012-11-21
>  I get the feeling that somehow, CPU speed locked down to 600Mhz again [ (link to original problem)]("http://%28link%20http://ubuntuforums.org/showthread.php?t=2034269%20%29"). :sad:
Your link doesn't work.
How did you increase the CPU speed.
Loading p4_clockmod module is just a cosmetic change.
The CPU remains at 630MHz.

---

### Post by elfuego on 2012-11-21
> **kalehrl said:**
> Your link doesn't work.
How did you increase the CPU speed.
Loading p4_clockmod module is just a cosmetic change.
The CPU remains at 630MHz.

I fixed the link, thanks;

I didnt increase the CPU speed. I just disabled speedstep in BIOS and out of sudden, the laptop worked as it should (in Lubuntu). At least at the beginning.

SSD is a good point - it is indeed slow, but the space should not be a problem - almost 7 out of 20GB is free. However, even if its slow, it shouldnt affect javascript performance... The problem with booting the old kernels is my habit of deleting the old stuff after update :( I guess now I learned why devs did not make it a feature to clean up the 'obsolete' kernels automatically.

I guess I'll reinstall the system and disable any further updates :|

---

### Post by elfuego on 2012-11-21
> **elfuego said:**
> The problem with booting the old kernels is my habit of deleting the old stuff after update :( 

Scratch this part. I just noticed that I was too lazy to do that; I still have the original kernel installed which was hidden behind "older linux versions" in grub :)

...aaaand it works awesome! :guitar: It's back to full speed again.

Thread issue solved thanks! 8-)

---

### Post by Peripheral Visionary on 2012-11-21
I'm delighted to hear that the older kernel works as it should.  But it raises a question I've had, still not answered in a way I can quite understand:

Why do the newer kernels sometimes not work, or slow things down, or worse sometimes?  Is it really a bad thing to continue with an older kernel that works when there's an "updated" kernel that may be more secure or whatever?

Just wondering.  Not a problem for me (yet, fingers crossed), but I always get really nervous when Update Manager shows me a kernel update and all that "Linux-image" stuff.

---

### Post by elfuego on 2012-11-23
> **Peripheral Visionary said:**
> 
Why do the newer kernels sometimes not work, or slow things down, or worse sometimes?  Is it really a bad thing to continue with an older kernel that works when there's an "updated" kernel that may be more secure or whatever?


I do not know, but starting from now, I'll follow the saying "if it works, don't fix it". :)

---

