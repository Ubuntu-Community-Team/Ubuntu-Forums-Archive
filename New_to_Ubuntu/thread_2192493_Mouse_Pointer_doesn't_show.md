---
title: "Mouse Pointer doesn't show"
date: 2013-12-08
forum: New to Ubuntu
---

### Post by tirab on 2013-12-08
I am running ubuntu 13.10 on a dual boot system with windows 8. Sometimes when I start-up ubuntu the mouse pointer does
not show and I need to reboot the system, which usually fixes the problem.

Any help would be appreciated.

Thanks
tirab

---

### Post by asus-user on 2013-12-09
> **tirab said:**
> I am running ubuntu 13.10 on a dual boot system with windows 8. Sometimes when I start-up ubuntu the mouse pointer does
not show and I need to reboot the system, which usually fixes the problem.

Any help would be appreciated.

Thanks
tirab

Hello, 

This is a reported bug in Ubuntu 13.10, see: [https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/1238410](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/1238410)

To solve this try to disable the gnome-settings-daemon cursor plugin from Terminal:

```
gsettings set org.gnome.settings-daemon.plugins.cursor active false

```
 
and re-enable it:

```


gsettings set org.gnome.settings-daemon.plugins.cursor active true

``` 

I am not running Ubuntu 13.10 right now, so report here if it works, or if you get any error/messages.

---

