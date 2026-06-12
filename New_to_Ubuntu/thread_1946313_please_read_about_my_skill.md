---
title: "please read about my skill"
date: 2012-03-24
forum: New to Ubuntu
---

### Post by stookin on 2012-03-24
Hi

So yeah I'm an absolute expert with computers, liek, I've been here all summer so yeah

I have a question however, my expertise is not willing to solve.

Where is the "start" windows-like button?

---

### Post by PhantomTurtle on 2012-03-24
For which desktop environment. KDE has a "start" button. Unity has the Ubuntu button on the launcher. Gnome fallback has an applet that will add a "start" button. XFCE and LXDE have "start" buttons. Gnome Shell also has an extension for that(the Frippery Applications Menu’ - [https://extensions.gnome.org/extension/13/applications-menu/]("https://extensions.gnome.org/extension/13/applications-menu/")).

---

### Post by stookin on 2012-03-24
Thank you. A lot. I wasn't really expecting an honest answer, because I tried to act cocky and dumb.

I have another question, a real one.
Whenever I check if my software is up to date in ubuntu 11.10 I get this error:

**Failed to download repository information**
Check your Internet connection.

Details:
W:Failed to fetch [http://archive.ubuntu.com/dists/oneiric/main/binary-i386/Packages](http://archive.ubuntu.com/dists/oneiric/main/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://archive.ubuntu.com/dists/oneiric/universe/binary-i386/Packages](http://archive.ubuntu.com/dists/oneiric/universe/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/crebs/ppa/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/crebs/ppa/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/crebs/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/crebs/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.


Please help

---

### Post by wieman01 on 2012-03-24
> **stookin said:**
> Thank you. A lot. I wasn't really expecting an honest answer, because I tried to act cocky and dumb.

I have another question, a real one.
Whenever I check if my software is up to date in ubuntu 11.10 I get this error:

**Failed to download repository information**
Check your Internet connection.

Details:
W:Failed to fetch [http://archive.ubuntu.com/dists/oneiric/main/binary-i386/Packages](http://archive.ubuntu.com/dists/oneiric/main/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://archive.ubuntu.com/dists/oneiric/universe/binary-i386/Packages](http://archive.ubuntu.com/dists/oneiric/universe/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/crebs/ppa/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/crebs/ppa/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/crebs/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/crebs/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.


Please help
Connect to the internet, as simple as that.

---

### Post by PhantomTurtle on 2012-03-24
> **stookin said:**
> Thank you. A lot. I wasn't really expecting an honest answer, because I tried to act cocky and dumb.

I have another question, a real one.
Whenever I check if my software is up to date in ubuntu 11.10 I get this error:

**Failed to download repository information**
Check your Internet connection.

Details:
W:Failed to fetch [http://archive.ubuntu.com/dists/oneiric/main/binary-i386/Packages](http://archive.ubuntu.com/dists/oneiric/main/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://archive.ubuntu.com/dists/oneiric/universe/binary-i386/Packages](http://archive.ubuntu.com/dists/oneiric/universe/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/crebs/ppa/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/crebs/ppa/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/crebs/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/crebs/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.


Please help

Well one of the ppa's you have is crebs, which does not have an oneric ppa. I am not sure about the others. Additionally I think the first two ppa's might be incorrect. But the last two are just not available for Ubuntu 11.10.

---

### Post by stookin on 2012-03-24
Thank you

How do I change my etc/apt/sources.list file in terminal?

I need sudo rights :s to change the file

---

### Post by PhantomTurtle on 2012-03-24
> **stookin said:**
> Thank you

How do I change my etc/apt/sources.list file in terminal?

I need sudo rights :s to change the file

You do need sudo. You cannot edit it without sudo. Also if you want you can open software sources in USC to change it(also requires admin rights, its just another (and maybe even) easier way to do it).

---

### Post by stookin on 2012-03-24
Ok, I tried sudo:

I entered this in terminal:
**sudo etc/apt/sources.list**

I got this error:
[B]sudo: etc/apt/sources.list: command not found

[/B]wtf?

---

### Post by howefield on 2012-03-24
Try 

```
gksudo gedit etc/apt/sources.list
```

---

### Post by stookin on 2012-03-24
> **howefield said:**
> Try 

```
gksudo gedit etc/apt/sources.list
```

Thank you but I got this error:
[I]
(gksudo:5535): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gedit:5537): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.6NOOBW': No such file or directory

(gedit:5537): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

[/I]edit: And a blank file opened

---

### Post by ksa618 on 2012-03-24
You need to put a / in front of etc:
```
gksudo gedit /etc/apt/sources.list
```
Just ignore the warnings you listed.

---

### Post by stookin on 2012-03-24
> **ksa618 said:**
> You need to put a / in front of etc:
```
gksudo gedit /etc/apt/sources.list
```Just ignore the warnings you listed.

Thank you

---

