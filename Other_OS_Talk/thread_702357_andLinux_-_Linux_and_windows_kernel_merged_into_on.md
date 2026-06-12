---
title: "andLinux - Linux and windows kernel merged into one seamless desktop"
date: 2008-02-20
forum: Other OS Talk
---

### Post by JurB on 2008-02-20
[U][Link]("http://www.andlinux.org/")

[/U][LEFT]Dunno what to think of it....
[/LEFT]

---

### Post by billgoldberg on 2008-02-20
As I understand it it's like wine but than the other way around.

I doubt alot of people will use it.

---

### Post by forrestcupp on 2008-02-20
Wow.:confused:

---

### Post by notwen on 2008-02-20
That's uh.. different.  Unfortunately, most Linux users will be put off by the inclusion of Windows and vice versa, lol.

---

### Post by quinnten83 on 2008-02-20
If I understand it correctly, it's like a virtualmachine anyway.
So it is not worse than a virtualbox. You also still have to pay for a windows version and just is now really seamlessly integrated.
granted I want my linux to stay on linux and those window users should keep their grimy paws off of my kernel, but still its a VM but then easier.

---

### Post by K.Mandla on 2008-02-20
> **notwen said:**
> That's uh.. different.  Unfortunately, most Linux users will be put off by the inclusion of Windows and vice versa, lol.
+1, or at least that's where I'm at with it. I understand that some people would have a use for Windows and Linux combined, but from my perspective, I don't see a point in sacrificing a perfectly good operating system to Windows. 

But hey, to each his own. It's all about freedom. :D

---

### Post by SupaSonic on 2008-02-20
I'm reluctant to try it - it's too much windows for me. I wish I had an icon in my gnome dektop to launch windows apps or games. As it stands, i have pretty much the same with Xming, cygwin and ssh with X forwarding to a Linux machine. 

Still an interesting idea I guess.

---

### Post by spamzilla on 2008-02-20
I'd never use it, but it looks interesting to say the least.

---

### Post by forrestcupp on 2008-02-20
Some of you may misunderstand.  It's not for Linux users.  It's made for Windows users.  It's kind of like putting a Linux compatibility layer in Windows so they can run our software.

---

### Post by EdThaSlayer on 2008-02-20
Looks pretty cool, but too windoish for me to try out though. Maybe this can get my Windows partition look a bit friendlier.

---

### Post by notwen on 2008-02-20
> **forrestcupp said:**
> Some of you may misunderstand.  It's not for Linux users.  It's made for Windows users.  It's kind of like putting a Linux compatibility layer in Windows so they can run our software.

Windows users actually wanting to run Linux software?  Isn't that normally the other way around? =p

---

### Post by Dark_X on 2008-02-20
> **notwen said:**
> Windows users actually wanting to run Linux software?  Isn't that normally the other way around? =p

Actually I really wish I could run linux programs in windows.  To bad this doesn't work with 64 bit.

---

### Post by oskarloko on 2008-02-26
Well, in my work I'm using Xp; but I wanted to use and test Linux. The servers are Debian or Solaris, so I want a *NIX enviorment to test server installations.

I've tried  VirtualBox and VMPlayer, both are great ( I like the first more, but they've their strengths and weakness )
But AndLinux have conviced me. 

It's a coLinux Ubuntu; a VM of Linux totally integrated into a Windows system. 
Easy to install, runs as a service ( automatically or manual ), with rootless apps. Synaptic, console, Firefox, Thunar without problem.
The speed and performance are impressive.

See more:
[Wikipedia ]("http://es.wikipedia.org/wiki/AndLinux")( sorry, only spanish and german for now )
[Life Hacker]("http://lifehacker.com/358208/seamlessly-run-linux-apps-on-your-windows-desktop")
[SlashDot]("http://ask.slashdot.org/article.pl?sid=06/02/02/2125248")

As more adaptable  is Linux, more will be used and expanded.

Pd. later I also tried Wubi to make a non-destructive linux install, I like it a lot, too.

---

### Post by angry_johnnie on 2008-02-26
It's pretty good, actually.  I just installed it yesterday, and i must say I'm impressed with it.  Whether we like it or not, some people have to use Windows for whatever reasons, and this gives us a very good, extremely functional, alternative.  I had tried kde4 for Windows and Cygwin before, but AndLinux is much better.

---

### Post by K.Mandla on 2008-02-26
Moved to Other OS Talk.

---

### Post by Calash on 2008-02-26
It looks very intersting, as noted above it seems more like Wne than a Virtual Machine.

Downloading to my Work computer now :)

---

### Post by imT on 2008-02-26
not tempting, probably will catch on newbies.

---

### Post by finferflu on 2008-02-26
I don't think it's for newbies. I think it's more oriented towards developers and people who actually need Windows for working. I think so far this is the best idea I have seen. I would prefer it the other way round though, allowing people to use Linux Window Managers (perhaps it's even possible) for example. In general I prefer the Unix environment much more than the Windows one. 
I'm hopefully not gonna need it, but I'm impressed anyway :)

---

### Post by pelle.k on 2008-02-26
> not tempting, probably will catch on newbies.
I don't think so. Wubi, yes, but coLinux/andLinux, no.
This is really cool though. I read up on coLinux a while ago, and the only catch back then was that that it was *complicated* to set up, so this is certainly a welcome surprise. At last i can run amarok and bash in windows. :)

---

### Post by Calash on 2008-02-27
It took a bit to get it to start up...it decided to run a disk check on my Windows partition when it first boot.

From what I can tell, it is a service in the background that loads a Linux kernel that is then accessed by the applications.  It installed a network device that is used by the apps for X.

Once booted everything runs very quickly, and there is a good amount of integration with the Windows OS via a SAMBA share.  I still have not gotten it to connect to the network yet.

I do not see much use for it though, be a developer or web designer could get some good function from it.


Edit:  Just got it on our work network.  Had to put our DNS server into the config and the correct proxy address.

---

### Post by dougsnell on 2008-02-27
I kind of like it.  I'm kind of stuck using Vista at my office, and this gives me familiarity with many of the Linux programs I prefer to use.

I know a lot of people who would be willing to try this long before they load a live CD (slow as crap to get started) or install a second OS (requires rebooting every time ... which means they wind up using Windows all the time).

Ideally, yeah, they'd go to Linux by default and use Wine or Windows only when needed.  In reality, people are much more apt to try something if they know they can simply uninstall it if they don't like it or use it.

---

### Post by DouglasAWh on 2008-02-27
> **dougsnell said:**
> I kind of like it.  I'm kind of stuck using Vista at my office, and this gives me familiarity with many of the Linux programs I prefer to use.

I know a lot of people who would be willing to try this long before they load a live CD (slow as crap to get started) or install a second OS (requires rebooting every time ... which means they wind up using Windows all the time).

Ideally, yeah, they'd go to Linux by default and use Wine or Windows only when needed.  In reality, people are much more apt to try something if they know they can simply uninstall it if they don't like it or use it.

+1

Now, I have a question.  How do web servers see this?  If I run Konquerer on Vista does it show up as Konquerer on Vista or Konquerer on Kubuntu?

It's a bit slow for my tastes, but then again, I didn't give it all that much RAM during the install...and I am running Vista, where nothing runs as fast as it should.  

I don't think I have any use for this on a daily basis, except maybe using evolution instead of Outlook at work.  Despite there being a Windows version of Evolution, I can't get it to work.

---

### Post by Calash on 2008-02-28
Just tested, it shows up as Linux.  Looking over it I think it is almost like a Virtual machine with a seamless setup more than a compatibility layer.

If Wine worked this well I think we would have a lot more people using it :)

---

### Post by argraff on 2008-02-28
Might be a good intermediate step when moving people from Windows to Linux - get used to the new, still have the old for security (personal security, not computer), handhold for a little while...

---

### Post by DouglasAWh on 2008-02-28
I suppose this could be a new thread, but has anyone seen activity similar to: 

[IMG]http://farm4.static.flickr.com/3015/2298833476_960e0450fd_o.jpg[/IMG]

I'm not really noticing any performance degradation, but I'm concerned about the life of the processor if it's getting hit like that all the time.  Is that just because coLinux has as much power over the kernel as Windoze and Vista doesn't know what to do about that?  I'm just curious.  Thanks! :)

---

### Post by jrusso2 on 2008-02-28
> **SupaSonic said:**
> I'm reluctant to try it - it's too much windows for me. I wish I had an icon in my gnome dektop to launch windows apps or games. As it stands, i have pretty much the same with Xming, cygwin and ssh with X forwarding to a Linux machine. 

Still an interesting idea I guess.

Yeah I would like to see this reversed.  I would like something like this to run some windows apps on Linux without needing a whole virtual machine.

---

