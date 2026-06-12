---
title: "ubuntu install no packages !??"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by Ancientmtk on 2008-05-08
I did a fresh install of Ubuntu 8.04, and I cannot find alot of the packages that normally come with other linux distro, such as ssh client, autofs, nfs, csh, etc.

Are those apps not included in the default installation? I cannot use apt-get since my comp has firewall that does not allow me to get thru.  Am i doing something wrong during installation?

Thx all:popcorn:

---

### Post by Ancientmtk on 2008-05-08
Can anyone help me out a bit?

---

### Post by Scheater5 on 2008-05-08
While I can't speak for most of those packages off the top of my head (but I'm pretty sure the c shell is excluded by default), ubuntu does leave out some packages you may be accustomed to, being a desktop-centric distro.  Since you can't use apt, you can find all the packages in ubuntu on [packages.ubuntu.com]("packages.ubuntu.com").  You may also be interested in a program called "[apt-on-cd]("http://www.google.com/url?sa=t&ct=res&cd=1&url=http%3A%2F%2Faptoncd.sourceforge.net%2F&ei=IDAjSLC-L5Si8ATb5MWRDA&usg=AFQjCNGemwqF2mshxzVQmsQKWwfYIQRA5w&sig2=tNhA7Lbu7NGFKa-tTuBuwQ")" which lets you make a repository on a CD that apt can use.

---

### Post by Ancientmtk on 2008-05-08
Thanks man.  I'll try it out asap!  thanks for the help.

---

### Post by Ancientmtk on 2008-05-08
Hm 1 more issue... is there a way to dl an appl without having to deal with all the dependencies?

Lets say if i want to download autofs, it needs alot of other dependencies which make it a lil too hard to dig thru.  

Are there installation discs that have these packages like that of Red Hat?

---

### Post by Scheater5 on 2008-05-08
You can make your own via apt-on-cd.  Such cd's exist, but to my knowledge they aren't official.  You can find them at all the popular linux cd distributors and online sales, and you can probably find them floating around torrent sites.  
If you have access to a computer sans-firewall, you can use apt's "download only" option to download all the packages and dependencies you need, and then copy them to a cd or pen drive per instructions [here]("http://ubuntuforums.org/showthread.php?t=20217").

---

