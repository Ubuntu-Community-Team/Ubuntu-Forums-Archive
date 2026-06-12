---
title: "GKSudo nautilus launcher"
date: 2013-01-04
forum: New to Ubuntu
---

### Post by lizandeen on 2013-01-04
I've checked the forums and web but cannot find an easy way to make a 'gksudu-nautilus/open programs as root' launcher. Does one exist or am I missing the forest because of the trees! Thanks,lizandeen

---

### Post by ibjsb4 on 2013-01-04
Depends on what forest your looking for  :)

[http://ubuntuforums.org/showthread.php?p=12436572#post12436572](http://ubuntuforums.org/showthread.php?p=12436572#post12436572)

Last post att.

---

### Post by dannyboy79 on 2013-01-04
> **lizandeen said:**
> I've checked the forums and web but cannot find an easy way to make a 'gksudu-nautilus/open programs as root' launcher. Does one exist or am I missing the forest because of the trees! Thanks,lizandeen
you could just create a new launcher, using alacarte you can figure out how the program is run normally, then in your launcher you'd add gksudo in front of the command
example
```
gksudo nautilus
```
would launch Nautilus with root privelages. I would weary about launching other apps as root however, the system normally installs them and the script created to launch them has set the user which is should run as already. With that said, there are times I want a root privelaged file manager so I can perm delete stuff and I do have a gksudo thunar launcher within my Xubuntu install.

---

### Post by Frogs Hair on 2013-01-04
I have done as above  with alacarte installed and created a Nautilus Root launcher from the main menu. It opens a password prompt when selected but eliminates some steps.

---

### Post by Catbells on 2013-01-04
I think you're looking for the command    	 	 	 	 	gksu nautilus, no punctuation just a space between the two words.  If you right click a panel, you'll be able to create a custom launcher.  I'm afraid I've moved onto Kubuntu and can't check the exact details of how to do this.

---

### Post by Frogs Hair on 2013-01-04
Below is how I made mine but how the launcher is created depends on what version. methods for Gnome 2 are different than Gnome 3.

---

