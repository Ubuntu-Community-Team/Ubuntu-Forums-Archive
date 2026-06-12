---
title: "Applications self start during startup"
date: 2023-03-22
forum: New to Ubuntu
---

### Post by skywalker007 on 2023-03-22
Hi

When I restart my laptop, SKYPE that I have previously installed always starts on its own even if it was closed when I previously shut down. I know there are settings in windows where you can activate apps to do this / stop them from doing this.

How would I do it in ubuntu to stop this app from starting on its own every time?

Thanks
Johan

---

### Post by TheFu on 2023-03-23
Skype is one of the tools that violates norms for startups.  

Depending on which DE you are using, there's a Desktop User's Guide, which will explain how to control startup programs on login. [https://help.ubuntu.com/stable/ubuntu-help/index.html.en](https://help.ubuntu.com/stable/ubuntu-help/index.html.en) is for 22.10.  You probably want 22.04, the most recent LTS. It can be found there too.  That's for the Gnome4 desktop used by the default "Ubuntu Desktop" install. If you are running XFCE, LXQt, Mate, or some other DE, look for their version of the Desktop Guide.

I suspect Skype won't show up in the normal location for startup. You'll want to duck-search for the specifics to disable skype.  I think Zoom might do something just as evil.  Most other applications will follow in the normal autostartup techniques for the DE.

I duck-searched for skype startup: [https://askubuntu.com/questions/517780/how-do-i-stop-skype-from-auto-launching](https://askubuntu.com/questions/517780/how-do-i-stop-skype-from-auto-launching)

---

### Post by ActionParsnip on 2023-03-23
[https://ubuntuforums.org/archive/index.php/t-2460369.html](https://ubuntuforums.org/archive/index.php/t-2460369.html)

---

