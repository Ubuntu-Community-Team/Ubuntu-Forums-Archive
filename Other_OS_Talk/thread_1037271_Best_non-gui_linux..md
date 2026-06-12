---
title: "Best non-gui linux."
date: 2009-01-11
forum: Other OS Talk
---

### Post by dragos240 on 2009-01-11
I want a linux system that has absolutely NO GUI! Can install via iso, and no fancy crap, i mean i want a linux that is as basic as it gets, with bash of cource <3

---

### Post by cardinals_fan on 2009-01-11
Arch might be good for you.  I prefer CRUX, but it is a bit more advanced.  Almost any distro can be installed without X.

---

### Post by wolfen69 on 2009-01-11
[INX]("http://inx.maincontent.net/") is a great command line distro based on ubuntu.

---

### Post by Twitch6000 on 2009-01-11
Arch or INX would be great for this.

---

### Post by dragos240 on 2009-01-11
> **Twitch6000 said:**
> Arch or INX would be great for this.

INX sounds promising.

Also, is there a slackware non-gui, i've heard all sorts of things about it, is there a non gui version of that?

---

### Post by cardinals_fan on 2009-01-11
> **dragos240 said:**
> INX sounds promising.

Also, is there a slackware non-gui, i've heard all sorts of things about it, is there a non gui version of that?
Slackware is whatever you want it to be, if you put in the effort.  Read up on the different package sets and CDs.

---

### Post by chucky chuckaluck on 2009-01-11
arch is great without x, especially with screen and dvtm.

---

### Post by fistfullofroses on 2009-01-11
> **dragos240 said:**
> INX sounds promising.

Also, is there a slackware non-gui, i've heard all sorts of things about it, is there a non gui version of that?
Slackware can easily be non-gui, just de-select the X package set during install. You may also want to look into Draco.

---

### Post by dragos240 on 2009-01-11
edit, i just tryed INX, it's pwnage! By the way, can you play music on it?

---

### Post by wolfen69 on 2009-01-11
> **dragos240 said:**
> edit, i just tryed INX, it's pwnage! By the way, can you play music on it?

yes you can. it comes with a media player (mplayer i believe) plus, it has shoutcast radio built in. check out the video tutorials on the inx website.

---

### Post by binbash on 2009-01-12
+1 for arch

---

### Post by kerry_s on 2009-01-12
debian base install, it has the largest repo at your disposal, so everything is just a apt-get away. install is the simplest and you don't have to spend tones of time configuring.

here's the net installer for lenny:
[http://cdimage.debian.org/cdimage/lenny_di_rc1/i386/iso-cd/debian-testing-i386-businesscard.iso](http://cdimage.debian.org/cdimage/lenny_di_rc1/i386/iso-cd/debian-testing-i386-businesscard.iso)

at the package selection stage, just uncheck everything for a base install, then it will ask you to install the boot loader and your done.

---

### Post by sertse on 2009-01-12
+1 INX. 

Mainly cause it's a distro that has explicitly given thought to making the console "user friendly". 

IMO, if you're dealing on a console only level, the performance differences are negligible between the Ubuntu base vs something lighter...unless its a *very* ancient machine.    

Though, I'm a bit confused now, since he said nothing fancy, yet INX  shows how the non-gui world could be fancy (and educational)

---

### Post by SomeGuyDude on 2009-01-12
Can someone please show me photographs of how a non-GUI system can do daily tasks? I'm baffled as to how someone could go day to day without any graphics whatsoever. I mean, if all I did was email, post on message boards, do my banking, and write essays... maybe.

---

### Post by cardinals_fan on 2009-01-12
> **SomeGuyDude said:**
> Can someone please show me photographs of how a non-GUI system can do daily tasks? I'm baffled as to how someone could go day to day without any graphics whatsoever. I mean, if all I did was email, post on message boards, do my banking, and write essays... maybe.
One of the stranger sarcastic posts I've seen...

---

### Post by ynnhoj on 2009-01-12
> **SomeGuyDude said:**
> Can someone please show me photographs of how a non-GUI system can do daily tasks? I'm baffled as to how someone could go day to day without any graphics whatsoever. I mean, if all I did was email, post on message boards, do my banking, and write essays... maybe.
please share with us what your daily tasks are (other than email, web browsing, banking, and writing essays ;)) and i'm sure we'll be happy to give you some ideas.

---

### Post by Bachstelze on 2009-01-12
Ubuntu, duh.

Seriously, especially when using them without X, Ubuntu, Debian, Slackware, Gentoo, Arch, LFS or whatever are really close to equivalent. The package manager is pretty much the only difference.

---

### Post by SomeGuyDude on 2009-01-13
> **ynnhoj said:**
> please share with us what your daily tasks are (other than email, web browsing, banking, and writing essays ;)) and i'm sure we'll be happy to give you some ideas.

Well, audio/video/image editing for one. I play some games, specifically I'm addicted to flash games, as well as being a YouTube nut. Also lots of the websites I visit aren't text-based.

I realize that non-GUI OS's aren't considered for everyone, but a lot of people act like it'd work for most people but I'm not sure.

---

### Post by sertse on 2009-01-13
Do we include mplayer-no-gui playing videos through frambuffer?

Elinks is now youtube-capable by doing the above.

See: [http://www.mail-archive.com/elinks-users@linuxfromscratch.org/msg00710.html](http://www.mail-archive.com/elinks-users@linuxfromscratch.org/msg00710.html)

Particualrly the later replies that show how to do it.

---

### Post by cardinals_fan on 2009-01-13
> **HymnToLife said:**
> Ubuntu, duh.

Seriously, especially when using them without X, Ubuntu, Debian, Slackware, Gentoo, Arch, LFS or whatever are really close to equivalent. The package manager is pretty much the only difference.
The init systems vary...

---

### Post by Sorivenul on 2009-01-13
> **SomeGuyDude said:**
> Well, audio/video/image editing for one. I play some games, specifically I'm addicted to flash games, as well as being a YouTube nut. Also lots of the websites I visit aren't text-based.

I realize that non-GUI OS's aren't considered for everyone, but a lot of people act like it'd work for most people but I'm not sure.
**As far as audio goes:**
sox
cuebreakpoints
shnsplit
mplayer

**For images:**
ImageMagick
feh
fbi

Video editing on the CLI may be more difficult, but I suppose it could be done using a framebuffer, mplayer, mencoder, and some ingenuity. See [this link]("http://michaelminn.com/linux/mmsuper8/") for an interesting view on CLI video editing.  

You can even watch some TV with FbTV, control a remote VNC server graphically, and as has been said, elinks for YouTube or links2 for graphical internet on a framebuffer.

In short, it takes some getting used to, but you can make it work.

EDIT:
> **cardinals_fan said:**
> The init systems vary...
You *would* have to bring this up... ;)

---

