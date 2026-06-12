---
title: "desktop startup script"
date: 2006-09-12
forum: Programming Talk
---

### Post by cccc on 2006-09-12
hi

I have dapper drake with Gnome and would like to start some sh programs,
vor example edonkey startup script runDonkey.sh:```

root@ubuntu:/home/eDonkey2000# ls
blacklist.txt  filters.txt  known.met  runDonkey.sh  skins
contact.dat    friend.met   log.txt    server.met    temp
edonkey2000    incoming     pref.xml   share.dat

root@ubuntu:/home/eDonkey2000# cat **runDonkey.sh**
LD_ASSUME_KERNEL=2.4.9 ./edonkey2000
```
with double click directly from the desktop.
knows someone, how it should work ?

p.s
edonkey is only an example

---

### Post by fritz_monroe on 2006-09-12
Did you add it to your start up programs section?  If not, you can get there from system then sessions.  Click the startup programs tab and put in the command.

---

### Post by Warbo on 2006-09-12
> **cccc said:**
> hi

I have dapper drake with Gnome and would like to start some sh programs,
vor example edonkey startup script runDonkey.sh:```

root@ubuntu:/home/eDonkey2000# ls
blacklist.txt  filters.txt  known.met  runDonkey.sh  skins
contact.dat    friend.met   log.txt    server.met    temp
edonkey2000    incoming     pref.xml   share.dat

root@ubuntu:/home/eDonkey2000# cat **runDonkey.sh**
LD_ASSUME_KERNEL=2.4.9 ./edonkey2000
```
with double click directly from the desktop.
knows someone, how it should work ?

p.s
edonkey is only an example

GNOME (and I think maybe KDE) use ".desktop" files, and these can be used as launchers in the menu, panel, desktop, file manager, etc. That means that you just need to go into Applications>Accessories>Alacarte Menu Editor and create a new entry. Put the command as "gksudo sh /the/whole/path/to/runDonkey.sh" (where you replace that path with the real one)

Once it has been added to the menu then you can just drag it onto the desktop, onto the panel, wherever, and disable it in the menu if you don't want it there by unticking the box next to it in Alacarte.

In that example gksudo is used to run the program as root, since the terminal in your example had a # instead of a $ (it is a pretty bad idea to run Internet-accessing programs as root by the way), then sh is used to run a shell, and the filename is the shell script to run.

You may find it useful to know that starting a script with the line "#!/path/to/executable" will make that file open with the program that path points to, for example "#!/bin/sh" will make that script open with sh automatically, so you can just use "gksudo /path/to/runDonkey.sh"

If you want to put files somewhere in the $PATH variable so that you can just use "runDonkey.sh" without specifying the path then I would recommend /usr/local/bin, since the normal /usr/bin is far too cluttered to be managable by anything other than a package manager.

I seem to have gone pretty in-depth here, so I hope I covered everything.

PS: I prefer MLDonkey from [http://mldonkey.sourceforge.net](http://mldonkey.sourceforge.net) anyway :)

---

