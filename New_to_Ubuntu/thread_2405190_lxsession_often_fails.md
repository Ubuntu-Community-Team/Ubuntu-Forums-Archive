---
title: "lxsession often fails"
date: 2018-11-02
forum: New to Ubuntu
---

### Post by cybervigilante on 2018-11-02
My lubuntu lxsession often fails so clicking on an icon doesn't start anything, and I have to restart it, but that doesn't always work either so I reboot. I tried listing it with lxsession -e and got this error.

** (lxsession:2355): CRITICAL **: 09:48:56.147: main.vala:98: Option parsing failed: Missing argument for -e

I also tried -r and got these errors, that I had to ctrl-C out of it, and for some odd reason the Safeeyes configuration screen popped up. Do they indicate what might be wrong?

** Message: 09:49:21.173: main.vala:102: Session is (null)
** Message: 09:49:21.173: main.vala:103: DE is (null)
** Message: 09:49:21.173: main.vala:107: No session set, fallback to LXDE session
** Message: 09:49:21.173: main.vala:113: No desktop environnement set, fallback to LXDE
** Message: 09:49:21.185: main.vala:134: log directory: /home/jim/.cache/lxsession/LXDE
** Message: 09:49:21.185: main.vala:135: log path: /home/jim/.cache/lxsession/LXDE/run.log

---

### Post by oldos2er on 2018-11-02
Which version of Lubuntu?

---

### Post by cybervigilante on 2018-11-02
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.1 LTS
Release:    18.04
Codename:    bionic

---

### Post by cybervigilante on 2018-11-02
Sometimes I lose the launch panel entirely. The best way to bring it back is a hard shutdown and cold start after the initial start which makes me think maybe it's just starting too soon. Is there a way to delay it from starting? I know that was sometimes necessary in windows for autostarted programs.

---

