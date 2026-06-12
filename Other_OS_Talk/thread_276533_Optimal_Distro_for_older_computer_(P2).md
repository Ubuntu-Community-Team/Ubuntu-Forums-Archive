---
title: "Optimal Distro for older computer (P2)"
date: 2006-10-13
forum: Other OS Talk
---

### Post by kopilo on 2006-10-13
Ok here is the computer specs.
Pentium II - 300 MHz
256MB RAM
6GB Hard Drive
Nvida graphics card.

All the computer needs to be able to do is, store documents, word process (Open Office), some image organisation, browse the internet (Firefox) and connect to other computers via ethernet.

So which distribution would you suggest for this old computer?

Currently it is running Mepis 3.3

---

### Post by swamytk on 2006-10-13
Here is my system:
PIII 800MHz with 192MB RAM.

I am using Debian-sid with xfce4.4 (latest) with amazing good speed. After a long search I settled with this. Though Ubuntu is good, but speed made me to go for Debian system. Refer: [http://cutecomputer.wordpress.com/2006/10/08/debian-the-king-of-linux-distros/](http://cutecomputer.wordpress.com/2006/10/08/debian-the-king-of-linux-distros/)

---

### Post by kerry_s on 2006-10-13
I think you should build it to your needs. Grab a copy of the alternate cd and do the server install, then just apt-get your system.

example:
server install
sudo su  <to become root
nano /etc/apt/sources.list
comment(#) out the cdrom and uncomment all the repos
ctrl and x and y and enter to save
apt-get update
apt-get install x-window-system-core xterm (xdm,wdm,gdm,kdm) (fluxbox,openbox,wmaker,icewm,gnome-core,kde-core,...)
reboot
login
continue building by apt-getting or grab synaptic and go graphical.

You'll end up with a system tailored to your needs. I'm using a very fast kde build up, i just did this->

apt-get install x-window-system-core xterm kdm kde-core synaptic

and then i just slowly grabbed what ever else i need. Since i'm running a very minimal kde it's very fast, compared to the whole desktop environment.

---

### Post by Anonii on 2006-10-13
**Debian sarge**
with Fluxbox.

I think it will be great for you.

---

### Post by kopilo on 2006-10-13
Thank you for your suggestions thus far. I don't know how user friendly Fluxbox is.. I'm not the regular user on the computer and the person who is, is fairly computer savvy but generally everything needs to work at the touch of a button. (This is actually why I'm looking for a different OS to Mepis because the networking isn't exactly working out).

---

### Post by Anonii on 2006-10-13
> **kopilo said:**
> Thank you for your suggestions thus far. I don't know how user friendly Fluxbox is.. I'm not the regular user on the computer and the person who is, is fairly computer savvy but generally everything needs to work at the touch of a button. (This is actually why I'm looking for a different OS to Mepis because the networking isn't exactly working out).
I still suggest Debian Sarge, but you may try Xfce, which is lighter than GNOME/KDE and still user friendly. Fluxbox requires some configurations.

---

### Post by kopilo on 2006-10-13
Thanks, I would like to test it out, but there doesn't seem to be a live Disc version.

By the way off the Debian website I came across [ubuntuLite]("http://www.ubuntulite.org") (it looks like what I am looking for)but unfortunatly it seems to still be in development.

---

### Post by kerry_s on 2006-10-13
ubuntulite is just ubuntu base(server) install and icewm->

alternate cd
server install
(see my post above)
apt-get install x-window-system-core xterm gdm icewm
reboot
login and enjoy

in the time your taking to look for a preconfigured system you could have already built a system to your needs.

---

### Post by dyefade on 2006-10-13
Not that I've used it myself, but if you're considering Fluxbox at all (and there's no reason not to, IMO), maybe [Fluxbuntu]("http://www.fluxbuntu.org/") would be of interest to you. There are a lot of other suggestions here, but I for one would suggest either Xfce or Fluxbox as a WM.

---

### Post by kopilo on 2006-10-13
> **kerry_s said:**
> ubuntulite is just ubuntu base(server) install and icewm->

alternate cd
server install
(see my post above)
apt-get install x-window-system-core xterm gdm icewm
reboot
login and enjoyThank you.

> in the time your taking to look for a preconfigured system you could have already built a system to your needs.
Yes but I can't touch the computer for a while anyway.

I'll probably go with Xfce or fluxbox in any case, because they tend to be lighter then KDE or Gnome. Although icewm looks light as well.

---

### Post by K.Mandla on 2006-10-13
> **kopilo said:**
> Ok here is the computer specs.
Pentium II - 300 MHz
256MB RAM
6GB Hard Drive
Nvida graphics card.

All the computer needs to be able to do is, store documents, word process (Open Office), some image organisation, browse the internet (Firefox) and connect to other computers via ethernet.

So which distribution would you suggest for this old computer?
I would try Xubuntu first, just to feel if it's terribly sluggish or not. I think you nail down most of your needs with Abiword, the Gimp, etc., and they're installed by default.

If that proves unusable, you have a variety of options. [Zenwalk]("http://www.zenwalk.org") is light and easier on the hardware. [Slax]("http://www.slax.org") is another excellent lightweight distro, and one of my recent favorites. You could even dip as far down as [DSL]("http://www.damnsmalllinux.org"), [Feather Linux]("http://featherlinux.berlios.de/") or [Puppy Linux]("http://www.puppylinux.org/"), but I think with a machine like that you can get away with more than those.

If it were me, I'd use kerry_s's suggestion and build up from there. That's what I used on [a similar machine]("http://www.ubuntuforums.org/showthread.php?t=273061"), and it's a marvel of modern science now. That will depend on your comfort level with linux, of course. 

Cheers and good luck!

---

### Post by kopilo on 2006-10-13
Thanks, I was looking at Xubuntu not that long ago.

However this is a little off topic, but could you point me in the direction of the Networking wikis or something, that is the only issue I have with the Ubuntu range. (I'm a newb with networking and can't seem to get the printer or files shared).

---

### Post by cunawarit on 2006-10-13
I have a very similar machine, a PII300 with 224Mb of RAM.

I ran it with DSL (HD install), and also Debian Sarge with fluxbox. Both ran great! Currently it has Debian Sarge.

---

### Post by seuaniu on 2006-10-13
one of my spare laptops:

Celeron 300
64MB memory
6GB drive

I run xubuntu on it without many problems.  The bootup and login is painfully slow, but after that it runs fine.  With as much memory as you have in your machine, you should be able to run firefox, Oo.o, gaim, etc without too much slowdown.

In the past, i've run dsl and debian sarge on it, both of which worked ok.  I currently use it for xdmcp connect to my main machine.  If thats an option for you, I highly recommend doing that since all the older machine gets used for is a display and input device.

---

### Post by K.Mandla on 2006-10-13
> **kopilo said:**
> could you point me in the direction of the Networking wikis or something. ...
Oh, my goodness. Where do we begin?

[https://wiki.ubuntu.com/?action=fullsearch&context=180&value=network&titlesearch=Titles](https://wiki.ubuntu.com/?action=fullsearch&context=180&value=network&titlesearch=Titles)

Actually, just jumping to [https://wiki.ubuntu.com](https://wiki.ubuntu.com) and searching for your topic is the best way to start. 

There's also the [Ubuntu Document Storage Facility]("http://doc.gwos.org/index.php/Main_Page"), which has some of the best of the forums in a concise and easy-to-manage location. 

Remember there's a subforum specific to Networking [here]("http://www.ubuntuforums.org/forumdisplay.php?f=136"). Short of that, a forum search or even a Google search might help you get started. 

(As an aside, I generally use [NFS]("http://www.ubuntuforums.org/showthread.php?t=249889") for file sharing, but I don't have any Windows machines. If you want to share with Windows machines you want [Samba]("http://www.ubuntuforums.org/showthread.php?t=202605").)

---

### Post by kopilo on 2006-10-14
Thank you for all the links.

Ok thus far I have tried 
Puppy Linux Community Edition 203 (doesn't seem to load).
Damn Small Linux 3 (*thumbs up* can't believe the difference between 3 and when DSL was still a hack).
Fluxbuntu (internet not working... A little bit sluggish but not as bad as Mepis 3, EDIT: Way too painful to shutdown safely).
Ubuntulite (requires install, learnt that the hard way)
Xubuntu (Xubuntu running, seems a little chunky).

---

