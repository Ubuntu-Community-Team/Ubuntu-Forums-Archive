---
title: "Problems after update to 11.10, reinstall question."
date: 2011-11-04
forum: New to Ubuntu
---

### Post by jotto! on 2011-11-04
I was very happily running 11.04 and resisted the urge to upgrade to 11.10 on my dual boot machine.....
Then in a fit of anticipation, I clicked upgrade!!!!

So now my pc runs like a dog with 2 legs, no eyes and a heart condition.
It wont shut down, the net is really slow, it takes about 30 seconds ( if it actually works ) to minimize a window.

Its just not working for me, too many bugs. Probably from my install but thats another discussion.

I want to do a clean install then cherry pick the info I have already on my PC. Not worried about installed apps, just the saved docs, music, videos etc.

If I simply make a copy of my home directory on an external backup drive, can I simply do  a clean install of 11.10 or 11.04 and copy over the stuff I want to keep from the saved home folder to the newly created folder or is it not as simple as that?

All info greatly received before I throw my pc out of the window...

Never had such major issues after a kernel upgrade but this really got me thinking about windows...EEEK!!!!!
TIA.

---

### Post by ajgreeny on 2011-11-04
You can do more or less exactly what you asked with all your personal /home folders and files, but I suggest you also keep all the hidden folders and files that may be important to you, such as .mozilla, .thunderbird, and any others that have actual data in them, rather than just configurations.

You may decide to backup everything, but be warned, I am not certain of this, but the move to gnome 3 in 11.10 may have made some of the files incompatible with gnome 2, should you go back to that DE.

---

### Post by jmajeremy on 2011-11-04
Yes, it's that simple. Just rsync your home dir to an external drive or another partition, do a fresh install, and copy everything back.

---

### Post by Ricx94 on 2011-11-04
surprisingly, i believe it *is* that simple. back up all the files you want to keep, and also keep in mind what ajgreeny said;
> **ajgreeny said:**
> I suggest you also keep all the hidden folders and files that may be important to you, such as .mozilla, .thunderbird, and any others that have actual data in them, rather than just configurations.
When you insert a cd of ubuntu 11.10, and click to install, it will pick up your other OS (I'm assuming windows, but not sure), as well as your current install of ubuntu. it then gives three options, and i can't remember which order they were in; erase everything and install on whole disc, upgrade your current install of ubuntu, or reinstall in place of your current ubuntu install. in this case, you would want to reinstall in place of current ubuntu, i am sure.

---

### Post by jotto! on 2011-11-05
Thanks for that so will rsync or grsync copy hidden folders or do I need to add a specific command to it in terminal?
Fairly new to terminal usage. looks like I need to use -avh to copy all, does that sound correct?

I did try simply copying/pasting the home file but got errors every time.

---

### Post by ajgreeny on 2011-11-05
What errors did you see?  What was the format type of the disk to which you copied?  I always ended with a few errors when rsync was used to copy to an ntfs or fat32 disk;  when I reformatted the external to ext3 the errors disappeared.

---

