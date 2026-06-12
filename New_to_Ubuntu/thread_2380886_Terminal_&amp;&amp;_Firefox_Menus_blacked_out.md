---
title: "Terminal &amp;&amp; Firefox Menus: blacked out?"
date: 2017-12-23
forum: New to Ubuntu
---

### Post by kenji_03 on 2017-12-23
[IMG]https://ibb.co/mMGuVR[/IMG]
Terminal is black, but will accept commands.

All of FireFox's menus (context, , information, hamburgers, etc) are black. But otherwise the browser works fine.

I tried updating my grapics ([1]("https://askubuntu.com/questions/760934/graphics-issues-after-while-installing-ubuntu-16-04-16-10-with-nvidia-graphics")), disabled hardware acceleration for Flash ([2]("https://superuser.com/questions/434762/disable-hardware-acceleration-for-flash-player-in-linux")), ensured Flash was running the latest version, and did a "sudo apt-update" as well as a "sudo apt-upgrade". Anyone have any leads?

I'm running the gaming distro of Ubuntu 16.4

---

### Post by vasa1 on 2017-12-23
Please post the outputs of```
cat /etc/*-release
```and```
inxi -Fxz
``` You may need to install *inxi* from the software center if you don't have the program.

---

