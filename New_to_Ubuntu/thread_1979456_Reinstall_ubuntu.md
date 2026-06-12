---
title: "Reinstall ubuntu"
date: 2012-05-13
forum: New to Ubuntu
---

### Post by earthshakergb on 2012-05-13
I broke it big time, now I need to reinstall it. Here is the problem, I "fixed" a number lock problem so I thought (I got the info here on ubuntuforums)
Now I can't reload ubuntu (any, I tried 11.10 and 12.04) the process just gets started then goes into panic mode.
I am doing a dual boot with XP, and I managed to get XP back up and running, but the ubuntu partition is still intact but dead.
What do I do now?

---

### Post by Daveth on 2012-05-13
what did you break? It may be fixable if you tell us. Also, are you trying to install from a live ubuntu CD, hit install, and the panic happens? Can you tell us what the panic involves (besides panic:))?

---

### Post by earthshakergb on 2012-05-13
Yes from the live CD. I will try to tell you what I see. 
[110.023803] Kernel Panic-not syncing: attempted to kill init!
[110.024091] Pid:1, comm: run-init Not tainted 3.2.0-23-generic-pae #36-ubuntu
[110.024318] Call Trace:
[110.024408]  [<c15927832>] ? printk+0x2d/0x2f
this kind of stuff goes on for another 12 lines or so
the last line reads
[110.025936] panic occurred, switching back to text console.
If this helps at all great, if not I will start over from a blank drive, it only takes a few hours.
I tried to take a picture...see attached

---

### Post by Daveth on 2012-05-15
um, looks nasty. I cannot see why a live distro will not load, as it will not touch the broken installation, but the dual boot thing is a bit beyond me, so I am hoping someone might be able to suggest something. Sorry not to be more helpful to you.

---

### Post by Face-Ache on 2012-05-15
If an Ubuntu re-install is they way you want to go, you could try formatting that partition via Windows, and then re-install Ubuntu from there - i'd say a clean install would be your best option.

If your LIVE CD doesn't work, perhaps you could re-download Ubuntu with your Windows install, and try to install Ubuntu via a USB stick that has a non-live install?

That's how i recently re-installed after messing up my whole system playing with Grub stuff, and it worked a treat.

Heh, fixing Ubuntu with Windows .... who woulda thunk it! :D

Please don't just blaze ahead and take my advice here - someone with more beans, and thus more Ubuntu knowledge might have a better suggestion as to how to recover the existing Ubuntu install.  :razz:

---

### Post by earthshakergb on 2012-05-15
Well here is my best guess, grub failed, and the image I posted is probably from a bad burn on the dvd, it just didn't know what to do.
Here is what I did to fix it and it actually worked much to my surprise. I reloaded windows first, and updated it, that took 2-3 hours. After that I tried to fix the bad partition that ubuntu was on, well formatting it didn't work so using a tool in winXP called compmgmt, then deleted the partition, so I had a brand new space to work on.
I didn't have another blank DVD, so I used my known good 11.10 cd to reload ubuntu, then upgraded to 12.04.

The whole process took about 8 hours a long drawn out thing to fix a damn annoyance. 
My advice for someone wanting their numlock to come on when ubuntu starts...unless you have no doubt how to make it work, unlike me, after ubuntu starts reach over and **push the damn button!**. it takes less than a second to accomplish, and you are good to go.

---

### Post by Face-Ache on 2012-05-15
I've learned that there are two main rules when using Linux .... First, you don't mess with the Grub, Second, _***you DON'T mess with the Grub***_.  :D

I had to do *exactly* the same as you to recover my system, and seriously, having a custom Plymouth screen wasn't worth the 8 hours of my life that i'll never get back!

I figured out that what you could have done, is boot to Ubuntu from the known good 11.10 cd, then run Boot-Repair - it's available in the Software Center, and will recreate your Grub in the boot sector of the HDD.

8 hours for a reinstall... ..... 1 second to push the Fn button .....  8 hours would have given you 216,000 Fn Button Pushes!!!!!!!!!!

:lolflag:

---

### Post by earthshakergb on 2012-05-15
I think what trashed grub was the line I added to the config file, I think that is what it was. I read about a numlock on by default item on here. Never again

---

