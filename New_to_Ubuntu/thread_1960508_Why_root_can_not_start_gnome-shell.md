---
title: "Why root can not start gnome-shell"
date: 2012-04-17
forum: New to Ubuntu
---

### Post by ulkoma on 2012-04-17
I've enabled the root account by setting a password for it  but not matter what I try I cant log into any DE but the default unity  one, while any other user (but root) can choose any DE 



Please dont start with the usual "it's a bad idea to log as root"
I am just trying to understand how things work

---

### Post by daslinkard on 2012-04-17
First off, Welcome to the Ubuntu Forums!

Have you tried simply logging out of your current session and logging in as "root" with the password you assigned?

<snip>

---

### Post by Frogs Hair on 2012-04-17
Even if you login to an administrator account you will still have to use a password to preform certain tasks. [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by ulkoma on 2012-04-17
Thank you for your most-welcomed answers

My question is simple: I keep choosing gnome as my DE before I log in as a root however as soon as I long in the OS transfers me to unity instead

I even tried to set the default DE to Gnome
Also I ve modified the dmrc file for the root to Session=gnome-shell but it always goes back to session=ubuntu

Any ideas?


[FONT=tahoma][/FONT]

---

### Post by nothingspecial on 2012-04-17
Logging in to a **graphical** desktop as root is not supported here.

Understanding how things work is.

So the answer must be why root can not start gnome-shell, not how to do it.

---

### Post by ulkoma on 2012-04-17
> **nothingspecial said:**
> Logging in to a **graphical** desktop is not supported here.

Understanding how things work is.

So the answer must be why root can not start gnome-shell, not how to do it.

Please change the title to "why root can not start gnome-shell"

Thank you

---

### Post by nothingspecial on 2012-04-17
> **ulkoma said:**
> Please change the title to "why root can not start gnome-shell"

Thank you

Done :)

---

### Post by coffeecat on 2012-04-17
Just to add to what nothingspecial has said, I have edited out a link from one post that describes how to log in to the graphical desktop as root. Please see the forum policy on this:

[http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)

> Our "line in the sand" is with tutorials or posts that show people how to LOG IN to a graphical desktop (gnome, KDE, etc) as root. This is completely inappropriate and unnecessary.


---

