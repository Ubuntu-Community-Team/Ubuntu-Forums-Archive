---
title: "Foresight Linux 1.3"
date: 2007-06-06
forum: Other OS Talk
---

### Post by tomcat1965 on 2007-06-06
Because your PC should be cool,say Foresight and they're not wrong. I want a cool looking desktop that works right out of the box,is easy to manage and I don't want to spend time trawling through pages on google getting encrypted DVD's to play,msttcorefonts,mp3 support etc. I want nicely rendered fonts and the latest gnome (2.18.2)and OOo 2.2. Well Foresight has all that plus Compiz,Firefox,Java 1.6,Seahorse,the latest HAL, Beagle, Avahi and Xorg 7.2!
The conary package manager is simple to use,powerful and actually makes it easy to roll back to a previous version of a package. Foresight system manager,a browser based and very professional gui is a 'fire and forget' manager that gives vital system info as well as managing package searches and updates. You decide whether to be notified of updates,whether they should be automatically applied and when. Cool,very,very cool.
This distro is fast too,in fact even on an old box running a 900 Mhz AMD Turon from the middle ages it feels fast,the speed on my new AMD X2 4800 box is just unbelievable!!
  
Check it out here:[http://www.foresightlinux.com]("http://www.foresightlinux.com")  :popcorn:

---

### Post by ThinkBuntu on 2007-06-07
I'm surprised I never took a hard look at this one...I've always wanted to try the Coronary package manager, and it comes with all the non-free goodies that I've come to expect. Looks very nice for a GNOME distro too. Maybe it can deliver the ease of use and attractiveness of Mint without the Ubuntu "grind effect", by which I mean how when you install your full suite of apps and features, the system becomes significantly slower in virtually every aspect beyond startup.

---

### Post by pelle.k on 2007-06-07
> the Ubuntu "grind effect", by which I mean how when you install your full suite of apps and features, the system becomes significantly slower in virtually every aspect beyond startup.
This is a bit OT, but i have to step in and question this.
The fact is that i often wonder what the h*ll people are talking about when they mention this. To be completely honest, i'm rather sure this phenomenon is psychological in nature since most (not all i would imagine) linux distros don't have the problem that microsoft windows has, and that is proper cleanup of leftovers from a previous installation, no registry to mess up, and for applications that is not "daemon" dependent - no auto start by default and last but not least a journaling filesystem that doesn't add up to a chocked hard drive at some time.
In fact, in theory this shouldn't be an issue with many linux distros. I have also not experienced this myself, wich adds to my confusion. Of course I could be wrong.

What i am prepared to belive is the problem is that people like to add more and more panel applets (yes, some of them is acctually quite demanding), maybe run a filesystem with tweaks that in the long run will actually give worse you _worse_ performance, Install fonts that by default get chached in xorg, do modifications with experimental software (beryl is not really something that should be considered stable _or_ mature. probably contains memory leaks and and threads that hang other parts of the system).
Now, these are all things that be definition are expected to slow down your computer.

What do you think?

Sorry for the OT. I've also tried foresight out, and it's a really nice distro. I can easily imagine it would be a perfect fit for an ubuntu user, since it comes preinstalled with some sweet applications, but not too many.
You'll have to get your hands a little bit dirty though since it's not as mature as ubuntu is. Less apps to choose from, and fewer GUI administration tools,  but to be completely honest i'm not very much for GUI tools anyway. At least not in those circumstances where a CLI app does a better job than a bad gui frontend. You know what i mean...
Nice irc channel too. You should check it out.

---

### Post by ThinkBuntu on 2007-06-07
I've noticed this effect in Ubuntu alone, other wise I wouldn't point it out as such. In Arch, PCLOS, Zenwalk, Debian, openSuSE, and a whole variety of other distros, I never experienced the same effect of getting "bogged down": performance was pretty much the same as when I first had my desktop running. I never use Beryl, and have only played around with Compiz a couple times.

I'm sure you're not for frontend tools, since Arch is pretty much devoid of them, except for what KDE and GNOME give you :^)

I'm going to get my hands dirty, but that's no big deal, because I've gotten them filthy trying to get Zenwalk just right (which is quite a challenge, but pays off).

---

### Post by pelle.k on 2007-06-07
Yeah, It's been a while since i ran ubuntu...
"Pacman -Rsn" is really nice when you made all these trials of one bazillion apps ;)
When i ran ubuntu i was an "aptitude" kind of guy, since it resolves dependencies when you uninstall applications, and if i'm not mistaken that feature should be in feistys apt-get from this release and beyond.
I can also imagine that quite a few daemons get left over and running as dependencies of "old" installations.
Can anyone confirm that apt-get resolves dependencies at uninstalls by know, or if you have to utilize an "option"?

Better yet, how does foresight handle installations/uninstallations?

---

### Post by hanzomon4 on 2007-06-09
apt-get autoremove or auto-remove(I forget which) it takes care of the stuff you no longer need. 


I've been wanting to try Foresight for sometime now. I've downloaded every release since 1.1 but it screws my usb hard drive every time. I'll give this one a go but I'm not optimistic

---

### Post by RAV TUX on 2007-06-09
> **pelle.k said:**
> Yeah, It's been a while since i ran ubuntu...
"Pacman -Rsn" is really nice when you made all these trials of one bazillion apps ;)
When i ran ubuntu i was an "aptitude" kind of guy, since it resolves dependencies when you uninstall applications, and if i'm not mistaken that feature should be in feistys apt-get from this release and beyond.
I can also imagine that quite a few daemons get left over and running as dependencies of "old" installations.
Can anyone confirm that apt-get resolves dependencies at uninstalls by know, or if you have to utilize an "option"?

Better yet, how does foresight handle installations/uninstallations?

to install Opera:
```
sudo conary update opera
```

---

### Post by H.E. Pennypacker on 2007-06-09
Foresight is very attractive, but I fear it is Ubuntu with Conary.  I can't afford to switch to another distro just it has a different package management.  All the other stuff I can download myself.  I just don't see the purpose in switching.

---

### Post by RAV TUX on 2007-06-09
> **H.E. Pennypacker said:**
> Foresight is very attractive, but I fear it is Ubuntu with Conary.  I can't afford to switch to another distro just it has a different package management.  All the other stuff I can download myself.  I just don't see the purpose in switching.

It's more then just a package manager, much more I will compile a screenshot tour/tutorial soon to illustrate how much more it really is.

(current Foresight is built on yet to be released rPath 2, is my understanding. )

---

### Post by H.E. Pennypacker on 2007-06-10
> **RAV TUX said:**
> It's more then just a package manager, much more I will compile a screenshot tour/tutorial soon to illustrate how much more it really is.

(current Foresight is built on yet to be released rPath 2, is my understanding. )

It is difficult to make distinctions between operating systems when you get right down to it.  I'll be using the Internet the same way, still be using OpenOffice, and I'll still be doing the same things.  I don't know if the migration is worth all the hassle.

---

### Post by RAV TUX on 2007-06-11
> **H.E. Pennypacker said:**
> It is difficult to make distinctions between operating systems when you get right down to it.  I'll be using the Internet the same way, still be using OpenOffice, and I'll still be doing the same things.  I don't know if the migration is worth all the hassle.Honestly if your happy with your current OS stick with it.

For those who come to the "Other OS" forum, to share and seek out Other OS's...

for those who seek out more, you'll find Conary and Raa based distros the way of the future.

I have published a screenshot tour of Foresights Package Manager:

[http://cafelinux.org/forum/index.php/topic,531.new.html#new](http://cafelinux.org/forum/index.php/topic,531.new.html#new)

---

### Post by H.E. Pennypacker on 2007-06-11
I'd like to view those screenshots, but you have to be a member.  Could you upload them to, say, imageshack.us?  It's too much trouble to sign up for message board you're only going to use once.

---

### Post by RAV TUX on 2007-06-11
> **H.E. Pennypacker said:**
> I'd like to view those screenshots, but you have to be a member.  Could you upload them to, say, imageshack.us?  It's too much trouble to sign up for message board you're only going to use once.
I'll work on it.

---

### Post by RAV TUX on 2007-06-11
> **H.E. Pennypacker said:**
> I'd like to view those screenshots, but you have to be a member.  Could you upload them to, say, imageshack.us?  It's too much trouble to sign up for message board you're only going to use once.

> **RAV TUX said:**
> I'll work on it.

here you go:


[http://www.flickr.com/photos/93809254@N00/sets/72157600336901509/show/](http://www.flickr.com/photos/93809254@N00/sets/72157600336901509/show/)

---

### Post by H.E. Pennypacker on 2007-06-11
That's quite cool.  Replacing Synaptic with a browser based package manager is interesting.  I certainly prefer doing things that way, because browsers are more universal, since people generally know how to use browsers, as opposed to an entirely new application (Synaptic).  

I wonder if Ubuntu is interested in switching over to something like this one day.

---

### Post by RAV TUX on 2007-06-11
> **H.E. Pennypacker said:**
> That's quite cool.  Replacing Synaptic with a browser based package manager is interesting.  I certainly prefer doing things that way, because browsers are more universal, since people generally know how to use browsers, as opposed to an entirely new application (Synaptic).  

I wonder if Ubuntu is interested in switching over to something like this one day.

I have heard that Canonical/Ubuntu did look into rPath I am not sure what became of it, or if it was just a rumor? 

I do believe that it is the way of the future for Linux, and it works flawlessly. I especially like the ability to set up updates via the web browser.

This is one of the many reasons why I have based Oz Enterprise, and Linux Nirvana on rPath.

---

### Post by garba on 2007-06-11
> **RAV TUX said:**
> here you go:


[http://www.flickr.com/photos/93809254@N00/sets/72157600336901509/show/](http://www.flickr.com/photos/93809254@N00/sets/72157600336901509/show/)

i love web based apps :D

---

### Post by RAV TUX on 2007-06-11
> **garba said:**
> i love web based apps :D
Yes they are pretty awesome, especially this one.

I added it as an external link to the Foresight Linux Wikipedia page:

[http://en.wikipedia.org/wiki/Foresight_Linux](http://en.wikipedia.org/wiki/Foresight_Linux)

---

### Post by 67GTA on 2007-06-11
I tried Foresight 1.1, but The web based Cornary/rPath thing was kind of confusing. When I would use the search tool, it would return four or five entries with no way to differentiate between them from the given descriptions. I never knew which to install. Have they changed this?

---

### Post by RAV TUX on 2007-06-11
> **67GTA said:**
> I tried Foresight 1.1, but The web based Cornary/rPath thing was kind of confusing. When I would use the search tool, it would return four or five entries with no way to differentiate between them from the given descriptions. I never knew which to install. Have they changed this?

take a look at the slideshow, when I typed in Opera it gave me 4 packages I choose the one that had "Foresight" in the file address, when doing this I found only one option.

---

### Post by 67GTA on 2007-06-11
Maybe I did not look close enough. Are the other options source packages or something? I just never understood why there were more than one.

---

### Post by RAV TUX on 2007-06-12
> **67GTA said:**
> Maybe I did not look close enough. Are the other options source packages or something? I just never understood why there were more than one.

if your using Foresight choose a Foresight package, if your using rPath use an rPath package, etc., etc. it's that easy.

---

### Post by afonic on 2007-09-23
Foresight 1.4 is out featuring Gnome 2.20.

And so is my review:
[http://www.dvd-guides.com/content/view/215/104/](http://www.dvd-guides.com/content/view/215/104/)

:D

---

### Post by pelle.k on 2007-09-23
I ust tried it out as well, and i agree with you in that the web based control panel is kind of clunky.
Other than that ver. 1.4 was really nice. I would like to do samba shares (instead of NFS) in nautilus right click menu by default though.
It took a whole lot of time to install, and installing nvidia binary driver was a bit unorthodox, even if they explain why, in the FAQ.

I say bring on a good GUI frontend to conary, and foresight will be a really good distro IMHO. Maybe when rpath 2 is released this will be possible.
I am a bit worried about using "rolling release" distros in general though. (oh the irony, arch linux user as i am primarily)

---

### Post by FuturePilot on 2007-09-30
I'm downloading 1.4 now. From what I hear it's a really nice distro. How's the stability?

---

### Post by RAV TUX on 2007-09-30
> **FuturePilot said:**
> I'm downloading 1.4 now. From what I hear it's a really nice distro. How's the stability?very stable...enterprise version stable

---

### Post by FuturePilot on 2007-09-30
Hmmm. I'm back on Ubuntu again:lolflag:
Foresight is really nice, but I had 3 maybe 4 major problems with it.
1) My volume buttons and multimedia buttons didn't work
2) My touchpad didn't work correctly
3) I found out there was no legacy Nvidia driver in the repos so I had to install it myself. Then it kept freezing because of that and I needed to disable CPU scaling to stop it from freezing (I have to do this with Ubuntu too:???:) but I couldn't find the script. In Ubuntu it's called powernowd and it's in /etc/init.d/.
4) I kept getting this FATAL error during boot up, but everything seemed fine.

Conary is really cool though.

---

### Post by pelle.k on 2007-09-30
> My volume buttons and multimedia buttons didn't work
Unless ubuntu has a patch specific for your multimedia buttons, you normally just bind them in gnome.
> but I couldn't find the script. In Ubuntu it's called powernowd and it's in /etc/init.d/
Oh, there are more ways than one to do this. pm-utils, powersave, cpufreq-utils. btw, in foresight you utilize the command "service" to list and run daemons.

---

### Post by Wiebelhaus on 2007-09-30
I've noticed the same damn thing thinkbuntu is talking about , on my lower end linux box specifically  , that's where the stigma that "Ubuntu needs a gig" comes from.

So command line installation adding my own processes tailor made for my specific application is what fixed it for me.

---

### Post by FuturePilot on 2007-09-30
> **pelle.k said:**
> Unless ubuntu has a patch specific for your multimedia buttons, you normally just bind them in gnome.

Oh, there are more ways than one to do this. pm-utils, powersave, cpufreq-utils. btw, in foresight you utilize the command "service" to list and run daemons.

Hey, thanks. I'll look into this. I just realized I never tried to bind those keys with Gnome.

---

### Post by FuturePilot on 2007-09-30
Well, it's a little better. I got the volume buttons to work, but I can't get the multimedia keys to work. Nothing happens when I press them in the Keyboard Shortcuts app. I still can't get my touchpad to scroll. I'm not sure what I should be looking for for the CPU scaling. Anyone know what it's called in Foresight?

---

### Post by pelle.k on 2007-09-30
> Well, it's a little better. I got the volume buttons to work, but I can't get the multimedia keys to work. Nothing happens when I press them in the Keyboard Shortcuts app.
If you run xev from a terminal, and get a reaction when you hit a key, then at least the buttons are recognized by the kernel.
If so, you can map "unmapped" keycodes to X symbols with xmodmap, and from there you can map them in gnome.
This is what i do for my few keys. I create a file called .Xmodmap in my home. In that i put;
```
keycode 162 = F13
keycode 174 = F14
keycode 160 = F15
keycode 176 = F16
keycode 144 = F17
keycode 153 = F18
```

Now, in many distros, this .Xmodmap file is run by gdm/kdm, but if it isn't, you can run it manually with "xmodmap ~/.Xmodmap" from gnome sessions...

As you see i've mapped those buttons to non existent F* buttons.
> still can't get my touchpad to scroll.
Maybe you should install synaptics and gsynaptics?
> 
not sure what I should be looking for for the CPU scaling. Anyone know what it's called in Foresight?
I would *really* advice you too visit #foresight on freenode (irc). They are very helpful and will probably answer you instantly.
I haven't got it installed atm.

---

### Post by FuturePilot on 2007-09-30
Thanks for all your help. I'm might wander over to #foresight :)

---

### Post by RAV TUX on 2007-09-30
> **FuturePilot said:**
> Thanks for all your help. I'm might wander over to #foresight :)

be warned Foresight is nice for the corporate environment but a bit boring for the home user.

---

### Post by FuturePilot on 2007-09-30
> **RAV TUX said:**
> be warned Foresight is nice for the corporate environment but a bit boring for the home user.

Oh?:-s
Hmmm. Maybe I'll give Gentoo a try again. I'm looking for a rolling release distro.
Or maybe I'll just stay with Ubuntu.

---

### Post by RAV TUX on 2007-10-01
> **FuturePilot said:**
> Oh?:-s
Hmmm. Maybe I'll give Gentoo a try again. I'm looking for a rolling release distro.
Or maybe I'll just stay with Ubuntu.Try Debian, awesome little known distro. ;)

---

### Post by FuturePilot on 2007-10-01
> **RAV TUX said:**
> Try Debian, awesome little known distro. ;)

Maybe I'll give Debian Testing a shot. I tried Debian Stable last time.
I think I'm suffering from "Acute Linux Distro Multiplicity Addiction Syndrome" again :eek:

---

### Post by afonic on 2007-10-01
> **FuturePilot said:**
> Oh?:-s
Hmmm. Maybe I'll give Gentoo a try again. I'm looking for a rolling release distro.
Or maybe I'll just stay with Ubuntu.

Give Arch Linux a try as well.

---

### Post by RAV TUX on 2007-10-01
> **FuturePilot said:**
> Maybe I'll give Debian Testing a shot. I tried Debian Stable last time.
I think I'm suffering from "Acute Linux Distro Multiplicity Addiction Syndrome" again :eek:

Meetings are always held at #cafelinux (freenode)

---

