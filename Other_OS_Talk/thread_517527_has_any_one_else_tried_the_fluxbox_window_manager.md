---
title: "has any one else tried the fluxbox window manager"
date: 2007-08-04
forum: Other OS Talk
---

### Post by jacob01 on 2007-08-04
i just tried dsl linux wich is a linux os built off a stripperd down version of  knoppics wich uses the fluxbox window manager and thought it was pretty good so i am bownloading the fluxbuntu iso to try

has any one else tried it

---

### Post by SunnyRabbiera on 2007-08-04
Off and on, its nice but not for me.

---

### Post by Gremlinzzz on 2007-08-04
A while back i tried it .What i use now is the ubuntu studio theme gives feisty a more mod look.I install using this site then went into synaptic to install the stuidio sounds and usplash and stuff.works great and looks good.
[http://www.belutz.net/2007/05/11/installing-ubuntu-studio-theme/](http://www.belutz.net/2007/05/11/installing-ubuntu-studio-theme/)

---

### Post by benx009 on 2007-08-04
fluxbox is ok, but if you wanna go light, try [xfce]("http://www.xfce.org/")

---

### Post by kerry_s on 2007-08-04
a few times. :)

---

### Post by jacob01 on 2007-08-04
yea i just thought the menu was cool and i like exploring new distros

ok yea ill have to try fxce 

i was wondering what are the minimum requirements for xubuntu on the site it said  the same thing as ubuntu and kubuntu

---

### Post by xpod on 2007-08-04
Wolvix is great.......xfce & fluxbox

---

### Post by SunnyRabbiera on 2007-08-04
> **benx009 said:**
> fluxbox is ok, but if you wanna go light, try [xfce]("http://www.xfce.org/")

Flux is still lighter thouugh, as XFCE is gtk based

---

### Post by Gremlinzzz on 2007-08-04
This system seems to be for low end computers
[http://distrowatch.com/?newsid=04341](http://distrowatch.com/?newsid=04341)

---

### Post by SunnyRabbiera on 2007-08-04
damn small is also quite good.

---

### Post by pooslinger on 2007-08-04
> **jacob01 said:**
> i just tried dsl linux wich is a linux os built off a stripperd down version of  knoppics wich uses the fluxbox window manager and thought it was pretty good so i am bownloading the fluxbuntu iso to try

has any one else tried it

Fluxbuntu is a waste.  They are taking a fast window manager and adding things to make a desktop environment which is not the point of fluxbox.  Just try basic fluxbox on your current machine.

> sudo apt-get install fluxbox

Change the session to fluxbox at once your display manager boots up.  Log in to fluxbox.

---

### Post by Bachstelze on 2007-08-04
Fluxbox is my WM of choice when the machine I run it on is too light for KDE. I'm also running it by default on my OpenBSD systems since KDE is a bit sluggish for my tastes there because of no nvidia drivers.

---

### Post by Nythain on 2007-08-04
100% pure fluxbox here... who needs a desktop environment anyways :)

---

### Post by Bachstelze on 2007-08-04
> **Nythain said:**
> 100% pure fluxbox here... who needs a desktop environment anyways :)

No one. But if you go this way, who needs a GUI ;)

---

### Post by RedSquirrel on 2007-08-05
> **jacob01 said:**
> i just tried dsl linux wich is a linux os built off a stripperd down version of  knoppics wich uses the fluxbox window manager and thought it was pretty good so i am bownloading the fluxbuntu iso to try

has any one else tried it

Yes I have tried it. It's all I use these days. :)

You can get it from the Ubuntu repositories (no need to install fluxbuntu unless you want to).

```
sudo apt-get install fluxbox && sudo update-menus
```The 'sudo update-menus' command will generate the default Fluxbox menu. If you don't run that command, you won't have a menu when you login to Fluxbox and your ability to use it might be impaired. ;)



> **jacob01 said:**
> yea i just thought the menu was cool and i like exploring new distros

ok yea ill have to try fxce 

i was wondering what are the minimum requirements for xubuntu on the site it said  the same thing as ubuntu and kubuntu


Xfce is not as light as Fluxbox.

The minimum system requirements for Xubuntu are lighter than ubuntu and kubuntu. From [http://xubuntu.org/get#requirements](http://xubuntu.org/get#requirements) ...

>  **Minimum system requirements**

To run the Desktop CD (LiveCD + Install CD), you need 128 MB RAM to run or 192 MB RAM to install. The Alternate Install CD only required you to have 64 MB RAM.

To install Xubuntu, you need 1.5 GB of free space on your hard disk.

Once installed, Xubuntu can run with 64 MB RAM, but it is strongly recommended to use at least 128 MB RAM.



You can also install the xfce4 metapackage instead of the whole xubuntu-desktop if you want.

---

### Post by Tux Aubrey on 2007-08-06
I enjoy fluxbox on older machines - or sometimes just for a change.

IMO, fluxbuntu was a great idea, but I just couldn't get it to work for me.  Straight fluxbox (from the repos) on a Feisty install is just sweet once you get the hang of setting up the config files from scratch.

I also like [Mepis antiX ]("http://cafelinux.org/distropedia/?q=node/98")(flux+icewm) but it certainly isn't anywhere near as "light" as DSL.  The default menus and the Mepis admin tools are really well done, IMO.  It will follow Mepis back to a pure Debian base (rather than Ubuntu Dapper) in its next release.

If Fluxbuntu is released on a Gutsy base, I'll try it again too.

---

### Post by fistfullofroses on 2007-08-06
No need for Fluxbuntu as mentioned above. Just make sure you install the menu package as well so that fluxbox will contain all of your programs. You might want xli for background images.

#apt-get install fluxbox menu xli

---

### Post by DreamcastJack on 2007-08-06
I recently tried out PCFluxBoxOS beta, its pretty nice. but I prefer TinyMe for light weight. and I just dont like how Flux Box is set up.. maybe its just me. but if it works for you. use it.

---

### Post by RAV TUX on 2007-08-07
> **jacob01 said:**
> i just tried dsl linux wich is a linux os built off a stripperd down version of  knoppics wich uses the fluxbox window manager and thought it was pretty good so i am bownloading the fluxbuntu iso to try

has any one else tried itfluxbox is nice but I prefer e17.

---

### Post by RedSquirrel on 2007-08-07
> **fistfullofroses said:**
> No need for Fluxbuntu as mentioned above. Just make sure you install the menu package as well so that fluxbox will contain all of your programs. You might want xli for background images.

#apt-get install fluxbox menu xli

The fluxbox package in the Ubuntu repositories has the menu package as a dependency, so there is no need to install 'menu' separately. ;)

I prefer **feh** for setting the background.

```
sudo apt-get install feh
```

---

### Post by RedSquirrel on 2007-08-07
> **RAV TUX said:**
> fluxbox is nice but I prefer e17.

How is e17 in terms of stability?

(Great avatar by the way. :))

---

### Post by Lividity on 2007-08-22
Fluxbox is great I run it on my OpenBSD box and Ubuntu laptop.

[http://hidebehind.com/5D957A]("http://hidebehind.com/5D957A")

---

### Post by Linux_noob1 on 2007-08-23
I have DeLi linux running fluxbox on an ancient pc I pulled out of my closet :D

---

### Post by jviscosi on 2007-08-28
> **RedSquirrel said:**
> How is e17 in terms of stability?

When I used to use E17 it was fairly stable, but some of the applets (especially the weather applet) had a nasty tendency to bring the entire WM down.  Usually when E17 crashed it would detect the problem and offer to restart, but it would sometimes hard lock up and I'd have to CTRL-BACKSPACE to kill X.  After a couple of times of that happening, I stopped using it.  I hate writing the same paragraph twice.  ;-)

Another problem I had with E17 is that fairly regularly, some major change would break existing themes, configurations, etc., and I would have to recreate my .e directory from scratch.

This was all some months ago, and E17 was pretty clearly labeled development code so I can hardly say the devs didn't warn me.

---

### Post by RedSquirrel on 2007-08-28
> **jviscosi said:**
> Usually when E17 crashed it would detect the problem and offer to restart, but it would sometimes hard lock up and I'd have to CTRL-BACKSPACE to kill X.  After a couple of times of that happening, I stopped using it.  I hate writing the same paragraph twice.  ;-)

Thanks for the reply. I have decided to stick with my usual Fluxbox for now. I was playing with Xfce for a couple of days and it crashed. I have since removed it. I don't like crashes. ;)

The stability of Fluxbox is a major reason I use it. My SVN builds have always been rock-solid.

---

### Post by jviscosi on 2007-08-28
> **RedSquirrel said:**
> The stability of Fluxbox is a major reason I use it. My SVN builds have always been rock-solid.

I agree about Flux; I also use the SVN version and the only times I have ever had trouble is when I try to do something funky, like run xcompmgr to get the transparency and shadow effects. Then CPU would occasionally run away and I would have to remotely kill xcompmgr from another machine to free X up again.  

I think the problem is that xcompmgr doesn't like one of my dockapps, because the same thing would happen in XFCE when I had a Kicker panel open with my favorite dockapps in it.  (Yes, I ran Kicker in XFCE.  I'm a freak.)  It doesn't happen with XFCE's native composite manager.

I'm more or less back to Fluxbox now after having dabbled with Window Maker for a while.  Window Maker is cool and fast but it just isn't Fluxbox.

---

### Post by fuscia on 2007-08-29
> **HymnToLife said:**
> No one. But if you go this way, who needs a GUI ;)

people who suck at typing.

i prefer openbox, by far, to fluxbox. openbox can be as light as fluxbox, or, in its current state, can almost be DE like.

---

### Post by fwojciec on 2007-08-29
> **fuscia said:**
> people who suck at typing.

i prefer openbox, by far, to fluxbox. openbox can be as light as fluxbox, or, in its current state, can almost be DE like.

you mean fluxbox can be as light as openbox - once you disable the icons in menus, excessive transparencies and these over-the-top window decorations (yuck!)

;)

---

### Post by RedSquirrel on 2007-08-29
> **jviscosi said:**
> I think the problem is that xcompmgr doesn't like one of my dockapps, because the same thing would happen in XFCE when I had a Kicker panel open with my favorite dockapps in it.  (Yes, I ran Kicker in XFCE.  I'm a freak.)  It doesn't happen with XFCE's native composite manager.

That's funny. The reason I installed Xfce last weekend was to play with the compositing. :) I was surprised by how well it worked. xcompmgr and transset (with Fluxbox) slowed things down to a crawl, so I quickly dropped them. I actually didn't mind Xfce, but when it crashed that was enough for me. I favor stability over eye candy any day. (By the way, the crash happened long after I had disabled the compositing, so that's not to blame in this case.)


> **jviscosi said:**
> I'm more or less back to Fluxbox now after having dabbled with Window Maker for a while.  Window Maker is cool and fast but it just isn't Fluxbox.

I tinkered with WindowMaker a while ago, but it just wasn't for me. :neutral:

---

### Post by jviscosi on 2007-08-29
> **fuscia said:**
> i prefer openbox, by far, to fluxbox.

I'm always happy to try another window manager so I installed Openbox from Synaptic.  My first impression is that it does look sharper out of the box than Fluxbox, is nice and snappy, and it has a pop-up when cycling windows with Alt-Tab.  Yay!  The lack of same has always bugged me about Fluxbox.  I also like the idea of XML-based configuration files.

On the other hand, Ubuntu-installed Openbox doesn't appear to bother with the local autostart.sh file, presumably because openbox-session is nowhere to be found.  (I wrote a dirty little script and changed openbox.desktop to invoke it).  

Also, for some reason, middle-click insists on being the button that moves the dock, even though I changed it in my rc.xml file (and, when that didn't work, in the systemwide rc.xml file as well).  Oddly, if I select Reconfigure from the OB menu, it does suddenly realize that I don't want middle-click to grab the dock.  This is relatively important as there are several dockapps in there that do something with middle-click.  I'll perhaps fool with it some more and see if I can figure it out.

One thing Flux has that I like is the toolbar, which, if you rotate it to be vertical, changes the orientation of all the text inside it to match. The other toolbars I've seen leave the text horizontal when you make them vertical.  If anyone has a suggestion for a toolbar for OB that will rotate text, I'd be interested in hearing about it.

Anyway, OB looks interesting enough to play with for a while.  I wonder why I never tried it before ...

EDIT: I do have to say, inserting an 0.75 second delay (as the FAQ recommends) between dockapps to make them sort into the dock adds like 10 seconds to my OB startup time.  I'm not sure I'm going to like that very much ...

---

### Post by urukrama on 2007-08-30
> **jviscosi said:**
>  On the other hand, Ubuntu-installed Openbox doesn't appear to bother with the local autostart.sh file, presumably because openbox-session is nowhere to be found.  (I wrote a dirty little script and changed openbox.desktop to invoke it).

I don't know what version is in the Feisty repos, but if you install the [Feisty deb]("http://icculus.org/openbox/releases/openbox_3.4.4-0ubuntu1_i386.deb") of the latest Openbox version, you get all the autostart goodness, and much more.

---

### Post by jviscosi on 2007-08-30
> **urukrama said:**
> I don't know what version is in the Feisty repos, but if you install the [Feisty deb]("http://icculus.org/openbox/releases/openbox_3.4.4-0ubuntu1_i386.deb") of the latest Openbox version, you get all the autostart goodness, and much more.

Thanks for the tip!  The repo version is 3.3.  I actually did grab the DEB file for OpenBox and OBConf this morning and autostart is working now.  (I think I actually did try OpenBox quite a while ago and stopped because there was no autostart.  IIRC it said to just use .xinitrc, which doesn't work for me because I start different things in different WMs/DEs.  I may be thinking of blackbox but I'm pretty sure it was OpenBox.)  EDIT:  By the way, I reduced the 0.75 to 0.25 and still get the correct ordering of dockapps.  My next experiment will be to see how low the delay can go and still work consistently.

I like that there's a "--reconfigure" option now so I can invoke it from scripts if I want to.  Also, I noticed that 3.4 adds a window handling option of "center new windows", which I had been using devilspie for in Fluxbox (and Window Maker).  Unfortunately the current version devilspie likes to segfault on my machine, so this is better.

For a vertical toolbar, I added a toolbar to fbpanel and made the max width 32px so that it only shows the app icon.  No text, no rotation worries.  Looks cool too.  ;-)

I made OpenBox my default for a while.  Tee hee -- this is going to be fun!  I love playing with window managers ...

---

### Post by Bungo Pony on 2007-08-30
DSL not only comes with Fluxbox, but it also comes with JWM to give it more of a "windows feel". I still like Fluxbox more though :)

---

