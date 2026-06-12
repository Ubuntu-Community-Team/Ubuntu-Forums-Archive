---
title: "Attempting to package Aptana... unsuccessfully."
date: 2009-08-25
forum: Packaging and Compiling Programs
---

### Post by brennydoogles on 2009-08-25
Hey all, I am trying to package Aptana (64bit), and having some issues. I created my directory structure:
```
AptanaStudio1.5.1/
|-- DEBIAN
|   |-- control
|   `-- control~
`-- usr
    |-- bin
    |   `-- aptana
    `-- share
        |-- applications
        |   `-- AptanaStudio1.5.1
	|       `-- All of the Aptana Stuff
        `-- pixmaps
            `-- Aptana-Studio.png

```

and then ran some commands:
```

sudo chown -R root.root AptanaStudio1.5.1/
dpkg -b AptanaStudio1.5.1/ ../AptanaStudio-1.5.1.deb
sudo chown -R brendon.brendon AptanaStudio1.5.1/

```
I now have a .deb that installs, but doesn't work correctly when installed. I am attaching the .deb, could anyone take a look and see what I may be doing wrong?

Ok, I am in the process of uploading the .deb somewhere else since it is to big for the forums... I will update with the link when it is ready.

---

### Post by Brandon Williams on 2009-08-25
My best guess is that the directory structure you've created isn't correct. Are you certain that you put all of the files where they would be if you simply ran 'make install'? What happens if you install all of the same files to the correct directories on your system by hand? Does aptana work correctly for you in that case?

---

### Post by brennydoogles on 2009-08-25
> **Brandon Williams said:**
> My best guess is that the directory structure you've created isn't correct. Are you certain that you put all of the files where they would be if you simply ran 'make install'? What happens if you install all of the same files to the correct directories on your system by hand? Does aptana work correctly for you in that case?

Since Aptana is written in Java (it's almost identical to eclipse in setup since it can be installed as an eclipse plugin and is a branch of eclipse) you do not actually compile it. The directory structure was created by the aptana team, and I simply copied it from their .zip file into /usr/share/applications/ for the deb. I then created a bash script that launches it, and put it into /usr/bin/. This same method of install works great in my home directory... I am just trying to create a .deb so that it integrates better with the menus, and so that it is easily usable with people who are new to Linux.

---

### Post by brennydoogles on 2009-08-26
Ok, so I was finally able to get the .deb up on some hosting... and here it is : 
::Edit:: I removed the broken .deb from my hosting upon creating a working one. ::/Edit::

It is pretty big, 209MB, but hopefully someone will be able to figure out what I'm doing wrong. Thanks again!

---

### Post by Brandon Williams on 2009-08-26
I'm not going to download a 209MB .deb, but I'll try to help anyway, at least until someone else does the download ...

What does the script you wrote look like? I assume that it looks something like this:
```
#!/bin/sh
exec /usr/share/applications/AptanaStudio1.5.1/AptanaStudio
```
Nothing else should be required, and in fact, you don't even need the script. A symbolic link would be enough.

When you install your deb, does /usr/share/applications/AptanaStudio1.5.1/ contain? Is it a complete copy of what's in the zip file's primary directory? Do all the files have the correct permissions? And what happens when you try to start the app?

Also, just for future reference, you aren't intended to put stuff like this in /usr/share/applications/. That directory should really just contain .desktop files. You should probably put the Aptana stuff in /usr/lib/AptanaStudio1.5.1/ instead, but that's just a minor point, and should not be the reason why it isn't working.

---

### Post by brennydoogles on 2009-08-27
Ok, so I had a stupid error in my script. I had spaces in the directory name which prevented the aptana binary from being run. After fixing that, it now launches Aptana successfully. I am still having some errors with the .desktop file, namely that it isn't using the icon I have set for it (at least in KDE) the .desktop file is as follows:
```

[Desktop Entry]
Version=1.5.1
Encoding=UTF-8
Name=Aptana
Comment=An Open Source Web Development Solution
GenericName=Aptana
Exec=/usr/bin/aptana
Icon=/usr/share/pixmaps/Aptana-Studio.png
Terminal=false
StartupNotify=true
Type=Application
Categories=Application;
GenericName[en_US]=Aptana
Name[en_US]=Aptana

```
Any ideas?

---

### Post by Brandon Williams on 2009-08-27
You probably don't need to specify the full path to the png file. Try just using the base filename with the extension:
```
Icon=Aptana-Studio
```

If that doesn't work, then use the menu editor to add the correct icon to that item in your own user menu, and then look at the .desktop file that results to see if there are any distinct differences.

One other possibility is that the bad Version number is causing the Icon to not be displayed correctly. If the Version number is present, it should be 1.0. It should not be the version number of the software, but rather the version of the .desktop file spec that your file conforms to. The only Version number that I see on my system is 1.0, and only around 10% of the .desktop files have a specified Version.

---

### Post by brennydoogles on 2009-08-30
ok, turns out that using a .xpm file instead of a .png worked like a charm... could this be a KDE issue? Either way, it appears that I now have a working .deb, so thanks so much for the help! I am working on setting up a ppa for this and a few other programs (and having issues: see [this thread]("http://ubuntuforums.org/showthread.php?t=1253773")), I will add a link to my signature when it is complete!

---

### Post by Brandon Williams on 2009-08-30
Be careful ... the Aptana license expressly prohibits redistribution without their approval.

---

### Post by brennydoogles on 2009-08-30
> **Brandon Williams said:**
> Be careful ... the Aptana license expressly prohibits redistribution without their approval.

Good to know, I will attempt to obtain that! Thanks for the help!

---

### Post by pSYcl0Ne on 2011-05-24
I'm guessing they said no?

---

