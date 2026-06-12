---
title: "Removing .desktop launchers created by gnome"
date: 2013-03-14
forum: New to Ubuntu
---

### Post by ThatBenderGuy on 2013-03-14
Ok so I used gnome to create .desktop launchers but I need to delete a couple. How can I delete my .desktop launchers?

---

### Post by deadflowr on 2013-03-14
Depending on what program you used.
The .desktop files are usually located in either the home folder .local/share/applications/, or in the system folder folder /usr/share/applications.

In the home folder locale, you can simply delete them.
In the system folder you will need to delete them as root.
```
sudo rm blah/blah/blah.desktop
```

A possible third place would be in the Desktop folder in your home folder.

---

### Post by ThatBenderGuy on 2013-03-14
Thanks!

Btw, do you know an easier way to create .desktop file on Ubuntu 12.10 rather than through the terminal?

---

### Post by deadflowr on 2013-03-14
> **ThatBenderGuy said:**
> Thanks!

Btw, do you know an easier way to create .desktop file on Ubuntu 12.10 rather than through the terminal?


I always just use gedit.

It's important to note that a desktop file must have three things always:Type, Exec, and Name. Icons are optional if you like.
After I've created it and save the file in the right spot with the .desktop extension, I either open a terminal or find the file in the file manager and set it to executable.

Looky here for more:

[http://linuxcritic.wordpress.com/2010/04/07/anatomy-of-a-desktop-file/](http://linuxcritic.wordpress.com/2010/04/07/anatomy-of-a-desktop-file/)

And here:

[https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles](https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles)

I think there's a create launcher app in the software centre, also.

---

### Post by vasa1 on 2013-03-14
> **deadflowr said:**
> ...
After I've created it and save the file in the right spot with the .desktop extension, I either open a terminal or find the file in the file manager and set it to executable.
...
I've made a few .desktop files and haven't yet found the need to set them as executable:
```
[06:08 AM] ~/.local/share/applications $ ll
total 40
drwxrwxr-x 2 vasa1 vasa1 4096 Mar  8 22:28 ./
drwx------ 8 vasa1 vasa1 4096 Mar 14 22:48 ../
-rw-rw-r-- 1 vasa1 vasa1   90 Feb 18 22:17 defaults.list
-rw-rw-r-- 1 vasa1 vasa1  439 Dec 26 17:38 firefox.desktop
-rw-r--r-- 1 vasa1 vasa1  441 Dec 26 17:43 google-chrome.desktop
-rw-r--r-- 1 vasa1 vasa1  223 Feb 19 12:10 lxterminal.desktop
-rw-rw-r-- 1 vasa1 vasa1 1823 Mar  5 16:27 mimeapps.list
-rw-rw-r-- 1 vasa1 vasa1  312 Mar  8 22:21 pcmanfm.desktop
-rw-r--r-- 1 vasa1 vasa1  447 Dec 26 17:43 Privo-chrome.desktop
-rw-rw-r-- 1 vasa1 vasa1  483 Oct  8 22:53 seamonkey.desktop
[06:08 AM] ~/.local/share/applications $ 

```

---

### Post by deadflowr on 2013-03-14
> **vasa1 said:**
> I've made a few .desktop files and haven't yet found the need to set them as executable:


Try launching one in unity, or gnome.
You'll get a pop-up window saying the launcher is untrusted, and nothing else will happen.

---

### Post by vasa1 on 2013-03-14
> **deadflowr said:**
> Try launching one in unity, or gnome.
You'll get a pop-up window saying the launcher is untrusted, and nothing else will happen.
I use Lubuntu and don't have a problem there and so was wondering. Anyway, [https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles](https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles) has this: "One last thing to add is that by setting executable rights to your .desktop file, it automatically takes the specified Icon and Name (specified in the corresponding fields), as it should be."

---

### Post by deadflowr on 2013-03-14
Odd little tidbit but it seems it only needs to be set in the home/.local folder. (in unity, at least)
Throwing a desktop file in the /usr/share folder doesn't need to be set  to execute.

But, all in know is whenever I create one and throw it in my folder, nothing happens until I mark execute.

---

