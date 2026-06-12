---
title: "Error16: Inconsistant filesystem structure"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by Spoken on 2008-08-15
WELL....i had to do a hard shutdown last night because of some random "hickups" on my computer.  When i tried to reboot, it loads the dell loading screen, then when it goes to the black screen right before the ubuntu loading screen, it will stay there for a few mins, then give me this error...

Error16: Inconsistant filesystem structure

Things that ive tried:
-----------------------------
1)Booting into different kernels
2)Booting into all available recovery modes
3)I have even tried restoring to factory default from the grub menu.  but it literally gives me ENDLESS lines of output.
4)Ive tried booting from the live cd (7.04), but when i do, it locks up on the ubuntu loading screen with the loading bar just going back and forth,  when i hit f6 at the ubuntu menu from the live cd, i take out quit splash and then boot, it gives me this error

cannot access tty, job control turned off

I am running out of options...and time, seeing as how i start college in a few days, and i NEED my computer...:confused:

---

### Post by Gannon8 on 2008-08-15
It means your filesystem is damaged. Hard shutdowns WILL do this, so you should really do it as a last resort and when your disk is not in use. You will have to check your root filesystem, which will need you to boot off of a livecd. Try a small distro such as Damn Small Linux.

---

### Post by Gannon8 on 2008-08-15
Oh, and what do you mean by your computer getting "hickups?"

---

### Post by Spoken on 2008-08-15
well, it was just acting weird, my wireless card stopped detecting signals and when i tried to shutdown "normally", it just...wouldnt.  idk how else to explain it.

and i cant boot off a livecd, whenever i do, my computer cant detect the screen, hence the cannot access tty error messege.  ive tried to reconfigure xserver and still the same results.

---

### Post by Gannon8 on 2008-08-15
Like I said, try going to a different computer and burning a copy of DSL and try that. You must have a different computer (or OS) if you are posting :)
Anyway, you need to run fsck.[filesystem] where [filesystem] is the type of filesystem you are using, like ext3 for, well ext3 :)

---

### Post by Herman on 2008-08-15
:) This is the third thread already on the same subject, please stop making more threads about the exact same subject. :)

---

### Post by Spoken on 2008-08-15
sorry HERMAN

but i have to get this problem fixed, i start college next week and i HAVE to have this fixed.  or i can just say goodbye to the 3 grand i spent on tuition.

---

