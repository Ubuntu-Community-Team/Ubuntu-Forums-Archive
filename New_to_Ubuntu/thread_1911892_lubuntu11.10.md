---
title: "lubuntu11.10?"
date: 2012-01-19
forum: New to Ubuntu
---

### Post by cheatos on 2012-01-19
Hi all,

I have lubuntu on my laptop and it everything has screwed up pretty much, even though I didn't do anything about any system files or so.
So here is what I experience:
When I try to start a program, I have to click the icon multiple times (like 20 times or so) and when the program finally started it closed itself at random.
Especially I have downloaded the ubuntu software center (which is pretty awesome) but this doesn't open in a large window anymore where I can choose stuff, it's basically just the top menu with File, Edit and stuff.
When I click maximize the Window maximizes but still there is no content inside, what makes the program useless.
I already tried reinstalling the Software Center, but that didn't help anything.
Does anybody have some ideas what can be the cause?

Thanks

---

### Post by Diametric on 2012-01-19
Can you give us the specs to your machine?

---

### Post by Rex Bouwense on 2012-01-19
Which icons are you clicking 20 times?  Are you talking about the menu?
Is this a new install or have you tweaked the system?
Are you talking about the Ubuntu Software Center or the Lubuntu Software Center?  I have both installed and they are both working flawlessly.

---

### Post by cheatos on 2012-01-19
Hi,

thanks for your quick responses!

I have the ubuntu software center not the lubuntu software center (don't even know, where to get this)

The specs I don't know at the moment, I'll be looking them up.

Its the icons right of the "start" menu button but also if I choose an application in the start menu it doesn't start, so I'd say it is independent of the place the icon is.

---

### Post by MG&amp;TL on 2012-01-19
Okay, a couple of things to try.

Get a terminal open(either by your hammering approach, or Ctrl-Alt-T), then type the names of a few apps. (I'm looking for errors to indicate something looping, etc.)

Possible things to launch:

```
gnome-mplayer
```
```
leafpad
```
```
ubuntu-software-center
```

etc.

LSC (pet project):

```
sudo add-apt-repository ppa:lubuntu-desktop/ppa
sudo apt-get update
sudo apt-get install lubuntu-software-center
```

Lubuntu is meant for old computers, but there is a limit to how old. If we're talking ten-fifteen years plus, maybe it's just run out of processing power.

---

### Post by Rex Bouwense on 2012-01-19
I thought Lubuntu Software Center was in the repository now.  I just checked the Synaptic Package Manager and it shows up.

---

### Post by MG&amp;TL on 2012-01-19
> **Rex Bouwense said:**
> I thought Lubuntu Software Center was in the repository now.  I just checked the Synaptic Package Manager and it shows up.

It is?

OK, ignore what I said!

Sorry, been running Precise, so I have NO idea.

---

### Post by cheatos on 2012-01-20
Here's what happens when I try starting Software Center:

```

user@MatinsNotebook:~$ ubuntu-software-center
could not open file '/etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_marblearena2_ubuntu.list'
ubuntu-software-center: Befehl nicht gefunden.
user@MatinsNotebook:~$ 

```btw, the computer is not that old, its a Siemens lifebook, so maximum 5 years I suppose (have bought it used though)

So here's also the info of my system:

Intel Core2Duo T2700 @ 2.00 Ghz
with 2GB RAM

so hardware shouldn't be a problem, right?

---

### Post by Diametric on 2012-01-20
No, that is a decent amount - should run all Ubuntu/Linux distro's.

---

### Post by cheatos on 2012-01-21
Oh, one thing is still possible, could it be, that the Software Center isn't compatible with the 64bit Lubuntu?

---

### Post by Rex Bouwense on 2012-01-21
When I first downloaded the Ubuntu Software  using Lubuntu 11.10, I thought it was broke because all I could see was a list of general topics running down the left side of the screen.  After much anguish I did notice that there were arrows indicating a submenu.  I clicked on one of the arrows and lo and behold the submenu came up.  Is this the case in your second problem or is there just nothing?

---

### Post by cheatos on 2012-01-21
Ubuntu Software Center IS compatible with lubuntu, I can run it as admin-user.
It does just not run as a normal user.

---

