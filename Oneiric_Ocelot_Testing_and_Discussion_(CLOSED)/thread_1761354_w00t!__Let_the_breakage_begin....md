---
title: "w00t!  Let the breakage begin..."
date: 2011-05-18
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by VinDSL on 2011-05-18
Today's updates (17-May-2011) totally blitzed my UbuOO desktop.  LoL!

More things are not working, than working.

I guess I'd better start backing up my important data before it's too late.

I love living life on the edge!

Anyway, best of luck, to all of you.  I fear the storm is upon us...  ;)

---

### Post by MacUntu on 2011-05-18
Working relatively fine here. Just make sure you have gnome-themes and gnome-themes-standard installed if you're on Intel graphics.

---

### Post by Quackers on 2011-05-18
One of my installs is fine while the other is unusable :-)  Same updates, same system, same graphics card - go figure :-)

---

### Post by zika on 2011-05-18
> **VinDSL said:**
> Today's updates (17-May-2011) totally blitzed my UbuOO desktop.  LoL!

More things are not working, than working.

I guess I'd better start backing up my important data before it's too late.

I love living life on the edge!

Anyway, best of luck, to all of you.  I fear the storm is upon us...  ;)[http://ubuntuforums.org/showthread.php?t=1760626](http://ubuntuforums.org/showthread.php?t=1760626)

---

### Post by VinDSL on 2011-05-18
Interesting!  Thank you, zika!

Well... I'm on 10.10 right now.  168 updates awaited me.  LoL!  

I was shocked to find that the newly updated Opera 11.11 is working.

Heh!  I have tried to like Opera for many years, but this the first time that everything has worked -- the bookmarks are even sorted correctly.

Soooo, maybe it was a good thing that UbuOO decided to become cantankerous.  Odd that it happened on a full moon.  Perhaps it's cosmic.

I'll wait and see if the next couple of update cycles work a treat.  If not, I'll patiently look forward to installing Alpha 1.

---

### Post by zika on 2011-05-18
> **VinDSL said:**
> Interesting!  Thank you, zika!

Well... I'm on 10.10 right now.  168 updates awaited me.  LoL!  

I was shocked to find that the newly updated Opera 11.11 is working.

Heh!  I have tried to like Opera for many years, but this the first time that everything has worked -- the bookmarks are even sorted correctly.

Soooo, maybe it was a good thing that UbuOO decided to become cantankerous.  Odd that it happened on a full moon.  Perhaps it's cosmic.

I'll wait and see if the next couple of update cycles work a treat.  If not, I'll patiently look forward to installing Alpha 1.
Try [http://snapshot.opera.com/unix/alpha_11.50-1009/](http://snapshot.opera.com/unix/alpha_11.50-1009/) ...

---

### Post by cecilpierce on 2011-05-18
What a mess! Time to rename Oneiric to Ornery
:P

Has any body noticed the Home folder opens on startup ?

---

### Post by Quackers on 2011-05-18
> **cecilpierce said:**
> What a mess! Time to rename Oneiric to Ornery
:P

Has any body noticed the Home folder opens on startup ?

Yep, does that here too, with a black background. Everything is clickable, but once used it won't close :-)

Incidentally I have gnome3/gnome-shell running on another Oneiric installation and that's fine. :confused:

---

### Post by afv on 2011-05-18
> **cecilpierce said:**
> What a mess! Time to rename Oneiric to Ornery
:P

Has any body noticed the Home folder opens on startup ?

Check the topic [Gnome3 packages in Oneiric repos](http://ubuntuforums.org/showthread.php?t=1760490). :)

---

### Post by cecilpierce on 2011-05-18
> **Quackers said:**
> Yep, does that here too, with a black background. Everything is clickable, but once used it won't close :-)

Incidentally I have gnome3/gnome-shell running on another Oneiric installation and that's fine. :confused:

Same here, too much to mention
:mad:

---

### Post by kansasnoob on 2011-05-18
It's not a storm. The total transition from gnome2 to gnome3 is going to require a lot of patience :D

I expect to see tons of breakage during our Alpha stages this time around.

Stock up on CD's and/or your preferred installation media ;)

Oh, and maybe be some Valium or ***** :lolflag:

Eeerm, why is the drug pronounced zanax blocked :confused:

Too many x rated minds?

---

### Post by julianb on 2011-05-18
I am using Lubuntu Oneiric. So far no breakage. Apt is upgrading the kernel and several other things - breakage may be just around the corner.

---

### Post by VinDSL on 2011-05-19
Still, no Oneiric goodness, on today's update cycle.

Tomorrow is a new day...  ;)

---

### Post by Johnsie on 2011-05-19
I  got 57mb of downloads coming this morning. I'm using gnome classic on the test vm and yesterday's update got rid of the theme in gnome panel. It looks like todays changes are mostly to do with networking.

---

### Post by Squonk07 on 2011-05-19
I just checked about half an hour ago and I got the dreaded Partial Update message. I've learned my lesson with those the hard way and will be waiting until that's sorted out before updating again. This thing's broken enough already.

I'm testing on VirtualBox and am keeping my VM open in a separate workspace. Annoyingly the window kept migrating over to my main workspace. I traced this to whenever Oneiric would blank the screen after a period of inactivity. I changed my Power and Screensaver settings to stop this from happening and now the window stays put. Anybody else able to verify this weird behavior?

---

### Post by julianb on 2011-05-19
I'm testing on the hardware directly rather than in a VM.

So the part of my system that broke today is wireless access (network-manager-gnome). Went and hooked up to wired internet, and look at that, apt was able to download a new version of network-manager-gnome and the wireless works just fine again.

---

### Post by VinDSL on 2011-05-19
> **Squonk07 said:**
> I just checked about half an hour ago and I got the dreaded Partial Update message.[...]

I'm testing on VirtualBox and am keeping my VM open in a separate workspace. Annoyingly the window kept migrating over to my main workspace.[...]

Anybody else able to verify this weird behavior?
I installed the 2.6.36-natty kernel, so I can (more easily) see what's going on during boot.

My two biggest problems are, the boot process wants to place runtime data in /run/udev (which doesn't exist) and...

When I do an update (Synaptic / apt-get) I get mad dependency errors.

Experientially, I have a *feeling* that this won't get sorted out until Alpha 1...  ;)

---

### Post by VinDSL on 2011-05-20
OO is getting uglier & angrier by the day, but it's still hanging in there.

Latest update cycle - lastest nVidia current - 2.6.39 kernel:

```

vindsl@Zuul:~$ date && uname -s -r && unity --version && cat /etc/lsb-release && /usr/lib/nux/unity_support_test -p
Fri May 20 19:46:40 MST 2011
Linux 2.6.39-020639-generic
unity 3.8.12
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu oneiric (development branch)"
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/AGP/SSE2
OpenGL version string:  2.1.2 NVIDIA 270.41.19

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          yes
vindsl@Zuul:~$ 

```

Dependency problems continue to plague my install, but I'll keep updating it, 'til it 'black screens' on me.  :)

---

### Post by VinDSL on 2011-05-21
Spoke too soon.  LOL!

Now, we're getting somewhere...


[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-25-may-2011(600x480).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-25-may-2011.png")[/INDENT]


Bring on the breakage!  

I'm reinvigorated now...  :D


**[COLOR="Red"]*[/COLOR]** **EDIT**:  Dependency probs appear to be gone!  Everything is installing / updating just fine, now.  Yeah, Team!

---

### Post by 3vi1 on 2011-05-21
What are the screenlets/desklets you're using on the right side there?  That looks pretty nice.

---

### Post by dino99 on 2011-05-21
> **3vi1 said:**
> What are the screenlets/desklets you're using on the right side there?  That looks pretty nice.

its conky
[http://translate.google.com/translate?js=n&prev=_t&hl=fr&ie=UTF-8&layout=2&eotf=1&sl=fr&tl=en&u=http%3A%2F%2Fvince.geek.free.fr%2Findex.php%2Fconky2%2F](http://translate.google.com/translate?js=n&prev=_t&hl=fr&ie=UTF-8&layout=2&eotf=1&sl=fr&tl=en&u=http%3A%2F%2Fvince.geek.free.fr%2Findex.php%2Fconky2%2F)

[http://ubuntuforums.org/showthread.php?t=869328&page=267](http://ubuntuforums.org/showthread.php?t=869328&page=267)

---

### Post by xeizo on 2011-05-22
Well, it's pretty broken right now, lightdm is about the only display manager working of those of the latest kind, since I also run Gnome-shell ppa. And the only desktop lightdm is able to bring up is the said Gnome-shell. 

Gnome-shell works, it's sort of usable anyway.

But not fully stable, I can be thrown out to a command prompt any time. WooHoo, Breakage!  :D

Gdm 3.0 can't login to ANY desktop, Kdm can only login to KDE or Gnome Classic(which ain't that classic anymore with all Gnome 3-files already in it).

Both Unity 3D and 2D are currently not accessible from any of the display managers, this happened about right now. Gdm worked a few hours earlier when it was still 2.3**.

---

### Post by chrismine on 2011-05-22
My desktop is working with Metacity on Gnome 3 and I also installed Evolution 3 from ppa. Need to click on the desktop folder to show desktop icons but otherwise everything seems to work fine.

---

### Post by VinDSL on 2011-05-25
WoW!  That was exciting!!!  :)

Work up, this morning (4 hours sleep).  Had to be to work in 45 minutes...

Did a quick update, and was met with a black desktop on reboot - no icons - no nothing.

During my meal period at work (lunch, supper whatever YOU call it), I checked into these forums and saw that libgdk-pixbuf2.0-0 was the culprit.

I checked the bug reports and saw that 'they' had already issued a fix.

When I got home, I booted into my (now) totally black UbuOO install, then:

[LIST]
[*]Ctrl-Alt-F1
[*]Log in
[*]sudo apt-get update && sudo apt-get upgrade
[*]Numerous updates were waiting
[*]Installed them
[*]Reboot
[/LIST]

Bingo!  Back up n' running!

My, how I love dev branches.  Ppl don't know what they're missing.

Okay, bring on the next breakage!  I'm ready...  :D

---

### Post by satanselbow on 2011-05-25
> **VinDSL said:**
> Okay, bring on the next breakage!  I'm ready...  :D

Thing is VinDSL that yesterdays updates played merry hell with Natty as well... I must have updated my G3S natty at completely the wrong time as it broke big style but G3S Oneiric survived the storm just fine :D

Now which release is the development one???? :D

---

### Post by VinDSL on 2011-05-25
> **satanselbow said:**
> Now which release is the development one???? :D
Funny you should mention that...

I like Oneiric better than Natty already, warts n' all. And, that's no bull!

Been thinking about it for a week.  I was just afraid to say it 'out loud'...  :D

---

### Post by VinDSL on 2011-05-25
2nd surprise of the day...

I've been updating my install, every hour or so.

After the last cycle, Nautilus doesn't auto-start on every boot / restart!

LoL!  That was irritating...  :)

---

### Post by meborc on 2011-05-25
> **VinDSL said:**
> 2nd surprise of the day...

I've been updating my install, every hour or so.

After the last cycle, Nautilus doesn't auto-start on every boot / restart!

LoL!  That was irritating...  :)

It is better not to upgrade more frequently than once per day. Nightly builds usually roll out in waves and when you try upgrading some packages while the dependencies have not yet been resolved (still building) you can get unto trouble.

I mean into trouble that is not related to you having the bleeding edge, but related to the upgrade process itself

At leas this is what I have witnessed over the dev cycles I have participated in.

---

### Post by Squonk07 on 2011-05-25
You can't say it hasn't been interesting so far. Well, actually you could, but at least there was some semi-exciting breakage yesterday. Not losing one's head in a crisis goes a long way toward fixing things. So does knowing how to use the Terminal. :D

---

### Post by satanselbow on 2011-05-25
Does being a dumb @£$ when running through the Fed15 installer count as an OO breakage?

... hell yeah! 

All sing-a-long-now...


"Heaven, I'm in breakage heaven,
and it won't get fixed with an apt-get dist-upgrade..."

... more verses later :popcorn:

---

### Post by chrismine on 2011-05-25
> **satanselbow said:**
> Does being a dumb @£$ when running through the Fed15 installer count as an OO breakage?

... hell yeah! 

All sing-a-long-now...


"Heaven, I'm in breakage heaven,
and it won't get fixed with an apt-get dist-upgrade..."

... more verses later :popcorn:

Maybe careless....

---

### Post by chrismine on 2011-05-25
I have a usable desktop now, were only able to login to a semi usable unity2d yesterday after gnome-session not upgrading. Interesting it is the first time I was able to get unity 2d since I installed it a while ago.

Now running Gnome3 with unity, working nicely except window borders not working properly. Also running Evolution 3 with no known issues. Evolution 3 crashed when I was logged in unity2d but is to be expected, I think.

---

### Post by seeker5528 on 2011-05-25
> **VinDSL said:**
> 2nd surprise of the day...

I've been updating my install, every hour or so.

Every hour is a bit excessive.

Typically I update once in the morning and depending on what's going on often once in the afternoon.

If something significant is borked, I might check for updates additional times, but not so much.

Plus if everybody checked for updates every hour, I hate to think what the load on the servers would be. :P

Later, Seeker

---

### Post by Squonk07 on 2011-05-25
I just update whenever it occurs to me I haven't in a while. Usually it comes out to at least once or twice a day. I keep my OO install open in VB in a separate workspace and switch over to it when I reach a lull in my "workload" (I'm on summer break, so no actual work). When something borks the system I boot into the recovery console and keep updating until it gets fixed.

---

### Post by VinDSL on 2011-06-10
Well...

I *feel* like I've died, and gone to heaven.  :D

I'm typing this in classic mode (UbuNN Alpha 1 install on UbuOO repos).  

"Classic" is throwing an error message, at boot, about not being able to load Gnome3, but it still works.  LoL!

Unity is totally borked.  UbuOO is holding back Compiz updates, and the old Compiz is using 100% of the CPU(s) - sitting idle at the desktop.

Linux 2.6.39 is still working.  I've read horror stories about 3.0 - glad I didn't install it.

Sooo, I'm going to sit under the cork tree, and lick my wounds for a few days.

If things don't clear up by the weekend, I'm going to wipe the partition and install UbuOO Alpha 1.

I don't know about you, but this is turning into a royal PITA...

Sweet challenge, though!  ;)

---

### Post by Harry33 on 2011-06-10
> **VinDSL said:**
> Well...

I *feel* like I've died, and gone to heaven.  :D

I'm typing this in classic mode (UbuNN Alpha 1 install on UbuOO repos).  

"Classic" is throwing an error message, at boot, about not being able to load Gnome3, but it still works.  LoL!

Unity is totally borked.  UbuOO is holding back Compiz updates, and the old Compiz is using 100% of the CPU(s) - sitting idle at the desktop.

Linux 2.6.39 is still working.  I've read horror stories about 3.0 - glad I didn't install it.

Sooo, I'm going to sit under the cork tree, and lick my wounds for a few days.

If things don't clear up by the weekend, I'm going to wipe the partition and install UbuOO Alpha 1.

I don't know about you, but this is turning into a royal PITA...

Sweet challenge, though!  ;)


You should add to that the removal of gdm and installation of the new lightdm with the latest glib2.0 packages. Then you do not have Unity no more, just a black screen without a working display manager.
:guitar:

---

### Post by VinDSL on 2011-06-10
> **Harry33 said:**
> You should add to that the removal of gdm and installation of the new lightdm with the latest glib2.0 packages. Then you do not have Unity no more, just a black screen without a working display manager.
:guitar:
I cannot believe 11.10 it still working, in classic mode!

It isn't any worse than running Windows 7...  :D

---

### Post by cariboo on 2011-06-10
The only thing that works on my system at the moment is Unity 2D, Unity 3D just shows the background, Gnome-shell seems to work, but then I get the oops screen when I try to do anything, I also get the oops screen in gnome-shell fallback mode. I haven't tried the classic mode lately, but I assume it won't work properly either.

---

### Post by mc4man on 2011-06-10
> Unity is totally borked. UbuOO is holding back Compiz updates, and the old Compiz is using 100% of the CPU(s) - sitting idle at the desktop.
Maybe you've fooled around a bit too much.. 
The compiz updates (3) of a few days ago should go thru fine, just a few bug fixes and some housekeeping.
Otherwise here unity is working fine, really just natty+some bug fixes.
 Some of what was missing previously has been returned, including the global menus which I've no real use for except nautilus's one on desktop focus, some small things will probably never return.

---

### Post by wojox on 2011-06-10
> **mc4man said:**
> Maybe you've fooled around a bit too much.. 
The compiz updates (3) of a few days ago should go thru fine, just a few bug fixes and some housekeeping.
Otherwise here unity is working fine, really just natty+some bug fixes.
 Some of what was missing previously has been returned, including the global menus which I've no real use for except nautilus's one on desktop focus, some small things will probably never return.

Same here. With the exception that when I installed Gnome-Shell it ate Unity beginning of last week everything has been great since.

---

### Post by VinDSL on 2011-06-10
> **mc4man said:**
> Maybe you've fooled around a bit too much.[...] 

The compiz updates (3) of a few days ago should go thru fine[...]

> **wojox said:**
> Same here.[...]
This is what I've been seeing, for the past several days...

```

The following packages have been kept back:
  compiz compiz-core compiz-gnome compiz-plugins compiz-plugins-main
  libdecoration0 seahorse unity unity-common
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.


```


> **cariboo907 said:**
> I haven't tried the classic mode lately, but I assume it won't work properly either.
Surprisingly, it's working quite well.

Weird, huh?  :)

---

### Post by mc4man on 2011-06-10
> This is what I've been seeing, for the past several days...
use synaptic

---

### Post by VinDSL on 2011-06-10
> **mc4man said:**
> use synaptic
Hrm...  Interesting!

Synaptic fixed the broken packages and allowed me to update Compiz et al.  Seahorse, is the only one being held back now, but...

Now I'm in the same boat as cariboo907:

> **cariboo907 said:**
> **[COLOR="Blue"]Unity 3D just shows the background[/COLOR]** [...]

At least that's a start.  Thanks for the suggestion!  ;)

---

### Post by mc4man on 2011-06-10
> Now I'm in the same boat as cariboo907:
Quote:
Originally Posted by cariboo907 View Post
Unity 3D just shows the background [...]

I'd open a terminal and run unity --reset and see if anything interesting happens. (unity is enabled?
or run ccsm from terminal and see what plugins load/check the tail end of .xsession-errors ect.

---

### Post by Bowmore on 2011-06-10
Same here, just had a background, no panel or launcher.

I downgraded these two packages to this version and got Unity back ;)
- compiz-plugins-main version 0.9.4+bzr20110527-0ubuntu2
- compiz-plugins-main-default version 0.9.4+bzr20110527-0ubuntu2

---

### Post by matthewgreyling on 2011-06-10
> **Bowmore said:**
> Same here, just had a background, no panel or launcher.

I downgraded these two packages to this version and got Unity back ;)
- compiz-plugins-main version 0.9.4+bzr20110527-0ubuntu2
- compiz-plugins-main-default version 0.9.4+bzr20110527-0ubuntu2
This saved me today.  Thanks

---

### Post by Bowmore on 2011-06-10
Fixed by version 0.9.4+bzr20110527-0ubuntu4 now in the repos.

---

### Post by mc4man on 2011-06-10
VinDSL - you should be ok now - poor timing, you upgraded all your compiz just about when the 2 new (bad) main & main-default came up.

Anyway - because you're using a 1GB/nvidia like me here on this machine - a heads up - 

The libcairo2 packages are updating to go back to using the --enable-gl option

If you remember this was never fixed in natty, the option, (useful for only wayland), was removed.
So if you upgrade libcairo2 today you'll go back to the 500+ MB in use at login deal...
(going to 're-open' the bug and revert or re-build cairo here for the moment

---

### Post by VinDSL on 2011-06-11
> **mc4man said:**
> VinDSL - you should be ok now - poor timing, you upgraded all your compiz just about when the 2 new (bad) main & main-default came up.[...]
I'm faced with a conundrum.

The present state of affairs isn't working - that is obvious.

I can wait it out - go backwards - or go forwards.  Those are my immediate choices.

Hrm... 

I really don't want to go backwards, pinning things, et cetera.

Alpha 1 doesn't sound too appealing either.

Chaos and mayhem are fun, but they never last.

I'm inclined to do nothing, actually.  :D

---

### Post by cariboo on 2011-06-11
I had several other problems besides the ones I mentioned in my earlier post, so I did a fresh install using the June 10th live iso. I can now use Unity 3D again, as well as Unity 2d and classic mode. I installed gnome-shell, but it still crashes on my system, and I was back to just seeing the background in Unity.  Purging gnome-shell and a reboot fixed the Unity problem. The one thing I didn't do was reboot after installing gnome-shell, so I'm not sure if that was the the problem, I'll re-install gnome-shell and reboot, to see if that solves the problem.

---

### Post by mc4man on 2011-06-11
> I'm inclined to do nothing, actually.
As I remember you seemed to be ok using the swap. For me that's not acceptable, so will have to see what happens.
It's almost 100% that gl support will stay in cairo this time. (egl1*, ect.

If you want a little possible breakage than open any folder with something other than nautilus, (like a folder of music with a player), from the context menu
While it won't affect nautilus directly this time, sooner or later it will... (easily fixed, but again will lead newer users to some confusion

---

### Post by VinDSL on 2011-06-11
> **cariboo907 said:**
> **[COLOR="Blue"]I did a fresh install using the June 10th live iso.[/COLOR]** I can now use Unity 3D again, as well as Unity 2d and classic mode.[...]
I think I'll do that, after I get a pot of coffee in me, and update my Facebook account - first things first, you know?  :D

I love running dev releases - and I don't mind breakage.  It's all part of the fun IMO.

Personally, I try to work inside "the system" as much as possible.

For the most part, I run the default proggies, and latest updates from the official repos.

My "thing" is making Ubuntu look visually appealing - custom fonts - custom themes - custom icon sets, et cetera.

Anyway, it doesn't do anybody, any good, if testers (like myself) are using a patched and mod'ed version of Natty, turned Oneiric.

Soooo, I guess today is the day, to wipe my root partition and install the "real thing".  ;)

---

### Post by 23dornot23d on 2011-06-11
I have just done the same as my 64 bit system was a upgrade - but no sound.
Will now see if that is the same from the fresh install .....

Now completely clean .... 64 bit system .... 

except for a couple of things  .....

aptitude safe-upgrade
aptitude install cairo-dock
aptitude install gnome-shell
aptitude install e17

apt-get remove firefox-globalmenu
apt-get remove indicator-appmenu
apt-get remove ubuntuone-client (dont use it or banshee - slows everything down too much too)

[IMG]http://img641.imageshack.us/img641/3774/screenshot1gj.png[/IMG]

Never going to look any cleaner ....works ok in 2d now too .... network is up ....

the Alt+F2 is back (command line input)
Ctrl+Alt+t (terminal)

[IMG]http://img405.imageshack.us/img405/6051/screenshot5sc.jpg[/IMG]

What next .... compiz and 3D

ok no flash ..... for 64 bit so add

conky works too .... calendar messes up sometimes but not sure why ... is ok on some of my systems

[IMG]http://img30.imageshack.us/img30/1214/screenshot7xn.jpg[/IMG]

---

### Post by VinDSL on 2011-06-11
> **23dornot23d said:**
> I have just done the same as my 64 bit system was a upgrade - but no sound.

Will now see if that is the same from the fresh install .....
Nice!

I'm locked n' loaded - and ready to pull the trigger.  :D


[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-11-jun-2011(6)(600x480).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-11-jun-2011(6).png")[/INDENT]


I just *need* to pry myself away from Facebook, for a few hours...  ;)

---

### Post by 23dornot23d on 2011-06-11
> 
Nice!

I'm locked n' loaded - and ready to pull the trigger.  :grin:

Looking forward to seeing what you do with the new system too ...... see you have gone 32 bit .... that one I had a few more problems with ...... than the 64 bit one ......

Its fun to try though on a clean partition ..... 

 .... and .... they are improving it all the time ..... ;)

---

### Post by VinDSL on 2011-06-15
Oh, my!  

Look who's back from the grave (after the last update cycle):


[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-15-jun-2011(2)(600x480).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-15-jun-2011(2).png")[/INDENT]


UbuOO is like a cat with nine lives...  :D
> 
"A cat has nine lives. For three he plays, for three he strays, and for the last three he stays." - *English/American proverb*



I swear... I thought my pre-Alpha install was a goner!

It seems to be working nicely - double the RAM usage - but, I'll take it.  ;)

Okay, bring on the breakage!  I'm ready for ya!  LoL!

---

### Post by VinDSL on 2011-06-16
Oh, joy!

What a difference 24 hours makes!?!?!

Everything worked fine, for a day, then...

Yesterday, I did an update, and Unity quit working.  After I logged into Unity, I was met with a black screen and the following error dialog:

```

Failed to load session "Ubuntu"

```

But, "Classic", so called, was still working.

This morning, I logged into "Classic" and performed another update.  I noticed that the update was going to remove nvidia-common, which sets off warning bells in my mind, but I rolled the dice anyway, and it came up [snake eyes]("http://en.wikipedia.org/wiki/Snake_eyes").  LoL!

On the next reboot, Plymouth was back to it's high-res goodness (haven't seen that for a while) but... there it sat, e.g. no login screen.

Oh, well, this too shall pass, or not.

I REALLY need to start downloading [the dailys]("http://cdimage.ubuntu.com/daily-live/current/") and see if I can get one of them to work.

The last ISO I tried was the June 2 build, and I couldn't get to 1st base with it.

Anyway, onwards and upwards...  ;)

---

### Post by Harry33 on 2011-06-16
At least the latest mesa package (7.10.3) will break proprietary drivers.
See the bug # 798007.
Downgrading to mesa 7.10.2 solves the issue by now.
Nvidia-current will be patched soon to accept the multiarch system and then a new mesa package is also uploaded.

---

### Post by VinDSL on 2011-07-01
**[COLOR="DarkOrange"]_1-Jul-2011_[/COLOR]**

WoW!  My patched and mod'ed A1 install is a horrid mess, right now!

My only saving grace is, the current Daily Build is even worse.  LoL!

I guess we're going through rough waters...

I'd make a screenie, but I'm embarrassed.

Oh, well, that too shall pass.

A2 can't come soon enough for me!  :D

---

### Post by cariboo on 2011-07-01
I have to agree, my A1 install is horrible, I did a fresh install of the June 30 daily iso on another system, and I'm amazed at the difference, Bootup from grub to lightdm is back to Lucid times, and themeing seems to be working too.

---

### Post by VinDSL on 2011-07-01
> **cariboo907 said:**
> I have to agree, my A1 install is horrible, **[COLOR="Red"]I did a fresh install of the June 30 daily iso[/COLOR]** on another system, and I'm amazed at the difference, Bootup from grub to lightdm is back to Lucid times, and themeing seems to be working too.
Looks like I'm going to have to do a wash, rinse n' style too.  ;)

I've got broken pipes today, which are unfixable - packages that are trying to overwrite things that are contained in other packages, et cetera.

Time to cut my loses and do a fresh install...

---

### Post by VinDSL on 2011-07-02
Once, again, procrastination has paid off.  LoL!  :D

I've done nothing but regular Synaptic updates and Oneiric magically repaired itself...


[INDENT]**Ubuntu 11.10 [COLOR="DarkOrange"] / [/COLOR] Conky 1.8.0 [COLOR="DarkOrange"] / [/COLOR] Lua [COLOR="DarkOrange"] / [/COLOR] Unity [COLOR="DarkOrange"] / [/COLOR] Banshee [COLOR="DarkOrange"] / [/COLOR] Imperial Weather**  [SIZE="1"]**(Click to expand)**[/SIZE]

[[IMG]http://vindsl.com/images/vindsl-desktop-2-jul-2011(5)(600x480).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-2-jul-2011(5).png")[/INDENT]


Okay, bring it on.  I'm ready...  ;)

---

### Post by VinDSL on 2011-09-10
WoW!  Classic breakage!  Been on a rocket sled to hell, for 2 days!

A couple of nights ago, an omnibus cycle of updates completely broke my Unity DE.  None of the usual stuff repaired it.

I won't bore you with all the things I tried, but believe me, it was a real corker!  

Suffice to say, after 2 days of banging on the command line, 11.10 was withering on the vine.  I was down to running Oneiric in Classic mode (no effects), via GDM.

Anyway, for s.... & giggles, I tried:

```

sudo apt-get install ubuntu-desktop

```

...haven't used that command in ages.

After answering a few prompts and doing a restart - boom!  Everything was back - never had so many options to choose from in the LightDM Greeter.

Amazing!

Okay, bring on the breakage.  I'm ready for ya...  :)

---

### Post by ventrical on 2011-09-10
Just for the sake of fun I am going to try that on my Intel PC desktop with 500GBSATA.

 Iv'e been having a heck of a time trying to get that beast running. Pulling my hair out. I was finally able to get it going on a 30GB IDE HDD.

---

 Ok .. so today , after updates and last night also  firefox will not close from the (x) on the top bar.

 so more stuff seemingly comming down the pipe. :)

---

### Post by VinDSL on 2011-09-10
The biggest problem I was having was...

I had reinstalled everything, using various processes - remove, purge, install, reinstall, blah, blah, blah.  I *knew* they were installed and sitting there, but...

I couldn't tie it all together.  LightDM wasn't seeing the various DEs, dittos for GDM.

I knew there had to be a way to get LightDM and GDM to recognize the DEs, and offer them as an option at login, but it was escaping me.  Eventually, they were blinded to everything except "Classic".

Finally, reinstalling the Ubu Desktop did the trick.  Gotta add that to my notes, for future reference...  ;)

I might add:  Unity 3D is very well behaved, at the moment.  CPU & RAM usage is low, and everything is performing quite sprightly.  

I'd be happy to run this install (in its current state) on a production machine - but, where's the fun in that?!?!?

---

### Post by ventrical on 2011-09-10
Thanks for sharing that .

  I went back to this beast (IntelDesktopMoBo) that has been giving me probs from day one since trying to install Oneiric to a 500GBSATA drive.

 I started it up , got the GRUB boot menu, clicked the instance of Oneric (3.0.0-9) and .. WOW .. it booted right up to the login screen (LightDM) it had only Unity2d and Ubuntu (Unity 3D). I tried both of them but I could not get them to come up. (I had earlier determined that it may be a video driver problem)<ATi Radeon Express>

  I tried all the suggestions but could not get that beats to work- so it has been on the shelf.

 I then went to terminal:

sudo apt-get install fvwm-crystal

and that worked great.

AFTER :

sudo apt-get install synaptic

I proceeded to update.

 I rebooted, went back to the login screen, chose Unity 3D and it just comes up with the Nautalis screen, no launcher .. etc....

 Well .. at least I know my SATA is working :)

I also installed GNOME-Shell from the ternimal but it tells me 'can't load Gnome" or somthing.

  Now I know that the video card is included and I had Unity working from an IDE HDD install of Oneiric on that same machine but the drive is so noisy-  anyways .. back to the drawing board I think. I tired to follow some proeceedures to get the Ati video driver installed but I think I am missing somthing.

I tried the fglrx thingy but that didn't work...

so ... I am occasioned to ask you oh great mojo master .. 'what am I doing wrong with this driver install?

:)

---

### Post by VinDSL on 2011-09-10
I haven't run an ATi card in years, so I'm of little help installing drivers.  Sorry!

I *think* the last time I ran an ATi card was on SuSe, and OMG!!!  It was like pulling your own teeth.

Maybe someone else will pop in here...  ;)

---

### Post by ventrical on 2011-09-10
Boom !!

 On a whim I decided to :

sudo apt-get install fglrx

and - voila'  UNITY!!!!!!!!!!!!!!!

:)

unbelivable !!

---

### Post by VinDSL on 2011-09-10
Heh!

Isn't testing fun?!?!?  :D

---

### Post by ventrical on 2011-09-11
> **VinDSL said:**
> Heh!

Isn't testing fun?!?!?  :D

Yes it is !!   :)

---

