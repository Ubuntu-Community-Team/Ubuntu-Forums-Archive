---
title: "HOWTO: Install GCfilms (movie collection management)"
date: 2005-06-23
forum: Outdated Tutorials &amp; Tips
---

### Post by infinito on 2005-06-23
[GCfilms](http://home.gna.org/gcfilms/) stands for french Gtk2 Catalogue de films.
It is a gtk2-perl application used to manage a movie collection. Information such as director, actors or even who borrowed it are associated to a movie. User can perform some searches using many criteria in order to find a movie (e.g. to watch or to lend it).

This is the way to get it installed on Ubuntu:

(1) Add this to your /etc/apt/sources.list
```
deb http://download.gna.org/gcfilms/ubuntu ./
deb-src http://download.gna.org/gcfilms/ubuntu ./
```
(2) Then run this two commands on terminal:
```
gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 3F8220A1
gpg --armor --export 3F8220A1 | sudo apt-key add -
```
(3) Update your sources and install gcfilms:
```
apt-get update && apt-get install gcfilms
```
More information : [http://home.gna.org/gcfilms/](http://home.gna.org/gcfilms/)
Take a look at the GCfilms Logo Contest at [http://home.gna.org/gcfilms/](http://home.gna.org/gcfilms/)

---

### Post by bored2k on 2005-06-23
Awsome. Thanks :D

---

### Post by RastaMahata on 2005-06-23
oops! double post!! :o

---

### Post by bored2k on 2005-07-05
This application is just great. Just now I was looking for cataloguing my anime and just remembered GCFilms.. awsome. You all need to try this one out.

---

### Post by tyfn on 2008-06-08
I like this app.

---

### Post by flitbee on 2010-11-08
I get an error while retrieving the keys:

```
gpg: requesting key 3F8220A1 from hkp server wwwkeys.eu.pgp.net
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error

```

Is there something I should be doing?

[IMG]http://img259.imageshack.us/img259/6765/38775890.png[/IMG]

---

### Post by qamelian on 2010-11-08
The program is now called GCStar and is in the official Ubuntu repos. You no longer need to follow this tutorial to install it.

---

### Post by flitbee on 2010-11-08
> **qamelian said:**
> The program is now called GCStar and is in the official Ubuntu repos. You no longer need to follow this tutorial to install it.

Oh ok, that sounds great. But umm.. how do I launch it? Where do I find it? (sorry Ubuntu newbie)

---

### Post by flitbee on 2010-11-09
I tried running GCstar per [http://wiki.gcstar.org/en/Install](http://wiki.gcstar.org/en/Install) but am stuck where the installation screen (text mode) says:

```
Error : Following Perl components have to be installed: 

XML::Simple

```

How do I get this Perl component?

---

### Post by qamelian on 2010-11-09
> **flitbee said:**
> I tried running GCstar per [http://wiki.gcstar.org/en/Install](http://wiki.gcstar.org/en/Install) but am stuck where the installation screen (text mode) says:

```
Error : Following Perl components have to be installed: 

XML::Simple

```How do I get this Perl component?
If you just installed it from the Ubuntu repos, you wouldn't need to worry about it because the package manager would resolve all dependancies. It's as simple as opening a terminal and typing:
```
sudo apt-get install gcstar --install-recommends
```The launcher then appears under Applications > Office.

Installing it the way you're going right now, you'll need to install some stuff by hand.  Doing:
```
apt-cache search XML::Simple
```in a terminal indicates that you should be able to get this component by installing libxml-simple-perl.
```
sudo apt-get install libxml-simple-perl
```After it is installed, you may get more errors about other missing components. Unless you have some pressing need to install it this way, you'd be much better off installing GCStar from the repositories via apt-get/Synaptic/Software Centre. YOu'll have far fewer headaches and if you decide it's not what you want, it will be much easier to uninstall cleanly!

Also, you can follow these specific instructions on the wiki to make sure you get the latest stable release on Ubuntu.

[http://wiki.gcstar.org/en/install_linux#ubuntu](http://wiki.gcstar.org/en/install_linux#ubuntu)

---

### Post by flitbee on 2010-11-09
OK, saw this [post]("http://ubuntuforums.org/showthread.php?p=1278352#post1278352:") and ran the below to install the Perl components:
```

sudo perl -MCPAN -e 'install XML::Simple'
```Hit ENTER to a bunch of Qns and then installed the gcstar like so:

```
./install --text

```and finally installed:

```
Base directory for installation [/usr/local]: 
gtk-update-icon-cache: Cache file created successfully.
Installing in /usr/local/

End of the installation
No error
To use this application you can launch /usr/local/bin/gcstar
```

---

### Post by qamelian on 2010-11-09
> **flitbee said:**
> OK, saw this [post]("http://ubuntuforums.org/showthread.php?p=1278352#post1278352:") and ran the below to install the Perl components:
```

sudo perl -MCPAN -e 'install XML::Simple'
```Hit ENTER to a bunch of Qns and then installed the gcstar like so:

```
./install --text

```and finally installed:

```
Base directory for installation [/usr/local]: 
gtk-update-icon-cache: Cache file created successfully.
Installing in /usr/local/

End of the installation
No error
To use this application you can launch /usr/local/bin/gcstar
```

Glad you got it working but you really did choose to do it the hard way!

---

### Post by flitbee on 2010-11-09
Ya sorry, didn't see your post before I posted mine. Got it working, but your method was far easier. Still getting to know Ubuntu. Thanks for the detailed tip!

---

### Post by qamelian on 2010-11-09
> **flitbee said:**
> Ya sorry, didn't see your post before I posted mine. Got it working, but your method was far easier. Still getting to know Ubuntu. Thanks for the detailed tip!
No problem. There's actually nothing wrong with the way you did it, since it was probably definitely an educational experience. I hope you enjoy using and learning Linux!

---

