---
title: "Can't get rid of PCLinux"
date: 2008-01-06
forum: Other OS Talk
---

### Post by The Cusp on 2008-01-06
Sick and tired of Windows Vista, I wiped my drive clean and installed PCLinux.  THen I discovered I couldn't play any of my games.  Obviously PCLinux is not for me, and I want to go back to XP.

The problem is I can't get rid of the damn thing.  Whenever I start with a boot CD (XP or Vista) it tells me to press any key to boot from the CD, but then Grub kicks in and Linux loads up.  I've spend hours trying to sabotage this damn system so my boot CD will work, but nothing I do will get rid of it.

Is there anyway I can reformat my hard drive in linux and start fresh?

---

### Post by The Cusp on 2008-01-06
I even went into the BIOS and removed my hard drives from the boot sequence, but I still get nothing but Linux!

---

### Post by joe.turion64x2 on 2008-01-06
> **The Cusp said:**
> Sick and tired of Windows Vista, I wiped my drive clean and installed PCLinux.  THen I discovered I couldn't play any of my games.  Obviously PCLinux is not for me, and I want to go back to XP.

The problem is I can't get rid of the damn thing.  Whenever I start with a boot CD (XP or Vista) it tells me to press any key to boot from the CD, but then Grub kicks in and Linux loads up.  I've spend hours trying to sabotage this damn system so my boot CD will work, but nothing I do will get rid of it.

Is there anyway I can reformat my hard drive in linux and start fresh?
Wrong forum mate. Anyway, your Windows CD should be able to reformat the drive if you trully start from it (check your BIOS).

---

### Post by The Cusp on 2008-01-06
just great...

---

### Post by benny bronx on 2008-01-06
What did you use to wipe your disk?  I always use dban and I never had the problem you are having.

[http://dban.sourceforge.net/](http://dban.sourceforge.net/)

---

### Post by joe.turion64x2 on 2008-01-06
If you _want to wipe your Linux system_ you can run the fearsome command **rm**.
Just log in to PCLOS and open a terminal:
> su
root password
rm -rf /*

that should kill your Linux system.

---

### Post by SunnyRabbiera on 2008-01-06
in the future why dont you dual boot, that way you can play games on XP and then run linux on the side

---

### Post by Salpiche on 2008-01-06
[QUOTE=The Cusp]I even went into the BIOS and removed my hard drives from the boot sequence, but I still get nothing but Linux![/QUOTE]

Go on your bios and make sure that you are booting from the cd/dvd rom. Then go on with your install as usual.
   Funny I didn't like PClinux!  hehe!

---

### Post by DarkDancer on 2008-01-06
Sounds to me as if his bios is set up right, as it asks him about booting from the cd. Might be a problem with the 2 cd's, or the motherboard. I myself would pull bios defaults and reset it up to boot from the cd, but that's just me.

---

### Post by K.Mandla on 2008-01-06
> **benny bronx said:**
> What did you use to wipe your disk?  I always use dban and I never had the problem you are having.

[http://dban.sourceforge.net/](http://dban.sourceforge.net/)
+1

---

### Post by ugm6hr on 2008-01-06
> **benny bronx said:**
> What did you use to wipe your disk?  I always use dban and I never had the problem you are having.

[http://dban.sourceforge.net/](http://dban.sourceforge.net/)

Or this: [http://www.killdisk.com/](http://www.killdisk.com/)

---

