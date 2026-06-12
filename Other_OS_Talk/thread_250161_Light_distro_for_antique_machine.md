---
title: "Light distro for antique machine"
date: 2006-09-03
forum: Other OS Talk
---

### Post by Rockyhead on 2006-09-03
Hi!

Having now got the courage and basic skills acquired with Ubuntu, I've given some thought to changing my third machine into a Linux-box. Could you guys help me find the right distro?

It's a Pentium2 266Mhz, 64mb RAM, 4gb HD, currently running Win98. Now it's only collecting dust, but maybe by adding a wifi-card I could turn it into something useful...

Damn Small Linux looks nice, but are there any other small ones out there? I do admit, I'm still a bit n00by when it comes to linux, so I'd like it to be...not that technical :D

---

### Post by ispmarin on 2006-09-03
You can try Xubuntu, or better, debian and XFCE (IMHO, ligher than Xubuntu)... If you are willing to get a _real_ clean system, try to install debian testing with the server option, and then do apt-get very carefully, choosing only the packages that you are really going to use.

---

### Post by Anonii on 2006-09-03
As far as the performance issue is concerned you can change your window manager to something "minimalistic" like [ratpoison]("http://www.nongnu.org/ratpoison/")
Unfortunately, I have never used it, but afaik its the best window manager for ice-age PCs.
Also, Debian is really simple and uses the APT package manager ,exactly like Ubuntu, so you will not have problems to install programs. I dont really know about the server option, that ispmarin said, but yes.. Debian testing (etch) or even stable (sarge) are nice for you. Probably there are even better, but dunno..

Good luck :")

---

### Post by ispmarin on 2006-09-03
Don't be afraid of the "server" installation. It just install a very basic system, giving you the freedom to install very few packages, what is good for your purposes. XFCE or even Window Maker are good choices.

---

### Post by K.Mandla on 2006-09-03
Start with a server install. Then

```
sudo aptitude install x-window-system-core xfce4
```
From there you can add whatever you like. You'll find it's much snappier than a full-blown Xubuntu installation.

Have fun!

---

### Post by ispmarin on 2006-09-03
Does the Xubuntu installation has a "server" install? The Ubuntu Dapper cd and the Kubuntu does not seems to have one... But in debian this is rock solid.

---

### Post by K.Mandla on 2006-09-03
I think you only get the server install option on the alternate (install) CD -- not the desktop CD.

If I were you I would use the alternate CD anyway, because the desktop CD needs about 192Mb to run properly. And it's a little buggy anyway.

If you get a Xubuntu alternate CD and boot to it, you'll get the option for a server installation. 

Let us know if you have any more questions, or run into problems. ;)

---

### Post by ispmarin on 2006-09-03
This alternate/desktop/server installation just give my nerves... But thanks for the information. Why just put the server kernel on desktop and easy or lifes? :D

---

### Post by K.Mandla on 2006-09-03
I'm not sure. Maybe they were thinking most people new to Ubuntu would want to try it, and install the entire version at once.

In a way, a server install is kind of an advanced technique. Maybe not to you and me, but for example, someone new to Linux. 

I'm sure it's all part of the master plan. :mrgreen:

---

### Post by ispmarin on 2006-09-03
Hehe... but this would save a lot of work, err, maybe a cdrom or two... I think that I will post a wishlist on this. Not a big trouble for the installation guys, and very good to us... The new user will just press enter... :p

---

### Post by deanlinkous on 2006-09-03
Debian - server install? Wha..???

One of the options of the older ubuntu CDs was a "server" install which was a tight small install with no GUI and so forth. Then you could add what you wanted. It was sweeeeet! I loved it.

---

### Post by ispmarin on 2006-09-03
Yeah, Debian server install. Exactly what you were saying about this ubuntu install: it was the old'n'good debian server install. No gui, very few packages. And this is exactly my complain: the new and shiny dapper does not give this option anymore, just the "alternative" one. No good...

---

### Post by deanlinkous on 2006-09-06
Well I just call that the base debian install. I usually do not even bother with the STANDARD SYSTEM selection in tasksel. Just the very core base of debian and then add what I want or dont want. One of the tightest lightest fully featured creations I have seen. :)

I wonder if the ALT cd of ubuntu offers the server install? I haven't tried latest ubuntu at all but do have it on the spindle looking at me. :D

---

### Post by SoundMachine on 2006-09-06
DSL is my preference for anything that has below 128MB.

---

### Post by SoundMachine on 2006-09-06
> **deanlinkous said:**
> Well I just call that the base debian install. I usually do not even bother with the STANDARD SYSTEM selection in tasksel. Just the very core base of debian and then add what I want or dont want. One of the tightest lightest fully featured creations I have seen. :)

I wonder if the ALT cd of ubuntu offers the server install? I haven't tried latest ubuntu at all but do have it on the spindle looking at me. :D

You can download the 6.06.1 server ISO from [here]("http://ubuntu.intergenia.de/releases/6.06.1/ubuntu-6.06.1-server-i386.iso")

---

### Post by stantheman286 on 2006-09-06
Hey guys,

I took your suggestion and put on the server install of xbuntu with xfce4, but I had a quick question:  How can I install the old xbuntu boot splash?  Stupif question I know, but I just wanted to see if there was a wuick setting or package that I needed to install.  Thanks!

Matt

---

### Post by RAV TUX on 2006-09-08
> **Rockyhead said:**
> Hi!

Having now got the courage and basic skills acquired with Ubuntu, I've given some thought to changing my third machine into a Linux-box. Could you guys help me find the right distro?

It's a Pentium2 266Mhz, 64mb RAM, 4gb HD, currently running Win98. Now it's only collecting dust, but maybe by adding a wifi-card I could turn it into something useful...

Damn Small Linux looks nice, but are there any other small ones out there? I do admit, I'm still a bit n00by when it comes to linux, so I'd like it to be...not that technical :D


I suggest the [DeadCD]("http://web.isteve.bofh.cz/deadcd/download.htm").

---

### Post by Rayston on 2006-09-11
> **K.Mandla said:**
> Start with a server install. Then

```
sudo aptitude install x-window-system-core xfce4
```
From there you can add whatever you like. You'll find it's much snappier than a full-blown Xubuntu installation.

Have fun!

I did the above, now what? when I type startx it gets to a screen that says 

Xsession: unable to start X session --- no "/home/username/.xse
"/home/username/.Xsession" file, no session managers, no window terminal emulators found; aborting.

and when I try startxfce4 I get 

command not found. 

I know this thread is a bit old, but anyone have any ideas? 

Thanx

Rayston

---

### Post by Dragonbite on 2006-09-11
[CentOS]("http://www.centos.org") works well with older hardware and is easy to set up as a server (including adding Gnome or KDE to get you started). It's graphical installer (anaconda) makes things pretty easy.

During installation you can have it automatically select packages for desktop, workstation or server use. Regardless of which you choose you can customize which programs are installed later on.

What I like about it is that it detected the sound and video card in my old (2000) Sony Viao desktop (Ubuntu and other distros don't recognize my video).

---

### Post by Lord Illidan on 2006-09-11
Zenwalk might also be nice.

EDIT..btw, Yozef you posted a 403 link to the Dead CD : [http://web.isteve.bofh.cz/deadcd/download.htm](http://web.isteve.bofh.cz/deadcd/download.htm) doesn't work.

---

### Post by Markkreuzz on 2006-09-14
For me ive tried dapper 6.06.1 dapper install and then fluxbox and i am very happy,  im running on pII 333 256 MB.

---

### Post by K.Mandla on 2006-09-14
> **Rayston said:**
> I did the above, now what? when I type startx it gets to a screen that says 

Xsession: unable to start X session --- no "/home/username/.xse
"/home/username/.Xsession" file, no session managers, no window terminal emulators found; aborting.

and when I try startxfce4 I get 

command not found. 

I know this thread is a bit old, but anyone have any ideas? 

Thanx

Rayston
Try rebooting. I've noticed that the *startxfce4* command doesn't seem to be "available" until you've rebooted the system. I don't know why, and I feel guilty suggesting a reboot, but it seems to fix things. :roll:

---

### Post by xmastree on 2006-09-14
I just saw this thread.
I have a P233/96 laptop and I tried to put ubuntu on it.Way too slow. I then tried three lightweights, dsl, puppy and feather.
I eventually settled on puppy.

ubuntu took two hours to install, and when it did it still took ages to boot up. It's the memory.

Here's my quick comparison of my experience with those three:
[http://www.openlaptops.org/index.php?topic=145.msg833#msg833](http://www.openlaptops.org/index.php?topic=145.msg833#msg833)

I know the machine in question isn't a laptop, so installing more memory may be easier. But at 64MB, ubuntu will crawl.

---

### Post by isTHEr3mOr3 on 2006-09-15
Have to agree here, Puppy is the way to go for the oldies! (and for everybody else who wants to experience lightning fast PC enjoyment :) )

---

### Post by grizzly on 2006-09-16
Take another vote for puppy here. Its a really nice thing to have.

---

### Post by Monsuco on 2006-09-19
I would go with [Damn Small Linux](www.damnsmalllinux.org). DSL is one of the lightest desktop distros around. It requires a little over 16 mb of RAM (4 MB or so for CLI only), 50 MB of disk space, and an x86 processor (I would reccomend at least a Pentium I or so). It is based on knoppix and you can install apt and the like. It comes with Firefox, Dillo, Ted Word Processor, Fluxbox, Gnumeric, a basic media player, a basic e-mail program, and a few other things (quite a lot for 50 MB). It is one of the fastest disto's I have ever seen. It was even reasonably fast on QEMU on an older PC. Another option is Slackware, but it ain't exactly easy to set up. Xubuntu and Puppy are fairly light too.

---

### Post by danomatika on 2006-12-28
I'm using a Xybernaut MA-IV wearable for a project and it is a PI 233 MMX with 160MB of RAM.  Since the damn thing cannot boot on a usb cd I used the Debian floppy install to setup Sarge on its nice roomy 4GB drive.

I have a very lightweight install running Window Maker and it is extremely awesome.  I definitely recommend Debian if you have the chops to spend an hour (or 10) paging through aptitude choosing only the packages you really need.

Now if only someone could help me port the xfree86 3.3 era touchscreen drivers to Xfree86 4+ / xorg .... I have the sources, I just haven't written an X (or linux) driver before :P

(as a matter of interest, I tried Debian Etch and xorg runs like molasses on the VESA driver versus Sarge + Xfree86 on the same driver, so I'm sticking to Sarge.  The Neomagic driver crashes on this beastie :P)

---

### Post by RAV TUX on 2006-12-29
> **Rockyhead said:**
> Hi!

Having now got the courage and basic skills acquired with Ubuntu, I've given some thought to changing my third machine into a Linux-box. Could you guys help me find the right distro?

It's a Pentium2 266Mhz, 64mb RAM, 4gb HD, currently running Win98. Now it's only collecting dust, but maybe by adding a wifi-card I could turn it into something useful...

Damn Small Linux looks nice, but are there any other small ones out there? I do admit, I'm still a bit n00by when it comes to linux, so I'd like it to be...not that technical :D

I would suggest anything but Damn Small Linux....a hideous disappointment for all the hype it recieves.

Try [Puppy Linux]("http://www.puppylinux.org/user/viewpage.php?page_id=1"), or better yet follow K.Mandla's advice:

> **K.Mandla said:**
> Start with a server install. Then

```
sudo aptitude install x-window-system-core xfce4
```From there you can add whatever you like. You'll find it's much snappier than a full-blown Xubuntu installation.

Have fun!

---

### Post by fplolz on 2008-09-02
ERm...Try this this site...my friend posted a something about light distros
[http://thefplolz.blogspot.com/](http://thefplolz.blogspot.com/)

---

### Post by zmjjmz on 2008-09-02
Reviving an antique thread about an antique computer?
Niiice.
But seriously that post has good advice, if the OP is still alive.

---

### Post by Bungo Pony on 2008-09-02
> **SoundMachine said:**
> DSL is my preference for anything that has below 128MB.

Agreed. If you put 128M or more, you could go with Puppy or TinyMe.

DSL v3.x is my personal favorite. I didn't like some of the changes they put into v4.

---

### Post by oswaldkelso on 2008-09-03
And the winner is .........

[SliTaz]("http://www.slitaz.org/en/about/")

---

### Post by snowpine on 2008-09-04
> **oswaldkelso said:**
> And the winner is .........

[SliTaz]("http://www.slitaz.org/en/about/")

They tell me that SliTaz requires 128mb by default, so with 64mb, you need to use the 'lo-ram' flavor: [http://wiki.slitaz.org/doku.php?id=quickstart:loram](http://wiki.slitaz.org/doku.php?id=quickstart:loram)

---

### Post by K.Mandla on 2008-09-04
Closed for necromancy.

---

