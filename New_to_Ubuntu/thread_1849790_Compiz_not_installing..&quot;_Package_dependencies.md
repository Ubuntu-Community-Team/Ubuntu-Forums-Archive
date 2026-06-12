---
title: "Compiz not installing..&quot; Package dependencies cannot be resolved&quot;"
date: 2011-09-25
forum: New to Ubuntu
---

### Post by benask on 2011-09-25
Hi! I am a new user and have never used this before! 
**Simple Compiz**

 
I have a problem with the program "compiz" on my computer i Ubuntu. When  I try installing it I get a warning " Package dependencies cannot be  resolved"

Any one knowing what to do? :wink:

Thanks!

---

### Post by mike555 on 2011-09-25
How are you trying to install it ? you should use your package manager, it will get everything for you.......

---

### Post by benask on 2011-09-25
Thanks, but the problem is downloading it from Ubuntu software center.. 

First i open Ubuntu software center, then search for files "compiz".

when I get the results, I want to install <advanced desktop effects settings (ccsm)>
AND <simple compizconfig settings manager> but then I get a warning (Package dependencies cannot be resolved)

sorry, but my English is not the best. ;)

---

### Post by mike555 on 2011-09-25
Try using the Synaptic package manager.

---

### Post by benask on 2011-09-25
how? it's no alternative..

System- administration-  synaptic package manager- password - status?- installed?- compizconfig settings - apply? 

I don't know the system yet. so I'm not sure what I'm looking for



The following packages have unmet dependencies:

simple-ccsm:

---

### Post by ClientAlive on 2011-09-25
I'm not sure if it's what you need, but here's a couple links that give information on using Synaptic. Hope it helps.


Ubuntu Community Documentation: [https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

YouTube Vid: [http://youtu.be/DbWk7GnyYkc](http://youtu.be/DbWk7GnyYkc)

---

### Post by pkg9991 on 2011-09-25
see if typing this in the command line helps
sudo apt-get install compiz-core
then after the install type
compiz --replace

---

### Post by SecretCode on 2011-09-25
To see what the conflicts are, run
```
sudo apt-get install compizconfig-settings-manager simple-ccsm
```
and post the output here (between code tags).

---

### Post by benask on 2011-09-26
Ok, but nothing happens than a warning, look I took some picture . Attach files x 3
Thanks for the help guys!

---

### Post by ClientAlive on 2011-09-26
Assuming nothing has happened to any of the default repos in his package manager, what happened to?

```

sudo apt-get update

```

On a side note, I just ran it on mine and for some odd reason I was given the following output:

```

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

```

I did. I ran.

```

sudo dpkg --configure -a

```

and lived happily ever after. Ahhh . . .

:D

Check the dpkg man page - lots you can do with it - lots!

Oh, and, by the way - sometimes something broke can come down the pipe with a routine upgrade and cause a little hiccup till they get it ironed out. Sometimes that happens, though rarely I think.

---

### Post by technosysind on 2011-09-26
Do the following
> sudo apt-get update && sudo apt-get upgrade
> sudo apt-get install ubuntu-restricted-extras

> sudo apt-get install compizconfig-settings-manager

My problem was solved like this

---

### Post by SecretCode on 2011-09-26
What is "Avhenger av"? Presumably something in your installed language, although everything else appears to be in English.

Please run the command I posted above (in a terminal). In fact, better, run these commands:
```
sudo apt-get install aptitude
sudo aptitude install compizconfig-settings-manager
sudo aptitude install simple-ccsm
```
and post the output here (between code tags).

Something may be not quite right with your repositories or your settings in Synaptic.

---

### Post by benask on 2011-09-26
> **SecretCode said:**
> What is "Avhenger av"? Presumably something in your installed language, although everything else appears to be in English.

Please run the command I posted above (in a terminal). In fact, better, run these commands:
```
sudo apt-get install aptitude
sudo aptitude install compizconfig-settings-manager
sudo aptitude install simple-ccsm
```and post the output here (between code tags).

Something may be not quite right with your repositories or your settings in Synaptic.



Well, it didn't work. And yes, some words are Norwegian ;) Avhenger av = depends on ;)

---

### Post by SecretCode on 2011-09-26
I can't really read that ... copy the text from the terminal window and paste it into a reply here (between code tags).

---

### Post by Krytarik on 2011-09-26
```
Package: compiz-core
Source: compiz
Version: 1:0.9.4+bzr20110606-0ubuntu1~natty2
Architecture: i386
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Installed-Size: 840
Depends: libboost-serialization1.42.0 (>= 1.42.0-1), libc6 (>= 2.4), libgcc1 (>= 1:4.1.1), libglib2.0-0 (>= 2.12.0), libglibmm-2.4-1c2a (>= 2.28.0), libice6 (>= 1:1.0.0), libsigc++-2.0-0c2a (>= 2.0.2), libsm6, libstartup-notification0 (>= 0.10), libstdc++6 (>= 4.5), libx11-6, libx11-xcb1, libxcb1, libxcomposite1 (>= 1:0.3-1), libxdamage1 (>= 1:1.1), libxext6, libxfixes3 (>= 1:4.0.1), libxinerama1, libxml2 (>= 2.6.27), libxrandr2, libxslt1.1 (>= 1.1.25)
Recommends: compiz-plugins (= 1:0.9.4+bzr20110606-0ubuntu1~natty2)
Suggests: nvidia-glx (>= 1.0.9625-1)
Conflicts: compiz-wrapper (<< 1:0.8.4-0ubuntu4)
[COLOR=Red]**Breaks**[/COLOR]: compiz-fusion-plugins-extra (<< 0.9), compiz-fusion-plugins-main (<< 0.9.2.1-0ubuntu6), libcompizconfig0 (<< 0.9.2.1git101125-0ubuntu3), [COLOR=Red]**simple-ccsm (<< 0.9)**[/COLOR], unity (<< 3.2.6-0ubuntu2)
Replaces: compiz-gnome (<< 1:0.8.4-4ubuntu1), compiz-wrapper (<< 1:0.8.4-0ubuntu4)
Provides: compiz-core-abiversion-20110322
Section: x11
Priority: optional
Description: OpenGL window and compositing manager
 Compiz brings to life a variety of visual effects that make the Linux desktop
 easier to use, more powerful and intuitive, and more accessible for users
 with special needs.
 .
 Compiz combines together a window manager and a composite manager using
 OpenGL for rendering. A "window manager" allows the manipulation of the
 multiple applications and dialog windows that are presented on the screen. A
 "composite manager" allows windows and other graphics to be combined together
 to create composite images. Compiz achieves its stunning effects by doing
 both of these functions.
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
```(scroll to the right)

I may summarize:

[LIST]
[*]CompizConfig Settings Manager is installed successfully.
[*]Simple-CCSM can't be installed because its development is ceased since a long while, and it doesn't work with the current version of Compiz anymore.
[/LIST]
So, it seems like you have to give up the idea to install Simple-CCSM. Why are you that eager to install it in the first place, as it doesn't offer any advanced options anyway!?

Greetings.

---

### Post by benask on 2011-09-27
> **Krytarik said:**
> ```
Package: compiz-core
Source: compiz
Version: 1:0.9.4+bzr20110606-0ubuntu1~natty2
Architecture: i386
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Installed-Size: 840
Depends: libboost-serialization1.42.0 (>= 1.42.0-1), libc6 (>= 2.4), libgcc1 (>= 1:4.1.1), libglib2.0-0 (>= 2.12.0), libglibmm-2.4-1c2a (>= 2.28.0), libice6 (>= 1:1.0.0), libsigc++-2.0-0c2a (>= 2.0.2), libsm6, libstartup-notification0 (>= 0.10), libstdc++6 (>= 4.5), libx11-6, libx11-xcb1, libxcb1, libxcomposite1 (>= 1:0.3-1), libxdamage1 (>= 1:1.1), libxext6, libxfixes3 (>= 1:4.0.1), libxinerama1, libxml2 (>= 2.6.27), libxrandr2, libxslt1.1 (>= 1.1.25)
Recommends: compiz-plugins (= 1:0.9.4+bzr20110606-0ubuntu1~natty2)
Suggests: nvidia-glx (>= 1.0.9625-1)
Conflicts: compiz-wrapper (<< 1:0.8.4-0ubuntu4)
[COLOR=Red]**Breaks**[/COLOR]: compiz-fusion-plugins-extra (<< 0.9), compiz-fusion-plugins-main (<< 0.9.2.1-0ubuntu6), libcompizconfig0 (<< 0.9.2.1git101125-0ubuntu3), [COLOR=Red]**simple-ccsm (<< 0.9)**[/COLOR], unity (<< 3.2.6-0ubuntu2)
Replaces: compiz-gnome (<< 1:0.8.4-4ubuntu1), compiz-wrapper (<< 1:0.8.4-0ubuntu4)
Provides: compiz-core-abiversion-20110322
Section: x11
Priority: optional
Description: OpenGL window and compositing manager
 Compiz brings to life a variety of visual effects that make the Linux desktop
 easier to use, more powerful and intuitive, and more accessible for users
 with special needs.
 .
 Compiz combines together a window manager and a composite manager using
 OpenGL for rendering. A "window manager" allows the manipulation of the
 multiple applications and dialog windows that are presented on the screen. A
 "composite manager" allows windows and other graphics to be combined together
 to create composite images. Compiz achieves its stunning effects by doing
 both of these functions.
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
```(scroll to the right)

I may summarize:

[LIST]
[*]CompizConfig Settings Manager is installed successfully.
[*]Simple-CCSM can't be installed because its development is ceased since a long while, and it doesn't work with the current version of Compiz anymore.
[/LIST]
So, it seems like you have to give up the idea to install Simple-CCSM. Why are you that eager to install it in the first place, as it doesn't offer any advanced options anyway!?

Greetings.

Ok, good question. No need, was just interested why it didn't work ;) Thanks for the help guys. Good to know it's people out there helping !

---

