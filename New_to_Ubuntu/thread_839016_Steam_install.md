---
title: "Steam install"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by chaddiesel on 2008-06-24
I'm attempting to install steam again. These are my results.

```
chadwick@Beast-desktop:~$ sudo msiexec /home/chadwick/Desktop/SteamInstall.msi
[sudo] password for chadwick:
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
Usage:
  Install a product:
    msiexec {package|productcode} [property]
    msiexec /i {package|productcode} [property]
    msiexec /a package [property]
  Repair an installation:
    msiexec /f[p|o|e|d|c|a|u|m|s|v] {package|productcode}
  Uninstall a product:
    msiexec /x {package|productcode} [property]
  Advertise a product:
    msiexec /j[u|m] package [/t transform] [/g languageid]
    msiexec {u|m} package [/t transform] [/g languageid]
  Apply a patch:
    msiexec /p patchpackage [property]
    msiexec /p patchpackage /a package [property]
  Modifiers for above operations:
    msiexec /l[*][i|w|e|a|r|u|c|m|o|p|v|][+|!] logfile
    msiexec /q{|n|b|r|f|n+|b+|b-}
  Register a module:
    msiexec /y module
  Unregister a module:
    msiexec /z module
  Display usage and copyright:
    msiexec {/h|/?}
NOTE: Product code on commandline unimplemented as of yet

Copyright 2004 Vincent B&#65533;ron
chadwick@Beast-desktop:~$ 

```

How can I get it to run the installer?

---

### Post by RiceMonster on 2008-06-24
Steam isn't a native Linux program. You'll need wine.

```
sudo apt-get install wine
```

Then, follow the guide here:

[http://appdb.winehq.org/appview.php?iVersionId=1554](http://appdb.winehq.org/appview.php?iVersionId=1554)

---

### Post by chaddiesel on 2008-06-24
I have wine but I don't understand why it's doing this. 
Any ideas?

---

### Post by RiceMonster on 2008-06-24
Well are you following the guide? 

First install the gecko engine with:
```
wine iexplore http://winehq.org
```

Then, install steam with:
```
wine start SteamInstall.msi
```

By the way, never run wine with sudo/as root.

---

### Post by chaddiesel on 2008-06-24
Well, i guess i'm not using the guide. I need to find the guide.

I'll start out with what you've got.

---

### Post by RiceMonster on 2008-06-24
I posted the guide earlier ;). Click this link then scroll down a bit:

[http://appdb.winehq.org/appview.php?iVersionId=1554](http://appdb.winehq.org/appview.php?iVersionId=1554)

My post earlier pretty much covered it (it's pretty simple).

---

### Post by chaddiesel on 2008-06-24
here is what i get....

```
chadwick@Beast-desktop:~$ wine start SteamInstall.msi
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
fixme:exec:SHELL_execute flags ignored: 0x00000500
Application could not be started, or no application associated with the specified file.
ShellExecuteEx failed: File not found

chadwick@Beast-desktop:~$ wine start /home/chadwick/Desktop/SteamInstall.msi
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
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
chadwick@Beast-desktop:~$ wine start SteamInstall.msi
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
fixme:exec:SHELL_execute flags ignored: 0x00000500
Application could not be started, or no application associated with the specified file.
ShellExecuteEx failed: File not found

```

I've also tried giving it the location of the file on the desktop and I get...
```
chadwick@Beast-desktop:~$ wine start /home/chadwick/Desktop/SteamInstall.msi
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
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

---

### Post by chaddiesel on 2008-06-24
Does that SteamInstall.msi file need to be in a certain directory before it is commanded to "wine start"?

---

### Post by RiceMonster on 2008-06-24
hmmm. Wine is a headache sometimes.

Here's a few things to try:
1) The troubleshooting options in the guide I posted
2) run winecfg, then go to Graphics and select "Emulate a Virtual Desktop"
3) get the latest version of wine (1.0) if you don't have it already (the one in the respositories is out of date).

Here's instructions on how to get the latest version for Ubuntu:
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Also, it doesn't need to be in a certain directory.

---

### Post by RiceMonster on 2008-06-24
Are you sure you saved the file on your desktop? The error you're getting seems like it can't find the file.

---

### Post by chaddiesel on 2008-06-24
yeah, i am running 7.1 because my system doesn't seem to work with 8.04. I had steam running great before I tried to update to hardy and I wrecked the system. Had to use my old 7.1 live cd to get linux back on my hard drive.

---

