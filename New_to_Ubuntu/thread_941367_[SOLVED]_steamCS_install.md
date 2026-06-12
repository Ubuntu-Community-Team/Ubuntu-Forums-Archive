---
title: "[SOLVED] steam/CS install"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by chaddiesel on 2008-10-08
I am using a guide online for installing Steam.
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=1554](http://appdb.winehq.org/objectManager.php?sClass=version&iId=1554)

I am getting an error on the 4th step:
```
chadwick@Beast:~$ wine start /home/chadwick/Desktop/SteamInstall.msi
Option '/home/chadwick/Desktop/SteamInstall.msi' not recognized
Start a program, or open a document in the program normally used for files with that suffix. 
Usage: 
start [options] program_filename [...] 
start [options] document_filename 

Options: 
/M[inimized] Start the program minimized. 
/MAX[imized] Start the program maximized. 
/R[estored]  Start the program normally (neither minimized nor maximized). 
/W[ait]      Wait for started program to finish, then exit with its exit code. 
/L           Show end-user license. 

start.exe version 0.2 Copyright (C) 2003, Dan Kegel 
Start comes with ABSOLUTELY NO WARRANTY; for details run with /L option. 
This is free software, and you are welcome to redistribute it 
under certain conditions; run 'start /L' for details. 
```

How can I fix this problem?

---

### Post by chaddiesel on 2008-10-08
nevermind.....i read the fine print

I cd command to the desktop and wine start SteamInstall.msi and it worked.

---

### Post by Maheriano on 2009-01-14
Thanks for the link, going to try this as well.

---

