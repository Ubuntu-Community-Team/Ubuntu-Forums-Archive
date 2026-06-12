---
title: "Firefox, Flash, Artsd &amp; Notification Sounds"
date: 2006-11-24
forum: Outdated Tutorials &amp; Tips
---

### Post by Buddha443556 on 2006-11-24
Like many I've run into problems with Flash and no-sound. I've tried many solutions but none seem to work. I final discovered the problem wasn't Firefox or Flash but artsd. artsd is KDE sound system. A simple test to see if this is also your problem is to kill artsd in KSysGuard. If Flash now has sound then bingo there's your problem. Killing artsd isn't exactly an elegant solution to the no-sound with flash problem because you lose your System Notification sounds. So here's what I did.

1. System Settings>Sound & Multimedia> Uncheck "Enable the sound system" and this kills artsd.
2. System Settings>Sound & Multimedia>System Notifications>Player Settings> Use External Player browse and select /usr/bin/ogg123 or a player of your choosing. This gets System Notification sounds working again.

Hope this helps someone else. I'll be back to refer to it next time I reinstall Kubuntu no doubt. ;)

---

