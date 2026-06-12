---
title: "Pidgin"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by jdmss1 on 2008-09-03
Each time i log out of Pidgin i can't log back in without trying a number of times.  I have tried uninstalling and reinstalling through Synaptic, installing from the Terminal, installing an older version, changing my idle settings, and everything else i have read so far.  It seems to be hit or miss, sometimes it will start up and sometimes it will just freeze as the Buddy List is coming up.  So i am just looking for fresh ideas to fix this problem.  Or looking for another way to run MySpace IM.  It won't run through Wine.  Are there any new programs to run this and other IM clients through?  Thank You :guitar:

---

### Post by LowSky on 2008-09-03
try deleting home/.pidgin folder, you will have to hit Ctrl+h to view it as its normally hidden.

Not log back into Pidgin and it should fix itself.
You may have to reset up your account.

---

### Post by jdmss1 on 2008-09-03
Ok, dumb newbie question, where do i go to get to that folder?](*,)

---

### Post by LowSky on 2008-09-03
on the top bar go to places and clcik on home folder

---

### Post by jdmss1 on 2008-09-03
ok, thank you, i will try that in a bit here. :)

---

### Post by Ryadt on 2008-09-03
There is no such folder as .pidgin. Look for .purple.

---

### Post by jdmss1 on 2008-09-03
ok so .pidgin .purple which one should i be looking for?  thank you

---

### Post by Ryadt on 2008-09-03
> **jdmss1 said:**
> ok so .pidgin .purple which one should i be looking for?  thank you
Go in your home folder and do Ctrl+H and look for .purple. .pidgin doesn't exist. You might look for it if you want.

---

### Post by sailor2001 on 2008-09-03
in pidgin, it doesn't close off via the X......... right click the icon on top panel to "quit"

---

### Post by Thelasko on 2008-09-03
> **jdmss1 said:**
> ok so .pidgin .purple which one should i be looking for?  thank you

It doesn't matter, delete them both if you find them.

Another thing you can do is open the terminal and type:
```
sudo apt-get remove --purge pidgin
```
and then reinstall it.

Purge does the same thing as deleting the .purple file (purple is the base library pidgin is built on).  Your .purple folder is where pidgin/purple saves all of its user specific information (usernames, passwords, settings, even buddy lists).  If you have a misconfigured setting, deleting the .purple folder will help.  However, by deleting your .purple folder, you will lose your settings (don't worry, your buddy list is also saved on the server side, all you will lose is your saved usernames and passwords)

---

### Post by jdmss1 on 2008-09-03
> **Ryadt said:**
> Go in your home folder and do Ctrl+H and look for .purple. .pidgin doesn't exist. You might look for it if you want.

Ok, and then after i delete it do i need to do anything else, i.e. reinstall something or download something, and maybe, just for the fun of it, i'll look for that folder, not like i've got anything else to do :lolflag:

---

### Post by Ryadt on 2008-09-03
> **jdmss1 said:**
> Ok, and then after i delete it do i need to do anything else, i.e. reinstall something or download something, and maybe, just for the fun of it, i'll look for that folder, not like i've got anything else to do :lolflag:

Just let me know if you find it.:lolflag:

---

### Post by jdmss1 on 2008-09-03
If i find it you'll be the second to know :guitar:

---

### Post by Thelasko on 2008-09-03
> **jdmss1 said:**
> Ok, and then after i delete it do i need to do anything else, i.e. reinstall something or download something, and maybe, just for the fun of it, i'll look for that folder, not like i've got anything else to do :lolflag:

When you restart Pidgin it will recreate the .purple folder.  All of your settings will be gone, it will be like it was the first time you installed it.

Lot's of programs save information in hidden folders in your /home directory.  This method should work on any of those programs.

---

### Post by jdmss1 on 2008-09-03
So far it's working, i appreciate all the help, but darn it if i still can't find the folder called .pidgin, oh well, guess i'll look for it tomorrow (stated with defeat mixed with heavy sarcasm) :guitar:

---

