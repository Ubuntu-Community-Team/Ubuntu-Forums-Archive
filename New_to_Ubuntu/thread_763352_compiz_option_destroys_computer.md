---
title: "compiz option destroys computer"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by Zopiac on 2008-04-22
so i have gotten my computer up and running perfectly fine, and have customized it nicely. But earlier today i went to the compiz fusion manager and decided to try a feature that i cant remember what it is called, but lets you draw on the screen. Once i activated that, my computer was pretty much going a frame a minute, it eas so slow. I could not do anything but pitifully move the cursor, so i forced a restart. when i logged back in, the login sound was made, and it went to the tan screen that temorarily comes on when i log in, its the default color for the desktop background; no biggy. but that went on for about 5 minutes, so i restarted and tried again , but even that failed. I can still boot ubuntu from the cd, but cannot find out how to, say, disable compiz for my account from there, or disable the draw-on-screen function. please, please help!!! (will repost if i get no replies and the post is on page 2 or so, desperato)

---

### Post by myusername on 2008-04-22
could be your video card driver or that you don't have a powerful enough video card 
edit: to disable compiz you right click the desktop and click change wall paper (or something like that) and click the desktop effects tab and you can disable it from there or you can use the terminal and enter sudo metacity -replace

---

### Post by redbob on 2008-04-22
Don't worry, guy. What you should do is not so difficulty.
- Log by command-line (Ctrl-Alt-F1);
- stop gui interface (sudo /etc/init.d/gdm stop);
- Uninstall compiz (sudo apt-get remove compiz*);
- Rebuild your gdm configuration (sudo dpkg-reconfigure xserver-xorg);
- start gui interface (sudo /etc/init.d/gdm start).

I already suffered from that yet. In my case I had a ATI card. These kind of graphics is terrible to deal with compiz!!
:popcorn:

---

### Post by Zopiac on 2008-04-23
> **redbob said:**
> Don't worry, guy. What you should do is not so difficulty.
- Log by command-line (Ctrl-Alt-F1);
- stop gui interface (sudo /etc/init.d/gdm stop);
- Uninstall compiz (sudo apt-get remove compiz*);
- Rebuild your gdm configuration (sudo dpkg-reconfigure xserver-xorg);
- start gui interface (sudo /etc/init.d/gdm start).

I already suffered from that yet. In my case I had a ATI card. These kind of graphics is terrible to deal with compiz!!
:popcorn:

i couldnt figure out what all to do :P but i figured my own way out. thx anyways!!!:lolflag:

i, when i went to the Login screen, i clicked on options and selected i think the fourth startup session after the safe(?) one. this seemed to work.

by the way, why does :lolflag: have goku's hair? lol ( <-- maybe thats why)

---

