---
title: "[SOLVED] I want a simpler OS"
date: 2008-04-05
forum: Other OS Talk
---

### Post by gobbles414 on 2008-04-05
Hi all,

Are there any **very simple** GUI operating systems that will run on modern x86 hardware without ROM images, etc.? I'd like for the operating system to have as few control panels as possible -- similar to the early Mac OSes. Any ideas?

---

### Post by LaRoza on 2008-04-05
What do you mean by "simple"?

Try a base install of Ubuntu, and install a GUI.

Try: KolibriOS (based on MenuetOS) also. They are not Linux, but they are light and GUI'd.

---

### Post by NightwishFan on 2008-04-05
Try out Fluxbuntu or perhaps minimal install with JWM.

---

### Post by amingv on 2008-04-05
Few control panels? You mean the least possible configuration needed (out-of-the-boxesness(R))?
I haven't tried any of the early Macs (or any Mac for that matter).

---

### Post by gobbles414 on 2008-04-05
Hi all,

Thanks for those links. Still a bit too complicated...

I've attached a screenshot of the original Mac OS's desktop for your reference. That's my definition of a simple GUI. Early versions of the Mac OS had a very small number of control panels -- about 10 as I recall. Similarly, each control panel had very few options in it. Many early GUI programmers believed that a user shouldn't even notice his/her operating system. I share that belief.

Any other ideas?

---

### Post by bren on 2008-04-05
have a look at [http://www.thinkgos.com/](http://www.thinkgos.com/)

---

### Post by SunnyRabbiera on 2008-04-05
why, what is making your linux experience so hard?
what do you need a IS targeted at pre schoolers or something?

---

### Post by tamoneya on 2008-04-05
Unless you actually get an old mac with an old OS you are going to have trouble finding something THAT simple.  There are just to many options on todays computers(video cards, CPUs, DVD, BluRay, etc) for OSes to not have lots of control panels.  That old Mac OS ran on a much more limited set of hardware.

Now if you just want something that comes very well preconfigured that is a different matter.  I would second the recommendation of gOS as well as recommend Damn Small Linux.  Those both work very well out of the box with almost all hardware.

---

### Post by SunnyRabbiera on 2008-04-05
also try linux mint, it too has a few tools to help you out

---

### Post by Slychilde on 2008-04-05
Any distro that you can install openbox, fluxbox or XFCE easily will do pretty much what you're looking for.  The distro doesn't really matter, it's the Desktop Environment that you're looking for.

Try out Zenwalk, Xubuntu, DSL, Puppy Linux or Arch with XFCE or Open/Flux-box installed.

---

### Post by LaRoza on 2008-04-05
> **gobbles414 said:**
> Hi all,

Thanks for those links. Still a bit too complicated...

I've attached a screenshot of the original Mac OS's desktop for your reference. That's my definition of a simple GUI. Early versions of the Mac OS had a very small number of control panels -- about 10 as I recall. Similarly, each control panel had very few options in it. Many early GUI programmers believed that a user shouldn't even notice his/her operating system. I share that belief.


Early Windows was simple as well... The reason for the many options is the wide range and capabilities of systems today.

If you don't want to notice your operating system, don't use a computer ;)

You can set up a desktop environment that has a simple interface. IceWM is like that.

If you want something simpler, JWM and the *boxes can provide that. If you want to ultimate in simplicity, use X only, RatPoison, or TinyWM ([http://incise.org/index.cgi/TinyWM](http://incise.org/index.cgi/TinyWM))

---

### Post by LaRoza on 2008-04-05
IceWM on Ubuntu with a Mac theme.

[[IMG]http://img166.imageshack.us/img166/8657/macsv7.th.png[/IMG]](http://img166.imageshack.us/my.php?image=macsv7.png)

If you want this, do a base install of Ubuntu with alternative disk, then run:

```

sudo apt-get update
sudo aptitude install icewm
sudo aptitude install icewm-themes

```

(There are many themes and there are no complex control applets. It is fast, it starts instantly for me when I log in.)

---

### Post by 3rdalbum on 2008-04-05
Have a look at Syllable and Haiku. Both are fully GUI operating systems in their (comparative) infancy, and they don't provide too many options. Unfortunately, there's not much software and not a lot of hardware supported, but when you're running on the x86 platform that's going to be a reality.

---

### Post by darrelljon on 2008-04-05
Have a look at OpenGEM although it needs to be run on top of FreeDOS.

---

### Post by LinuxGuy1234 on 2008-04-05
Try Syllable. It's simple, but not Linux.

---

### Post by MONODA on 2008-04-05
try using GNUStep or WMaker, both very simple

---

### Post by kerry_s on 2008-04-05
i agree with every one else here the set up or look is what you make it. it doesn't matter what you use, most are very configurable. there can be a thousand people using the same os, yet can look very different for each person.

i use jwm, which is very simple for me and there are many ways it can be setup, but i choose to keep mine very simple, almost barren, even my menu is almost empty. i'm not even using icons, cause i don't want to.

so just put a little effort into what you got, make it what you want.

mine->

---

### Post by gobbles414 on 2008-04-05
Hi all,

Thank you all for your replies. Just to clarify my intentions, I'll still be using Ubuntu (nice) and Vista (yuck) as my primary operating systems. **I'm searching for a simple OS because I want to relax with a bit of nostalgia from time-to-time.** I've looked at all of your suggestions. I'm currently considering GNUstep, Haiku, Kolibri, Shane Land OpenGEM, and Syllable. Of these, I'd have to say that the OpenGEM GUI looks the most like what I want. **I'm going to try running OpenGEM in VirtualBox on my Vista PC.**

I just prefer the simple approach to computing. But I also prefer 70s disaster films and 80s action films over any of the blockbusters that Hollywood produces today. So, I must just be too old fashioned. And I'm only 24 years old! :???:

---

### Post by cardinals_fan on 2008-04-05
How about [Mac-on-a-stick]("http://nothickmanuals.info/doku.php?id=minivmac")?

---

### Post by ibuclaw on 2008-04-05
Afterstep mimics the NextStep look.

NEXTStep was made by an apple developer, before the company went bust and was bought back by Mac again.

The interface is the basis of what Macs are today.

Only it's very, very pre-historic look (very basic).

[http://www.afterstep.org/](http://www.afterstep.org/)

Other than that... I wonder if there is a Desktop Interface that is built entirely on CURSES or NCURSES.

hmm... Now that would be nostalgia. 8)

---

### Post by gobbles414 on 2008-04-05
> **cardinals_fan said:**
> How about [Mac-on-a-stick]("http://nothickmanuals.info/doku.php?id=minivmac")?

That look REALLY promising! I'll try using the pre-built version and report back.

---

### Post by gobbles414 on 2008-04-05
> **tinivole said:**
> Afterstep mimics the NextStep look.

NEXTStep was made by an apple developer, before the company went bust and was bought back by Mac again.

The interface is the basis of what Macs are today.

Only it's very, very pre-historic look (very basic).

[http://www.afterstep.org/](http://www.afterstep.org/)

Other than that... I wonder if there is a Desktop Interface that is built entirely on CURSES or NCURSES.

hmm... Now that would be nostalgia. 8)
Thanks... I've added Afterstep to my list.

---

### Post by init1 on 2008-04-06
I recommend FreeDOS and OpenGEM for this. It's about as simple as it gets. 
[www.freedos.org](www.freedos.org)
[http://gem.shaneland.co.uk/](http://gem.shaneland.co.uk/)
This is my GEM desktop

---

### Post by gobbles414 on 2008-04-06
Hi all,

Mac-on-a-stick is working brilliantly on my Vista PC! It works both on the PC's hard drive and on my USB flash drive. I may experiment with OpenGEM in the future. But for now, I'm too busy enjoying the old Mac OS and its 12 control panels. :)

---

