---
title: "I could use some help with update...."
date: 2020-01-22
forum: New to Ubuntu
---

### Post by Avinator on 2020-01-22
I am trying to update and then upgrade and I am getting an error...

I'm using 
sudo apt-get update followed by sudo-apt-get upgrade

"The following packages have been kept back:
  aptdaemon python-apt python-aptdaemon python-aptdaemon.gtk3widgets
  python3-aptdaemon python3-aptdaemon.gtk3widgets python3-aptdaemon.pkcompat
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded."

Can anyone help ? Thanks

---

### Post by CatKiller on 2020-01-22
*apt-get* isn't the only upgrade option. The default has moved to *apt*, although I couldn't tell you what the differences are between them without looking it up. Another one is *aptitude* which handles dependencies differently to apt-get and has a neat ncurses interface if you like that kind of thing. Again, I couldn't tell you the exact differences without looking them up.

In addition to picking a different tool you can also pick different options: *apt-get dist-upgrade* or *apt full-upgrade* relax the dependency handling to allow the removal of packages to help with dependency resolution.

Or it might just be a temporary issue, and just waiting to do it will fix whatever it is.

---

### Post by Frogs Hair on 2020-01-22
Post the output the following.

```
sudo dpkg --configure -a 
```If there are errors follow any suggested commands in the ouput.

---

### Post by Impavidus on 2020-01-23
Your apt-get upgrade doesn't report any errors, so I don't expect inconsistencies in your package management.

This could be a temporary server issue. Try again later. Run **sudo apt update** again. If that doesn't resolve it, show us the contents of /etc/apt/sources.list and tell us which version of Ubuntu you use (although we should be able to tell from the contents of that file).

FWIW, I just upgraded 6 packages related to the 7 you have trouble with.

---

### Post by rsteinmetz70112 on 2020-01-23
I would try sudo ```
apt full-upgrade

```
I find that usually works with packages that have been kept back.

---

