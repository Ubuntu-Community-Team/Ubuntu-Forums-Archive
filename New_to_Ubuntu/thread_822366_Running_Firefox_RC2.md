---
title: "Running Firefox RC2"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by UnWarierMage224 on 2008-06-08
Hi folks, 

So I downloaded the .tar.bz2 file from Mozilla (Firefox RC2) and I untarred the folder to my desktop. What's the code to run RC2 out of this folder (so I don't have to uninstall FF 3.0b5?) 

I tried changing into this directory and running the command "firefox" (sans quotes) but all I got was running 3.0b5 instead of RC2. 

Also tried running gksudo firefox and updating it... didn't get anything.
Standard Ubuntu repos do not have RC2... do I have to add any more repos? 

Thanks, 

-'Mage

---

### Post by Nepherte on 2008-06-08
In the folder you untarred should be a executable file called firefox. Just run that one.

---

### Post by Bubba64 on 2008-06-08
Even better this link will give you the launchpad url and it will automatically install saving all your goodies with it.
[http://www.ubuntugeek.com/how-to-install-firefox-3-rc1-in-ubuntu-hardy.html](http://www.ubuntugeek.com/how-to-install-firefox-3-rc1-in-ubuntu-hardy.html)
It says rc1 but the repository is now sending rc2
If you don't want to overwrite what you have just open the file and there is a folder you can hit to get it to run

---

### Post by jardeeq on 2008-06-08
Try this command in unpacked directory:

```

./firefox

```

If you type only name of the executable, Linux looks for it in directories included in system PATH variable, which does not contain current directory for security reasons. "." (dot) is representing current directory.

---

### Post by UnWarierMage224 on 2008-06-08
so I did get FF RC2 working. Thanks guys. 

Now something I've been trying for ages to figure out... where does ubuntu keep all its program files, per se?

Example: If I install a program from the repos, say thunderbird, then run the command "thunderbird" from a terminal - what is the full path that is being executed? 

-'Mage

---

### Post by Nepherte on 2008-06-08
The typical location is somewhere in /usr. It can be /usr/lib, /usr/share. If you want to find the all the locations of the files of an installed program:
```
locate programname
```

---

### Post by shifty_powers on 2008-06-08
```
/usr/bin
```

---

### Post by The Cog on 2008-06-08
In a standard Hardy install, there is a file firefox in /usr/bin, but it is just a symbolic link to /usr/bin/firefox-3.0 which in turn is a symbolic link to /usr/lib/firefox-3.0b5/firefox.sh which is the real program.

Be aware that you cannot launch a new version of firefox while you have an older version running (or vice versa) because the launcher will just open another window with the currently running version.

---

