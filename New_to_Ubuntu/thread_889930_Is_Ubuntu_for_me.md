---
title: "Is Ubuntu for me?"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by Vinegarcat on 2008-08-14
I recently found myself in the possession of a reformatted computer (my own).  My usual range of activities is:

- Medium to casual level of gaming, including games on Steam such as TF2 and the occasional MMO (EQ2, EVE Online, Warhammer, etc.).  I've got a bit of a crush on trying out the newest MMOs
- Developing websites and web apps, including basic PHP/XML/JS all the way up to Coldfusion/Java servers and "applications"
- Watching anime (subtitled) and movies (downloaded legal and some import DVDs)
- Surfing news, forums, managing websites, heavy internet usage
- The rare chat tool, webcam conference and such for business type meetings, also webcasting with tools such as "Glance"

I've had a bad experience long in the past with linux (more than 10 years ago now) and tried it again 5 or 6 years ago with much better results but still not quite "ready".  The last time I ran into one too many issues running a local development machine with a basic Apache setup to mimic my live server (PHP).  Now I'm doing Java and PHP so the setup is bound to be more complicated, and I'm wondering if Ubuntu will be good with that setup.  Listening to music and anime/TV/Movies/games are also pretty important to me because it's how I relax after work (I noticed the sound card I had wasn't recognized by default, hopefully this won't be a big issue).

I want to know, very specifically, if you think a programmer could get reasonably comfortable with Ubuntu in about a month or two worth of time and rely on it more than Vista or if I should forget the whole experiment and run with Windows?

I'm interested in Linux because I like to do modifications to software, interfaces and the like.  I did remember speed being a big pro to Linux's usage with a low number of memory leaks compared to Windows and the development environment (once running) to be more stable.  One of the major downsides last time was that it took more than a month to just get good sound drivers installed much less video drivers and gaming was almost entirely out of the question due to just that.  I also "messed something up" last time, possibly by accidentally uninstalling a package I wasn't supposed to (trying to get KDE running) and ended up with a crash screen everytime I tried to log off (and it showed the KDE bootscreen, yet booted into Gnome).  I want to know if I can run Linux without having to reinstall everytime something goes wrong.

So are all these wants and needs fulfillable, or are they just pipe dreams?

P.S. I have the latest version of Ubuntu currently as of this morning.

---

### Post by finer recliner on 2008-08-14
linux is great for developers, web surfers, watching media

its not good for gaming. however wine has made great strides in this area to bring windows games to linux distros.

EDIT:
and if you're still not sure, you can always dual boot windows and linux together. also try booting from the ubuntu install disc. this will give you a chance to try the entire OS before making any changes to your computer. (it will run slower than usual because its from a CD/DVD, but that should be the only difference)

---

### Post by starcannon on 2008-08-14
If you play EQ2 regularly, your going to require a dual boot situation.
EQ2 graphics are too intense for wine or cedega to handle last I looked, indeed I'm not even sure if either wine or cedega are even attempting to make this game playable (someone correct me if my information is outdated).

That said, if you want a great system to do everything but high end gaming on, Ubuntu is for you. We have games, but we don't have EQ2.

GL

Starcannon

---

### Post by dca on 2008-08-14
Most of the devs I know either use MAC OSX or some Linux distro.

---

### Post by gioland71 on 2008-08-14
Well, you won't be able to play Windows-only games at the same level... I've not tried emulators, as I do not like gaming, but I am sure some other gamers will help you with that. I still have dual boot, just in case.
I know several people who use ubuntu as their main OS at work, doing heavy imaging processing and software development - they love it! I use it on my tiny laptop to do everything else you described (well, except for games :-) ) and I am very happy with it. I didn't have a single software issue to date.

---

### Post by Vinegarcat on 2008-08-14
> **starcannon said:**
> If you play EQ2 regularly, your going to require a dual boot situation.
EQ2 graphics are too intense for wine or cedega to handle last I looked, indeed I'm not even sure if either wine or cedega are even attempting to make this game playable (someone correct me if my information is outdated).

That said, if you want a great system to do everything but high end gaming on, Ubuntu is for you. We have games, but we don't have EQ2.

GL

Starcannon

Thanks for the responses!  I wouldn't mind dual booting, thanks for the reality check on that, it'll save me a lot of time down the road I imagine.  Do you think that it would be reasonable to assume someone fairly computer literate and a programmer to be able to feel "very" (4 out of 5) comfortable with Ubuntu within a month or two?  Or is the break in period *generally* longer?

Also, I downloaded the first version I saw, not sure which version I've got (32 or 64) but I'm running an intel dual core 64, is there a way to check which version I'm running?

---

### Post by LowSky on 2008-08-14
My "break-in"  comfort period was about 2 weeks. I no programmer, but I do build systems for a little extra cash. but to the point I was complete Settled with my install was about 2 months.
Gnome is very friendly and ubuntu's version makes the most out of trying to get everything working from the get go.

---

### Post by aaaantoine on 2008-08-14
I got pretty comfortable with Ubuntu pretty quickly.  Two weeks is about right.

For gaming, currently nVidia is your best bet for performance and compatibility.  ATI/AMD has been turning itself around for the past year by releasing their hardware specifications (for FOSS driver development) and completely reworking its proprietary Catalyst driver.  However, their drivers don't play well with wine, and are otherwise still pretty buggy.  Intel probably has the best open source drivers of them all, but as you probably already know, their underlying graphics hardware is crap.  On Linux, you could at the very least do casual gaming.  (As an aside, EVE Online officially supports Linux.)

I started getting into programming with PHP somewhat recently.  It works very well with Apache.  The Ubuntu community documentation has a great How-To for putting together a LAMP (Linux, Apache, MySQL, PHP) system.

DVD playback isn't supported out of the box for legal reasons (unless you buy an Ubuntu Dell).  But there is a way to get it working in a few steps.

Ubuntu comes with Firefox by default.  This basically depends on your feelings about Firefox.  Alternatively, Opera is in the repositories, and there are open source browers such as Epiphany and Konqueror.

Included with Ubuntu is an application named Pidgin.  It's a cross-protocol IM client that covers AIM, MSN, Yahoo, ICQ, Jabber, and a bunch of others.  It does not support video chat, however.  I don't know much about video chat on Linux (my Acer Orbicam isn't supported yet, but some dedicated reverse engineers are developing the drivers as I write this).  I also cannot tell you about webcasting tools.

Linux has certainly come a long, long way in the past 10 years.  How well it compares to Windows and Mac OS-X is up to the preferences of the user.

---

### Post by Vinegarcat on 2008-08-14
I've been working with it for the past few hours and it is MUCH easier to work with, especially due to these forums and the magical search button.  I've got video and my sound card up and running, even though my sound card is one of the dreaded X-Fi ones (took me an hour but I got it running :) ).  Overall, much smoother presentation than previously entailed, and the commands seem easier to use as well as more experienced users actually willing to help people out there.  I suspect it's also due in part to better drivers able to work across more platforms.  Glad I took another plunge :)

---

### Post by erickghint on 2008-08-14
Tested as of July 20th, EQ2 works on WINE. With gold status no less =)

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=358&sAllBugs](http://appdb.winehq.org/objectManager.php?sClass=version&iId=358&sAllBugs)

---

