---
title: "Eeebuntu vs Easy Peasy"
date: 2009-01-06
forum: Recurring Discussions
---

### Post by AndyCee on 2009-01-06
Ok. So everyone knows the Eeepc by now.

Which do you think is better for the Eeepc range: Eeebuntu or Easy Peasy (Formerly Ubuntu-eee)?

If you've tried either, state the model of Eeepc (or other).

---

### Post by Zeroberry on 2009-01-06
Basically ubuntu-eee is ubuntu 8.04, Hardy Heron and Easy Peasy is 8.10, Intrepid Ibex.

Easy Peasy has it's bugs but seems to be getting stable. Running it atm and happy with it.

Would point out that ubuntu-eee and easy peasy aren't actually covered on these forums. Check out [http://www.ubuntu-eee.com/forum/](http://www.ubuntu-eee.com/forum/) instead.

---

### Post by wolfen69 on 2009-01-06
> **Zeroberry said:**
> 
Would point out that **ubuntu-eee and easy peasy** aren't actually covered on these forums. Check out [http://www.ubuntu-eee.com/forum/](http://www.ubuntu-eee.com/forum/) instead.

ubuntu-eee and easy peasy are the same thing. Eeebuntu is a different project altogether.

click on the forum link and it takes you to easy peasy. [Here]("http://www.eeebuntu.org/") is Eeebuntu.

i have not used either. i did  a command line install of ibex on my eeepc and built it up from there.

---

### Post by stalkingwolf on 2009-01-07
Im using UbuntuEEE 8.04.1 on my EEE 701 and it works great.  At times
I get better wifi connections than on some full sized laptops.  I think
my best so far was connecting from about a half mile away at 40%.  I have also connected with as little as 8%.

---

### Post by jnw222 on 2009-01-07
i used a cli intrepid, installed xorg, and a good wm

---

### Post by Fenris_rising on 2009-01-16
Hi there

eeepc 904HD with easy peasy. It has proved to be rock solid so far.


Regards

Fenris

---

### Post by Old_Grey_Wolf on 2009-01-16
I installed Eeebuntu on my wife's 701/4G. She is VERY happy with it. She has been using it for several weeks with no problems. It was very easy for me to install.

---

### Post by wolfen69 on 2009-01-16
> **Old_Gray_Wolf said:**
> I installed Eeebuntu on my wife's 701/4G.

i would have liked to put regular eeebuntu on mine, but the 2G surf is just too small to put a regular distro on. but i'm happy with my cli install. it has on it only what i want and no more. wicd, firefox, terminal, leafpad, vlc, and 3 games.

---

### Post by billgoldberg on 2009-01-17
I used eeebuntu 1 and it was ok, but eeebuntu 2 is a perfect distro for the eeepc 900.

The array kernel is great (not done by the eeebuntu project).

Just remember people, use ext2 as filesystem if you have a ssd, journaling file systems will wear out the ssd much faster.

---

### Post by Hobart on 2009-01-28
Some posts from people who have actually tried both would be helpful.

"I have tried only one but it works OK" doesn't help answer the initial poster's question.  I'll edit this post when I've tried Easy Peasy as well.

I currently am trying EEEBuntu:
[LIST]
[*]I'm rather disappointed with its lack of both a top level metapackage like 'ubuntu-desktop' for its various 'flavors' (standard, netbook, base).  Mainline Ubuntu does this well (ubuntu/kubuntu/xubuntu/edubuntu), any fork has no excuse to not follow suit.
[*]I'm frustrated by the possibility of collision between the separate eeepc-specific control solutions [the 'array' kernel's asus_eee kernel module conflicts and interferes with the 'eee-control' userspace daemon
[*]All soluitons have mediocre taskbar applets ...  both the applet and something else seem to try to take over brightness controls.
[*]The Array kernel module w/o the userspace daemon seems to not let me raise brightness to maximum
[*]Still trying to get full power management to work.  EEE900A - I read a note on the eee-control guy's site that on some models "the BIOS hides acpi info" or something similar.
[/LIST]

I wonder if the egos of the people involved (both at the application level and distro level - array kernel/eeecontrol/easypeasy/eeebuntu) are so big that there's no hope of them working together.

It's also not clear to me if either side project is trying to get their changes up into the mainline Linux kernel, or Debian package archive.  If anyone knows more, please post.

Is the as-shipped-by-Asus Xandros distro's relevant software closed/proprietary?  If not, is it possible to push the working code forward?

This post seems to also be comparing the distros:
[http://forum.eeebuntu.org/viewtopic.php?f=9&p=4100](http://forum.eeebuntu.org/viewtopic.php?f=9&p=4100)

---

### Post by Hobart on 2009-01-28
> **billgoldberg said:**
> Just remember people, use ext2 as filesystem if you have a ssd, journaling file systems will wear out the ssd much faster.Bill, 
Do you have a citation for this?  

And do you know specifically if the ASUS-PHISON SSD does wear-levelling? ( [http://www.phison.com/English/ProductViewEmbedded.asp](http://www.phison.com/English/ProductViewEmbedded.asp) seems to indicate Phison's chips do it)  (warning: Google reports phison.com as a malware host, probably hacked)

And if not, why do you recommend ext2 instead of jffs2 or logfs (as the OLPC XO-1 uses on its NAND?)

Thanks,
-jon

---

### Post by pierre.s.rosen on 2009-02-16
I've tried both EEEbuntu and Easy Peasy.  EEEbuntu is clearly superior.  Everything seems to work right out of the box.  No problems connecting to wifi, or inserting a usb stick or immediately watching a video on YouTube.  It also seems to boot up about 15 seconds faster.

I've had too many problems with Ubuntu-eee/Easy Peasy.  Issues with wireless and usb sticks and navigating around the netbook interface drove me crazy.  I couldn't control sound volume.

---

### Post by NTolerance on 2009-02-16
Bugs and other issues aside, I can't take Easy Peasy seriously due to the apps it includes by default such as Songbird.  As a result of this it is pretty much the anti-netbook distribution, with 85% disk space consumed on first boot with a 4GB SSD.

I'm happy with EEEBuntu, but I'm intrigued by Debian Lenny's netbook support.  A minimal netiso install would be great for a netbook.  My only concern is somehow getting the Netbook Remix interface installed on Debian.

---

### Post by nigj on 2009-02-18
Iv tried eeebuntu standard. After installing it I used it for one whole day before I downloaded and installed easypeasy.
eeebuntu worked right out of the box for me but, my eeepc 900 had some problems  that I had with ubuntu 8.10. It didn't seem like my graphical driver could cope with my graphical hardware. Allot of graphical noise between windows changing an a pretty slow performance.
So far easypeasy seems to be working just fine.
But and there is a but. It seems like my program would like me to install eeepc all over again every time I turn on my eeepc. After loading the first side of the installation program appears. (step one of seven).

Any suggestions (I downloaded directly not torrent);)

---

### Post by ugm6hr on 2009-02-18
> **nigj said:**
> But and there is a but. It seems like my program would like me to install eeepc all over again every time I turn on my eeepc. After loading the first side of the installation program appears. (step one of seven).

Any suggestions (I downloaded directly not torrent);)

```
sudo apt-get remove ubiquity
```

---

### Post by nigj on 2009-02-18
;)What can I say TAL = Thanks allot:popcorn:

By the way how can I remove the front menu, and get a plain desk top?
;)

Found the solution my self. I went to session and disabled note book launcher. 

my following up question is how to add a new panel?

---

### Post by ugm6hr on 2009-02-18
> **nigj said:**
> my following up question is how to add a new panel?

Right-click somewhere with no launhers on existing panel -> New panel

Although I would advise against it for a netbook where screen real-estate is at a premium.

---

### Post by nigj on 2009-02-19
I`v tried that but the option you mentioned is missing. Like I said I`v deactivated netbook launcher and maximus in the session menu. Why would you not recomend to add a new panel? (might be a stupid question, but linux is still quite new to me):popcorn:

---

### Post by ugm6hr on 2009-02-19
What options do you have?

It should read: Add to panel; Properties; Delete this panel, New Panel; Help; About panels.

There is no problem with having 2 panels, but the screen size is already small; a second panel just reduces the usable space further.

---

### Post by nigj on 2009-02-19
My only options are remove from panel, move and lock to panel.;)

---

### Post by solwic on 2009-02-19
> **nigj said:**
> My only options are remove from panel, move and lock to panel.;)

You're clicking on something other than the panel then.  Find a blank spot.  Keep clicking around until you get the options listed in the previous post.

Good luck. :)

---

### Post by ugm6hr on 2009-02-19
> **jrock612 said:**
> You're clicking on something other than the panel then.  Find a blank spot.  Keep clicking around until you get the options listed in the previous post.

Indeed. You need to click on an EMPTY part of the panel.

---

### Post by Crafty Kisses on 2009-02-19
Very soon I'm going to get a Netbook, probably an Asus EEEPC, I think I'm going to go with Easy Peasy, but I'm not too sure.

---

### Post by nigj on 2009-02-20
Not a bad idea if you like to have a handy little thing to bring along. I`v tried several linux versions on my eeepc 900 and this is the one with almost no bugs. My only problem so far is to edit the panel. I`v done it with the other distros but I can`t do it with easy peasy.
Since my SSD only is a 16 GB I`v bought a 8 GB SD-card for music and stuff.

---

### Post by Tzi on 2009-04-20
I have used ubuntu-eee since soon after it was first released, simply because it was friendly.
I tried eeebuntu, but after installing it just hangs at a blank screen.

I am installing the latest version of easy-peasy as we speak, and even on the first live run, its faster than the older ubuntu-eee

I cant stand netbook remix interface, because it was so slow(now appears to be better), and didnt allow me to work as I do on every other computer... I have persisted with it though... Until now :D


Btw...after stopping netbook remix in the sessions manager...and re-loading X (ctrl-Alt-Backspace), right click on the "go home" icon (top left of your screen) and click 'remove from panel'. This will give you some unoccupied space where you can right click again, and 'add to panel' 
Scroll down until you find 'Main Menu"... click add, and close... and your done ;)
This means you still keep the window picker applet, and use no more screen space than you would running the netbook interface ;)

hmm... I spose I could just add a menu to the existing netbook interface. Will have to try both I think :)


Oh... I have an eeepc 901, XP model

---

### Post by paranoiahax on 2009-04-21
I'm really stumped. I have an Eee PC 1000, with Xandros installed. I am currently using that as I write now. I cannot stand this Operating System, I hate it as it's so limited and it's so difficult to install your own custotm software, and there is so little support for software. I have had so many issues with installing simple programs such as VLC on Xandros, and other programs too like aMSN. I've managed to set up aMSN successfully, but am yet to install VLC properly because several dependencies are missing.

So I've come to the decision to ditch this waste of an Operating System. I've had a couple of years experience with Ubuntu already, and I love the Operating System, and I've used it mainly on my main laptop. However, now I'm stumped on whether to install Easy Peasy or Eeebuntu, I really am stuck. I prefer the look of Easy Peasy because it's stayed with the traditional ubuntu themes and colour, but I hate the tabbed interface, the Netbook Remix one. That's why I've ditched that on Xandros, it's just too basic and limited.

I also want everything to work out the box and as little work to be done as possible, all my hardware such as my webcam and mic and speakers to be working would be great, as well as bluetooth and wifi.

It would be good to be able to install other applications with great ease too, because Xandros is a debian branch also, but it's so difficult to do that. 

so basically I'm asking for your advice, as so far on this thread there doesn't seem to be much of a decisive outcome, and it does seem as if Eeebuntu is more popular on the polls but that could just be because more people have used eeebuntu and not bothered with Easy Peasy.


Thanks in advance! Josh

---

### Post by ajm24019 on 2009-04-21
I use Ubuntu 8.10(using Array kernel + AHCI Scripts) on my 1000H and everything works very well.

---

### Post by JeffAtET on 2009-04-21
I've installed EasyPeasy on 2 eeepc-701, and eeepc1002ha/XP.

The girls, both 10 love EasyPeasy, vs the stock Xandros.  But it didn't work well for me.  I kept trying to tweak it to my purposes and it got very unstable.  I've installed about 20 OS's on my 1002HA including Windows 7, the rescue DVD has XP Home (sp3), tried that 3 times, fluxflux for eeepc, puppy, eeepup, damnsmalllinux, debian, Xubuntu, Ubuntu 8.04/8.10/9.04UNR, PCOSLinux9, PCOSLinux8.  and finally the EEEBUNTU-2.0 Standard, EEEBUNTU-2.0 Base.  

Ubuntu 9.04UNR looks just like EasyPeasy and worked ok on the 1002ha, but was sluggish.  Windows 7, worked great except for mapping buttons and waking from sleep.  

So far my all time favorite is ==---------> *** EEEBUNTU-2.0Base ***.  
It lets me do all my work (remote tech support via BOMGAR support) and remote server administration via ssh, email via firefox/gmail, run my accounting/billing software (Appgen Business Software in GnomeTerminal). Watch movies, download pictures from my camera... it's great for me.

But to each his/her own, I'm happy that there are so many OS's that will run on the EEE.

Yours truly,

Jeff

---

### Post by JeffAtET on 2009-04-21
Hi Paranoihax,

I really like EEEBUNTU-2.0-Base, there are 3 flavors, Standard, Remix(like easypeasy) and base.  Also, I'm installing on the eeepc-1002HA model.  All the drivers come with it and everything works, plus you have Ubuntu's standard apt-get/aptitude available.  The eee specific parts are pinned so you don't have to worry about wiping them with an upgrade.  If you want all the 'bells and whistles' EEEBUNTU2.0-Standard has them,  too many in my opinion.  But I like a clean desktop and menus and I'm happy to install just what I need.  I did have to set the sound, it's very low after the install.  The setting to change is accessible by starting 'gnome-volume-control' from the terminal, then use the sliding control for "Line Out" to set the volume to the top and click 'close', all fixed.

Have fun,

Jeff

---

### Post by paranoiahax on 2009-04-21
Hi Jeff, thanks for that advice there! I am now currently torrenting Eeebuntu standard. I like the bundles you get with it so I'd be appy ot use the standard version.

Quick question for you: how quick is the boot time on Eeebuntu? Because on Xandros it's incredibly quick, and that is feature I really like because it's impressive. I'm happy with anything under a minute though and don't expect anymore than a minute on a SSD (I've got the 1000 model).

But it does seem I am going to be using Eeebuntu. I would try out Easy Peasy if it weren't for my slow download speeds, and this is going to take me 18 hours to download the Eeebuntu ISO which is a bit of a pain.

Thanks for your swift reply though Jeff,

Para

---

### Post by Andavane on 2009-04-22
> **paranoiahax said:**
> .....

Quick question for you: how quick is the boot time on Eeebuntu? Because on Xandros it's incredibly quick, and that is feature I really like because it's impressive. I'm happy with anything under a minute though and don't expect anymore than a minute on a SSD (I've got the 1000 model).

But it does seem I am going to be using Eeebuntu. .....

Para

Just adding that this is what I found: very impressed at the fast boot time on Xandros. But I found that little by little I ran into the limitations of the program, and that somehow it seemed to be nudging me into buying something. I think Xandros has commercial ties. It ended up rather irritating. Now using eeebuntu 2.0 standard. Booting time is longer, but there's an endless universe of what you can do in it.

And at the end of the day, fast booting time shows one thing only: fast booting time.

Regards

John

---

### Post by paranoiahax on 2009-04-26
Hi John, thanks for the reply. I've now set up eeebuntu on my Asus, and it's running really smoothly and I'm impressed with it; it's very visual and looks great, and so far is far superior than Xandros in almost every way. But yeah I am very disappointed with the boot time, I think they'll be improving on that sooner or later though, but as it stands I'm happy overall with the OS, it's a nice little alternative with the Eee PC and to be honest I'd far prefer it if netbooks came pre-installed with this; it would be far easier!

---

### Post by NTolerance on 2009-04-26
Now that Jaunty has been released with near-complete support for eeepcs, both of these distros are obsolete IMHO.  They have served their purpose well.  Jaunty works works well with everything on my 900A with the exception of the touchpad, and that problem can be worked-around by changing some driver settings.

---

### Post by Bezdomny on 2009-04-30
Well you could say that regarding all Ubuntu based distro's.  Mint is going from strength to strength so I fear that the rumours of the mini distro's deaths are severely exaggerated... :P

We'll be around a while yet, as long as people continue to download and use what we create I can't see us disappearing any time soon and people do like choice, not everyone is a fan of the mucky brown.

---

### Post by sprucemoose on 2009-04-30
> **billgoldberg said:**
> eeebuntu 2 is a perfect distro for the eeepc 900.

I couldn't agree with you more.  I'm yet to find a better distro.

---

### Post by fewt on 2009-04-30
> **NTolerance said:**
> Now that Jaunty has been released with near-complete support for eeepcs, both of these distros are obsolete IMHO.  They have served their purpose well.  Jaunty works works well with everything on my 900A with the exception of the touchpad, and that problem can be worked-around by changing some driver settings.


Jaunty doesn't nearly have "near-complete" support for Eee PCs.  If they did you would get 8 hours out of your battery, and when you pressed FN-F2 your WIFI light would go on and off.

To date, you need a new kernel (one from the intel bug report for i915, or the one from array.org), you need custom xml or xorg.conf for multi-touch, mute toggling still doesn't work across all Eees, you need to add configuration lines to grub for your WIFI to go on and off (and then extra tools to toggle it), and modules to /etc/modules. The list goes on and on depending on the Eee.

Please don't mislead users into believing that 9.04 is all that for users, out of the box, because it isn't yet.  I've been redirecting people to the i915 bug report for days now who are complaining of issues with driver support.

;-)

---

### Post by Eupho on 2009-04-30
Now 9.04 is out I will stay with Ubuntu. I tried Eeebuntu and Easypeasy but allways ended up comming back to 8.04 then 8.10 with the Array.org kernel.

---

### Post by aysiu on 2009-04-30
> **fewt said:**
> Jaunty doesn't nearly have "near-complete" support for Eee PCs.  If they did you would get 8 hours out of your battery, and when you pressed FN-F2 your WIFI light would go on and off.

To date, you need a new kernel (one from the intel bug report for i915, or the one from array.org), you need custom xml or xorg.conf for multi-touch, mute toggling still doesn't work across all Eees, you need to add configuration lines to grub for your WIFI to go on and off (and then extra tools to toggle it), and modules to /etc/modules. The list goes on and on depending on the Eee.

Please don't mislead users into believing that 9.04 is all that for users, out of the box, because it isn't yet.  I've been redirecting people to the i915 bug report for days now who are complaining of issues with driver support.

;-)
Jaunty may not have near-complete support for Eees, but I just tried Easy Peasy, and the support wasn't any better, frankly.

On my Eee 701, the only thing not working (apart from the Wifi key, which I prefer to have disabled, lest I turn off my wireless by accident) is the mic in Skype (and, again, that didn't work in Easy Peasy 1.1 either).

---

### Post by vredley on 2009-04-30
9.04 is very good on the Eee 701, but only after a fair bit of tweaking. A lot of people simply don't want to install different kernels and drivers, or mess around with xorg.conf, and that's where distros like Eeebuntu come in.

Many people complain about Linux on the Eeeuser forums, because the only thing they've tried is Xandros. It's nice to be able to recommend a drop-in replacement; without these Eee-specific distros, I think a lot of Eee owners would have switched to XP.

---

### Post by NTolerance on 2009-04-30
> **fewt said:**
> Jaunty doesn't nearly have "near-complete" support for Eee PCs.  If they did you would get 8 hours out of your battery, and when you pressed FN-F2 your WIFI light would go on and off.

To date, you need a new kernel (one from the intel bug report for i915, or the one from array.org), you need custom xml or xorg.conf for multi-touch, mute toggling still doesn't work across all Eees, you need to add configuration lines to grub for your WIFI to go on and off (and then extra tools to toggle it), and modules to /etc/modules. The list goes on and on depending on the Eee.

Please don't mislead users into believing that 9.04 is all that for users, out of the box, because it isn't yet.  I've been redirecting people to the i915 bug report for days now who are complaining of issues with driver support.

;-)

Near-complete, as in everything works but the F2 function key.  Multi-touch worked out of the box for my 900A, with the exception of some erratic cursor movement which was resolved via a conf file addition.  I have yet to run into the i915 bug you're referring to.  

I'm sorry your Jaunty eeepc experience hasn't been as good as mine.  I didn't make that statement as fact, that's where the "IMHO" comes in.

---

### Post by Bezdomny on 2009-05-01
> **Hobart said:**
> I wonder if the egos of the people involved (both at the application level and distro level - array kernel/eeecontrol/easypeasy/eeebuntu) are so big that there's no hope of them working together.

I don't think ego's are playing a part in this, there are different philosophies regarding the distro's, namely the target user base.  Both distro's use the same array kernel and either eeecontrol or acpi utils. Plus, the more cooks involved the more chance that the broth will definitely be spoiled with the unavoidable politics of the user/developer base. We learn from each others mistakes and having a little friendly competition can only progress the development in the pursuit of creating a better distro.  If everyone relied on one distro then the creators would inevitably become lazy and just push releases through the door.  Alternatives and choice is what Linux is all about.  Jon and I occasionally chat regarding the distro's and share idea's and ideals. In the end we both want to give our users the best experience possible and leave the choice of what they use down to personal opinion.

Doesn't sound like big ego's to me.

---

### Post by fewt on 2009-05-01
> **NTolerance said:**
> Near-complete, as in everything works but the F2 function key.  Multi-touch worked out of the box for my 900A, with the exception of some erratic cursor movement which was resolved via a conf file addition.  I have yet to run into the i915 bug you're referring to.  

I'm sorry your Jaunty eeepc experience hasn't been as good as mine.  I didn't make that statement as fact, that's where the "IMHO" comes in.

I'm not speaking from just my experience. ;-)

[http://forum.eeeuser.com/viewtopic.php?pid=568133](http://forum.eeeuser.com/viewtopic.php?pid=568133)
[http://forum.eeeuser.com/viewtopic.php?id=65198](http://forum.eeeuser.com/viewtopic.php?id=65198)
[http://forum.eeeuser.com/viewtopic.php?id=66597](http://forum.eeeuser.com/viewtopic.php?id=66597)
[http://forum.eeeuser.com/viewtopic.php?id=63814](http://forum.eeeuser.com/viewtopic.php?id=63814)
[http://forum.eeeuser.com/viewtopic.php?pid=568029](http://forum.eeeuser.com/viewtopic.php?pid=568029)
[http://forum.eeeuser.com/viewtopic.php?id=67121](http://forum.eeeuser.com/viewtopic.php?id=67121)
[http://forum.eeeuser.com/viewtopic.php?id=66153](http://forum.eeeuser.com/viewtopic.php?id=66153)
[http://forum.eeeuser.com/viewtopic.php?pid=567373](http://forum.eeeuser.com/viewtopic.php?pid=567373)
[http://forum.eeeuser.com/viewtopic.php?pid=566684](http://forum.eeeuser.com/viewtopic.php?pid=566684)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/349314](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/349314)

etc.

---

### Post by stanjam on 2009-05-01
I have Eeebuntu, Puppy, and Backtrack 4 on my eee pc 1000.  Love it!  What I really like about Eeebuntu is that it comes in base, standard, and nbr, so you can choose the one that works best for you, all based on 8.10.  Eeebuntu 3.0 will be out soon, based on 9.04.  Also, they will be coming out with an LXDE version, which is awesome!  Using LXDE and Wicd makes the eee pc experience so much better!  Things run faster, battery lasts longer!

---

### Post by Guitaraholic on 2009-05-01
Hi Guys,

the netbook OS is far from dead... with just over a year since first release EEEbuntu Has came on leaps and bounds and ALOT of work is going on in the backgroud to make it into a truly different entity then simply Ubuntu+.

> * I'm rather disappointed with its lack of both a top level metapackage like 'ubuntu-desktop' for its various 'flavors' (standard, netbook, base). Mainline Ubuntu does this well (ubuntu/kubuntu/xubuntu/edubuntu), any fork has no excuse to not follow suit.

After we release version 3 in the coming weeks we will be looking at ways for meta-packages to function correctly so that future updates can be installed using the dist upgrade options and installation of different desktops is easier.

> * I'm frustrated by the possibility of collision between the separate eeepc-specific control solutions [the 'array' kernel's asus_eee kernel module conflicts and interferes with the 'eee-control' userspace daemon

After gaining the Expertise of FEWT into our team we now have the eeepc-acpi utilities which works on all eeemodels so far. Also a tray app has been developed to replace eee-control for v3 which will be functional by default.

[QUOTE]* All soluitons have mediocre taskbar applets ... both the applet and something else seem to try to take over brightness controls.
    * The Array kernel module w/o the userspace daemon seems to not let me raise brightness to maximum[QUOTE]

The brightness issues is gained from its parent Ubuntu- I have has the same issues in ALL of the jaunty beta's on my eee as in eeebuntu 2
    
[QUOTE}* Still trying to get full power management to work. EEE900A - I read a note on the eee-control guy's site that on some models "the BIOS hides acpi info" or something similar.{/QUOTE}

eee-control is a separate project to eeebuntu and we have now adopted the eeepc-acpi util and eeepc-tray into the project. 

Ourselves and easy peasy have similar goals but simply different ways of getting there. Suggesting its down to ego's is like saying Ubuntu shouldn't exist and we should all just work on Debian rather than customize it at all.


I would speak to adamm about the ideas of passing his work into the mainline kernel.

Go EEEbuntu!

---

### Post by NTolerance on 2009-05-01
> **fewt said:**
> I'm not speaking from just my experience. ;-)

[http://forum.eeeuser.com/viewtopic.php?pid=568133](http://forum.eeeuser.com/viewtopic.php?pid=568133)
[http://forum.eeeuser.com/viewtopic.php?id=65198](http://forum.eeeuser.com/viewtopic.php?id=65198)
[http://forum.eeeuser.com/viewtopic.php?id=66597](http://forum.eeeuser.com/viewtopic.php?id=66597)
[http://forum.eeeuser.com/viewtopic.php?id=63814](http://forum.eeeuser.com/viewtopic.php?id=63814)
[http://forum.eeeuser.com/viewtopic.php?pid=568029](http://forum.eeeuser.com/viewtopic.php?pid=568029)
[http://forum.eeeuser.com/viewtopic.php?id=67121](http://forum.eeeuser.com/viewtopic.php?id=67121)
[http://forum.eeeuser.com/viewtopic.php?id=66153](http://forum.eeeuser.com/viewtopic.php?id=66153)
[http://forum.eeeuser.com/viewtopic.php?pid=567373](http://forum.eeeuser.com/viewtopic.php?pid=567373)
[http://forum.eeeuser.com/viewtopic.php?pid=566684](http://forum.eeeuser.com/viewtopic.php?pid=566684)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/349314](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/349314)

etc.

For those that are having problems with Jaunty I definitely recommend EEEbuntu.  It was my EEE distro of choice prior to Jaunty.  

I'd like to see a Jaunty-EEEbuntu hybrid that incorporates the under the hood improvements of EEEbuntu but keeps the Jaunty experience intact.  I was not a fan of the default look and feel of EEEbuntu base.  It was easy enough to add the standard Ubuntu themes back into EEEbuntu, but I think they should be there by default.  

One thing that puzzles me is storage space consumed by the OS.  My 900A has the crappy stock 4GB SSD, so this is an obvious concern.  EEEbuntu base, which is supposed to be stripped down to the core, takes up about 2GB of the SSD.  Stock Jaunty with all the non-notebook centric apps installed takes up around the same amount of space.  I wonder why this is.  

At any rate, EEEbuntu is a great OS for the EEEPC, and I can easily recommend it to anyone.

---

### Post by ufugu on 2009-05-01
I've tried the default Xandros, UNR, Eeebuntu, Easy Peasy, Pupeee Crunchee and Mandriva on my eee 900.

You know what worked perfectly with a minimum of effort, had the best selection of installed apps, with all the eee buttons and the webcam working out of the box?

Ubuntu Jaunty 9.04, full install. :guitar: Works like a dream and is as zippy as any of the others.

---

### Post by BeBoBli on 2009-05-02
> **NTolerance said:**
> For those that are having problems with Jaunty I definitely recommend EEEbuntu.  It was my EEE distro of choice prior to Jaunty.  

I'd like to see a Jaunty-EEEbuntu hybrid that incorporates the under the hood improvements of EEEbuntu but keeps the Jaunty experience intact.  I was not a fan of the default look and feel of EEEbuntu base.  It was easy enough to add the standard Ubuntu themes back into EEEbuntu, but I think they should be there by default.  

So I've noticed this trend where it seems like people are completely oblivious of UNR. The release didn't have an official torrent and kind of just went under everyone's radar. Which is probably a good thing, because it's pretty hit or miss if it works with your net-top well. However, I do believe the 900A was a pretty well supported one. I've got one (900 4GB) as well, but it's still heading back to me for repairs. I installed on a 16GB 900 and it was hell.

---

### Post by ppyo on 2009-05-05
I got an EeePC 701 (4G Surf) from eBay, and tried Xandros for a while. It was just ok, but not what I needed, so I started looking for a replacement. I installed UbuntuEee, and I was satisfied with it, but wanted to have a netbook interface, as the regular Ubuntu interface is kind of too small for my tired old eyes :). I learned about Eeebuntu 2.0 NBR and installed it. It's perfect!
Yesterday I downloaded Ubuntu 9.04 NBR on a USB stick, and it looks just as well as Eebuntu NBR 2.0. I am impatiently awaiting the release of NBR 3.0, as that will be the final showdown: Eeebuntu NBR 3.0 vs Ubuntu 9.04 NBR. The winner will reside in my EeePC.

Long live Linux in EeePC's!

---

### Post by piousp on 2009-05-05
Ubuntu Netbook Remix is awesome. I tried it in my eeepc 900A after Eeebuntu... UNR is what i use now

---

### Post by NTolerance on 2009-05-05
> **BeBoBli said:**
> So I've noticed this trend where it seems like people are completely oblivious of UNR. The release didn't have an official torrent and kind of just went under everyone's radar. Which is probably a good thing, because it's pretty hit or miss if it works with your net-top well. However, I do believe the 900A was a pretty well supported one. I've got one (900 4GB) as well, but it's still heading back to me for repairs. I installed on a 16GB 900 and it was hell.

I'm holding off on UNR until Maximus can completely deal with all types of windows, especially those found in the prefs/admin section.

---

### Post by Guitaraholic on 2009-05-13
FYI 


We are releasing a new version of Eeebuntu hopefuly friday 15th May. For teaster shots and info regarding the launch please visit [http://forums.eeebuntu.org](http://forums.eeebuntu.org)

---

### Post by maestrobwh1 on 2010-01-10
> **wolfen69 said:**
> i would have liked to put regular eeebuntu on mine, but the 2G surf is just too small to put a regular distro on. but i'm happy with my cli install. it has on it only what i want and no more. wicd, firefox, terminal, leafpad, vlc, and 3 games.

I assume the Surf has an SD card slot?  You can install eeebuntu or easy peasy there as I have then follow this thread to make it faster:
[http://stevehanov.ca/blog/index.php?id=48](http://stevehanov.ca/blog/index.php?id=48)

---

### Post by Sef on 2010-01-10
Moved to Recurring Discussions.

---

### Post by luca.cappelletta on 2010-03-26
Hi

at this development stage, which is the distro would you suggest ?
easypeasy, Eeebuntu or UNR ?

any experience using eeepc 1201HA ?


cheers

---

### Post by Guitaraholic on 2010-06-14
well eeebuntu is changing : [http://eeebuntu.org](http://eeebuntu.org)  :)

---

### Post by formaldehyde_spoon on 2010-06-14
I tried to install Eeebuntu on my 1005PE but it wouldn't play nice during install, so I installed vanilla 10.04 - very happy with it after a bunch of power saving tweaks.

---

### Post by ohooligan on 2010-12-06
> Some posts from people who have actually tried both would be helpful.I've had an ASUS eee 900 for over 2 years.  I found the supplied OS (Xandros) to be very frustrating, especially its treatment of wireless networks.  Which surprised me, I'd imagined that the primary purpose of the thing was to connect to wifi in different places with ease, but on my travels - and even at home - I found it tedious and sometimes just plain impossible to get online.  I finally decided to Do Something about it, and went searching for an alternative OS (Dec 2010).

I found eeebuntu being rebranded as Aurora, and ubuntu eee rebranded as EasyPeasy.

I tried both, downloading on a desktop computer, and making a bootable USB stick.

eeebuntu/Aurora latest version seems to be eeebuntu-3.0.1-nbr (I chose the NBR variant for no good reason, except it seemed like it should be better tailored for a netbook).

Ubuntu eee/EasyPeasy latest version seems to be EasyPeasy-1.6

First I tried eeebuntu.  Booting from USB worked fine, but the desktop was surprisingly slow, visibly lagging behind on mouse movements and clicks.   I connected to LAN (wired) and tried Firefox, that worked.  I didn't try wireless as there was no available
wifi network.

I couldn't find the webcam, at least no application that would let me test it.  Sound worked, but when I ran Skype I couldn't do a test call because it failed to find the sound device (sorry, don't recall exact message).  I found this in one of the logs:

> process 'skype.real' is using obsolete setsockopt SO_BSDCOMPAT
That concluded my trial of eeebuntu.  Skype not working "out of the box" is for me a fatal error.

Next up, Easy Peasy.   Same deal to make a bootable USB and boot it up.  Much better desktop, no problems with lag.  This time I was in range of my home wifi network, and I connected with remarkable ease, and launched Firefox to verify that I really was on the Internet.  Then I found an app that let me play with the webcam.  Then I tried Skype, and successfully made a test call, everything worked exactly as it should.  Lastly I made a real Skype video-call, which worked just fine, including fullscreen.

That concluded my trial of EasyPeasy, and I went ahead and installed it, overwriting the previous OS and accepting the default partitioning it offered.  Rebooted and set up a user account for my wife, shut it down and left it for her to try.  Later I found her watching something on YouTube, completely unaware of any issues (like, connecting to wifi).  She found it just as easy to use as her MacBook.

Verdict:  EasyPeasy good, eeebuntu bad (based on the versions I tried).

I should qualify that a little, though:  What happened was I very quickly found a fatal flaw in eeebuntu (Skype).  Fatal for my needs, that is.  EasyPeasy may also have a fatal flaw, I just haven't hit it yet.   Also, I made no attempt to find out if there was a fix to the Skype problem, because I'm not that interested - I have nothing invested in eeebuntu except for the short evaluation session.  Finding no such obvious problem with EasyPeasy means I'm going to be investing a lot more time in it, and no doubt I'll be more willing to hunt for fixes to any problems that I do find.

I've added this comment because I see there are eeebuntu developers on this forum, and I don't want to be offensive.  It's not pleasant to have your best efforts dismissed out-of-hand, probably due to something trivial that you could fix in a minute, had you noticed it yourselves.  Unfortunately, since computers became consumer appliances, the end user (me included) has very little tolerance for things that don't Just Work.

---

### Post by Plumtreed on 2010-12-07
Thanks for the 'review', timely for me since I have recently bought a 'new' eeePC 700. I have Peppermint ICE running on a USB drive/stick and it runs very well....suits me because I lean heavily on Cloud for accounting and documents...suggest you look at Peppermint One or the ICE varient.

I will try 'Easy Peasy' when I get home from my travels....downloading is too difficult via shaky USB Broadband.

Erm..what about Ubuntu Netbook Version??

---

