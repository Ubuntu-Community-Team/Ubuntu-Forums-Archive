---
title: "Ubuntu 12.04  and program lock out"
date: 2012-09-05
forum: New to Ubuntu
---

### Post by TFSinclair on 2012-09-05
I'm using Ubuntu 12.04 and loaded a program from the software center.  This program is "FLDIGI" and is a ham radio digital and logging program.  This program worked well for a few days and then would not load. When I looked it up in "files", I  found the program but almost all of the program files have a padlock on them. I can reasoably assume that this is why the program will not load.

Any ideas why this happened and suggestions on how I might correst it??

---

### Post by Bashing-om on 2012-09-05
TFSinclair;  Hi !

   The pad lock symbol denotes that as the current user you do not have permissions/authority to do anything with these files.

Suggestion: Fire up nautilus with administrative authority (gksudo nautilus),and change the access/permissions. Insure that the program "FLDIGI"  is not started in admin mode.

[INDENT]hth <==BDQ

[/INDENT]

---

### Post by shad0w_walker on 2012-09-05
That means they are owned by a user that you don't have rights to (Almost certainly root)

If you've found the files outside of your /home/ folder then DO NOT change any permissions on them. Those are the actual program parts and will almost certainly have some kind of issue if you start randomly changing permissions.

If you open nautilus (File browser) and goto your home folder, then press CTRL + H it will show all the hidden folders for your user. These will be folders/files beginning with a .  like .mozilla or .config

There should be a folder that is named after the program (Might need to dig into a couple of folders like Gnome-config to find it)
This is where all the settings for the program are stored. These are the files that you have permission to alter. If there is a problem, it is almost certainly with these.

When you've found the folder, you can rename it (Chuck -old on the end or some such) or delete it entirely. When you run the program, it should create a new version of the folder with all the default settings.
Hopefully this will get your program up and running again. If it doesn't delete the programs new settings folder and then use software centre to uninstall/reinstall it.

---

### Post by Bashing-om on 2012-09-05
+1 on sounder advise.
[INDENT]BDQ

[/INDENT]

---

### Post by TFSinclair on 2012-09-06
In doing what was suggested above, I ran into another issue that has me stopped and stumped.  To accomplish what was suggesteed above, I needed to enter my password. I did so and was told  that this password was incorrect.
I opened  "user accounts" to check that password and it is a five character string that I do not know.  My password is   13 characters long.
When I try to change that 5 character string to what it should be, it needs the current password that I did not creat and do not have.
How do I delete the five character string when I do not know what the string is??? :sad:

---

### Post by TFSinclair on 2012-09-07
Bump

---

### Post by shad0w_walker on 2012-09-08
If you're being asked for a password, i'm assuming you're following the advice posted before mine. As the other poster said, try mine. It's safer for the system over all rather than poking around as root. 

The password it's asking for will be the same one you use to login with.

---

