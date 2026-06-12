---
title: "Firefox 3.0 problems"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by drexell0680 on 2008-06-21
Hi all,

I've been trying to update to Firefox-3.0 unsuccessfully for a few days now.  Where I am now:

I used ubuntuzilla to install firefox 3.0 (from bash)...  I don't remember the exact syntax, but something like 

ubuntuzilla.py -a install -p firefox

Before this, when I clicked on my firefox launcher, firefox 2.0xx was loaded (so I could use the addons).  Now it just gives me the mozilla crash report window and doesn't start.

Now, if I go to bash and type

gksudo firefox-3.0 & 

I can get in to the firefox 3.0 beta that came with ubuntu (I think), but I can't update it from the help menu (it says it's the current version).  

What's going on??

---

### Post by PinkFloyd102489 on 2008-06-21
Firefox has to be updated via apt or compiled from source.

---

### Post by akkiraju on 2008-06-21
can you check the  firefox installations that are present on  your system. 

1.Are you using Hardy distro ?. 

2.Can you use synaptic manager to check the firefox packages  currently installed on your system.

System->Adminsitration->synaptic manager.

3. Search for "Firefox" and remove old firefox versions.

---

### Post by nanotube on 2008-06-21
start with a fresh profile - using ff3 with a leftover ff2 profile will not make ff3 very happy.

---

### Post by phil66 on 2008-06-22
I had the same problem

The incompatible add-ons were causing the crash report

I used safe mode to revert to the default add-ons

Then downloaded and installed using ubuntuzilla

Now using firefox 3 to post this thread

---

### Post by billgoldberg on 2008-06-22
Just update your system and you should have firefox 3 (RC2?).

Or download it from the firefox website.

Extract the package and run the executable.

---

### Post by drs305 on 2008-06-22
For hardy, FF 3.0 is in the Recommended (hardy-updates) section of synaptic (Settings > Repositories > Updates Tab > tick Recommended (hardy-updates). I've read that in gutsy, it is now in the Unsupported (gutsy-backports) section.

If you are going to install it via the unsupported gutsy-backports, it is recommended for normal users to untick this after you have installed Firefox.

---

