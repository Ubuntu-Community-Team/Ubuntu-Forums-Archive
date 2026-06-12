---
title: "old laptop how to strip down xubuntu"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by duruttye on 2008-10-24
Hello!

One quick question: how to strip down an already installed xubuntu 8.04?

This is what I need: 
Lightweight browser
wine - for SPSS statistical application
lightweight music player 
ssh
open office (spreadsheet - only)
and pidgin
lightweight photo viewer

The rest of the applications (games, cd burning and stuff) will not be used at all.

Using a dell latitude CPX with 128ram and a little more the 600mhz

I want to strip it down, 'cause it is pretty slow right now.

I found only guides to install from scratch a minimal system, but I don't want to install it again, but if someone thinks that installing from scratch would much more simple, just say so.

Thanx guys!

---

### Post by kellemes on 2008-10-24
Couple of links about lightweight apps.
[http://kmandla.wordpress.com/software/]("http://kmandla.wordpress.com/software/")
[http://bbs.archlinux.org/viewtopic.php?id=18880]("http://bbs.archlinux.org/viewtopic.php?id=18880")
[http://bbs.archlinux.org/viewtopic.php?id=41168]("http://bbs.archlinux.org/viewtopic.php?id=41168")

[Gnumeric]("http://www.gnome.org/projects/gnumeric/") could be a lighter alternative to Open Office as a spreadsheet.
Also I think you're going to gain the most results by using a different window manager, like Fluxbox or IceWM or something.

---

### Post by Dr Small on 2008-10-24
If that's all you are going to install on it, I wouldn't use Xubuntu, as it isn't lightweight by any standards anymore. Best bet would be to try ArchLinux with Openbox (of XFCE if that is your taste), or Icebuntu or Fluxbuntu.

---

### Post by snowpine on 2008-10-24
> **duruttye said:**
> Hello!

One quick question: how to strip down an already installed xubuntu 8.04?

This is what I need: 
Lightweight browser
wine - for SPSS statistical application
lightweight music player 
ssh
open office (spreadsheet - only)
and pidgin
lightweight photo viewer

The rest of the applications (games, cd burning and stuff) will not be used at all.

Using a dell latitude CPX with 128ram and a little more the 600mhz

I want to strip it down, 'cause it is pretty slow right now.

I found only guides to install from scratch a minimal system, but I don't want to install it again, but if someone thinks that installing from scratch would much more simple, just say so.

Thanx guys!

Hi there, I have a Dell Latitude Cpx too, amazing! I've tried many distros on it over the past year (Ubuntu, Xubuntu, Fluxbuntu, Crunchbang, Debian, Slitaz, Puppy, DSL, etc). The reason Xubuntu is slow is because our computers are slow. :) The first thing you need to do is upgrade your ram--256mb minimum, 512mb even better. But Xubuntu will never be super-fast even with the extra ram. Removing applications you don't need unfortunately won't speed up the computer, it will only free up a little bit of hard drive space. 

Personally I was never happy with Xubuntu on that computer, even with the ram upgrade. It was usable but not fast enough for me. You can get a big boost in performance by using a lightweight windows manager like Openbox, Fluxbox, Icewm, etc. (look around the Forums for some good tutorials). The advantage to this method is you get to keep your current install.

If you are open to trying different distros, one that's definitely worth checking out is called Crunchbang. It uses Ubuntu 8.04 minimal plus Openbox (plus Crunchbang also has an Xfce option, which I've never really checked out). I used Crunchbang on my Dell Cpx (with upgraded ram) for several months with good results. 

Currently I am using a distro called SliTaz on my Dell Cpx, and I am very satisfied with its speed and performance. Definitely worth checking out (although I don't think it has Wine). I have also had pretty good luck with Debian Etch (I installed the Gnome desktop, but I have heard good things about Debian Etch Xfce too). Debian has almost the exact same interface as Ubuntu, but the difference in speed on old hardware like ours is quite noticeable. 

Good luck! Let me know if you have any questions. :)

---

### Post by bhadotia on 2008-10-24
> This is what I need:
Lightweight browser
wine - for SPSS statistical application
lightweight music player
ssh
open office (spreadsheet - only)
and pidgin
lightweight photo viewer

Lightweight browsers- Kazehakase, epiphany (I know its not spelled right!), or many of the CLI based ones like lynx (If you can use them:popcorn:)
ssh- openssh
openoffice- abiword, googledocs
pidgin- pidgin:)
photoviewer- mirage, riesserto

Turn off the services you don't need (e.g., I don't need bluetooth so I turned bluetooth off in System>Administration>Services and edited the /etc/modprobe.d/alaises file to disable hidden services, in my case irda and ipv6). And search the net for other tweaks I can't remmember:)

---

### Post by kpkeerthi on 2008-10-24
Try gnumeric for spreadsheeting.
gmusicbrowser for music (I actually found this installed by default in Zenwalk which uses XFCE and I found it really cute and very functional)
Mirage for photos.

---

### Post by duruttye on 2008-10-29
Well, xubuntu isn't the right choice for this laptop, i's sure now. I had to give it a try. It is killing the pore old thing.

Right now I'm downloading Fluxbuntu, lets see how will that go.

For the memory upgrade: I had a spare memory, but it was ddram2, and it doesn't fit :) and I have no idea from where will I get ram of this kind. So I'm stuck with 128 :)

I will keep you updated about the fluxbuntu try-out.

Thanx!

---

### Post by MinstrelBoy on 2008-10-29
I use Puppy Linux 4.1 on an HP 300Mhz with 192mb ram and it runs fine.
Well recommended.

---

### Post by bodhi.zazen on 2008-10-29
You are better off installing a minimal system (either from the Alternate CD or the Ubuntu minimal CD) then installing only the apps you need.

For example, install XFCE rather then xubuntu-desktop.

See this link for light weight distros :

[http://ubuntuforums.org/showthread.php?t=575456](http://ubuntuforums.org/showthread.php?t=575456)

---

### Post by OldTimeTech on 2008-10-29
Check out ebay for an upgrade to your memory....or tigerdirect.com

---

### Post by duruttye on 2008-10-29
I have to check out the puppy linux>wine>SPSS configuration.

For the minimal install: the laptop doesn't have an ethernet card, so if I try a minimal install will the make the usb wireless adapter work? 'cause if not, I didn't do a thing. These days, without the internet... :)

Oh, yeah, checking out ebay is okay, but shipping anything in Romania is not okay at all... :)

Fluxbuntu question:
cannot make the wireless adapter work, lspci shows it, the network-configuration tool sees it, but after a short connection it always drops it.
No idea why...

This is something like the last lines in dmesg:

phy0 -> rt2x00usb_vendor_request: error - vendor request 0x06 failed for offset .....

...many times
any ideas?

---

### Post by PhilipGanchev on 2009-09-18
The laptop might also have a PCMCIA port. If so, you can get a PCMCIA-ethernet dongle.

As for light browsers, there are Dillo and Links graphical (links2 -g).

---

### Post by fooman on 2009-09-18
for a minuscule install,  fast & very lightweight os....give masonux a try.  based on ubuntu and using lxde....its super light.  i run it on my netbook and i am impressed.

needs 256 ram for the *graphical* installer....the os itself can run on less.  see here for info:

[http://sites.google.com/site/masonux/home](http://sites.google.com/site/masonux/home)

---

### Post by coolbrook on 2009-09-18
You bumped a really old thread. Anyways, Puppy Linux 4.3 was just released today.  I downloaded it and will see how it goes on one of my old systems.  I didn't care too much for the installation of an older version. The current one is running on kernel 2.6.30.5.

---

