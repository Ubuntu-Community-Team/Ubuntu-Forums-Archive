---
title: "Backup Command in Terminal"
date: 2014-02-05
forum: New to Ubuntu
---

### Post by BadMichael on 2014-02-05
The upgrade from 13.04 to 13.10 hosed Unity's lens along with some other UI elements. I'm looking to perform a complete reinstall within the next few days.

In terminal, what is the command to start Ubuntu's GUI default backup program (the one with the picture of the safe)?

TIA,
-- Michael
(Recent Windows refugee)

---

### Post by deadflowr on 2014-02-05
I believe the program is deja dup.
so try
```
deja-dup
```
or run
```
man deja-dup
```
for more options.

---

### Post by monkeybrain20122 on 2014-02-05
Well "upgrade" is always a bad idea judging from the number of threads reporting upgrade problems. There should be a big warning sign against it. I always do fresh install. Much faster and safer. 

Since you are doing a clean install, you may as well make a separate /home partition. So next time when you do a clean install of the next Ubuntu release (Don't do "upgrade"!) you just install over the / partition without formatting the /home and all your data and settings will be saved.

---

### Post by BadMichael on 2014-02-05
I didn't think that 13.04 to 13.10 would be that great a leap. If upgrades are that problematic, it shouldn't be presented as an option.

I was hoping to back up my current /home directory to my external hard drive, perform a clean install, and then restore the backup.

Is there a way to start the *graphical version* of Ubuntu's backup program from the command line?

---

### Post by monkeybrain20122 on 2014-02-05
If you already have a separate /home can just do a clean install on / (and format it) but without formatting /home.

"Upgrade", if it works at all would take a long time. And it only works (theoretically) if you have a very pristine system (no ppas, no third party applications including proprietary drivers) So, one should restore the system to that 'clean state' to even attempt any "upgrade". It is much simpler just to do a clean install.

---

### Post by deadflowr on 2014-02-05
```
deja-dup-preferences
```
should get you the gui.
Or at least the gui to set where and how to do the backup.
You should get a backup now button in the lower right corner.
If you run
```
deja-dup --backup
```
it'll simply backup to whatever the default place is.


Off topic though, I run Release upgrades all the time, with ppas, closed source drivers, and a whole bunch of extra stuff and only problems have only been the length of time it took.
But that probably has more to do with my preparation for breakage.
It's an odd cosmic thing.The more you prepare for the worst the less likely it'll come to pass.

---

### Post by BadMichael on 2014-02-06
The deja-dup-preferences command works and is exactly what I was looking for. And I'll keep the /home info in mind when I do a clean install.

Thanks to both of you.

---

