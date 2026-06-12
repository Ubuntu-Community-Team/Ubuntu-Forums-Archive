---
title: "[SOLVED] Root Account"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by mal_conductor on 2008-07-22
I am up and going on Ubuntu.  All help is much appreciated.

Some questions:

1) I remember having a password for ROOT (when I used Red Hat for a few weeks some years back).  Is a ROOT password not necessary in Ubuntu?

2) I see that the account used to install Ubuntu is used as Administrator.  How do I log off once I have finished doing an "administrator" task?  For example; to create a new user I unlock the User Tool by putting in the admin password.  How do I lock it up again so I don't remain logged on as Admin?

3) How do I know if I have WINE installed?

4) How do I enable the wireless radio to see my wireless home network?

5) How do I change the order in which the Operating Systems are shown when booting up?

6) If I plug in a USB Memory stick, How do I unplug it?  Is there an unplug button (like Windows has) and then the system tells me it's safe to remove the USB key?

7) If I unmount the USB port, does it get mounted automatically next time I insert a USB key into the port or will I have to manually mount the port?

Thank you for your help.  Please respond to any/all of the questions above.

Cheers!

---

### Post by andrewc6l on 2008-07-22
Here are a few answers:

1. No, you don't need the root password. Ubuntu uses sudo to do the equivalent. If you want a root shell, you can sudo sh.

2. sudo expires after 5 minutes or so. You actually aren't logging in as a root user, you're just temporarily asking for root powers. (This is part of why sudo is better than using a root login :-)

3. aptitude search wine. If it's got an "i" in front, it's installed.

6. Right click on the icon on the desktop and select "Eject Volume".

7. Mine get mounted every time I insert them, whether or not I unmount them before ejecting.

---

### Post by aysiu on 2008-07-22
I thought ```
sudo -i
``` was the way to get a root shell.

---

### Post by a0u on 2008-07-22
[LIST=1]
[*]The root account is [locked by default]("https://help.ubuntu.com/community/RootSudo").  You should not need the root password on a day-to-day basis.
[*] "Administrator" in GNU/Linux is not the same concept as it is in Windows.  You are always implicitly a restricted user; whenever you need to perform an administrative function (e.g., using the sudo command), you are prompted for your password.  There is a timeout for sudo, so root privileges are not permanent.
[*] Simply enter "wine" in the terminal.  If the command exists, then Wine is installed.  Alternatively, you can search for the package "wine" in Synaptic ("System -> Administration -> Synaptic Package Manager") to see if it is installed.
[*] Without further details, I can't really tell...check the [WiFi documentation]("https://help.ubuntu.com/community/WifiDocs").
[*] You need to [modify the GRUB configuration file]("http://www.gnu.org/software/grub/manual/html_node/Configuration.html").  You can do it manually, but there are also [GUI frontends]("http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=grubeditor").
[*] In GNU/Linux, "unplugging" is called "unmounting".  Simply right-click the drive's icon and select "Unmount".
[*] Normally, the drive will be automounted.  For more information, check the [USB mounting]("https://help.ubuntu.com/community/Mount/USB") documentation.
[/LIST]
 I hope you will enjoy using Ubuntu. :)

---

### Post by redfox1160 on 2008-07-22
To get root access in the terminal (if you need it) type
```
sudo -s
```

---

### Post by aysiu on 2008-07-22
I think *sudo -i* may be better, since it uses root's environment: ```
username@ubuntu:~$ sudo -s
[sudo] password for username:
root@ubuntu:~# $HOME
bash: /home/username: is a directory
root@ubuntu:~# exit
exit
username@ubuntu:~$ sudo -i
root@ubuntu:~# $HOME
-bash: /root: is a directory
root@ubuntu:~# 
```

---

### Post by aysiu on 2008-07-22
I think *sudo -i* may be better, since it uses root's environment: ```
username@ubuntu:~$ sudo -s
[sudo] password for username:
root@ubuntu:~# $HOME
bash: /home/username: is a directory
root@ubuntu:~# exit
exit
username@ubuntu:~$ sudo -i
root@ubuntu:~# $HOME
-bash: /root: is a directory
root@ubuntu:~# 
```

---

### Post by Joeb454 on 2008-07-22
> **aysiu said:**
> I thought ```
sudo -i
``` was the way to get a root shell.

> **redfox1160 said:**
> To get root access in the terminal (if you need it) type
```
sudo -s
```

Preferably the first one - using the 2nd can cause Environment Variable issues - which can result in root owning your home dir ;)

Edit: Too late

---

