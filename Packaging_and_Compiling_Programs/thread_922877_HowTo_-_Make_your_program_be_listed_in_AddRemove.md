---
title: "HowTo - Make your program be listed in Add/Remove"
date: 2008-09-17
forum: Packaging and Compiling Programs
---

### Post by Vadi on 2008-09-17
I wrote a short guide on this here: [https://wiki.ubuntu.com/GnomeAppInstallDesktopDatabaseAdd](https://wiki.ubuntu.com/GnomeAppInstallDesktopDatabaseAdd)

Should appeal mostly to PPA/.deb makers. Let me know how it works out.

---

### Post by jpeddicord on 2008-09-20
Moved from Tutorials & Tips; it's an offsite tutorial.

---

### Post by Vadi on 2008-09-20
I believe forums.ubuntu.com and wiki.ubuntu.com are the same site...

---

### Post by jpeddicord on 2008-09-20
> **Vadi said:**
> I believe forums.ubuntu.com and wiki.ubuntu.com are the same site...

Technically, but I meant offsite as in "outside of the forums."

> The following items are not considered as tutorials.

    * Posts that contain only links to offsite pages or blog posts. To be admitted, the tutorial must be a single, complete on-site post. Files or packages can be hosted offsite, but a tutorial must include all the pertinent information here, on the forums.

[http://ubuntuforums.org/showthread.php?t=677396](http://ubuntuforums.org/showthread.php?t=677396)

---

### Post by qforce on 2008-09-25
update-app-install <directory of .desktop>

... which directory??? I put my .desktop file into /usr/share/applications, and after running update-app-install /usr/share/applications, the add/remove database is completely **empty**. Can somebody please explain to me what I'm doing wrong?

update-app-install without the directory parameter works, but only if I put my .desktop file into /usr/share/app-install/desktop.

---

### Post by Vadi on 2008-09-25
I ran into that issue also and would investigate it. The thing is that if you specify the directory, it works faster then... but seems to wipe the original db.

The syntax is **update-app-install -d <directory of .desktop>** though.

---

### Post by qforce on 2008-09-25
> **Vadi said:**
> The syntax is **update-app-install -d <directory of .desktop>** though.

Oops... Could've been worse though. I almost posted "update-install-app" or something like that :rolleyes:

Concerning the directory issue, I took a quick look at the python script that handles the above command (this one: /usr/lib/python2.5/site-packages/AppInstall/update.py) and it looks as if the default desktop directory is set to /usr/share/app-install.

Btw, am I the only one who thinks AppInstall is very poorly documented?

---

### Post by Vadi on 2008-09-25
I talked with mvo, who is the guy who wrote it (and a lot of other things. He's quite busy. I guess that explains the lack of documentation - unless you missed the stuff in bzr), and he said that yes the -d flag is supposed to overwrite the db and set it to just the ones in the directory.

He said that a patch for making it actually update the normal db, with a directory only, would be relatively easy to implement - but he's too busy for now and would only have time during 8.10 beta. 

But since you seem to know Python (I know zero!), do you think you can do that? Maybe add a "-u DESKTOP_DIR, --uodate-desktop-dir=DESKTOP_DIR" flag, where it would search *only* in the given directory, and update the main db?

---

### Post by qforce on 2008-09-25
> **Vadi said:**
> But since you seem to know Python (I know zero!), do you think you can do that? Maybe add a "-u DESKTOP_DIR, --uodate-desktop-dir=DESKTOP_DIR" flag, where it would search *only* in the given directory, and update the main db?

Yes, I do know Python. However, I'm quite busy myself, just trying to get the next release of my [open source baby]("http://sourceforge.net/projects/docfetcher") out of the door. In addition to that I do not think I have enough Python experience to mess around with someone else's code, especially when it's code that made it into the official Ubuntu release.=;

---

### Post by Vadi on 2008-09-25
Well, it gets reviewed first and whatnot.

Don't worry, I patched apturl myself with zero knowledge of python (just looked at existing code). It got in ok ;)

(but was like a 4 line patch heh)

---

### Post by qforce on 2008-09-25
Okay, I took a closer look at the Python code. Forget it! Since the code is very sparsely commented, it would take days to disassemble this thing. Only God and the author know what does what. =;=;=;

---

