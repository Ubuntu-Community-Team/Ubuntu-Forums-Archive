---
title: "Starting graphics interface (XFCE?)"
date: 2019-06-01
forum: New to Ubuntu
---

### Post by ceblair on 2019-06-01
I used netinst to install Xubuntu (perhaps not a good choice).  I am able to log into a character-based interface, but do not see how to start a graphics window for things like web browsing.  Is mozilla or iceweasel available for browsing?

---

### Post by cruzer001 on 2019-06-01
What you have installed is just a building block for a complete system and that is why you have only a text interface.  This is a Debian installer and may not be suitable for a Ubuntu install.  I don't know for sure, never used it.  The Ubuntu equivalent is our mini.iso, but why not just use the Xubuntu live installer?

---

### Post by Bashing-om on 2019-06-01
ceblair; Hello

As cruzer001 says :) From here one builds what they want. There is no GUI until you install the foundations to support the GUI as well as a GUI. Takes a bit of know-how, if you are not somewhat already handy it can be a chore.

For what it is worth - I do "roll-my-own"; and I am very pleased with the results running on old hardware.

We can advise better when you tell us the situation and your goals.
If it is a lightweight install with a GUI then may I recommend (x)ubuntu's core install ?
[https://unit193.net/xubuntu/core/](https://unit193.net/xubuntu/core/)

[INDENT]you can have it your way
[/INDENT]

---

### Post by again? on 2019-06-01
The word "Netinst" is often used when referring to an ubuntu install from a mini.iso

As a start check you have a graphical session installed and a display manager.
eg 
```
sudo apt install xfce4-session lightdm lightdm-gtk-greeter
```

---

### Post by ceblair on 2019-06-01
> **guber2 said:**
> The word "Netinst" is often used when referring to an ubuntu install from a mini.iso

As a start check you have a graphical session installed and a display manager.
eg 
```
sudo apt install xfce4-session lightdm lightdm-gtk-greeter
```

Thank you *very* much.  I was afraid I would have to burn a new CD for a different installer.

After "sudo apt install xfce4-session" and "sudo apt install xdm" I am at least able to
get to a graphics interface.

The browser I used to use on debian was "iceweasel" (I think also known as mozilla).
sudo apt did not want to install either of these.  What should I do?

Thanks again, everyone.

---

### Post by again? on 2019-06-01
Just install firefox.
Iceweasel is a debian branded version of firefox. [https://en.wikipedia.org/wiki/Mozilla_software_rebranded_by_Debian](https://en.wikipedia.org/wiki/Mozilla_software_rebranded_by_Debian)

Something else you might stumble on is make sure you have a policykit agent installed and added to startups.
This presents an admin confirmation dialog when gui applications require elevated privileges.
Xubuntu (xfce4) uses policykit-1-gnome but there are others.
[https://wiki.archlinux.org/index.php/Polkit](https://wiki.archlinux.org/index.php/Polkit)

---

### Post by ceblair on 2019-06-02
Thanks again.  I had a senior moment forgetting about "firefox".  You're quite right that I need to learn about policykits

---

### Post by ceblair on 2019-06-02
> **guber2 said:**
> Just install firefox.
Iceweasel is a debian branded version of firefox. [https://en.wikipedia.org/wiki/Mozilla_software_rebranded_by_Debian](https://en.wikipedia.org/wiki/Mozilla_software_rebranded_by_Debian)

Something else you might stumble on is make sure you have a policykit agent installed and added to startups.
This presents an admin confirmation dialog when gui applications require elevated privileges.
Xubuntu (xfce4) uses policykit-1-gnome but there are others.
[https://wiki.archlinux.org/index.php/Polkit](https://wiki.archlinux.org/index.php/Polkit)

I think I have stumbled on the policykit issue badly.

Yesterday, I started a graphics session with xwm, downloaded some files, did a little browsing, compiled a few programs, nothing fancy.

Full of confidence, I typed what I used to use with debian:

shutdown -h now

Today, I turned the machine on, and got a blank screen.

In desperation, I went through the xubuntu install process from the beginning, getting a character-based thing.

Before trying to install things, I thought it might be a good idea to see if I could log off and log back on with:

shutdown -r now

I got

ignored: the name org.freedesktop.policykit1 was not provided

I really have no idea what I'm doing, as is probably apparent already,
and hope you can continue to bail me out.

---

### Post by again? on 2019-06-02
I don't really know myself what relies on what although I have managed to get a workable minimal system from a mini.iso.
If you did use an Ubuntu mini.iso you may find it easier to install the complete Xubuntu desktop with...
> sudo apt install xubuntu-desktop
You would then choose the Xubuntu session at the greeter.

---

### Post by ceblair on 2019-06-02
Thank you very much.  These seem to be the "magic words."

I hope I may pester you with something basic.   The installer gave me a set of
boxes for possible packages.  I was supposed to check boxes for what I wanted.
I couldn't figure out what key to press to put an X in a box!

---

### Post by again? on 2019-06-02
Usually with ncurses dialogs it's the space key to select and arrow keys or tab to move.

---

