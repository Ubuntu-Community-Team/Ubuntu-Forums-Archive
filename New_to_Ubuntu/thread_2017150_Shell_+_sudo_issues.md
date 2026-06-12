---
title: "Shell + sudo issues"
date: 2012-07-04
forum: New to Ubuntu
---

### Post by pooloo1 on 2012-07-04
Fresh install of Ubuntu 12.04 64-bit.
First set of commands used:
```
root@server:~# apt-get update
root@server:~# apt-get upgrade
root@server:~# adduser newguy
root@server:~# moduser -a -G sudo newguy
```

Logged in as newguy.
```
newguy@server:~# sudo
sudo: must be setuid root
```

Before I do any chmod's or chown's I want to know what I did wrong or if I did anything wrong? This is a FRESH install on a VPS, thus I am using a shell and no GUI.

---

### Post by Krytarik on 2012-07-05
> **pooloo1 said:**
> 
```
root@server:~# adduser newguy
root@server:~# [COLOR=Red]**moduser -a -G sudo newguy**[/COLOR]
```... what I did wrong or if I did anything wrong?
The latter command should instead be:
```
[COLOR=Blue]**usermod**[/COLOR] -a -G [COLOR=Blue]**admin**[/COLOR] newguy
```Regards.

---

### Post by mlentink on 2012-07-05
```
sudo
```is not used as a command by itself, but to precede other commands for which elevated privileges are needed. As in:
```
sudo cp picture /usr/share/backgrounds/picture
```
usage: sudo [-D level] -h | -K | -k | -V
usage: sudo -v [-AknS] [-D level] [-g groupname|#gid] [-p prompt] [-u user
            name|#uid]
usage: sudo -l[l] [-AknS] [-D level] [-g groupname|#gid] [-p prompt] [-U user
            name] [-u user name|#uid] [-g groupname|#gid] [command]
usage: sudo [-AbEHknPS] [-C fd] [-D level] [-g groupname|#gid] [-p prompt] [-u
            user name|#uid] [-g groupname|#gid] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AknS] [-C fd] [-D level] [-g groupname|#gid] [-p prompt] [-u
            user name|#uid] file ...

---

### Post by Fernhill Linux Project on 2012-07-05
You are trying to add 'newguy' to the admin group, which is now called 'sudo' in 12.04. This command will work 

```
adduser newguy sudo
```

---

### Post by matt_symes on 2012-07-05
Hi

As pointed out, the group to add for admin privileges in 12.04 and greater is now sudo and not admin (although admin will work for a while).

From

[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuServer](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuServer)
> 
Up until Ubuntu 11.10, administrator access using the sudo tool was  granted via the "admin" Unix group. In Ubuntu 12.04, administrator  access will be granted via the "sudo" group. This makes Ubuntu more  consistent with the upstream implementation and Debian. For  compatibility purposes, the "admin" group will continue to provide  sudo/administrator access in 12.04.The command to add users to the sudo group is (under root)

```
usermod -aG sudo newguy
```Kind regards

---

### Post by Krytarik on 2012-07-05
> **matt_symes said:**
> As pointed out, the group to add for admin privileges in 12.04 and greater is now sudo and not admin (although admin will work for a while).
Thank you and Fernhill Linux Project for pointing that out, didn't know of that change till now. :D

---

