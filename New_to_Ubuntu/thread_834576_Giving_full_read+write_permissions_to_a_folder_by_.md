---
title: "Giving full read+write permissions to a folder by all users and apps?"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by linkmaster03 on 2008-06-19
RuneScape, and Java applet game in Firefox, needs to make a cache folder for some files. It says it cannot do that because it has no permissions. I tried reinstalling Firefox. No dice.

It says to make /rscache. I made it, but it could not read/write to it still. 

How do I give full read+write permissions to a folder by all users? I tried chmod 777 and sudo chmod 777, no luck either.

---

### Post by stchman on 2008-06-19
> **linkmaster03 said:**
> RuneScape, and Java applet game in Firefox, needs to make a cache folder for some files. It says it cannot do that because it has no permissions. I tried reinstalling Firefox. No dice.

It says to make /rscache. I made it, but it could not read/write to it still. 

How do I give full read+write permissions to a folder by all users? I tried chmod 777 and sudo chmod 777, no luck either.

```
chmod -R 777 <desired folder>
```

---

### Post by linkmaster03 on 2008-06-19
Didn't work. :( I may add that these things work in Opera fine but not Firefox.

---

### Post by linkmaster03 on 2008-06-20
I'm thinking this is an easy fix because RuneScape works in Opera, just not Firefox. :(

---

### Post by linkmaster03 on 2008-06-21
Anyone? The person who helps me fix this gets: :popcorn:

---

### Post by smo0th on 2008-06-21
sudo chmod -R 777 <desired folder>

this should work.

---

### Post by sam_delta on 2008-06-21
you can also right click a folder, and click on properties, then select the permissions tab

if you do not currently own the folder, then open nautilus as root ```
gksudo nautilus
``` a window manager will open, navigate to your folder, right click it, then properties,,and select the permissions tab

sam

---

### Post by cardinals_fan on 2008-06-21
```
chown -hR *your username*:users /your/directory
```

---

### Post by linkmaster03 on 2008-06-22
None of those worked! :( :confused:

This started happening after I once accidentally opened Firefox with sudo.

---

### Post by vanadium on 2008-06-22
> his started happening after I once accidentally opened Firefox with sudo. 

There is the origin of your problem. Some of the configuration files of the program have wrong permissions (or probably are owned by root rather than the user) because of this.

---

### Post by Biggy on 2008-06-22
Download [NScripts]("http://www.gnomefiles.org/download.php?soft_id=2194&where=http%3A%2F%2Fwww.nanolx.org%2Ffree%2FNScripts-3.2.tar.bz2") extract from archive,copy nscripts folder and paste to /home/name of user/.gnome2/nautilus-scripts

---

### Post by linkmaster03 on 2008-06-22
I copied it to /home/brad/.gnome2/nautilus-scripts/NScripts and RuneScape still doesn't work.

---

### Post by Biggy on 2008-06-22
if you copy and paste nscript folder to nautilus-scripts folder, right click in folder you want to get full permissions ,se screenshot atach 

click rootilus to open the same folder full perm

---

### Post by linkmaster03 on 2008-06-22
I tried editing the permissions from there, but that didn't help either. :(

---

### Post by Biggy on 2008-06-22
if you open Rootilus folder ,you have root access,permissions on folder and file into .

can delete,edit,copy/paste

---

### Post by vanadium on 2008-06-23
You should try looking for hidden folders or configfiles (hidden = starts with a dot; in nautilus: View - Show hidden files) of the runescape application in your home folder. Deleting these will cause them to be recreated - correctly this time - the next time you run this application.

---

### Post by linkmaster03 on 2008-06-23
vanadium, I didn't think of that one. I deleted all the current cache folders for the game but it still doesn't work...

---

### Post by Stefanie on 2008-06-23
have you tried reinstalling firefox?

---

### Post by linkmaster03 on 2008-06-23
Yes.

---

### Post by vanadium on 2008-06-23
The next quite drastic thing to try is to purge - uninstall java, then reinstall it. This should get rid of all downloaded java code of the program and hopefully all configuration. Then reinstall java and visit the site again, this time with a Firefox as normal user. I once removed a java citrix client this way before I discovered that deleting .citrix woul do the trick.

Since you are using Synaptic, the process, albeit drastic, is without risk for your system. Short of being able to locate the little file likely causing the issue ...

---

### Post by linkmaster03 on 2008-06-23
Wow, thank you vanadium!! For anyone else having this problem, run this command:

```
sudo apt-get remove --purge icedtea-gcjwebplugin
```

---

