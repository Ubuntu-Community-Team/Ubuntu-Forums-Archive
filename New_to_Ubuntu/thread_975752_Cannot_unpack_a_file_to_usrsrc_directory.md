---
title: "Cannot unpack a file to /usr/src directory"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by jesuis personne on 2008-11-08
Downloaded a package for Lazarus programming environment that needs to be extracted to the usr/src directory. The install that's managed by Ubuntu doesn't work. This operation should be simple but isn't because of permission problems. I know about root and sudo and Ubuntu restrictive security policies and I have googled this thing for hours. Any simple way of doing this or should I give up and do it all at the command line? What's the use of the GUI then? Wouldn't I be better served by using a distro that allows me to log in as root? This thing is going to kill Ubuntu. Any help shorter than a dissertation would be greatly appreciated.

---

### Post by Steve1961 on 2008-11-08
How about running sudo nautilus.  Then just right-click the file and extract to /usr/src

---

### Post by oldos2er on 2008-11-08
> **Steve1961 said:**
> How about running sudo nautilus.  Then just right-click the file and extract to /usr/src

 Since Nautilus is a graphical program, call it with "gksu" instead of "sudo."

---

