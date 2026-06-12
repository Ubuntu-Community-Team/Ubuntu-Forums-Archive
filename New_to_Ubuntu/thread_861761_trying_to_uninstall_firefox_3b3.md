---
title: "trying to uninstall firefox 3b3"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by slickh20 on 2008-07-16
I am trying to uninstall firefox 3 b3 however even after removing all entries under the synaptic rout i still have firefox.  I have tried deleting it from my home folder and it remains.

I love fire fox but i want the final release and it wont let me upgrade for some reason.

help me please.

---

### Post by Blahblah54 on 2008-07-16
What problems were you having updating it?

---

### Post by adamogardner on 2008-07-16
this is a stupid question and i don't know if it will make a difference but on the slim chance that it does albeit is just a wild guess withought understanding ubuntu at all but do you need to restart your computer?

---

### Post by drs305 on 2008-07-16
If you go to system, admin, update manager is firefox listed there. Running the update manager should work. 

In synaptic, if just 'firefox' is checked it should update, but I guess you are saying it doesn't.

How did you install Firefox 3 Beta?

---

### Post by tuxxy on 2008-07-16
whats the output of this command in a terminal;

```

firefox --version
```

---

### Post by slickh20 on 2008-07-16
i tried downloading from the mozilla site and it wouldnt install the file it downloaded.  i tried getting the package through synaptic and it would install but i couldnt run it because 3b3 was still there after i installed the new version. and there is no where to get rid or 3b3 that i can find.

---

### Post by slickh20 on 2008-07-16
:~$ firefox --version
Mozilla Firefox 3.0b3, Copyright (c) 1998 - 2008 mozilla.org

---

### Post by slickh20 on 2008-07-16
to tell you the truth i do not remember how i installed it,  i havent touched this computer in 2 months and i didnt know hwat i was doing then.  oops

---

### Post by tuxxy on 2008-07-16
Search for firefox in synaptic remove anything that has firefox in name, now do a fresh install should sort it out if no luck.

Also be sure to delete usr/lib/firefox /usr/lib/mozilla and any other locations to be certain you removed all firefox.

---

### Post by drs305 on 2008-07-16
It's possible it isn't registered with 'apt', but try this anyway. Back up your profile if you want to save anything, then run:
```
sudo aptitude purge firefox
```

If you compiled it yourself, do you know if you have any configuration folders still on your machine. You can run this to search:
```
sudo find / -type d -iname firefox
```

If you compiled it you may find a file called "uninst" or a subfolder called "postinst" with an uninstall script.

---

### Post by kansasnoob on 2008-07-16
Is this Hardy Heron 8.04 or Gutsy 7.10?

---

### Post by slickh20 on 2008-07-16
> casey@desktop2:~$ sudo aptitude purge firefox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages are unused and will be REMOVED:
  xulrunner-1.9-gnome-support 
The following packages will be REMOVED:
  firefox{p} 
0 packages upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 152kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 142477 files and directories currently installed.)
Removing firefox ...
Purging configuration files for firefox ...
(Reading database ... 142468 files and directories currently installed.)
Removing xulrunner-1.9-gnome-support ...
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done     

and then firefox still started.

and then for the second

> casey@desktop2:~$ sudo find / -type d -iname firefox
/home/casey/.mozilla/firefox
/etc/firefox
/opt/firefox
/usr/lib/firefox
/usr/share/firefox

---

### Post by slickh20 on 2008-07-16
um i just upgraded to hardy.

---

