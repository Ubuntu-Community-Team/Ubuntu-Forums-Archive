---
title: "Problem with Nvidia"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by Sadbird on 2008-06-21
Hi.  I hope you can help me.
I have feisty fawn 7.04, a Dell dimension, Pentium II.
I tried to install an Nvidia card, but it said it needed a driver.
It downloaded a driver and installed it, but I can't use the computer for it says it has a wrong driver and needs to be reconfigured.
What can i do?
I can only use the recovery mode.
How can I uninstall the driver?  And how can I make the card to work.
Thanx.

---

### Post by bred on 2008-06-21
[COLOR="Blue"]try envy[/COLOR]

[http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

---

### Post by Sadbird on 2008-06-21
How do I download and use it on recovery mode?
(Sorry, I'm a newbie on this)
When I type things on the terminal, logged as root, I get a pop out window saying:
Failed to start the Xserver (your grapphical interface). It is likely that it is not set up correctly.  WOuld you like to view the xserver output to diagnose the problem?
And then something about Nvidia Linux X86.

---

### Post by PinkFloyd102489 on 2008-06-21
What model graphics card is it?

---

### Post by bred on 2008-06-22
> **Sadbird said:**
> How do I download and use it on recovery mode?
(Sorry, I'm a newbie on this)
When I type things on the terminal, logged as root, I get a pop out window saying:
Failed to start the Xserver (your grapphical interface). It is likely that it is not set up correctly.  WOuld you like to view the xserver output to diagnose the problem?
And then something about Nvidia Linux X86.


[COLOR="Blue"]install envy from terminal

wget [http://somewhere.com/something](http://somewhere.com/something)

So for Envy it would be
[/COLOR]

[COLOR="DarkRed"][wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.3-0ubuntu5_all.deb]("wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.3-0ubuntu5_all.deb")[/COLOR]

[COLOR="Blue"]if you have the repositories all you have to do is

sudo apt-get install envy[/COLOR]


[COLOR="Blue"]Kind regards,
A.[/COLOR]

---

### Post by phidia on 2008-06-22
If you would rather work in a graphical desktop, and a lot of us would, you can either edit your /etc/X11/xorg.conf or type sudo dpkg-reconfigure xserver-xorg. If you use the dpkg command don't worry about questions the program asks that you don't know you just want to select either the open source "nv" or the "vesa" driver. 
That should get you a useable desktop again.

---

