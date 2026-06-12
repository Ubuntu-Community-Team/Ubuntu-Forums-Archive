---
title: "Internal error failed to initalize HAL!"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by LarryJ2 on 2008-05-20
OK, round and round we go.  It's fixed, it's not fixed.  Gracious sakes!

1. Upon loging in to Hardy 8.04 GDM (gnome), I get an error message and lack internet connectivity among other problems.   The error  pop up window  announces "Internal error failed to initiazlize HAL!" The only solution I have found is to open a terminal and enter the command
> ~$ sudo /etc/init.d/dbus restart
2. I read that the problem might be the sound module for my KWorld TV card.  So I blacklisted it in /etc/modprobe.d/blacklist then rebooted:
> #[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=755077&page=2](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=755077&page=2)
#f you have a TV tuner card and are experiencing similar issues, chances are that it is the audio component of your tuner card
blacklist saa7134_alsa
But alas the same error HAL not init'd persisted.

3. I read that the kernel  2.6.21-12  would work if selected from the grub boot menu.  Tried that... didn't work. (Neither does 2.6.24-16 which is the current kernel in my installation "DISTRIB_RELEASE=8.04")

4. In the launchpad bug reporting area,  I read the problem might be in the priority given to  S20hal.  So I tried various combinations in /etc/init.d/rc2.    Nothing helped.

Has anyone successfully posted a fix for this problem?  (Apparently it comes and goes,  I see references clear back to fiesty)
:confused:

---

### Post by Psykotik on 2008-05-20
I had the same issue. Resolved doing a
```

sudo apt-get --reinstall install dbus
```

and 

```
sudo dpkg-reconfigure hal
```

Don't know if both are necessary, but since it resolved my problem...

---

### Post by Xerius_fire on 2008-05-20
I have this same problem but I can't restore it using 

sudo /etc/init.d/dbus restart

because avahi-daemon comes up [FAIL] when I run it. I can't restore HAL without restoring my internet first. Anybody know a fix?

---

### Post by LarryJ2 on 2008-05-20
For me, "sudo apt-get --reinstall install dbus" and "sudo dpkg-reconfigure hal" restores my network (that is I can connect to the internet through eth0) but the "fix" doesn't survive a reboot.  Reboot and I get the "Internal Error Failed failed to initialize hal...." message box again .  Another artifact, if I click System intending to "restart",  there is a delay (about 30 seconds) between clicking System and the appearance of the shut down choices (Restart, Suspend, Shutdown etc).

---

### Post by LarryJ2 on 2008-05-21
For benefit of those following this thread.  Apparently a fix has been proposed for a future version of Hardy Heron 8.04.1.   Read more here:

[https://bugs.launchpad.net/bugs/227838](https://bugs.launchpad.net/bugs/227838)

which relates this from Canonical:

** Changed in: gdm (Ubuntu Hardy)
       Target: None => ubuntu-8.04.1

---

