---
title: "can i remove xtern from the system?"
date: 2014-06-30
forum: New to Ubuntu
---

### Post by tojonukokhadush on 2014-06-30
okay i have these installed in my system 12.04-

=> Byobu Terminal
=> UXTerm
=> Xterm
=> Terminal

i guess i only need Terminal so far! so can i remove other then from the system? or anyone can make me understand their usage please? that would be appreciated!!

one thing i think i am missing is python programmer! how do i get back that?


also do i need Apper and GDebi Package Installer when i have Synaptic Package Manager in ubuntu?

THANK YOU!

---

### Post by oldos2er on 2014-06-30
I assume by Terminal you mean gnome-terminal; if something goes wrong with it it's nice to have xterm for a backup. It's small (~1.7MB), so it's not as though it's taking up a lot of space. 

Gdebi can install local *.deb files, which Synaptic can't, so they have different functions. I don't know what "Apper" is.

---

### Post by Rob Sayer on 2014-07-01
Apper is a KDE package management tool.  If you're not running kubuntu or the KDE desktop it probably got installed when you installed some kde program.  This happens to me because I run KDE mostly at home but xfce based xubuntu on this netbook and I use dolphin for a file manager.  It installs a shedload of kde dependencies when you install it.  Which is worth it to me.

If it's giving you pop up notifications telling you an update is available you should be able to stop that in notifications settings somehow.

Otherwise I'd just leave it alone.

I'd never yank gdebi.  As mentioned it can do things synaptic won't.  Actually, since all linux programs end up in a terminal anyway, there's absolutely nothing you can do in synaptic you can't do in the terminal and then some.  I like synaptic because it keeps pretty nice records but I use the terminal more to install.

At this point you could cause more problems than you solve by yanking programs when you don't understand how dependencies work.  I'd just leave it.

Also, is your signature up to date?  Are you running 10.04?  That's been unsupported for over a year now.

---

### Post by buzzingrobot on 2014-07-01
Gdebi is a standalone deb installer.  I usually use it as the default installer. I.e., click on a .deb and Gdebi offers to install it.

All those terminal emulator apps run Bash, unless you've switched the shell to something else.  So, the differences are down to the interface you like.

---

### Post by robert107 on 2014-07-01
Check out terminator too

---

### Post by bapoumba on 2014-07-01
```
apt-cache rdepends xterm
```
You'll see xterm comes as a dependency of your distro-desktop package. Removing metapackages is not an issue by itself. But it can bring in some confusion when using autoremove or other apt-get commands in the future, in particular if you forget you have removed them.

What do you mean by "python programmer" ?

---

### Post by tojonukokhadush on 2014-07-02
okay thanks everyone a lot! i am on ubuntu 12.04 with gnome-fallback-session! quite getting idea about all these! and [[COLOR=#990303]bapoumba[/COLOR]]("http://ubuntuforums.org/member.php?u=171805"), by python, i mean to say the programming tool which was there by default in 10.04 by which one develops .py files!

---

### Post by bapoumba on 2014-07-02
Well, a simple text editor will do as python is installed by default.
[https://wiki.python.org/moin/IntegratedDevelopmentEnvironments](https://wiki.python.org/moin/IntegratedDevelopmentEnvironments) < may be you can find what you are looking for here, not knowing which precise tool you are talking about.

---

