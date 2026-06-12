---
title: "passwordless user account"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by techno-mole on 2008-07-13
hello, ive been trying to set up a user account for my son (he's 4) on kubuntu (8.04) ive added him as a user but i cant seem to enable the passwordless login feature, ive gone through the login manager steps to do it, but it still asks for a password, and it wont let me put a simple one, eg - dog or something that a 4 year old wouldnt have too much trouble typing in.

so is there a safe method to create a user account for my son, just so he can play games, use the internet (cbeebies website etc etc) that doesnt need him to enter a password at the login screen ?
cheers in advanced for any help.

---

### Post by Vishal Agarwal on 2008-07-13
U can do it by using Login window preferences.

Go to System->Administration->Login Window.

In Login Window preferences, there is the security tab.

There u will find your problem solution.

---

### Post by techno-mole on 2008-07-13
ive tried that (using kubuntu at the moment)
system settings - advanced - login manager, then you go to convenience and enable passwordless login.
only it doesnt work, it still asks for a password when you try to log in with the user account, there is a way to sort it out though, it involves editing a shadow file (or something like that) see this - 
[http://ubuntuforums.org/showthread.php?t=513820&highlight=passwordless+login](http://ubuntuforums.org/showthread.php?t=513820&highlight=passwordless+login)

it does work, although i was a little worried about doing it, but it seems to be working okay.
cheers

---

### Post by Dr Small on 2008-07-13
Try:
```
sudo passwd -u *username*
```

---

### Post by The Cog on 2008-07-13
You can set a short password like "dog" using this command:
**sudo passwd username**
because root is allowed to set shorter passwords.

Setting blank passwords is a little harder - see this thread (I haven't tried it myself though):
[http://www.linuxforums.org/forum/misc/26641-how-make-passwd-accept-blank-passwords.html](http://www.linuxforums.org/forum/misc/26641-how-make-passwd-accept-blank-passwords.html)

---

### Post by lazyart on 2008-07-13
maybe autologin for your son's account?

---

### Post by techno-mole on 2008-07-14
cheers for the help, i dont knwo why it wouldnt work through the settings menus etc, but i tried the method in the post i linked to and its working fine, all he has to do is select his little icon and press enter.
cheers again.

---

### Post by darrelljon on 2008-08-31
I have the same problem. It simply doesn't work graphically.

---

