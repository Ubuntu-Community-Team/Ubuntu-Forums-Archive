---
title: "Get URL of chrome browser instantly"
date: 2022-01-26
forum: New to Ubuntu
---

### Post by kilbha on 2022-01-26
Hello community,

            I am new to ubuntu. I am trying to get the URL of chrome browser. I worked with session files to get URL information. I am getting the URL data but it's not useful for my requirement. Is there any way I can get URL instantly as soon as you access URL using chrome? In windows OS, we have Automation Element( .NET ) to grab URL instantly but there is no automation element in Ubuntu version of .NET. Is there any way we can achieve this? Can we access GUI of ubuntu to get information of GUI appllicaiton? Suggestions are appreciated.

---

### Post by TheFu on 2022-01-27
I don't know about chrome. I've never used it, but I do use chromium.

In Ubuntu, chromium runs inside a sandbox environment (this is the default since 20.04) as a snap package, so that memory isn't available to other processes.  There are ways to remote control the keyboard and mouse which work due to security flaws in X11, but those are quite hackish.  xdotool and cnee come to mind, but there are others.  I doubt any will work with Wayland, but I don't honestly know.  There are ways to install chromium so it doesn't use snap packaging, but this isn't Canonical's choice. They are pushing snaps really hard - even when they break other core things that have worked a specific way 25+ yrs.

Might look into web testing tools that can remotely control a browser, then you'd know the URL.

Are you certain that session files on Linux don't contain the same information?  A little grep or strings|grep on the files should be quick enough to do.   ~/.config/chromium/Default/Sessions seems to have some URLs inside it.

```
$ strings ~/.config/chromium/Default/Sessions/Sessions* | egrep  'http' 
```
The permissions of the files and directory means that only the owner userid can see those, so other users cannot.  I only use chromium in a private firejail, so none of my sessions touch any real storage, but I did run 1 with a --private toggle and that URL did show up in the Session_* file.

---

### Post by kilbha on 2022-01-31
Thank you TheFu.

I worked with session files but it will take time to update session files. I need to get URL as soon as it is accessed.

---

### Post by TheFu on 2022-01-31
The only way I know to do it, is to use a proxy server and prevent all clients from having any external access that doesn't got through the proxy. This is how corporations do it.  The URLs would be in the proxy logs.  Monitoring those or setting up white-lists/black-lists or even looking at the content is relatively easy (after getting the networking correct).  Plus, proxy servers work for all devices on the network, not just 1 application.

---

