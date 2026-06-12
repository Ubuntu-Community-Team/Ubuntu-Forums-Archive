---
title: "REstricted user account (web-cafè-ish)"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by mormor on 2008-06-18
8.04 - Guest/web-cafè/restricted user.

Is there any way I can create a second useracount with only the basics possible?

I want an account able to only do theese things:

Emesene.
Word.
Full internet experience.
Acces to music-directory
Amarock
Gnomebaker (to burn cd's.)

Thats all I want this account to be able to do. The first 3 are the most important. No acces to anything at the comp at all. : ) Thanx in advance.

All help and pointers apriciated: )

---

### Post by Hospadar on 2008-06-18
yup, make another user account, and remove them from the admin group.  This will deny them write access to anything outside of their home directory.  (they'll be able to run anything installed on the machine, and view system files, but not edit anything else, or view the files of other users).

If you have a music directory, I think probably the best way to give them access to it is to put it outside your home directory, and change the permissions so that: you are the owner, your group has read access, and then add the restricted user to your group.  (make sure your group does not have read access to your home directory, otherwise they will be able to read everything there as well)

so the process might look something like this (after you created the other user and dropped them from admin see [here]("http://www.cyberciti.biz/faq/howto-linux-remove-user-from-group/") how to do that), let's say the user's name is sally. (anything followed by a '#' is a comment, no need to type it)```
sudo mv ~/Music /home/Music #move your music directory out of your homedir
chmod -R g+r /home/Music #this gives anyone in your group (the g part) read access (the r part) to anything inside the /home/Music folder
useradd -G <your username> sally #this adds sally to your group
chmod -R og-rwx /home/<your username> #this removes any access priviledges to your home folder for anyone but yourself and root (or anyone in the administrator group
```Note also, some of these commands may require sudo, if they complain about lack of permissions, just sudo them.

Furthermore, it's possible to do all of this graphically, I just think it's a little more concise to explain it this way.  you may want to google a tutorial on "chmod" (the tool used to alter permissions) or on linux permissions in general in case either I misunderstood what you want, or if you don't understand what the heck I'm doing.
Good luck!

---

