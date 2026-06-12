---
title: "how to replace ubuntu with lubuntu 13.10 without losing my files"
date: 2013-11-08
forum: New to Ubuntu
---

### Post by fatharraxman on 2013-11-08
please if possible with terminal step by step for newbies

---

### Post by speartip on 2013-11-08
Do you want to reinstall Lubuntu over Ubuntu or just add the LXDE Desktop as an alternative at login?
If the former did you install Ubuntu with a separate home partition?
If the latter you could just try:```
sudo apt-get install lubuntu-desktop
``` then choose at login which desktop environment you want.

---

### Post by fatharraxman on 2013-11-08
I installed Ubuntu without other partition I do not like partitions, Then I installed LXDE, but I wounder if there is any way to replace Ubuntu for full lubuntu system without removing my documents and stuffs and without partitions, just as one do for upgrading!

I appreciate your kind response thank you

---

### Post by speartip on 2013-11-08
I think what you're asking is possible, but personally, I would back up all my important documents, music etc to an external source, then install Lubuntu & copy your stuff back again.

---

### Post by Impavidus on 2013-11-08
In principle you could just install lubuntu-desktop and then uninstall all Ubuntu-specific packages. These are some instructions on how to do that: [http://www.psychocats.net/ubuntu/purelubuntu](http://www.psychocats.net/ubuntu/purelubuntu). Unfortunately this is only for 11.10–13.04, so you may have to do some things differently. If you don't uninstall them, most will only take some disk space without using other resources.

---

### Post by fatharraxman on 2013-11-08
I did it 
I removed gnome completely from tty by alt +F3 usinng sudo apt-get purge gdm then installed unity and installed lubuntu and here it is full lubuntu thank YOU guys

---

