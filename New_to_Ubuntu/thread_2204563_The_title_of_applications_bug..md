---
title: "The title of applications bug."
date: 2014-02-09
forum: New to Ubuntu
---

### Post by ameeno on 2014-02-09
Hi All,

This is basically a minor niggle, but annoying because i cant fix it. All help is majorly appreciated.

Chromium has a weird name, in Unity and Ubuntu 13.10 - How to revert?

---

### Post by ameeno on 2014-02-09
bump

---

### Post by ameeno on 2014-02-09
OK Figured it Out.


[https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles](https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles)

is a good guide.

Basically i went to ~\.local\applications

and used a gksu gedit session to edit the .desktop file, renamed the file.. and rebooted.

job done :)

---

### Post by ameeno on 2014-02-09
[http://ubuntuforums.org/showthread.php?t=2067574](http://ubuntuforums.org/showthread.php?t=2067574) also helps :)

---

### Post by monkeybrain20122 on 2014-02-10
> **ameeno said:**
> OK Figured it Out.


[https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles](https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles)

is a good guide.

Basically i went to ~\.local\applications

and used a gksu gedit session to edit the .desktop file, renamed the file.. and rebooted.

job done :)
The .desktop file should be in /usr/share/applications unless you installed the program locally (without sudo, usually by compiling ). There shouldn't be a duplicate in .local/share/applications (though if it exists I assume it would override the one in /usr/share/applications) You don't need sudo or gksudo to edit files in your /home (and it is not recommended as it can be problematic for security), so gedit xxxx.desktop would do.

---

