---
title: "Enlightenment"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by TNAFan on 2008-11-11
I'm interested in checking out the enlightenment DE, but first want to know exactly what packages I would need to give me a full robust desktop.  Could anyone "enlighten" me, so to speak?

---

### Post by loell on 2008-11-11
state first your ubuntu version, so someone could give you the right repository :)

---

### Post by TNAFan on 2008-11-11
lol  Yeh I suppose that would be a necessary thing huh?  Ubuntu 8.10

---

### Post by jimmy the saint on 2008-11-11
First try
```
apt-get install "descriptive thread title"
```

As far as enlightenment goes, E16 is what is in the repos, but it is not very exciting.  E17 is most likely what you are after, and is not yet in the repos, at least for Hardy.  Your best bet is to look for a tutorial describing how to install E17 desktop on either Hardy or Intrepid depending on which you have.  E17 is not a robust as Gnome or KDE in that it focuses soley on providing a good desktop experience, not a complete computing environment.

---

### Post by TNAFan on 2008-11-11
Hmmmmm how about?  Oh I know!  sudo apt-get remove smart_***_reply | apt-get install genuine_assistance  I think that might be a good idea.  Now, can you assist me with such a thing?  If not, probably just simply ignoring the thread might be a better idea.

---

### Post by loell on 2008-11-11
stop both of you :rolleyes:, LoL..

try adding this in your sources.list

[B]
deb [http://greenie.sk/ubuntu](http://greenie.sk/ubuntu) intrepid e17
deb [http://greenie.sk/ubuntu](http://greenie.sk/ubuntu) intrepid opengeu[/B]

then

```

sudo apt-get update
sudo apt-get install opengeu-desktop
```

---

### Post by SunnyRabbiera on 2008-11-11
Well I think someone has a extra repository for enlightenment, but question:
why do you want to install it?
You just want something more lightweight for your system or you just want something different?

Anyhow try this guide out first, its a bit complex but should work for you:

[http://ubuntuforums.org/showthread.php?t=546746](http://ubuntuforums.org/showthread.php?t=546746)

Note: I am not trying to be smart in my reply I was just wondering why you are interested in E17

> **loell said:**
> stop both of you :rolleyes:, LoL..

try adding this in your sources.list

[B]
deb [http://greenie.sk/ubuntu](http://greenie.sk/ubuntu) intrepid e17
deb [http://greenie.sk/ubuntu](http://greenie.sk/ubuntu) intrepid opengeu[/B]

then

```

sudo apt-get update
sudo apt-get install opengeu-desktop
```

ah, so thats still around then, I was wondering about opengeu

---

### Post by loell on 2008-11-11
> **SunnyRabbiera said:**
> 
ah, so thats still around then, I was wondering about opengeu

it seems so, the link is still alive and there build date was fairly recent "09-Sep-2008 17:43"

---

### Post by SunnyRabbiera on 2008-11-11
> **loell said:**
> it seems so, the link is still alive and there build date was fairly recent "09-Sep-2008 17:43"

Yeh I didnt mention it at first as i was unsure of its status.

---

### Post by TNAFan on 2008-11-11
No, I realize that wasn't smart.  Nitpicking my post was a little smart.  As for why, sometimes I just get curious as to check out the other DE's out there, I heard about this one, but I couldn't figure out what I needed.
> **SunnyRabbiera said:**
> Well I think someone has a extra repository for enlightenment, but question:
why do you want to install it?
You just want something more lightweight for your system or you just want something different?

Anyhow try this guide out first, its a bit complex but should work for you:

[http://ubuntuforums.org/showthread.php?t=546746](http://ubuntuforums.org/showthread.php?t=546746)

Note: I am not trying to be smart in my reply I was just wondering why you are interested in E17



ah, so thats still around then, I was wondering about opengeu

Update, I just tried doing this (through synaptic actually, easier for me) and it said it couldn't be authenticated. DOn't know how I go about finding the GPG key.  But adding the repos went well.

---

### Post by SunnyRabbiera on 2008-11-11
Well I can understand curiosity.
As for enlightenment I think its worth trying out, even though for me it never did the trick.
Also try KDE, XFCE, Blackbox, fluxbox and the others as linux has so many choices :D

---

### Post by TNAFan on 2008-11-11
> **SunnyRabbiera said:**
> Well I can understand curiosity.
As for enlightenment I think its worth trying out, even though for me it never did the trick.
Also try KDE, XFCE, Blackbox, fluxbox and the others as linux has so many choices :D

KDE I like, the problem with KDE4 though is whenever I try and use the keyboard to adjust the volume by using Fn+arrowup/down it pops up the level indicator, but doesn't change anything.  Not sure how to get around that one.  

XFCE is very cool, though I am working on the differences between it and Gnome a little more.  Jury is stil open.

Blackbox and fluxbox I was really interested in trying out, because they reminded me a bit of NeXT, unfortunately they weren't close enough, so they both had to go.  Know of any options that are more exact as far as NeXT goes?

And still looking for how to go about putting in GPG keys for the first enlightenment option given to me by loell.

---

### Post by SunnyRabbiera on 2008-11-11
> **TNAFan said:**
> KDE I like, the problem with KDE4 though is whenever I try and use the keyboard to adjust the volume by using Fn+arrowup/down it pops up the level indicator, but doesn't change anything.  Not sure how to get around that one.  

XFCE is very cool, though I am working on the differences between it and Gnome a little more.  Jury is stil open.

Blackbox and fluxbox I was really interested in trying out, because they reminded me a bit of NeXT, unfortunately they weren't close enough, so they both had to go.  Know of any options that are more exact as far as NeXT goes?

And still looking for how to go about putting in GPG keys for the first enlightenment option given to me by loell.

Actually fluxbox and blackbox are not really that close to NeXT for me, actually windowmaker is more close to NeXT.
But windowmaker can be a pain in the **** to set up.

---

### Post by TNAFan on 2008-11-11
> **SunnyRabbiera said:**
> Actually fluxbox and blackbox are not really that close to NeXT for me, actually windowmaker is more close to NeXT.
But windowmaker can be a pain in the **** to set up.

Yeh, tried out that one too, but I don't have the patience for that kind of configuration.

---

### Post by Tux Aubrey on 2008-11-12
I'm a big Enlightenment fan so I thought I'd jump in with few observations so you know what you are in for:

1. The version in the Ubuntu and Debian repos is a very early pre- pre- alpha build dated December 2004 and pretty much e16.  Don't touch it.

2. The next most up-date package was done very recently (and is on the Debian experimental repos)and is pretty close to the current version available from code (It is labelled e16.999.050, believe it or not).  It is the one used in the latest versions of OpenGEU and Maryan Linux, both of which are based on Ubuntu.  I did install the one in the debian experimental repos on Ubuntu 8.04but had to grapple with a few incompatible packages.  I don't recommend going that way on a "production" machine.

3. The Enlightenment devs are not at all keen on people packaging e17 and seem to have a particular aversion to debian-based distros.  Do not expect any help or encouragement from the Enlightenment forums or IRC.  They are very newbie unfriendly.

4.  If you are game, it is entirely possible to get the most up-to-date version by using a script called "easy_e17.sh" - this is the basis for Rui Pais post [**here**]("http://ubuntuforums.org/showthread.php?t=916690") (also referenced above).  Rui's approach is to pare e17 back to the basic window manager and a few essential and stable apps.  A lot of native e17 applications and utilities are still quite raw and unstable.

5. The idea behind OzOS is to take the "easy_17.sh" script, take out the stuff that is unstable or broken and add a few additional touches that help the user maintain and update the e17 code base.  You can add these elements to any 'buntu (or other debian-based distro) via the instructions in Rui's post (or by following my take on it [**here**]("http://cafelinux.org/OzOs/content/how-install-ozos-desktop-existing-os")).  That way, you will still have your existing set-up and an OzOS Enlightenment session available at login.

6. The whole OzOS thing is also packaged as a stand-alone fairly minimal and lightweight distro based on Xubuntu (8.04)(minus most of the xfce and gnome stuff) - you can get a 64 or 32 bit iso [here]("http://cafelinux.org/Downloads/oz-os/iso/").  The 0.9 release came out this week, so its fresh.

7. If you have any general e17 questions, feel free to ask them at [CafeLinux]("http://cafelinux.org/forum/index.php").  We have enough users there to solve most things.


8. As you can tell from other posts here, e17 is certainly not for everyone.  It is geneuinely a different experience.  I find it elegant and very useable without "getting in the way".  That said, the past month has been one of the worst I've known for broken code being uploaded on the e17 svn (their server system). At least with OzOS you can recover quickly and easy and with Maryan or OpenGeu you don't deal with updates at all as the rebuilds are so infrequent.

---

### Post by Skripka on 2008-11-12
To the OP:

Give OpenGEU a try--it is currently only set-up for Hardy though.  Ergo I don't know if the Greenie Repos will let you.


E17 is still classified as "beta" and can behave very much as such.  I'm still a fan of it (I used it until Ibex came along), but E17 and Hardy don't play well with my hardware.

---

### Post by TNAFan on 2008-11-12
Wel, I did go ahead and install the opengeu desktop (without it have being authenticated).  Which I might add, I am impressed with in and of itself.  The problems I now have after doing so, is usplash doesn't show up any more at boot or shutdown.  Also, in GNOME, Firefox doesn't show up.  And in Enlightenment, instead of Firefox showing up in the internet category, it shows up in the "other" category.  Any help here?


> **loell said:**
> stop both of you :rolleyes:, LoL..

try adding this in your sources.list

[B]
deb [http://greenie.sk/ubuntu](http://greenie.sk/ubuntu) intrepid e17
deb [http://greenie.sk/ubuntu](http://greenie.sk/ubuntu) intrepid opengeu[/B]

then

```

sudo apt-get update
sudo apt-get install opengeu-desktop
```

---

### Post by Skripka on 2008-11-12
> **TNAFan said:**
> Wel, I did go ahead and install the opengeu desktop (without it have being authenticated).  Which I might add, I am impressed with in and of itself.  The problems I now have after doing so, is usplash doesn't show up any more at boot or shutdown.  Also, in GNOME, Firefox doesn't show up.  And in Enlightenment, instead of Firefox showing up in the internet category, it shows up in the "other" category.  Any help here?

The menu structure in OpenGEU was one of those things that in some themes worked fine, and in others it did not.  As far as Usplash--I can't remember which tool it is from OpenGEU, but there is one to pick and choose your usplash, I just can't remember it off the top of my head....

---

### Post by TNAFan on 2008-11-12
Oh, something else I have noticed.  How do I control volume in Enlightenment?  I'm not seeing anything on the GUI, and my Fn+arrowup/arrowdown doesn't seem to do anything.

---

### Post by Skripka on 2008-11-12
> **TNAFan said:**
> Oh, something else I have noticed.  How do I control volume in Enlightenment?  I'm not seeing anything on the GUI, and my Fn+arrowup/arrowdown doesn't seem to do anything.

If you go to the Control Panel>Modules> there should be a software mixer gadget (click "Load Module")....then go to one of your shelves and right click, on it> "shelf contents">add the mixer gadget.

---

### Post by TNAFan on 2008-11-12
Got that up, thank you! :)  Now do you know how to control it with my Fn key?

> **Skripka said:**
> If you go to the Control Panel>Modules> there should be a software mixer gadget (click "Load Module")....then go to one of your shelves and right click, on it> "shelf contents">add the mixer gadget.

---

### Post by Skripka on 2008-11-12
> **TNAFan said:**
> Got that up, thank you! :)  Now do you know how to control it with my Fn key?

That I do not know--I never was able to get my volume controls on my G15 keyboard working under OpenGEU/E17--they work under Kubuntu and Amarok naturally...but something about how Enlightenment routs keyboard inputs wouldn't let Amarok (under OpenGEU) accept my G15 audio control inputs :confused:

I used OpenGEU for 6 months regularly and loved it...until I went wiped and installed Hardy 64-bit on my /root partition.....and I couldn't get it to work right (constant crashing, DE hanging during rendering), after a few evenings of frustration-I'm back in mainstream Kubuntu.  It is a beautiful environment, and if it had more support/development I'd be back over there pretty quick.

---

### Post by mikjp on 2008-11-12
A couple of days ago I installed E17 for the first time, and it really shines! See my post in [http://lightlinux.blogspot.com/2008/11/enlightened-experience-e17.html](http://lightlinux.blogspot.com/2008/11/enlightened-experience-e17.html)

---

