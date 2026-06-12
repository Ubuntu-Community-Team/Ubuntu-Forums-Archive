---
title: "oafiid:gnome_clockapplet error"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by humby on 2008-11-28
Hello - just installed Ubuntu on my 2GB USB drive. Once I launch it I get the following error:

> the panel encountered a problem while loading oafiid:gnome_clockapplet

Can anyone direct me as to how to fix this?

I have Googled it but all the threads seem to be bug reports yet no valid solution provided... they were like 2005 and 2006 threads so I thought maybe a solution is present now.

---

### Post by Michael.Godawski on 2008-11-28
Try this:

```
sudo apt-get install -f libgnomekbd-common libgnomekbd2 libgnomekbdui2
sudo apt-get install gedit gnome-applets-data gnome-applets gnome-app-install
```

Taken from:
[http://dreamlinuxforums.org/index.php?action=printpage;topic=3194.0](http://dreamlinuxforums.org/index.php?action=printpage;topic=3194.0)

---

### Post by humby on 2008-11-28
OK this might sound stupid but how do I get into the "command terminal" mode?

---

### Post by Michael.Godawski on 2008-11-28
Open up the terminal which can be found in Applications > Accessories > Terminal 
Copy and paste one command, execute it with enter; then the next one:).

I guess you get through the login window and are able to use the desktop as such?

---

### Post by humby on 2008-11-28
Not really - it freezes on launch, so I can't really do anything from within the GUI.

Anyone - can you tell me how to enter the Terminal without logging into the desktop?

---

### Post by humby on 2008-11-28
Bumping - please help. I'm so close to using a Linux platform for the first time and yet so stuck...

---

### Post by theozzlives on 2008-11-28
> **humby said:**
> Not really - it freezes on launch, so I can't really do anything from within the GUI.

Anyone - can you tell me how to enter the Terminal without logging into the desktop?

hit esc during the 3 sec that GRUB loads and choose recovery mode

---

### Post by humby on 2008-11-28
> **Michael.Godawski said:**
> Open up the terminal which can be found in Applications > Accessories > Terminal 
Copy and paste one command, execute it with enter; then the next one:).

I guess you get through the login window and are able to use the desktop as such?

I put my USB drive on my notebook and it didn't freeze like my desktop does. So I was able to open the Terminal. And I typed the first command but I get the following error:

apt-get: error while loading shared libraries /usr/lib/libstdc++.so.6: cannot read file data: input/output error

---

