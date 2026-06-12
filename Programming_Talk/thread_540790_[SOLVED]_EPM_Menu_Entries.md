---
title: "[SOLVED] EPM Menu Entries"
date: 2007-09-02
forum: Programming Talk
---

### Post by jediborger on 2007-09-02
If anyone else here has experience using EPM to create some simple .deb packages for script programs (python, ruby, etc) what have you done to get a menu entry in the menu? I have the .desktop file put in /usr/share/applications with everything else but it doesn't show up in the menu. Is there a command that I need to run? I've tried installing the debian menu but that didn't help. I have a simple three file python program that I want to have a menu entry but everything I've tried has failed.

---

### Post by nanotube on 2007-09-02
> **jediborger said:**
> If anyone else here has experience using EPM to create some simple .deb packages for script programs (python, ruby, etc) what have you done to get a menu entry in the menu? I have the .desktop file put in /usr/share/applications with everything else but it doesn't show up in the menu. Is there a command that I need to run? I've tried installing the debian menu but that didn't help. I have a simple three file python program that I want to have a menu entry but everything I've tried has failed.

i use epm for the ubuntuzilla project...

but i suspect that your problem is not with epm, but with the content of your .desktop file, maybe? have you given it a "type=application" and the "categories=application;yourcategory"? look at some existing .desktop files to see what they should contain (if you haven't already).

when you put stuff into /usr/share/applications, it should just show up, there's nothing else you need to do. (that works for me).

---

### Post by jediborger on 2007-09-02
I wrote my .desktop file off of looking at others in the /usr/share/applications directory. Actually I figured out that gnome put it under the "Other" category on the menu. Not what I want, I'd rather it be under the Internet category since it's a AOL dialer. So here's my .desktop file and maybe someone else will see what I'm doing wrong here.
```
[Desktop Entry]
Name=gPenggy AOL Dialer
Comment=AOL Dialer
Exec=gpenggy
Icon=/usr/share/pixmaps/gnome-talk.png
Terminal=false
Type=Application
Categories=Application;Internet
Encoding=UTF-8
```

---

### Post by jediborger on 2007-09-02
Well after some quick tinkering. I noticed that several other applications used the "Network" listing, not "Internet" despite the name on the menu. So I changed my .desktop file to list ```
Categories=Application;Network
``` and suddenly it showed up in the correct place. Thanks for the help, maybe this will help someone else out there.

---

