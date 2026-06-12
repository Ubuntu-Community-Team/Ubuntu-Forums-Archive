---
title: "Why do I have nemo desktop"
date: 2019-06-02
forum: New to Ubuntu
---

### Post by crip720 on 2019-06-02
I was just adding an indicator to my start up applications and notice that nemo desktop was listed.  Thought I was using nautilus.  I am on ubuntu 19.04 using the unity desktop, is this why?  Synaptic lists both nemo and nautilus installed, but have not installed cinnamon desktop.  Just wondering where it came from, this is a new clean install of 19.04 and I think I have only installed unity desktop, none of the other installs/downloads had anything to do with cinnamon or nemo that I can remember.

---

### Post by deadflowr on 2019-06-02
nemo runs the desktop for unity.
nautilus is still the file manager, but nemo is what now handles the desktop.
They had to make the change as nautilus wasn't working well enough in that capacity any more.

You can probably read through this meandering thread about the change:
[https://community.ubuntu.com/t/testing-unity-session-in-19-04/8451/25]("https://community.ubuntu.com/t/testing-unity-session-in-19-04/8451/25")
I think that's abouts as good a starting point in that thread as anywhere.

---

### Post by crip720 on 2019-06-02
Thanks.  I am the only user so I know it was not something that I had installed, did not know about unity using it though.

---

### Post by #&amp;thj^% on 2019-06-02
deadflowr gives the correct answer:
```
apt show nemo
Package: nemo
Version: 3.8.5-1build1
Priority: optional
Section: universe/misc
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Cinnamon Team <debian-cinnamon@lists.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 4,645 kB
Depends: cinnamon-desktop-data (>= 3.8), desktop-file-utils (>= 0.7), gsettings-desktop-schemas, gvfs (>= 1.3.2), libcinnamon-desktop4 (>= 3.8), libglib2.0-data, libnemo-extension1 (= 3.8.5-1build1), libxapp1 (>= 1.2), nemo-data (= 3.8.5-1build1), shared-mime-info (>= 0.50), libatk1.0-0 (>= 1.32.0), libc6 (>= 2.14), libcairo-gobject2 (>= 1.10.0), libcairo2 (>= 1.10.0), libexempi8 (>= 2.5.0), libexif12 (>= 0.6.21-1~), libgail-3-0 (>= 3.0.0), libgdk-pixbuf2.0-0 (>= 2.22.0), libglib2.0-0 (>= 2.49.2), libgtk-3-0 (>= 3.21.5), libnotify4 (>= 0.7.0), libpango-1.0-0 (>= 1.20.0), libpangocairo-1.0-0 (>= 1.14.0), libselinux1 (>= 1.32), libx11-6, libxml2 (>= 2.7.4)
Recommends: cinnamon-l10n (>= 3.8), gvfs-backends, gvfs-fuse, librsvg2-common, nemo-fileroller (>= 3.8)
Suggests: eog, evince | pdf-viewer, totem | mp3-decoder, xdg-user-dirs
Breaks: cinnamon (<< 3.8), cinnamon-core (<< 3.8~), nemo-fileroller (<< 3.8)
Homepage: http://cinnamon.linuxmint.com/
Task: ubuntu-budgie-desktop
Download-Size: 883 kB
**_APT-Manual-Installed: no_**
APT-Sources: http://archive.ubuntu.com/ubuntu disco/universe amd64 Packages
Description: File manager and graphical shell for Cinnamon
 Nemo is the official file manager for the Cinnamon desktop. It allows one
 to browse directories, preview files and launch applications associated
 with them. It is also responsible for handling the icons on the Cinnamon
 desktop. It works on local and remote filesystems.
 .
 Several icon themes and components for viewing different kinds of files
 are available in separate packages.
```

And:
```
me@me-ThinkPad-T430:~$ echo $DESKTOP_SESSION
unity
``` 
BTW: I plan on scraping nautilus all together>>Gnome should too. :p

---

### Post by crip720 on 2019-06-02
My outputs are same as yours 1fallen, first one doesn't mention unity, only cinnamon and budgie.  Is bugie and unity the same, thought budgie was a different desktop?  Was wondering for next time if there was a code that for example would mention/show that X was downloaded for/by Y.  Like I saw nemo, but did not know what package downloaded it

---

### Post by #&amp;thj^% on 2019-06-02
> **crip720 said:**
> Is bugie and unity the same, thought budgie was a different desktop?  Was wondering for next time if there was a code that for example would mention/show that X was downloaded for/by Y.  Like I saw nemo, but did not know what package downloaded it
Well that's kind of duel edged question, originally>>NO! >>It is a fork of Gnome and GNOME Files (formerly named Nautilus).
deadflowr gave you a link to browse on why this is the case for unity, Nautilus has become a problem for Gnome and Ubuntu Devs as it has not had "ANY" proper loving for quite some time now. (And not really a Gnome package to start with)
I hear in the wind (Key in rumors) they are considering Nemo file manager. **As for now _that's all it is_, A Rumor.**
Try this for X
```
apt show Xorg
```

---

### Post by crip720 on 2019-06-02
That's funny, seems like I don't have Xorg.  I know there is an option on login to use wayland, but don't use it.  Thought the other two options, gnome and unity both use Xorg.  Do have 'xorg', and that lists almost all ubuntu desktops except ubuntu unity.  Does list ubuntu-desktop, but that is the standard gnome desktop now, isn't it.  Really just wanted to know if there was something like apt (something) nemo, that would show that it was installed by unity.  What started this was, I was doing something, notice the name nemo, google it and found it was file manager for cinnamon, but I did not install cinnamon.  Did not know at the time that unity is also using it.

---

### Post by kurt18947 on 2019-06-02
It's fairly simple to set Nemo as default file manager in mainline Ubuntu as well. I prefer it to Nautilus but I know that Ubuntu is running an older version of Nautilus due in part to current Nautilus not supporting desktop icons, Gnome has decreed that Nautilus not support desktop iconsthough I think they have legitimate reasons. I think Gnome is working on an extension that will provide desktop icons. Nemo seems to be seamless in Ubuntu 18.04.2 as far as I can tell and yes I have my desktop icons.

---

### Post by #&amp;thj^% on 2019-06-02
Well it has many other things and packages that go along with it, depending on your usage. 
X11 is always installed by default unless you manually removed it.
I'm a bit surprised that did not show any thing, maybe my code was off, but this works just to see if Xorg is indeed installed and running:
```
**type Xorg**
Xorg is /usr/bin/Xorg
```
And:
```
**ps -e | grep X**
 1065 tty7     00:04:13 Xorg
```
And:
```
dpkg -l | grep xserver-xorg-core
```
I'm currently not on Ubuntu now so I'll post back later with a better method on Xorg.
Cheers

---

### Post by crip720 on 2019-06-02
Seems I have Xorg, just don't have Xorg but do have xorg for apt show.

---

### Post by yetimon_64 on 2019-06-02
> **crip720 said:**
> ... but do have xorg for apt show.

That sounds right, they are one and the same. I don't think I've ever seen a package name using a capital letter in it in 11 years of using Ubuntu. 

I note the same effect with "apt-cache policy" ("policy" below is a bash alias for "apt-cache policy")...
```
yetiman:~ $  policy Xorg
N: Unable to locate package Xorg
yetiman:~ $  policy xorg
xorg:
  Installed: 1:7.7+19ubuntu7.1
  Candidate: 1:7.7+19ubuntu7.1
  Version table:
 *** 1:7.7+19ubuntu7.1 500
        500 http://archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     1:7.7+19ubuntu7 500
        500 http://archive.ubuntu.com/ubuntu bionic/main amd64 Packages

```
Packages don't have any capitalization in their names but as you can see from 1fallen's post above paths and process names can use the capital letters. Can get a bit confusing at times :-).
> ...maybe my code was off Caught out by package naming it seems, paths and processes can use the capitals ;).

Cheers, yeti.

---

### Post by #&amp;thj^% on 2019-06-03
> **yetimon_64 said:**
> 
 Caught out by package naming it seems, paths and processes can use the capitals ;).

Cheers, yeti.

Yep ;) when your running several very different systems, along with different syntax used for each makes it hard to remember.) ):P

---

