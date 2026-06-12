---
title: "Is that possible to remove Nautilus/Gedit/Treminal ?"
date: 2012-11-29
forum: New to Ubuntu
---

### Post by ThrashManiac on 2012-11-29
So, the question is - is that possible to fully remove Nautilus & Gedit & Terminal without harming Unity? What's the level of integration? 

I'd like to fully replace all of those with Thunar & SciTE & Terminator, but I'm afraid, that I can get this state only in raw Gnome 3... 

Correct me if I'm wrong, please.

---

### Post by pkadeel on 2012-11-29
I am also interested to know the answer to this question. Is it possible without uninstalling unity-desktop or shall we install our desired softwares and forget about the ones already present?

---

### Post by Pletched on 2012-11-29
I think you can replace most of it, except for nautilus. 

Scite really? It's shoddy and it was only meant as a testing place of the library. There is a good text editor on Windows called notpad++ that uses scintella but that's only Windows based.

---

### Post by pkadeel on 2012-11-29
> **Pletched said:**
> I think you can replace most of it, except for nautilus.How is going to be tricky i guess :)
I am primarily interested in gedit out of 3 apps mentioned by OP but I think same method will apply to atleast the Terminal aswell.

---

### Post by audiomick on 2012-11-29
I wouldn't bother removing the ones you don't want. I am pretty sure that Nautilus is so integrated in Ubuntu that you can't remove it without killing the desktop.

As far as the others go, I don't think they take up that much drive space, and they wont use resources if they are not running.

Also, gedit at least is a default gnome appication, and I think the terminal is, so I wouldn't be surprised to see them come in with a "raw" installation of gnome, but that is a guess.

---

### Post by oldos2er on 2012-11-29
You could run something like ```
sudo apt-get remove -s nautilus
``` to see exactly what would be removed. The "-s" means "No action; perform a simulation of events that would occur but do not actually change the system."

---

### Post by audiomick on 2012-11-29
Good idea, Ann.
This is what I get on a 10.04 install

```
mick@mick-laptop:~$ sudo apt-get remove -s nautilus
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gnome-session nautilus nautilus-share ubuntu-desktop
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
Remv ubuntu-desktop [1.197]
Remv gnome-session [2.30.0-0ubuntu1]
Remv nautilus-share [0.7.2-12build1]
Remv nautilus [1:2.30.1-0ubuntu1.2]

```

According to that, if you remove Nautilus it will  break your desktop, unless you aren't using the standard Ubuntu desktop.

---

### Post by AstroLlama on 2012-11-29
there really is no need to remove them. for example you could just install terminator and set that as your default terminal emulator. is it really necessary to remove it?

xfce uses thunar, you could install xfce as an extra desktop environment.

---

### Post by oldos2er on 2012-11-29
> **audiomick said:**
> Good idea, Ann.
This is what I get on a 10.04 install

```
mick@mick-laptop:~$ sudo apt-get remove -s nautilus
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gnome-session nautilus nautilus-share ubuntu-desktop
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
Remv ubuntu-desktop [1.197]
Remv gnome-session [2.30.0-0ubuntu1]
Remv nautilus-share [0.7.2-12build1]
Remv nautilus [1:2.30.1-0ubuntu1.2]

```

According to that, if you remove Nautilus it will  break your desktop, unless you aren't using the standard Ubuntu desktop.

ubuntu-desktop is actually safe to remove; it's a metapackage ([https://help.ubuntu.com/community/MetaPackages](https://help.ubuntu.com/community/MetaPackages)). gnome-session would be the deal- (or desktop-) breaker.

---

### Post by LABcqX on 2012-11-30
> **oldos2er said:**
> ubuntu-desktop is actually safe to remove; it's a metapackage ([https://help.ubuntu.com/community/MetaPackages](https://help.ubuntu.com/community/MetaPackages)). gnome-session would be the deal- (or desktop-) breaker.

oldos2er, do you know of exactly what ubuntu-desktop does? I faced a similar dilemma when removing the ubuntu-sso-client package. I ended up removing it and solved the issue that prompted me to want to remove it. Best I could tell is that there may be issues if I try to perform an ubuntu upgrade. But I like stability so I am using the .04 version of the ubuntu so i dont upgrade often. Is the ubuntu-desktop of unused nature when not upgrading and after the desktop environment has already been installed?

Big Thanks for posting this command because it is command I find very useful.```
sudo apt-get remove -s
```

---

### Post by LABcqX on 2012-11-30
> **oldos2er said:**
> You could run something like ```
sudo apt-get remove -s nautilus
``` to see exactly what would be removed. The "-s" means "No action; perform a simulation of events that would occur but do not actually change the system."

How did you learn of this command? I have tried the MAN command but it does not say anything about the -s option.

---

### Post by arpanaut on 2012-11-30
Try 'man apt-get"
w/o quotes

---

### Post by oldos2er on 2012-11-30
> **LABcqX said:**
> oldos2er, do you know of exactly what ubuntu-desktop does? 

All of the *buntu-desktop packages are metapackages; they don't really do much by themselves. If you run ```
apt-cache show ubuntu-desktop
``` you'll see a large list of packages that ubuntu-desktop installs. 

> **LABcqX said:**
> Is the ubuntu-desktop of unused nature when not upgrading and after the desktop environment has already been installed? I believe so. It's so much easier to run **#apt-get install ubuntu-desktop** than **#apt-get install huge-list-of-packages**

> **LABcqX said:**
> Big Thanks for posting this command because it is command I find very useful.```
sudo apt-get remove -s
``` You're welcome.

---

### Post by ThrashManiac on 2012-12-02
Wow, thanks for replies, people! 

So, the bottom line - ubuntu desktop can actually be removed, because of it's meta-nature, and the unity will not suffer?

P.S. Debain also has some kind of deep file-manager desktop integration?

---

### Post by oldos2er on 2012-12-02
If you want to upgrade to a newer version of Ubuntu, you will need to have ubuntu-desktop installed. With that caveat, if you're removing a package and see that ubuntu-desktop is going to be removed, that's not a cause for concern.

---

### Post by ThrashManiac on 2012-12-04
I was curious, so I tested it under the VirtualBox: 
> * removed gedit/nautilus/gnome-terminal via synaptic 

* installed gnome3-shell via command line, because those 3 packages have brought the GUI down 

* startx caused an error
Conclusion: those 3 packages are nailed into the system, and there's no way to get rid of them. End of story. RIP.
:confused:

---

