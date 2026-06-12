---
title: "update error, can't find details for it"
date: 2013-02-27
forum: New to Ubuntu
---

### Post by fr33z0n3r on 2013-02-27
I just updated a new laptop Ubuntu 12.10 install.  Its been off for a week, and was only recently built.

I checked for updates, and about 80MBs of updates were found.  After several minutes I saw an error, something about error with package.  I don't have the details.  I figured it would handle the error as needed and give me any necessary follow-up steps, like a mandatory roll-back or something.

Nothing happened when I clicked the OK button.  The updates said a reboot was needed, so I did.

Since then there are no new updates.  But how do I    1) determine what happened, and 2) if I need to repair something?

I checked in the dpkg.log file, but didn't notice any obvious error messages.  

Thanks!

---

### Post by audiomick on 2013-02-27
I wouldn't be too worried just yet. What I would do is 

```
sudo apt-get update
```

and then 

```
sudo apt-get upgrade
```

Look at the man page
```
man apt-get
```

for an explanation of the update and upgrade options of apt-get.

Basically, the first command refreshes the package list and the second one makes sure all installed packages are on the newest available version.

See if those commands show you any errors. I believe that if your system has hung up on a package somehow, those commands will either sort it or throw up an error message about what has gone wrong.

---

### Post by grahammechanical on 2013-02-27
> After several minutes I saw an error, something about error with package. I don't have the details. 

That is a pity. It makes it very difficult to give advice. Ubuntu 12.10 is a stable Ubuntu release. It will not get updates every day. Especially if it is set to notify us of updates weekly, two weekly or never. What setting do you have?

Open the Dash and search for Software Manager or Software Updater or something like that and open it and check what the setting is under the Updates tab. Software Manager may check for updates or allow you to tell it to check for updates. Do so.

It should also be possible to open System Settings>Details and tell it to check for updates. Or you can open Software Sources and get to the Updates tab that way.

The point is, you need to check for updates and then make a note of any error messages.

Regards.

---

### Post by Rokkross on 2013-02-27
Just for future reference, when you see an error try to remember it (or better yet, copy and paste it if you can). Errors are important when it comes to knowing what problem is actually happening. This probably doesn't help much, but it will help us help you in the future.

---

### Post by deadflowr on 2013-02-27
If you ever have errors on updating and need to relocate them, for whatever reason, they are stored in the file history.log in the /var/log/apt directory.

---

### Post by fr33z0n3r on 2013-02-27
> **deadflowr said:**
> If you ever have errors on updating and need to relocate them, for whatever reason, they are stored in the file history.log in the /var/log/apt directory.

Thnaks deadflowr!   Found this.  It appears to be the related error.


Start-Date: 2013-02-27  09:34:48
Commandline: aptdaemon role='role-commit-packages' sender=':1.75'
Upgrade: libglapi-mesa:i386 (9.0-0ubuntu1, 9.0.2-0ubuntu0.1), thunderbird-globalmenu:i386 (17.0.2+build1-0ubuntu0.12.10.1, 17.0.3+build1-0ubuntu0.12.10.1), libpurple0:i386 (2.10.6-0ubuntu2.1, 2.10.6-0ubuntu2.2), thunderbird:i386 (17.0.2+build1-0ubuntu0.12.10.1, 17.0.3+build1-0ubuntu0.12.10.1), thunderbird-gnome-support:i386 (17.0.2+build1-0ubuntu0.12.10.1, 17.0.3+build1-0ubuntu0.12.10.1), libxatracker1:i386 (9.0-0ubuntu1, 9.0.2-0ubuntu0.1), libgnutls26:i386 (2.12.14-5ubuntu4.1, 2.12.14-5ubuntu4.2), linux-image-extra-3.5.0-25-generic:i386 (3.5.0-25.38, 3.5.0-25.39), linux-libc-dev:i386 (3.5.0-25.38, 3.5.0-25.39), thunderbird-locale-en-us:i386 (17.0.2+build1-0ubuntu0.12.10.1, 17.0.3+build1-0ubuntu0.12.10.1), flashplugin-installer:i386 (11.2.202.270ubuntu0.12.10.1, 11.2.202.273ubuntu0.12.10.1), linux-headers-3.5.0-25-generic:i386 (3.5.0-25.38, 3.5.0-25.39), linux-image-3.5.0-25-generic:i386 (3.5.0-25.38, 3.5.0-25.39), linux-headers-3.5.0-25:i386 (3.5.0-25.38, 3.5.0-25.39), libgl1-mesa-dri:i386 (9.0-0ubuntu1, 9.0.2-0ubuntu0.1), libpurple-bin:i386 (2.10.6-0ubuntu2.1, 2.10.6-0ubuntu2.2), thunderbird-locale-en:i386 (17.0.2+build1-0ubuntu0.12.10.1, 17.0.3+build1-0ubuntu0.12.10.1), libgl1-mesa-glx:i386 (9.0-0ubuntu1, 9.0.2-0ubuntu0.1), transmission-common:i386 (2.61-0ubuntu2.1, 2.61-0ubuntu2.2), transmission-gtk:i386 (2.61-0ubuntu2.1, 2.61-0ubuntu2.2)
Error: Sub-process /usr/bin/dpkg returned an error code (2)
End-Date: 2013-02-27  09:36:21

---

