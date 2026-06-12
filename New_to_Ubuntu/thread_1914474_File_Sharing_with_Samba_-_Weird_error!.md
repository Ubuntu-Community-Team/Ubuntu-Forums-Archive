---
title: "File Sharing with Samba - Weird error?!"
date: 2012-01-24
forum: New to Ubuntu
---

### Post by FFabian on 2012-01-24
Hi

I'm using an iMac with Lion and installed Lubuntu 11.10 on my Netbook. I want to share files/folders between the two machines. I can access the shared folders located on the iMac with pcmanfm Go to->Network->... but can't share a folder on the Laptop( i.e. no shared folders visible when accessing the Laptop with the Finder on the iMac). 

I searched the forum and read that installing system-config-samba would install a GUI and samba as a dependency. Now Samba has a menu entry but when clicking it, it asks for my password but doesn't seem to launch (screen flickers a bit). 

Launching via Terminal shows this:
```
fabian@fabian-meenee:~$ system-config-samba
Traceback (most recent call last):
 File "/usr/sbin/system-config-samba", line 44, in <module>
   import mainWindow
 File "/usr/share/system-config-samba/mainWindow.py", line 30, in <module>
   import gtk.glade
ImportError: No module named glade
fabian@fabian-meenee:~$ gksu system-config-samba
 File "/usr/sbin/system-config-samba", line 44, in <module>
   import mainWindow
 File "/usr/share/system-config-samba/mainWindow.py", line 30, in <module>
   import gtk.glade
ImportError: No module named glade
fabian@fabian-meenee:~$ 
```

What's wrong?

---

### Post by FormatSeize on 2012-01-24
> **FFabian said:**
> What's wrong?
The error you are receiving is due to the computer looking for glade and not finding it. You have to install the glade module, according to [this thread](http://ubuntuforums.org/showthread.php?t=1746055).
 
Hope that helps.

---

### Post by FFabian on 2012-01-24
Edit: I installed just python-glade2 as suggested in the other thread and system-config-samba started without any further problem. Btw file sharing now works too. 

Thx for your help FormatSeize.

---

