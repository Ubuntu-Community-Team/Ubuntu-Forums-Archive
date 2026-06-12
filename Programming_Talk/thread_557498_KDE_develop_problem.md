---
title: "KDE develop problem"
date: 2007-09-22
forum: Programming Talk
---

### Post by Z.K. on 2007-09-22
I am not sure if this is the right forum to post this in, but it was the only one that seemed appropriate.

I am new to programming in linux and I started a very simple KDE application.  It works fine and the window or gui pops up okay, but I get this error and I am not sure why.

X Error: BadDevice, invalid or uninitialized input device 166

Major opcode: 144
Minor opcode: 03
Resource id: 0x0

ksimulate: WARNING KSMLGUIClient: setXMLFile: cannot find .rc file ksimulateui.rc

the file is there though in a src sub directory.  I was wondering if someone with more knowledge of KDEDevelop could help me figure out why I am getting this error and why KDEDevelop cannot find the *.rc file even though it looks like it is where it is supposed to be.

Oh, one other thing.  I have not added any code of my own yet.  I just used what KDEDevelop created.

:confused:  ](*,)

---

### Post by csabimeta on 2007-10-19
I have the same error, when launching any programs with gui from the terminal. If I'm using dpkg, apt-get, aptitude ,etc. then too. Everythings starts up fine, but it makes me nervous. Can it be a problem vith xserver-xorgs input device configurations?.

---

### Post by csabimeta on 2007-10-19
> **csabimeta said:**
> I have the same error, when launching any programs with gui from the terminal. If I'm using dpkg, apt-get, aptitude ,etc. then too. Everythings starts up fine, but it makes me nervous. Can it be a problem vith xserver-xorgs input device configurations?.

Sorry i mean xorg.conf
But I've found the possible solution:
[http://ubuntuforums.org/showthread.php?t=212025&highlight=invalid+input+device+166]("http://ubuntuforums.org/showthread.php?t=212025&highlight=invalid+input+device+166")

---

