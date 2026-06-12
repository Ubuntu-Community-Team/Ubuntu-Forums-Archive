---
title: "Can't login as root user after installing Ubuntu desktop on VDS with 15.04..."
date: 2015-12-20
forum: New to Ubuntu
---

### Post by mohaafan on 2015-12-20
Hi,

I have a Virtual Dedicated Server VDS and I installed Ubuntu server 15.04.  After installing the OS, I was able to login as root user at the terminal prompt.  I then installed Ubuntu desktop with the following command:

```
sudo apt-get install ubuntu-desktop
```

After I restarted the VDS I was brought to the login screen of the desktop gui but all I see is the guest account login window.  I don't see the root user account option.  Even if I login as guest and open the settings panel, the user account list is empty and locked.  I can't use sudo as it gives me a message stating that "permission is denied".  I can't reboot into safe mode as this is a remote server. What can I do to get root/sudo access to the Ubuntu desktop environment?

Thanks.

---

### Post by Jonathan Precise on 2015-12-21
Ok. That's going to be tricky!

I've never used a VDS, but if you in some way try to do a CTRL-ALT-F1 , you can get into a console. Login as root, and run:

```
sudo adduser *username*
gpasswd -a *username* sudo
```

to add the user *username*. Then restart the VDS, or restart lightdm.

Log in with the new user created, and then use [FONT=Courier New]sudo[/FONT] before any command that require root privileges

---

### Post by sandyd on 2015-12-21
> **mohaafan said:**
> Hi,

I have a Virtual Dedicated Server VDS and I installed Ubuntu server 15.04.  After installing the OS, I was able to login as root user at the terminal prompt.  I then installed Ubuntu desktop with the following command:

```
sudo apt-get install ubuntu-desktop
```

After I restarted the VDS I was brought to the login screen of the desktop gui but all I see is the guest account login window.  I don't see the root user account option.  Even if I login as guest and open the settings panel, the user account list is empty and locked.  I can't use sudo as it gives me a message stating that "permission is denied".  I can't reboot into safe mode as this is a remote server. What can I do to get root/sudo access to the Ubuntu desktop environment?

Thanks.

by default, the login interface (lightdm?) will not allow you to login using the root user. It will hide that user on the list. The guest account is locked down and does not allow access to root even if you have the password.

What you will need to do is create a "normal" user that can be used to login to the system
```

adduser *username*
## Give user ability to use sudo
usermod -a -G sudo *username*
```

---

### Post by QIII on 2015-12-21
As a reminder to any who follow, we do not allow discussions of any method  that may be used to log in to a graphical desktop as root.  So don't go there.

Please refer to [http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138) and to [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) for the "official" Forums Staff position.

---

### Post by mohaafan on 2015-12-22
Sorry QIII. I was unaware of that policy as I am new to linux/ubuntu and the ubuntu community.  

[SOLVED] As for my issue.  I solved it.  After installing ubuntu-desktop I still had sudo access as I was still at the command prompt.  So all I did was create a new user with: sudo [COLOR=#000000][FONT=Ubuntu Mono]adduser [/FONT][/COLOR]*username*

and then after I rebooted the VDS I was presented with the option of logging on with that username instead of guest. I am good to go.

Thank you all for your help.

---

