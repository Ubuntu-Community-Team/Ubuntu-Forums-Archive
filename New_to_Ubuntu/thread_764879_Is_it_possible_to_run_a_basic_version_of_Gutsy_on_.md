---
title: "Is it possible to run a basic version of Gutsy on 700MHz 256mb?"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by carloslosgrande on 2008-04-24
[FONT="Comic Sans MS"][I]I've finally got somebody to fix my wife's little sony vaio sr17k.
I want to use it with my files and stuff from my desktop. I installed Fluxbuntu but I'm finding that difficult, and it uses Abiword which won't read OpenOffice files - I tried once before.
I read, in one of the threads here, that someone was running Feisty on 256mb.
I tried Xubuntu previously and didn't like that much either - I need real simple (read *[COLOR="Red"]very easy to use[/COLOR]*)systems, just like me.
I've got Linux Mint running in virtual on my desktop, which is simple enough, but I think thats basically the same as to requirements as Gutsy.
Really, I just prefer standard Ubuntu to anything else I've tried (pclinuxos, pcbsd, sam, sabayon) and I'd rather have the same basic setup.
Is it possible? pretty please?[/I][/FONT]

---

### Post by billgoldberg on 2008-04-24
> **carloslosgrande said:**
> [FONT="Comic Sans MS"][I]I've finally got somebody to fix my wife's little sony vaio sr17k.
I want to use it with my files and stuff from my desktop. I installed Fluxbuntu but I'm finding that difficult, and it uses Abiword which won't read OpenOffice files - I tried once before.
I read, in one of the threads here, that someone was running Feisty on 256mb.
I tried Xubuntu previously and didn't like that much either - I need real simple (read *[COLOR="Red"]very easy to use[/COLOR]*)systems, just like me.
I've got Linux Mint running in virtual on my desktop, which is simple enough, but I think thats basically the same as to requirements as Gutsy.
Really, I just prefer standard Ubuntu to anything else I've tried (pclinuxos, pcbsd, sam, sabayon) and I'd rather have the same basic setup.
Is it possible? pretty please?[/I][/FONT]

Yes, I'm pretty sure that gutsy (you should really consider the new hardy version) will work on 256mb of ram. The livecd won't run, use the aleternate cd to install it.

Xubuntu will be faster, but ubuntu should run decently. You could tweak it a bit to make it faster. Disable certain programs on start-up, use thunar instead of nautilus,  delete unneeded software, ... (maybe even a different file system like reiserfs)

---

### Post by linuxlizard on 2008-04-24
You might try tinyme:
screenshots:

[http://www.thecodingstudio.com/opensource/linux/screenshots/index.php?linux_distribution_sm=TinyMe%202007%20Test%206](http://www.thecodingstudio.com/opensource/linux/screenshots/index.php?linux_distribution_sm=TinyMe%202007%20Test%206)

homepage:
[http://www.mypclinuxos.com/doku.php/tinyme](http://www.mypclinuxos.com/doku.php/tinyme)

It has synaptic and you can add whatever features you want.
I use it's sister distro called pcfluxboxos on my p3 700 with 192 mb ram and it's very fast compared to xubuntu, set everything up on my laptop without my touching it or fiddling with files, and like ubuntu it is very easy to use and comes with app repositories loaded with the latest software. But it sounds like you don't like fluxbox and TinyMe is supposed to be just as light as pcfluxboxos and it's got the same foundation, so setup should be just as easy and running should be just as fast.

Of course, you could simply use synaptic with xubuntu to get open office...

---

### Post by carloslosgrande on 2008-04-24
[FONT="Comic Sans MS"]*[SIZE="4"]Thanks for the quick replies. I'll check out those links. I'm also waiting for Hardy but the servers are full at the moment, I'll wait till things calm down a bit. I might just give Gutsy a try to see how it goes.[/SIZE]*[/FONT]

---

### Post by cykotiktek on 2008-04-24
on my slower pc's here at work i run xubuntu.  The front end is much lighter on it and pretty much any packages i want i can install.  mine are 933 p3's with 256mb of ram and it runs very well.  I am going to do some testing this afternoon though running hardy on one of these boxes to see how it goes.  I tried to run gutsy and it was pretty slow.

---

### Post by carloslosgrande on 2008-04-24
[FONT="Comic Sans MS"]Ok, TinyMe won't run. It gets stuck right at the beginning with can't 'load live cd'.
I tried Gutsy Minimal cd and it gets stuck at 'select ubuntu archive' after the problem at 'no network interfaces detected'
This machine can uses an external ethernet card bus, so its net OR cd, but not both. I have a wireless adapter but it needs the driver, which can't be loaded before the OS....right?
Fluxbuntu got past the 'no network...' problem.[/FONT]

---

### Post by Paqman on 2008-04-24
On 256MB you'll be pretty restricted to what desktop you can use. I put Xubuntu on my girlfriend's 512MB Celeron because Gnome doesn't run smoothly on that, and it's got twice the RAM you have.

Your easiest route to happiness might be a RAM upgrade, if possible. Otherwise you're pretty much stuck running the lighter desktops like XFCE or Fluxbox.

---

### Post by k4sgt on 2008-04-24
The Hardy release of Xubuntu seems to be working very well on my P4 1.4 Ghz with only 128MB RAM.  The new release is fetching codecs for me just like regular Ubuntu as well.  It also auto configured my wifi.  I think I like!  You should give it a try.  Xubuntu has never felt "hard" to me, but the Hardy release seems to feel easier than ever.

Barry

---

### Post by SOULRiDER on 2008-04-24
> **carloslosgrande said:**
> [FONT="Comic Sans MS"]*[SIZE="4"]Thanks for the quick replies. I'll check out those links. I'm also waiting for Hardy but the servers are full at the moment, I'll wait till things calm down a bit. I might just give Gutsy a try to see how it goes.[/SIZE]*[/FONT]

You and everyone should use Bittorrent to download it instead of using a direct HTTP/FTP link.

---

### Post by carloslosgrande on 2008-04-24
[FONT="Comic Sans MS"]Soulrider, I thought that was automatic now.
Guess not?
Paqman, can't upgrade ram - 256 is system max.[/FONT]

---

