---
title: "Ubutu 18.04 LTS taking too much time to load"
date: 2019-05-15
forum: New to Ubuntu
---

### Post by alexemperor on 2019-05-15
Iam using ubuntu 18.04. It takes about a minute to show login screen and then after logging in it takes a while for the showing desktop.


Login screen showing following


gnome
gnome flashback
gnome xorg
ubutu
untutn on wayland


I only need gnome flashback. Do i need to uninstall others ? Will that help to increase the speed.


Also when i try to upgrade using sudo apt-get update && sudo apt-get upgrade, its showing like below




E: The repository 'http://ppa.launchpad.net/webupd8team/sublime-text-3/ubuntu bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

---

### Post by Rubi1200 on 2019-05-15
Hi,

Not able to help directly with first issue, though it may also be related to the second one.

You need to disable that PPA in order to upgrade and also better to use "apt" rather than "apt-get".

Go to Software and Sources >> Other >> uncheck the PPA for webupd8team

Then in the terminal:

```
sudo apt update && sudo apt upgrade
```

Hopefully, that should resolve some of the issues.

If you are wanting to do an upgrade to 18.10 then backup all your data and issue the following command:

```
sudo apt update && sudo apt full-upgrade
```

---

### Post by oldfred on 2019-05-15
I am using flashback on 18.04. 
Boot was slower as install is on SSD and used to be very quick.

Some systems need boot parameters. What brand/model system.
I made the changes posted here and it improved boot time in both my 18.04 and test install on HDD of 19.04.
[https://ubuntuforums.org/showthread.php?t=2417453](https://ubuntuforums.org/showthread.php?t=2417453)
[https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html](https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html)

---

### Post by drvshrm on 2019-05-15
Have you checked for boot time starting programs. Or just press down arrow key while starting Ubuntu, it will show you the processes running in background during startup. Check for any countdown timers running after processes...

---

### Post by alexemperor on 2019-05-18
@drvshrm How to check the boot time? 

The main issue is not showing the menus like calendar, time, shutdown and network in top right side of the screen when login using gnome flashback.

---

### Post by oldfred on 2019-05-18
You can run these commands. First is a summary of time to boot.

systemd-analyze
systemd-analyze blame
systemd-analyze critical-chain

---

