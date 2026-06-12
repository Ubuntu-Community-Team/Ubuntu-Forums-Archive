---
title: "gdm not starting xwindow app at login (ubuntu9.10)"
date: 2010-06-14
forum: Programming Talk
---

### Post by alibaba163 on 2010-06-14
I need to start xwindow app at login screen

I have tried to put following line /usr/bin/xeyes & (as a test), just before last line(exit 0 ) in script /etc/gdm/Init/Default

This does start xeyes and show xeyes window during bootup but that xeyes seems to disappear (not visible on screen, however i can see it running in list of running processes) when login screen arrives.

After I login xeyes dies (there is none in ps aux | grep xeyes)

Also I've done  some research and found similar thread

[http://ubuntuforums.org/showthread.php?p=9458839#post9458839](http://ubuntuforums.org/showthread.php?p=9458839#post9458839)

Can anyone tell me what this guy means when he says he switched to kdm, where and what files did he make changes.

Any suggesstions.

---

