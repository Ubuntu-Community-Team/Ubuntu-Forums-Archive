---
title: "how to edit sshd_config?"
date: 2015-03-22
forum: New to Ubuntu
---

### Post by junkone on 2015-03-22
I want to edit sshd_config to make my machine accesible remotely using ssh. however when i open it in gedit, it is Read-only.
How do i make it editable and then make a change. 
When i navigate to that file, it says that i am not the owner and cannot change the permissions.

I am logged in the ubuntu desktop as root user and dunno how to fix this.
please help.

---

### Post by matt_symes on 2015-03-22
Hi

> I am logged in the ubuntu desktop as root user and dunno how to fix this.

There is no need to do this and it is a security risk. 

Log in as a user with admin (sudo) privileges and type this to run gedit with admin rights.

```
pkexec gedit /etc/ssh/sshd_config
```

You can also use the terminal and nano.

```
sudo nano /etc/ssh/sshd_config
```

Kind regards

---

### Post by DuckHook on 2015-03-23
Are you sure pkexec works with gedit out of the box? Mine doesn't (14.04). Had to install [this]("http://www.webupd8.org/2015/03/how-to-run-gedit-and-nautilus-as-root.html") gedit policy in policykit to make it work.

---

### Post by matt_symes on 2015-03-23
Hi

> **DuckHook said:**
> Are you sure pkexec works with gedit out of the box? Mine doesn't (14.04). Had to install [this]("http://www.webupd8.org/2015/03/how-to-run-gedit-and-nautilus-as-root.html") gedit policy in policykit to make it work.

Thanks for the info. 

It's been a while since i used vanilla Ubuntu so... and i mostly use the terminal for editing configuration files.

Kind regards

---

### Post by DuckHook on 2015-03-23
> **matt_symes said:**
> ...Thanks for the info.My pleasure. Always happy if I can help.> It's been a while since i used vanilla Ubuntu so... and i mostly use the terminal for editing configuration files.This whole issue/problem/mess with the question of properly invoking a root *gedit* coincidentally was raised by *TheFu* in [this]("http://ubuntuforums.org/showthread.php?t=2269093&page=6&p=13248751#post13248751") recent thread. In summary, recent versions of Ubuntu have deprecated gksudo, which isn't even installed by default anymore. Yet, no polkit policy exists for *gedit* or *nautilus* either, so *pkexec* doesn't work. New users are either forced to use command line tools, which I contend (in the aforementioned thread) will just drive them away, or to invoke graphical tools using various workarounds, one of which is installing the missing policies. A superficially less complicated option is:```
sudo -H gedit file_name
```or```
sudo -i nautilus
```...though I find the use of *sudo* with flags too murky for the new user to get their head around. Unless one is familiar with the guts of the OS, it seems superfluous to use the -H flag for graphical apps when it isn't needed for CLI counterparts.

I hope the developers change their minds and install policies for *gedit*, *nautilus*, *zenity*, etc in upcoming releases. Until then, we will just have to continue wrestling with the quandary of how to advise new users every time a config file needs changing.

---

