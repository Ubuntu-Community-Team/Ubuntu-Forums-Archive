---
title: "files locked-change permissons?"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by camppen2 on 2008-05-10
I am running Hardy Heron. I installed gcover using alien but I cannot run the program. I found the files but they have a lock icon and in properties it says I am not the owner and cannot change the permissions. I am the only user so I don't know why it locked the files and I don't know how to unlock them.
Can anyone help?

ubuntu44

---

### Post by tamoneya on 2008-05-10
this means that they are owned by root.  Chances are they should remain that way.  The program probably knew what it was doing when it installed them unless of course it is a virus which would be unlikely.  As for how to run them you should use ```
sudo gcover
``` assuming that the command you were using before was```
gcover
```

---

### Post by camppen2 on 2008-05-10
Thank you for responding.
I tried the command in the run an application box but nothing happens. I tried it in the command line and it says command not found. I checked in Synaptic and the program is installed. I was so proud of myself for figuring out how to install it and now I can't run it!I installed it using these directions
-http://www.howtogeek.com/howto/ubuntu/install-an-rpm-package-on-ubuntu-linux/ 
after downloading the rpm to my desktop.
I know there is some simple explanation. I've googled it every which way trying to figure it out but no luck.

---

### Post by tamoneya on 2008-05-10
how have you been trying to run it.  The problem is probably the fact that gcover isnt the command.  I haven't used gcover before so I don't know what it is and commands are often but not always just the program name so I assumed it was gcover as you can see in the post above.  Basically you just need to preceed what you are currently using with sudo.

---

### Post by camppen2 on 2008-05-10
gcover is an application for gnome to create cd covers, it sounds pretty neat. So what I am trying to do is run it. Sorry, I should have been clearer about that in my post. Is there a specific command to use to run an application?

---

### Post by Monicker on 2008-05-10
What is the output of the following command?

```
dpkg --listfiles gcover
```

---

### Post by camppen2 on 2008-05-10
Sorry I didn't get back to you right away, I had to leave.
This is what it came up with-
penny@penny-ubuntu:~$ dpkg --listfiles gcover
/.
/opt
/opt/gnome
/opt/gnome/share
/opt/gnome/share/locale
/opt/gnome/share/locale/es
/opt/gnome/share/locale/es/LC_MESSAGES
/opt/gnome/share/locale/es/LC_MESSAGES/gcover.mo
/opt/gnome/share/locale/hu
/opt/gnome/share/locale/hu/LC_MESSAGES
/opt/gnome/share/locale/hu/LC_MESSAGES/gcover.mo
/opt/gnome/bin
/opt/gnome/bin/gcover
/usr
/usr/share
/usr/share/doc
/usr/share/doc/gcover
/usr/share/doc/gcover/copyright
/usr/share/doc/gcover/changelog.Debian.gz
/usr/share/doc/gcover-0.1.3
/usr/share/doc/gcover-0.1.3/COPYING.gz
/usr/share/doc/gcover-0.1.3/INSTALL.gz
/usr/share/doc/gcover-0.1.3/AUTHORS
/usr/share/doc/gcover-0.1.3/README
/usr/share/doc/gcover-0.1.3/ABOUT-NLS.gz
/usr/share/doc/gcover-0.1.3/NEWS.gz
/usr/share/doc/gcover-0.1.3/ChangeLog
penny@penny-ubuntu:~$

---

### Post by Monicker on 2008-05-10
I would venture to say that this file is the one you need to run
```

/opt/gnome/bin/gcover
```

Do ALT + F2 and enter the above line in the dialog box.  If that works, then you can add a custom launcher or menu item for it.

---

### Post by camppen2 on 2008-05-10
Tried it and nothing happens. Tried it twice actually.

---

### Post by camppen2 on 2008-05-10
I looked in the file you suggested and gcover is there. I tried to open it directly (right click-open) and nothing happened again. I must have done something wrong.

---

### Post by camppen2 on 2008-05-10
I found a site-checkinstall. It says there should be files at:/usr/doc/gcover but they are in:usr/share/doc/gcover-0.1.3. Does this make a difference? All the files are there except one called "install". I guess these are text files as they are called docs? gcover is for gnome 1.4- what version does Hardy have? Guess maybe I ought to find out how to uninstall it.

---

