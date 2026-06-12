---
title: "HOWTO: Use normal root instead of Sudo"
date: 2004-11-26
forum: Outdated Tutorials &amp; Tips
---

### Post by UnixDaemon on 2004-11-26
I'm sure theres probably a howto something like this already laying around somewhere on the forums, but for you people who want classic root access by just using the su command and typing in your password instead of using sudo commands, just do this on the command line:

```
sudo passwd
``` 

Now you will need to type in your account password to login to root of course like normal sudo commands in Ubuntu.

After you do that it'll prompt you with this:

```
Enter new UNIX Password:
```

enter the password you want in there for root access. Then it'll prompt you with this:

```
Retype new UNIX password:
```

Just type the same password you typed above of course, hit enter and it should say:

```
passwd: password updated successfully
```

Now you should be able to type in su and the password you just put in and you should now have old styled root access for those who don't like Ubuntu's sudo commands ;)

---

### Post by p!=f on 2004-11-26
[http://www.ubuntulinux.org/support/documentation/faq/root](http://www.ubuntulinux.org/support/documentation/faq/root)

If you want to use su, typing "su -" may save you some headaches.

---

### Post by mongolito404 on 2004-11-29
You can also use```
sudo su -
``` to get into a root shell :)

---

### Post by lmo on 2006-12-13
linux administrator needs root/su sometimes.

Add a root password using sudo (or by some means)
sudo passwd root
password: [my_secret]
Enter new UNIX password: [roots_secret]
Retype new UNIX password: [roots_secret]
passwd: password updated successfully


Become root
su
Password: [roots_secret]


Fix invalid MIT-MAGIC-COOKIE-1

Add the following 2 lines to /root/.bashrc
DISPLAY=:0.0
export DISPLAY


'Steal' a user .Xauthority file
by adding the following 2 lines to /root/.bashrc
XAUTHORITY=/home/[some_user]/.Xauthority
export XAUTHORITY


Link /usr/X11R6/bin/xauth (stupidly missing for gksu in dapper)
ln -s /usr/bin/xauth /usr/X11R6/bin/xauth


Make gksu act like su
gconf-editor
apps -> gksu
 uncheck sudo-mode


Now I can login as root on the text console (ctrl-alt-F1), 
use su, use gksu, gksudo, run gvim (Yea!)


My 2 cents: 
 'sudo rm -r /*' is as effective for total destruction as su.
 sudo safety is imaginary.
 sudo has its gotchas.
 not everything works with sudo the same way it does with su.
 sudo is cool for its purposes, but it doesn't replace su.
 sudo is ok, and linux as linux with root is ok.
 nobody make me believe that linux does not need su/root sometimes.

---

