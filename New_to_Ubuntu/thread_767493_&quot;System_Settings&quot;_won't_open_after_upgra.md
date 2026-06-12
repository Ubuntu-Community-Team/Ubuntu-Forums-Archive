---
title: "&quot;System Settings&quot; won't open after upgrade."
date: 2008-04-25
forum: New to Ubuntu
---

### Post by BSAB_80 on 2008-04-25
Hi there, guys.
Just upgraded a while ago, and i ran into a few nags.
(but other than that, it's been refreshingly smooth, i must say)

The main one is that "System Settings" won't open, it crashes immediately.
Here's the debugging:
```
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0xb685a6c0 (LWP 12886)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[KCrash handler]
#6  0x0805bced in ?? ()
#7  0x08113310 in ?? ()
#8  0x00000000 in ?? ()
```

Any clues?
I've searched around a bit, but my search-fu must be weak today.

Also, as long as i have your attention, two more things if i may.


1 - Ever since the upgrade, the ALT+SPACE shortcut i used to launch Katapult has been disabled, i had to change the shortcut to WIN+SPACE. This happened to anyone else, anyway of getting to use ALT+SPACE again?
(also, what is better, GnomeDo or Katapult?)

2 - Screenlets, just won't work, i launch it, the icon floats around for a few seconds but then just disappears, and the program is never actually launched. Again, any suggestions?

Thanks for everything!

---

### Post by BSAB_80 on 2008-04-26
Hum, should i assume that i can't change my global shortcuts because the main system settings doesn't work and that takes precedence over programs' shortcuts?

This is incredibly annoying, i can't even lower my volume, it's stuck at 100%!

---

### Post by martrn on 2008-04-26
I presume you are talking about kubuntu system settings.

Have you tried uninstalling it and re-installing it, that usually fixes anything broken if it is with the systemssettings package.

From a terminal
> sudo apt-get remove systemsettings
sudo apt-get install systemsettings

or even 
> sudo apt-get remove -purge systemsettings
sudo apt-get install systemsettings

??

---

### Post by BSAB_80 on 2008-04-26
> **martrn said:**
> I presume you are talking about kubuntu system settings.

Have you tried uninstalling it and re-installing it, that usually fixes anything broken if it is with the systemssettings package.

From a terminal


or even 


??

Yeah,sorry, i meant KDE System Settings.
The package is kde-systemsettings. Purging seemed to do the trick, at least now i can get into System Settings.

Cheers, man, now lets see what else is broke, heh.

---

### Post by BSAB_80 on 2008-04-26
Er, i wanted to mark this thread as solved, since i got System Settings to work in Kubuntu again, but i don't seem to have the choice in Thread Tools.

Am i doing something wrong?

---

### Post by macetw on 2009-03-19
This worked for me, too. Wow, why was this necessary?

---

### Post by OneStyle07 on 2011-02-08
I had a same problem like BSAB_80,and the solution martrn gave didn't help me...the way i open System Settings is via konsole...
type: 

sudo systemsettings

---

