---
title: "failing to update flashplayer in ubuntu 12.10"
date: 2013-09-17
forum: New to Ubuntu
---

### Post by yath2 on 2013-09-17
Hie guys, i need your help.i have installed ubuntu 12.10 with windows 8 and it installed well however, the terminal is not installing flashplayer as it is tells me it has pertially installed it and cannot download the other portion. on running the command; sudo apt-get updates, this is what it gives me: ~$ sudo apt-get update

E: Malformed line 56 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.

need your help as even the software centre is launching and shutting immediatelly.

---

### Post by Impavidus on 2013-09-17
The first part, "cannot download the other portion", means the installation script for flashplugin-installer cannot download the actual flash plugin. The package itself only contains the installation script, not the player itself. This has something to do with legal stuff. It may be there was a glitch in your server or so. Try again later.

The second part, "E: Malformed line...", means something is wrong with your sources.list. Could you post your file /etc/apt/sources.list? We need specifically line 56, but it may be easiest if you post the entire file.

---

### Post by ibjsb4 on 2013-09-17
Welcome to the forum :)

[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

```
cat -n /etc/apt/sources.list
```

And please post the output.

---

