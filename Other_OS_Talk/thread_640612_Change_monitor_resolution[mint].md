---
title: "Change monitor resolution[mint]"
date: 2007-12-14
forum: Other OS Talk
---

### Post by suffer1989 on 2007-12-14
I recently installed mint onto my sisters PC, and the resolution is 800X600. How can you change it to 1024X768 ?

Their PC is connected to the internet, and i have installed the latest Nvidea drivers. 
 

I myself rum Ubuntu 7.10 and XP MCE. Gotta say, Ubuntu is [SIZE="6"][COLOR="Black"]very stable[/COLOR][/SIZE], as compared to windows, but a little less intuitive.....

---

### Post by Technoviking on 2007-12-14
I'm moving your post a section of the forums where people can discuss other Linux distros. You may want to ask people on the Linux Mint forums ([http://linuxmint.com/forum/](http://linuxmint.com/forum/)).

---

### Post by wolfen69 on 2007-12-14
> **suffer1989 said:**
> I recently installed mint onto my sisters PC, and the resolution is 800X600. How can you change it to 1024X768 ?

Their PC is connected to the internet, and i have installed the latest Nvidea drivers. 
 

I myself rum Ubuntu 7.10 and XP MCE. Gotta say, Ubuntu is [SIZE="6"][COLOR="Black"]very stable[/COLOR][/SIZE], as compared to windows, but a little less intuitive.....

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by mips on 2007-12-14
One way would be to edit the /etc/X11/xorg.conf file to include more resolutions.

But then again I have never used Mint, will soon though as I downloaded the iso a few days ago.

---

### Post by dpar on 2007-12-14
I find that just about any fix that will work on Ubuntu, will work on Mint.

---

