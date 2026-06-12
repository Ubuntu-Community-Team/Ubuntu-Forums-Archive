---
title: "can xubuntu be used for a server?"
date: 2014-07-23
forum: New to Ubuntu
---

### Post by tmstare on 2014-07-23
hello,
 I am trying to use ubuntu to build a minecraft server. I would also like to be able to use the server machine as a desktop computer on occasion. I have considered dual booting ubuntu server alongside xubuntu but I am not having much luck getting that done. I don't think I understand partitioning well enough to do this. I thought it could possibly be better to do a solitary install of xubuntu if I could somehow temporarily disable the desktop so I don't waste any resources that I'm not using when the computer is only running the server. I have an older machine and it doesn't have a lot of extra resources to spare. Any opinions on what my best option is here? I have been tinkering with ubuntu off and on for a few years now and have gotten the minecraft server working on Ubuntu server but I still have a very vague understanding of it (e.g. im not sure exactly what "root" means), so I would appreciate it if you speak to me as though I'm completely ignorant, which probably isn't far from the truth :) any help would be greatly appreciated.

specs:
core2duo@ 2.9ghz
2G ram
160G HD

---

### Post by deadflowr on 2014-07-23
Sure, you can install xubuntu on a server, and vice versa as well.

If you want to stop the deskop session you need stop X, 
to do this press ctrl + alt + F1(or F2-F6)
It'll open a full screen-like terminal(console)
login like normal (username and password)
then run
```
sudo stop lightdm
```
as far as I know xubuntu uses lightdm.
This will kill X, simply.
To restart, change stop to start.

Don't know if that'll help, but it's something to ponder.

---

### Post by mastablasta on 2014-07-23
also if you install Xubuntu you don't actually need a server edition of the OS to run minecraft server.

edit serve edition is ment for webserver, mail server or any other server where no GUI is necessary. it has some preinstalled server packages.

but your game server is a completely different thing. the game provides the server software that can then be run eother on desktop or to make it more efficient on system with no GUI that will act as game server.

---

