---
title: "changing folder permissions"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by dgkulzer on 2008-04-28
Hello,
I got a book on learning Python and it came with a cd with various files on it. In the book it is mentioned by the author that on his system he put it in his /usr/local/lib/python2.5/site packages folder. I tried to do that but I get a error because I don't have permissions. If I right-click and select 'Properties' I can open up the Permissions tab but at the bottom of the window it says "You are not the owner, so you can't change these permissions"

Any help would be appreciated in how I change folder permissions. Thanks

---

### Post by cm.squared on 2008-04-28
You probably don't want to change the folder permissions.  Instead what you can do is use a terminal to act as root (the name of the administrator account and owner of the directory) and copy the files into the folder.

I would copy the files into a folder on your desktop, maybe called "python".  Then open a terminal window (Applications > Accessories > Terminal) and copy and paste this command:

```
sudo cp $HOME/Desktop/python/* /usr/local/lib/python2.5/site-packages/
```

You'll be asked to enter your password to verify you have access, which you should if it's your computer (nothing will show up when you're typing but that's normal, just type your password and hit enter).

This command will copy the files into the folder that you want without having to mess with any permissions.  The reason for this is that linux/unix is designed to prevent a normal user from messing up the whole computer by placing restrictive permissions on important system files so they aren't accidentally deleted.  By issuing commands as the administrator you have the rights to modify those files, but you want to do this sparingly so you don't break things by accident.

---

### Post by dgkulzer on 2008-04-28
Cool, that worked!!

thanks cm.squared :)

---

