---
title: "Lightest Linux GUI Distro Ever"
date: 2011-07-04
forum: Recurring Discussions
---

### Post by createdcreature on 2011-07-04
Which do you think is? I think Feather, Damn Small, and Tiny Core.

---

### Post by Spice Weasel on 2011-07-04
[BL]("http://distro.ibiblio.org/pub/linux/distributions/baslinux/") possibly? It's 3mb.

---

### Post by snowpine on 2011-07-04
"of all time" you'd have to go back to the early days, lots of distros from the 90's were distributed on floppy discs!

"that I'd want to use today" I am a big fan of SliTaz! :)

---

### Post by createdcreature on 2011-07-04
What about Puppy?

---

### Post by jerenept on 2011-07-04
> **Robert Moyse said:**
> What about Puppy?

DSL:50MB
TinyCore:10MB
Puppy:150MB

---

### Post by createdcreature on 2011-07-04
I mean on RAM.

---

### Post by snowpine on 2011-07-04
> **Robert Moyse said:**
> I mean on RAM.

How much RAM does your computer have?

---

### Post by createdcreature on 2011-07-04
Not saying. I just want to know the lightest post 2004 distro on RAM.

---

### Post by Lucradia on 2011-07-04
> **Spice Weasel said:**
> [BL]("http://distro.ibiblio.org/pub/linux/distributions/baslinux/") possibly? It's 3mb.

Alone, it's 12 MB, so Tiny Core still wins. (The 3mb version requires DOS.)

MINIX is 16 MB: [http://www.minix3.org/](http://www.minix3.org/)

Booting a Live image unloads everything into RAM, hence why they're asking for RAM.

---

### Post by createdcreature on 2011-07-04
WHEN will tiny core get a proper installer?

---

### Post by Lucradia on 2011-07-04
> **Robert Moyse said:**
> WHEN will tiny core get a proper installer?

Tiny core is modular, you have to know what to install, or else it won't work (it cannot search for depends.) This is to reduce image size.

---

### Post by createdcreature on 2011-07-04
I mean OS installer to HDD.

---

### Post by Spice Weasel on 2011-07-04
TinyCore is not meant to be installed on a HD. However, you can still do it:

[http://wiki.tinycorelinux.net/wiki:install_hd](http://wiki.tinycorelinux.net/wiki:install_hd)

It really isn't that hard, and I expect they will make a GUI FLTK installer at some point.

---

### Post by BrokenKingpin on 2011-07-04
Probably TinyCore these days. Damn Small Linux used to be awesome for a really light desktop, but I do not think it is actively maintained anymore.

---

### Post by createdcreature on 2011-07-04
The Damn Small developers fell out, and Feather is basically alpha, and has never been changed for 6 years.

---

### Post by Lucradia on 2011-07-04
> **Robert Moyse said:**
> The Damn Small developers fell out, and Feather is basically alpha, and has never been changed for 6 years.

Boot debian netboot if you can, and just install xorg, openbox and sakura.

I'd suggest getting some devs to make a slimmer xorg based on framebuffer or whatever it's called. For those of us who edit our configs via text files, rather than GUI.

---

### Post by shobon on 2011-07-04
> **Lucradia said:**
> Alone, it's 12 MB, so Tiny Core still wins. (The 3mb version requires DOS.)

MINIX is 16 MB: [http://www.minix3.org/](http://www.minix3.org/)

Booting a Live image unloads everything into RAM, hence why they're asking for RAM.

Minix isn't a Linux distribution.

---

### Post by Spice Weasel on 2011-07-04
I think KolibriOS beats everything when including non-Linux operating systems. Completely written in Assembly. How awesome is that?

It's useless, but still cool to mess around with in a VM.

---

### Post by BrokenKingpin on 2011-07-04
> **Lucradia said:**
> Boot debian netboot if you can, and just install xorg, openbox
This is what I do if I need a lightweight distro for an older machine... would probably give you a more usable system than TinyCore. TinyCore is probably only needed if it is an ancient machine that even Debian netinstall won't even work on.

---

### Post by curaga on 2011-07-05
Old info guys.

> **Robert Moyse said:**
> WHEN will tiny core get a proper installer?
[http://distro.ibiblio.org/tinycorelinux/install.html](http://distro.ibiblio.org/tinycorelinux/install.html)
[http://distro.ibiblio.org/tinycorelinux/videos/installer.html](http://distro.ibiblio.org/tinycorelinux/videos/installer.html)

> Tiny core is modular, you have to know what to install, or else it won't work (it cannot search for depends.) This is to reduce image size.

That was true in the 1.x days.

---

### Post by createdcreature on 2011-07-05
Only talk about Linux here, no Minix, BSD or anything like that.

---

### Post by Lucradia on 2011-07-05
> **Robert Moyse said:**
> Only talk about Linux here, no Minix, BSD or anything like that.

But it's still UNIX-based, like LINUX.

---

### Post by createdcreature on 2011-07-06
I only want Linux.

---

### Post by Spice Weasel on 2011-07-06
Why?

---

### Post by jhonan on 2011-07-06
Is this a Turing Test?

---

### Post by Lucradia on 2011-07-06
> **Spice Weasel said:**
> Why?

Well for one, MINIX doesn't like newer graphic cards from even 2005+

---

### Post by createdcreature on 2011-07-06
I think it is Damn Small.

---

### Post by dargaud on 2011-07-06
The smallest Linuxes are the custom versions built with tools such as BuildRoot for embedded systems, but they can be built for x86 as well. I create new ones every day below 2Mb with ssh server, plenty of user apps, etc. It's based on uClibc and BusyBox. In the end you can reduce it to no more than 3 static files and one link (the bootloader, busybox, the kernel, init) and still have a functional OS. It all depends how much functionality you want to remove (FPU, hardware, command line...) but you could probably build one for a couple of 100kb or so.

---

### Post by Random_Dude on 2011-07-06
> **Spice Weasel said:**
> [BL]("http://distro.ibiblio.org/pub/linux/distributions/baslinux/") possibly? It's 3mb.

That's _2 entire floppy disks_!
Bloated.

---

### Post by createdcreature on 2011-07-06
Too old.

---

### Post by wolfen69 on 2011-07-07
> **curaga said:**
> 
[http://distro.ibiblio.org/tinycorelinux/install.html](http://distro.ibiblio.org/tinycorelinux/install.html)
[http://distro.ibiblio.org/tinycorelinux/videos/installer.html](http://distro.ibiblio.org/tinycorelinux/videos/installer.html)


I just tried it in vbox, and there was no installer available. What's up with that?

---

### Post by createdcreature on 2011-07-07
I had the same problem!

---

### Post by Spice Weasel on 2011-07-07
I don't know why that screenshot shows the installer as an icon in the dock.

Click on the 'Panel' icon in the dock and then select HD/USB Install.

You need to have dosfstools and perl installed first.

---

### Post by createdcreature on 2011-07-07
Anyway, I think, for modern distros, Tiny Core.

---

### Post by Lucradia on 2011-07-07
> **Robert Moyse said:**
> Anyway, I think, for modern distros, Tiny Core.

Remember, you have to know what you need to install on your HD to have a functional Tiny Core, as it doesn't search for depends when installing stuff (all modular.) I'm sure there are tutorials out there though.

---

### Post by createdcreature on 2011-07-08
Tiny Core 3x does!

---

