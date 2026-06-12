---
title: "Where are the programs installed to in Ubuntu?"
date: 2012-09-04
forum: New to Ubuntu
---

### Post by random20150727 on 2012-09-04
Where is the Ubuntu equivalent to the "Program Files" in Windows? I have spent an hour looking all over the internet trying to find it. i want to create a launcher to a program but I cannot find where the programs are installed.

---

### Post by PaulW2U on 2012-09-04
This might help - [http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

---

### Post by BlinkinCat on 2012-09-04
Hi,

You may wish to look at this too -

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

Cheers - ;)

---

### Post by random20150727 on 2012-09-04
So how do I create a launcher to my desktop? I do not know where the programs are so I cannot create a launcher to them.

---

### Post by PaulW2U on 2012-09-04
The link in post #2 shows that programs or binaries are located in the /bin, /sbin, /opt and /usr/bin directories.

Use the locate command in a terminal window to search for the program if you know the name of the binary, e.g. locate <filename>.

---

### Post by deadflowr on 2012-09-04
/usr/share/applications.

Note this isn't where your programs are installed, but it is an easy way to execute your programs. I simply open up nautilus and f3 an extra pane, then in the second pane change it to desktop in the side pane then copy(not move)my application to the desktop folder.

---

### Post by houseworkshy on 2012-09-04
Synaptic package manager can be used in a diagnostic way too.  Left click on any installed package and it will open a window, in that window is an "installed files" tab which will show both the files and where they are.

---

### Post by oldos2er on 2012-09-04
> **houseworkshy said:**
> Synaptic package manager can be used in a diagnostic way too.  Left click on any installed package and it will open a window, in that window is an "installed files" tab which will show both the files and where they are.

And you can see the same info in the terminal with ```
dpkg -L <package name>
```

---

### Post by TheMTtakeover on 2012-09-05
> **1dustpelt said:**
> Where is the Ubuntu equivalent to the "Program Files" in Windows? I have spent an hour looking all over the internet trying to find it. i want to create a launcher to a program but I cannot find where the programs are installed.

When I first came to ubuntu I was looking for the same thing but from what I understand there is no folder like program files or an app folder like on osx. But use what have other people have posted and uiu should be able to get through it.

---

### Post by mcduck on 2012-09-05
The "which" command will tell you where a program's executable is located:
```
which programname
```

Although in almost every case any user-level application's executable will be in /usr/bin/*nameoftheprogram*. ;)

For the rest of the files, you usually don't need to worry about them. If the aplication has system-wide configuration files, you should find them in /etc. And any user-specific config fiels will of course be in each user's home. Documentation should be in /usr/share/doc/*nameoftheprogram*, and any random stuff with no better place in /usr/share/*nameoftheprogram*.

---

