---
title: "Kubuntu 13.10: Two new issues after upgrade from 13.04"
date: 2013-10-25
forum: New to Ubuntu
---

### Post by Matt_Smigielski on 2013-10-25
Hello all,

I recently upgraded from Kubuntu 13.04 to 13.10 and I see a couple new issues:

1.) Pressing the Power button immediately turns off the computer despite me asking it to prompt me for a dialog. This worked in 13.04. I found the bug below and ran "sudo apt-get install qt5-default qttools5-dev-tools" but it still doesn't work. Does anyone know of this issue or how to fix it?

[https://bugs.launchpad.net/ubuntu/+source/kde-workspace/+bug/1124149](https://bugs.launchpad.net/ubuntu/+source/kde-workspace/+bug/1124149)

2.) For any screensaver except a blank screen, the process stays active and consumes a lot of CPU even after it turns off. Multiple processes stay running. I tried Googling for any known issues but didn't find anything. Does anyone know of this issue or how to fix it?

---

### Post by Matt_Smigielski on 2013-10-25
1.) I've managed to fix the first issue by commenting the last line of /etc/acpi/powerbtn.sh:

#/sbin/shutdown -h now "Power button pressed"

I don't really understand why this works but it does... so here's a possible solution for anyone who finds this post.

3.) I also noticed another issue - whenever I log it, I get the gear icon in the taskbar telling me I have updates when I really don't. This happens every time I log in. Any ideas?

---

### Post by undoIT on 2013-10-30
> **Matt_Smigielski said:**
> 1.) I've managed to fix the first issue by commenting the last line of /etc/acpi/powerbtn.sh:

#/sbin/shutdown -h now "Power button pressed"

Wow! Thanks for the fix. This has been an issue for every Kubuntu release over the past maybe 5 years now. It affects every laptop I install on, Macbook Air, Lenovo Thinkpad T410S/T420S etc etc...

Are there any plans to fix this? Just one little # sign would do it. All other distros I use properly support a prompt for action when pressing the power button (Fedora KDE, Sabayon KDE, etc...). It's really annoying when you are expecting a prompt (perhaps to suspend or logout) and the laptop immediately goes into shutdown.

---

