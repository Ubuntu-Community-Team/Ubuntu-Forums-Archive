---
title: "[SOLVED] Ubuntu on Acer Aspire 5630"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by Kinetic_lord on 2008-11-17
Hello!

I just recieved an Acer Aspire 5630, with Windows Vista Home edition on it. I want to install Ubuntu 8.04 on it but i don't know if it will work. What i mean is that Windows has a lot of software that goes with this Acer (Acer eNet management, Secure locks...) will everything work fine if i put Ubuntu on it? (wireless, bluetooth, drivers).

---

### Post by markjensen on 2008-11-17
Boot Ubuntu as a Live CD?

If it seems to work, maybe do a "wubi" install, as that does not alter partitions, and can be easily undone, should things not work.

---

### Post by cariboo on 2008-11-17
THe best way to find out if Ubuntu will work with your computer is to download the LIveCD and try it. If everything works using the LiveCD, then go ahead and in stall it.

Jim

---

### Post by Kinetic_lord on 2008-11-28
Ok, made it, works great :D. Batterie lasts longer (strange, acer recommends windows vista but it works better on linux... they suck at software...)

I kept Vista... unfortunately... i installed Ubuntu from windows too... now i want only Ubuntu on my computer. What can i do to uninstall Windows?

P.S. Also, there is no GRUB there is Windows Boot Manager.

---

### Post by caljohnsmith on 2008-11-28
> **Kinetic_lord said:**
> Ok, made it, works great :D. Batterie lasts longer (strange, acer recommends windows vista but it works better on linux... they suck at software...)

I kept Vista... unfortunately... i installed Ubuntu from windows too... now i want only Ubuntu on my computer. What can i do to uninstall Windows?

P.S. Also, there is no GRUB there is Windows Boot Manager.
If you are sure you don't want Vista any more, you could boot your Ubuntu Live CD, go to System > Admin > Partition Editor, and simply delete all the partitions and start over fresh. You would probably want to set up at least three partitions, one for the main Ubuntu install (mounted as "/" during the installation), one for swap (mounted as "swap"), and one for /home (mounted as "/home"). Just run the Ubuntu installer from the Live CD desktop, and if you want a tutorial to help guide you step-by-step through the process, you might find this [web page]("http://www.herman.linuxmaniac.net/p23.html") helpful. You won't have to do anything special to have Grub installed as your boot loader. Let us know how it goes or if you run into problems. :)

---

### Post by caljohnsmith on 2008-11-28
sorry double post.

---

### Post by Kinetic_lord on 2008-11-28
... I installed Ubuntu FROM windows... like any ordinary programs... this sucks. Well i'll have to keep it, i dont want to reinstall all the stuff anymore.

---

### Post by caljohnsmith on 2008-11-28
You can use "[LVPM]("http://lubi.sourceforge.net/lvpm.html")" to transfer your existing Ubuntu installation to a dedicated partition.

---

### Post by rixtr66 on 2008-11-28
Im curious..did you use a live cd?i have an acer aspire and have been running ubuntu studio happily,mine came with vista as well,and i immediatly
got rid of it by installing ubuntu 8.04,its really simple,if you dont have a
live cd burn one,and when the install comes to the partitioning,choose use
entire disk.this will remove windows and format your hardrive for ubuntu!
another option is to use gparted,but i think if your new to ubuntu,
the above method will work for you.i know you mentioned you didnt want to reinstall programs,however if you really want to run ubuntu as your main os
be patient and reinstall,trust me on this i went through the same dillema
months ago.i hope this is helpfull!!:)
whatever you choose to do i wish you luck!
peace
Rick

---

### Post by Kinetic_lord on 2008-12-05
Yeah, well it worked fine ...at the beginning, now it's annoying...

---

### Post by Circus-Killer on 2008-12-05
ubuntu will always work better running natively as apposed to running it within windows. this is cos your pc uses A LOT of resources running vista. with 1gb of ram, vista uses about 80%.
As apposed to the 40% that ubuntu uses. plus those together and you got your ram used up completely, relying heavily on windows virtual memory, which works off your windows partition as apposed to its own.

also, you have more chance of ubuntu working with hardware when you not running within windows. this is cos ubuntu will have to talk to the windows hardware driver, if i'm not mistaken.

ubuntu will always run best when it is running natively on a machine. you have two choices. run ubuntu exclusively, or do a dual boot.

as for your acer, you will be able to do most things. the ones i've had problems with is wireless and bluetooth. other than that everything worked fine for me. oh yeah, and the internal mic (positioned by the screen/built-in webcam) doesnt work all that well, but i should imagine that hopefully this will be sorted in the next release of ubuntu.

anyways, hope you have better luck. ;)

---

### Post by Kinetic_lord on 2008-12-20
I reinstalled Windows (pissed me off, i'll NEVER connect to internet with Vista) and installed Ubuntu afterwards. It works a lot better... Thx guyz :)

---

