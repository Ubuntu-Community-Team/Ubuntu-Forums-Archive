---
title: "Blank screen at startup"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by Stephen_A on 2008-06-07
Running 8.04 on a Dell 1150. At startup the machine locks up to a blank screen. Pressing Esc and running it in recovery mode two or three times, then Ubuntu works. 
If anyone can suggest anything I can do to fix this, I'd appreciate it.

---

### Post by iaculallad on 2008-06-07
Boot normally and when you're on the blank screen, press Ctrl+Alt+F2 to get you to your terminal:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Then you try answering (with your utmost knowledge) the questions that pops out. Restart your system afterwards.

```
sudo shutdown -r now
```

---

### Post by Stephen_A on 2008-06-07
Thanks for your answer. I've installed updates and it seems to boot OK now. The command you gave generated: 

```
Package `x-server-org' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: x-server-org is not installed

```

Is this a problem?

---

### Post by bumanie on 2008-06-07
I would try this code in terminal to install xorg. Hope it works.
> sudo apt-get update && sudo apt-get install xorg Seemingly the installer did not quite work properly.

---

### Post by Stephen_A on 2008-06-07
Thanks for that. I'll give it a try when I get to the Ubuntu box.

---

