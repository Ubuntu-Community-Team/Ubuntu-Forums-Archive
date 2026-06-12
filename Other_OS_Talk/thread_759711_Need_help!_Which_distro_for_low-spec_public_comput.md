---
title: "Need help! Which distro for low-spec public computers?"
date: 2008-04-19
forum: Other OS Talk
---

### Post by Cifra on 2008-04-19
Looking for a working mini distro

I am the maintainer of a few public computers in a school library. I didn’t really check, but if I remember correctly, the computers are pretty old 900 MHz Pentiums with 90-128 mb RAM.

Now these computers had XP on them before, but I removed this horrible operating system in order to install Linux. Of course, there is a huge number of distros to choose from, even in the low-end computer niche.

All I needed was a word processor like Abiword, multiple user support with login manager, a basic file manager like PCman, Flash support, a home directory for the user ’student’, a WM, a desktop with a background, and a panel with FOUR icons - Abiword, Net browser, Home and shutdown. Also, I wanted to restrict the user ’student’ not to change the system’s theme, background and configuration files.

The KDE Kiosk Tool is great, though I think you know how fast KDE on 92 mb of RAM runs (if it runs, that is).


You cannot imagine how difficult it was for me to find something even close to this.

Sadly, some of these mini distros have huge flaws which need to be fixed. Others, on the other hand, aren’t really mini distributions.


I’m checking out TinyMe at the moment, a small PCLinuxOS derivative , and it looks promising… by changing the Openbox configuration and a few other things, I think I’ll be able to generate a stripped-down LiveCD for those school computers. It looks alright, too.

SOem of you would probably suggest Debian.  Non-base Debian is slow. I love Debian, but it’s way too slow and I’m too lazy to install it from scratch. If I’ll be forced to do this, I’ll rather play with Arch.

What do you think? Do you have any recommendations for a web kiosk computer with low specs? What do you think of TinyME? What is your favourite low-end window manager? I NEED INFORMATION GUYS!:confused::confused::confused:

---

### Post by jimbren on 2008-04-19
Have you tried Xubuntu?

I had it running very well on a P3 500 with 128MB RAM--The machines you're referring to should be more than adequate.  You may not be able to do a live CD session, but you should be able to do an alternate install without any problems.

my .02

jimbo

---

### Post by cardinals_fan on 2008-04-19
Zencafe is based off of Zenwalk and designed for use on public computers ie internet cafés.

---

### Post by barbedsaber on 2008-04-19
> **cardinals_fan said:**
> Zencafe is based off of Zenwalk and designed for use on public computers ie internet cafés.

thats it, thats the one that I was racking my brains trying to remember.

---

### Post by Cifra on 2008-04-19
Seems like it uses XFCE. Nevermind, I'm downloading it! :D

---

### Post by myusername on 2008-04-20
fluxbuntu

---

### Post by amazingtaters on 2008-04-20
I'd recommend SliTaz. You wanna talk about small? Try under 25 Megs for the iso. It's really well featured for something that small, and it is definitely light on the resources. Give it a try.

---

### Post by Cifra on 2008-04-20
Yeah, I tried SLitaz, but it lacks local qwertz keyboard support, isn't very fast when it comes to booting it's version of Firefox, has problems with flash and doesn't look very nice :)

---

### Post by K.Mandla on 2008-04-20
Moved to Other OS Talk.

Also note the sticky at the top of this forum.

---

### Post by amazingtaters on 2008-04-20
> **Cifra said:**
> Yeah, I tried SLitaz, but it lacks local qwertz keyboard support, isn't very fast when it comes to booting it's version of Firefox, has problems with flash and doesn't look very nice :)

Hmm I guess the look is all opinion but I really like it. I'm surprised you had problems with it, it's always run really solidly for me on the various school computers I use running it off of my flash drive. Perhaps try out Puppy then. I've also used DamnSmall but there's just a few little things about it that annoy me (like I think it's beyond ugly).

---

### Post by Pogeymanz on 2008-04-20
+1 for Puppy. Puppy is amazingly fast and very very full-featured.

---

### Post by volkswagner on 2008-04-20
You may want to give Slax consideration.  I have been messing around with older hardware.  Most of which have 256meg ram or more.  Slax can be installed to the HD using lilo.  You may want the older version (5.0).  The support forums are pretty good.  One thing I noticed on my AMD700mhz 384meg, tripple boot, fluxbuntu, slax, ubuntu 7.10 (yes 7.10 is quite usable for web browsing and office).  Slax was the only one in the list to handle ACPI properly out of the box.  Not to say I could not configure "force-ACPI".  Slax was the only one which would completely power off on halt.

I did not use lilo so I ran into trouble.  If you like KDE it runs well under Slax.

---

### Post by CREEPING DEATH on 2008-04-20
> **Cifra said:**
> SOem of you would probably suggest Debian.  Non-base Debian is slow. I love Debian, but it’s way too slow and I’m too lazy to install it from scratch. If I’ll be forced to do this, I’ll rather play with Arch.

Have you tried Debian XFCE?  It installs a fairly small base with what you need and ought to work fine for your purposes.

CD

---

### Post by chris4585 on 2008-04-20
DSL, puppy, icebuntu.... 

;)

---

### Post by Cifra on 2008-04-21
Puppy - the last version I used had no multiuser support, so it's out of the question.

What would be teh best DE and WM to use if I only wanted a backgorund (no icons) and a simple panel?

---

### Post by eriqjaffe on 2008-04-21
> **Cifra said:**
> What would be teh best DE and WM to use if I only wanted a backgorund (no icons) and a simple panel?I'd say either Fluxbox (which has a built-in panel, although I don't think it looks all that great) or Openbox (which doesn't have a panel, but you can add one like pypanel, fbpanel, lxpanel, etc).

In either case, all the configuration (startup, menus, etc) is done via text files, so they're both pretty easy to set up the way you want.

---

### Post by Cifra on 2008-04-21
Cool... what about the panel?

---

### Post by eriqjaffe on 2008-04-21
With Openbox (which I use most often these days), I prefer PyPanel, which I think just looks the best.  I have also used fbpanel, which has the nice plus of having an auto-updating "start menu".  You might want to look into lxpanel, which is based on fbpanel - I wasn't thrilled with it when I tried it, but you might.

---

### Post by jseiser on 2008-04-22
you could always just do a base arch install, put on kdemod, and then load your kde kiosk.  Cant say how fast it will run untill you try it, but its supposed to be a stripped down, faster kde.  

Openbox and pypanel is also a good way to go, if you dont mind setting up your menu, and then copying it over to the other PC's.  as far as multi user support, I really wouldnt know how to help you, Ive always only had one user logged in at a time.

---

### Post by Cifra on 2008-04-22
> **jseiser said:**
> you could always just do a base arch install, put on kdemod, and then load your kde kiosk.  Cant say how fast it will run untill you try it, but its supposed to be a stripped down, faster kde.  

Openbox and pypanel is also a good way to go, if you dont mind setting up your menu, and then copying it over to the other PC's.  as far as multi user support, I really wouldnt know how to help you, Ive always only had one user logged in at a time.

I probably used the wrong term; I just want it to support user accounts, so it doesn't log in as root by default, like Puppy Linux. 

Yeah, I could do a base Arch install, but that would take a lot of work.

SO basically, I don't need a menu... just a panel with Firefox, Abiword (or Openoffice) and Shutdown... you people say it can all be done via text files, right? Openbox has got xml conf files?

I'm looking at Larch now, whic is arch with some kind of CD remaster script built in!

---

### Post by NightwishFan on 2008-04-22
Puppy as a first choice but fluxbuntu is great as well, and looks nice.

---

### Post by eriqjaffe on 2008-04-22
> **Cifra said:**
> SO basically, I don't need a menu... just a panel with Firefox, Abiword (or Openoffice) and Shutdown... you people say it can all be done via text files, right? Openbox has got xml conf files?Yes, Openbox uses XML files.

If you don't need the panel to act as anything other than a launcher, you could also look into [iDesk](http://idesk.sourceforge.net/wiki/index.php/Main_Page), which will just let you put icons right on the desktop.  Personally, if you go that route, check out [wbar](http://freshmeat.net/projects/wbar/), which provides a pseudo-transparent launcher with some basic animation effects.

---

### Post by Twitch6000 on 2008-04-22
Well with the specs you got I would say arch or fluxbuntu.Either one can can be made to work with what you need I believe.

---

### Post by smoker on 2008-04-23
> **eriqjaffe said:**
> ...  Personally, if you go that route, check out [wbar]("http://freshmeat.net/projects/wbar/"), which provides a pseudo-transparent launcher with some basic animation effects.

i would second 'wbar', excellent iconbar, easy to configure, and uses little in the way of resources, looks fantastic as well!

---

### Post by eriqjaffe on 2008-04-23
Just for a quick reference, here's a screenshot of my old (P2/366/128mb) laptop running wbar & Fluxbox:

[img]http://img516.imageshack.us/img516/3527/desktopscreenshot200802so1.png[/img]

Just make sure you load it **after** your wallpaper is set.  ;)

---

### Post by DJiNN on 2008-04-23
Give [antiX]("http://antix.mepis.org/") a try. It's based on Mepis (Debian), uses fluxbox, has pretty much all that you're asking for and is lightweight. yet snappy, even on older boxes with reduced ram.

---

### Post by DJiNN on 2008-04-23
> **eriqjaffe said:**
> Just for a quick reference, here's a screenshot of my old (P2/366/128mb) laptop running wbar & Fluxbox:

Just make sure you load it **after** your wallpaper is set.  ;)

That looks great!! 8)  Did you have a hard time setting up wbar? I've tried it here (using fluxbox but also with xcompmgr) and had mixed success. 

Is that the standard fluxbox panel at the top?

---

### Post by tashmooclam on 2008-04-23
What about Teenpup (variant of puppy linux)? I think it has all of the codecs etc already on it.

---

### Post by Cifra on 2008-04-23
> **tashmooclam said:**
> What about Teenpup (variant of puppy linux)? I think it has all of the codecs etc already on it.
Again, Puppy does not support user accounts, you login as root by default.


**Eriqjaffe,** that screenshot looks really cool. Is it Debian?

---

### Post by tashmooclam on 2008-04-23
Teenpup
[http://www.puppylinux.org/wikka/TeenPup](http://www.puppylinux.org/wikka/TeenPup)

puppy linux

[http://puppylinux.org/wikka/AboutPuppy](http://puppylinux.org/wikka/AboutPuppy)

---

### Post by tashmooclam on 2008-04-23
Oops. Sorry for jumping the gun.

---

### Post by eriqjaffe on 2008-04-25
**DJiNN**:  I found wbar to be a breeze to set up, actually.  There's a .deb hidden in the comments on the Freshmeat page that installed (on Feisty) without issue.  The config is just a simple text file in ~/.wbar:

```
# The Bar && Font
i: /usr/share/wbar/iconpack/wbar.osx/osxbarback.png
c:
t: /usr/share/wbar/OldSansBlack.ttf/14

i: /usr/share/wbar/iconpack/wbar.osx/nautilus.png
c: pcmanfm
t: pcmanfm
```...and so on.  **I**con, **c**ommand, **t**itle.

I invoke it from the ~/.fluxbox/startup with

```
wbar -bpress -nanim 3 &
```

...and, yes, it's the standard Fluxbox panel, although I don't remember off-hand which style I had applied at the time.

**Cifra**:  Nope, it's Fluxbox on top of a Ubuntu command-line install with a wallpaper that I found on...uh...Gnome-Look.org, I think.

---

### Post by DJiNN on 2008-04-28
> **eriqjaffe said:**
> **DJiNN**:  I found wbar to be a breeze to set up, actually.  There's a .deb hidden in the comments on the Freshmeat page that installed (on Feisty) without issue.  The config is just a simple text file in ~/.wbar:

```
# The Bar && Font
i: /usr/share/wbar/iconpack/wbar.osx/osxbarback.png
c:
t: /usr/share/wbar/OldSansBlack.ttf/14

i: /usr/share/wbar/iconpack/wbar.osx/nautilus.png
c: pcmanfm
t: pcmanfm
```...and so on.  **I**con, **c**ommand, **t**itle.

I invoke it from the ~/.fluxbox/startup with

```
wbar -bpress -nanim 3 &
```...and, yes, it's the standard Fluxbox panel, although I don't remember off-hand which style I had applied at the time.

Thanks for the info.... i have now got wbar running, and it's all working really well! Looks great too! +1  :) 

Looks a bit strange with xcompmgr, but that's probably something to do with the startup order.... i'll keep playing until i get it spot on!  

Thanks again.

---

### Post by Thundera on 2008-04-28
School Library? Try Edubuntu (probably spelled that wrong) yet?
Also, they have many educational minimal distro's for schools. Just look around, try googling "Linux Distro for Schools"

---

### Post by eriqjaffe on 2008-04-29
> **DJiNN said:**
> TLooks a bit strange with xcompmgr, but that's probably something to do with the startup order.... i'll keep playing until i get it spot on!  

Thanks again.No problem.  I never tried using wbar with xcompmgr (no point in putting unnecessary strain on the old system)...I would imagine it's doing some sort of pseudo-transparent window, and xcompmgr is revealing the normally invisible window borders.

I had that with conky on my desktop, showing shadows around it.  I just disabled the shadows in xcompmgr, and now conky just sits there like it's supposed to...

```
xcompmgr -c -t-5 -l-5 -r0 -o.55 -f &
```

The key is the "-r0", which sets the shadow offset to 0, effectively disabling them.

---

### Post by DJiNN on 2008-04-29
> **eriqjaffe said:**
> No problem.  I never tried using wbar with xcompmgr (no point in putting unnecessary strain on the old system)...I would imagine it's doing some sort of pseudo-transparent window, and xcompmgr is revealing the normally invisible window borders.

I think that's what it is. I have the same setup (well, similar) on 2 computers, both with different hardware, and the older of the two definitely has a harder time with the whole graphics thing. 

> I had that with conky on my desktop, showing shadows around it.  I just disabled the shadows in xcompmgr, and now conky just sits there like it's supposed to...

I guess i could disable it, although i quite like the whole "Shadows" effect, because it gives the screen some "Depth" IYKWIM? :)  But i'll give it a try & see how it goes. 

> 
```
xcompmgr -c -t-5 -l-5 -r0 -o.55 -f &
```

The key is the "-r0", which sets the shadow offset to 0, effectively disabling them.

Thanks for your help eriqjaffe, it's much appreciated. I'll have to write that down & save it, because i'm bound to need it again sometimes soon, especially as i'm doing a lot of distro-changing & testing at the moment, and xcompmgr seems to work well where compiz just slows the whole thing down. :)

---

