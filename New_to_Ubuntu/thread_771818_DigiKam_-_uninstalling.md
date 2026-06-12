---
title: "DigiKam - uninstalling"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by David1000 on 2008-04-28
I have lost the menu and tool bar in didKam.  I tried installing it and then reinstalling it but they are still missing.  There must be a setting file which is not deleted when the programme is deleted/uninstalled.  I have confirmed this by setting up a second user and installing digiKam - it works just fine.

My only option seems to be to manually delete all digiKam files.  Does anyone know how I can find the complete list of files that digiKam uses?

---

### Post by sam_delta on 2008-04-28
have you tried using the --purge option?

sudo apt-get remove --purge digikam?

---

### Post by David1000 on 2008-04-28
Just tried it.  Got the message -purge not recognised (or similar).  Maybe I'll try it with the -purge.

---

### Post by David1000 on 2008-04-28
Didn't work.  Menus still not there.

---

### Post by Paqman on 2008-04-28
Try uninstalling from Synaptic. Choose the full uninstall, then install it again.

---

### Post by sam_delta on 2008-04-28
have you serched under your user hiden files?, as it is a single user problem, it must be a file under your user home directory,  , so into a terminal and type 

```
 ls -f 
```

ull get a list of your whole files, including hidden files (those that beggin with a dot ), serch for some hidden configuration files for digikam, something like .digikam/

sam

---

### Post by David1000 on 2008-04-28
Ive tried Synaptic (first way I tried).  Also searched for hidden files.  Found several but obviously didn't find them all.  I suspect there may be a file called something other than digiKam.  Maybe a shared file - does linux do that?

---

### Post by David1000 on 2008-04-28
Problem solved!

Control-shift-F displays menu (and tool bar) so no need to reinstall.

---

