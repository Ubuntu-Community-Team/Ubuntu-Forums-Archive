---
title: "How do you re-install the desktop?"
date: 2013-12-28
forum: New to Ubuntu
---

### Post by justinchen044 on 2013-12-28
Hello, Yesterday i messed around and tried to install gnome 13.10 without really knowing what i was doing (bad idea, i know). After a couple of hours, i uninstalled it (tried) using ppa - purge. Now when i boot up my computer, there's a gnome splash screen. When i try to use unity, the background is completely black.

So, how do you re-install / reset everything related to the desktop?

After all this is over, would a good fellow recommend a book that teaches all this technical stuff?

Thanks in advance :D

---

### Post by vanadium on 2013-12-28
As a beginner, the easiest way of reparing this is a reinstall. It takes less than half an hour nowadays. Make sure you have a copy of user data (documents, pictures, ...) in a safe place.

---

### Post by steeldriver on 2013-12-28
What do you mean exactly by "background is completely black"? is the Unity desktop otherwise functional (launcher, dash etc)? or is it a completely empty desktop?

---

### Post by justinchen044 on 2013-12-28
What i mean by black desktop is that the desktop picture is completely black. Launcher and menu bar are functional. However, it freezes when i minimize a app sometumes, and i have to shutdown from tty1. Shutdown had its own problems. Instead of showing the ubuntu screen, it shows a gnome icon. Then it asks me something about low graphics, then it shuts down.

So, how do you back up applicarion files?,i have some steam games i dont fee) like download ing again

---

### Post by vanadium on 2013-12-29
Try first wether perhaps it is the account settings that are corrupt. As your system is still working, you can create a new user. Do that, then log in on the new user's account. If the problem persists, you know it is a system wide issue. If it isn't, it is a user config problem.

You can reinstall an Ubuntu system without erasing the disks. That way, you could revert to a working system without having to reinstall everything. This is not guaranteed to work, though. The most clean approach after messing up with your system remains a reinstall, which takes about 30 minutes.

---

### Post by steeldriver on 2013-12-29
First I'd try resetting your own Unity settings using the instructions here --> [http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html](http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html)

Then make sure you're using lightdm not gdm

```
sudo dpkg-reconfigure lightdm
```

After that, to get rid of the gnome splash stuff you could try

```
sudo update-alternatives --config default.plymouth
```

and making sure the ubuntu option is selected - I *think* that is what worked for me in the past.

---

