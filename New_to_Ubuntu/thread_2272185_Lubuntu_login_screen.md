---
title: "Lubuntu login screen"
date: 2015-04-04
forum: New to Ubuntu
---

### Post by RobGoss on 2015-04-04
[COLOR=#333333][FONT=Lucida Grande]Hello I just installed Lubuntu and I was wondering how to customize the login screen. It looks to plain for my taste.  Thanks so much[/FONT][/COLOR]

---

### Post by Siddhartha_Kashyap on 2015-04-04
I tried hard but couldn't find a way to change the wallpaper in the login screen of lubuntu. I used "ubuntu tweaks" but failed :( however there is a way to customise your own pic on the login screen. There's an app in the Lubuntu software centre called "ABOUT ME". You can edit your user picture in it

---

### Post by kamlesh3 on 2015-04-04
Yeah using 3rd party app you can do it

---

### Post by Dennis N on 2015-04-05
> **robert159 said:**
> [COLOR=#333333][FONT=Lucida Grande]Hello I just installed Lubuntu and I was wondering how to customize the login screen. It looks to plain for my taste.  Thanks so much[/FONT][/COLOR]

If you know how to use root privileges, you can customize it to some extent by editing the configuration file:

**[FONT=Courier New]/etc/lightdm/lightdm-gtk-greeter.conf[/FONT]**

For example, you can change the background by editing the line **background=** to use a different image - your new background should first be copied into the same directory as the default background (**/usr/share/lubuntu/wallpapers**).

As a general practice, suggest you make a backup of the configuration file before editing.

---

### Post by RobGoss on 2015-04-05
Oh Ok sounds to hard just a change the login screen I'm testing this OS and I think I will just use another one that's a bit simple but thanks for the help

---

### Post by flaymond on 2015-04-05
* This reply is doubled.

---

### Post by flaymond on 2015-04-05
Lubuntu is pretty nice lightweight customized flavor, you can try XFCE(Xubuntu) instead. It give you more functionality, features and it's very flexible. Login screen for it is also beautiful. You can try install different DE in only one PC without doing a fresh install. Example :

```
 # Will install xfce4 desktop environment
           sudo apt-get install xfce4 
```

It's not a big download (Most of them under 150MB and for this install probably will be 60MB). You can activate it by log out and change the DE at the login prompt.

Read more here.

[http://www.howtogeek.com/193129/how-to-install-and-use-another-desktop-environment-on-linux/](http://www.howtogeek.com/193129/how-to-install-and-use-another-desktop-environment-on-linux/)

Or you can do something better, using minimal install (install the kernel, and then choose which package and app you want to install. Save your PC from bloats of useless softwares)

---

### Post by RobGoss on 2015-04-05
Hi were would I get the download for Xubuntu? I'll give it a try to see how it goes. and thank you so much for your help

---

### Post by flaymond on 2015-04-05
Here, take a look at this link - [http://xubuntu.org/](http://xubuntu.org/)

Ubuntu use Unity dekstop enviroment (that compaque and small, but flexible), but somehow use a lot of resources and slow (for some old machines).

Lubuntu use LXDE = A light desktop environment, but lack of beautiful features that Unity, GNOME, Cinnamon, MATE, and XFCE has. Good for old machines.

Xubuntu use XFCE = XFCE sitting between both of Unity and LXDE, and share some of the characteristic, but improved for users need. It's very customized, looks like
                            Windows (a bit) and LXDE but give more beautiful 3D features like Unity. It's smaller and use less resources than Unity.
Kubuntu use KDE  = KDE is a desktop enviroment build with Qt tool kit. It's size just a bit same like Unity, and more to Windows-like.

Ubuntu MATE = Lightweight than Unity but heavier than some flavor (try type top at terminal to compare, and see the memory it use). It use Gnome 2 DE. A lot of veterans prefer MATE because it use the GNOME 2 DE and make them feel like at 'home'.

Ubuntu GNOME = I don't see much different with Ubuntu Mate, but Ubuntu Gnome use GNOME 3 and more resource using than Gnome 2 (MATE). The softwares and the look of the new GNOME 3 is the thing that make a different between MATE and GNOME.

Note: Distro is a distribution like Linux Mint and CentOS that not in the same family of the organization or tree project, while flavors like Xubuntu is the same distribution and base, just different customization and softwares.

Other than Ubuntu distros/family =

Linux Mint = The second popular distribution of Linux, based Ubuntu, the best attraction about it..is..it use Cinnamon DE for it's main flavor, a nice and beautiful DE. other flavor is also available like Linux Mint MATE and Linux Mint GNOME.

Fedora = Red Hat Linux based, and sponsored by Red Hat Linux itself, good for servers and desktops. Fedora softwares is mostly the latest.

Red Hat Linux = A strong and good Linux for Enterprising and servers.

Debian = This is the Ubuntu based from.

---

### Post by RobGoss on 2015-04-05
Wow a  lot of good info just downloaded Xubuntu and I will configure it accordingly thank you for all the great tips

---

### Post by newb85 on 2015-04-05
> **InterProg said:**
> Ubuntu GNOME = I don't see much different with Ubuntu Mate, but Ubuntu Gnome make the old/experience and veterans users  feel like 'home'. The softwares is the thing that make a different between MATE and GNOME.

Ubuntu GNOME should be *very* different than Ubuntu Mate.  Mate is a fork of Gnome 2.  Ubuntu Gnome uses Gnome 3.  They have an entirely different look and feel.  If they seemed the same for you, I would suspect that the system on your machine defaulted to a fallback DE (which would look a lot like Gnome 2) because your machine had limited resources.

---

### Post by flaymond on 2015-04-06
[QUOTE=newb85]Ubuntu GNOME should be *very* different than Ubuntu Mate.  Mate is a fork of Gnome 2.  Ubuntu Gnome uses Gnome 3.  They have an entirely different look and feel.  If they seemed the same for you, I would suspect that the system on your machine defaulted to a fallback DE (which would look a lot like Gnome 2) because your machine had limited resources.[/QUOTE]

I think you right, it's been a while not testing the DE's. I should say the Mate is the one that make them feel like at 'home'. Thanks for correcting me. I appreciated it.

@robert159

Another tips, mark your thread as ***solved***. It help everyone in here to identify if the thread is done or got the answer that sastified the OP.

You can do this by going to thread tools, at the top right. Thanks and have a good day. :KS

---

### Post by mytien on 2015-04-09
I tried hard but couldn't find a way to change the wallpaper in the login screen of lubuntu. Help me, please!

---

### Post by newb85 on 2015-04-10
@mytien, did you try Dennis N's suggestion in post #4 of this thread?  I don't use Lubuntu, but from what I understand, it doesn't have a graphical tool for changing the wallpaper of the greeter.

---

