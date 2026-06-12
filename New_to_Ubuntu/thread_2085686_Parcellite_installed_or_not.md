---
title: "Parcellite: installed or not"
date: 2012-11-18
forum: New to Ubuntu
---

### Post by BeeeZeee on 2012-11-18
Ubuntu 12.04     Unity2D

Hello.

I think I installed Parcellite using this code in terminal

                                  berniezzz@berniezzz-p7-1235:~$ sudo apt-get install parcellite
 [sudo] password for berniezzz:  
 Reading package lists... Done
 Building dependency tree        
 Reading state information... Done
 The following packages were automatically installed and are no longer required:
   linux-headers-3.2.0-29 linux-headers-3.2.0-29-generic
 Use 'apt-get autoremove' to remove them.
 The following NEW packages will be installed:
   parcellite
 0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
 Need to get 0 B/242 kB of archives.
 After this operation, 688 kB of additional disk space will be used.
 Selecting previously unselected package parcellite.
 (Reading database ... 198242 files and directories currently installed.)
 Unpacking parcellite (from .../parcellite_1.0.2~rc5-0ubuntu1_amd64.deb) ...
 Processing triggers for man-db ...
 Processing triggers for desktop-file-utils ...
 Processing triggers for bamfdaemon ...
 Rebuilding /usr/share/applications/bamf.index...
 Processing triggers for gnome-menus ...
 Setting up parcellite (1.0.2~rc5-0ubuntu1) ...
 berniezzz@berniezzz-p7-1235:~$
  

So my first question would be, did parcellite get installed? I think it did because I put this into terminal:


                                  berniezzz@berniezzz-p7-1235:~$ which parcellite
 /usr/bin/parcellite
 berniezzz@berniezzz-p7-1235:~$ whereis parcellite
 parcellite: /usr/bin/parcellite /usr/bin/X11/parcellite /usr/share/man/man1/parcellite.1.gz
 berniezzz@berniezzz-p7-1235:~$
  

I then went to dash/recent apps and the icon for Parcellite was there. I left clicked with the mouse and nothing. It did not come up in the launcher or did it go to the desktop menu. I tried this 3-4 time with the same results. I even right clicked the icon and nothing.

How can I bring up Parcellite so that I can change some of the prefs and actually use the application.

Bernie

---

### Post by newb85 on 2012-11-18
I think you successfully installed it.  Unfortunately, from what I've read, Parcellite does not play well (or maybe at all) with Unity.

---

### Post by squakie on 2012-11-18
To try to test this, I just installed the package myself, then went to a terminal window and typed "parcellite".  It's doing SOMETHING, but I have no idea what.  The terminal sits there like the process is running and I have to use ctrl-c to get back to the command prompt.  Nothing showed on my screen - no new window, etc..

So, I don't have a clue what it even is, how to use it, or what it's supposed to look like, but it runs in terminal but nothing happens.

EDIT:  forgot to mention it does put it in the unity menu, when you click it no error is returned, and when you check running processes it is there.  I don't see any indicators on the top bar or the unity bar that says anything is happening, so I wouldn't know how to tell if you can use it or not (some kind of clip board thing, isn't it?).  

Perhaps [newb85]("http://ubuntuforums.org/member.php?u=833049") is correct and it just doesn't play well with unity.

---

### Post by stinkeye on 2012-11-18
You need to add it to the systray-whitelist in dconf for it to show in the panel.
Easy way is to install unsettings (has many other useful Unity settings)
```
sudo add-apt-repository ppa:diesch/testing
sudo apt-get update
sudo apt-get install unsettings
```

---

### Post by BeeeZeee on 2012-11-19
stinkeye, Unsettings installed but went to panel and in the systray-whitelist, parcellite is not in there.

squakie, parcellite is a clipboard manager similar to Ditto for Windows and CopyPaste for Macs.

---

### Post by stinkeye on 2012-11-19
> **BeeeZeee said:**
> stinkeye, Unsettings installed but went to panel and in the systray-whitelist, parcellite is not in there.

squakie, parcellite is a clipboard manager similar to Ditto for Windows and CopyPaste for Macs.
You need to add parcellite to unsettings then logout/in and launch parcellite.

---

### Post by |{urse on 2012-11-19
Just a sidenote, I find this works better than 'which'
> aptitude show parcellite | grep State

---

### Post by BeeeZeee on 2012-11-19
stinkeye, I typed "Parcellite" into the list, clicked on the "Apply", closed Unsettings.

Went to dash and clicked on Parcellite and still nothing. I then went back to Unsetting to make sure that Parcellite was still in the list and it was.

When you said "logout/in" should I have restarted Ubuntu for this to take effect. I am going to restart now and give you the results in a minute or two.

Bernie

---

### Post by BeeeZeee on 2012-11-19
Stinkeye, that did the trick. I had to restart to get it to work. The Parcellite icon is in the desktop menu and I clicked on it and there were several clips that I had previously copied in there.

Thanks for the help. I'll leave this  thread here until tomorrow morning when I'll mark it as solved. Any other suggestions  will be much appreciated.

Thanks stinkeye.

Bernie.

---

### Post by stinkeye on 2012-11-19
Ok,good.
If you have any problems with parcellite try another clipboard manager.
I use **glipper** which doesn't need to be added to the systray-whitelist.
You can also try **ClipIt** which was forked from Parcellite.

---

