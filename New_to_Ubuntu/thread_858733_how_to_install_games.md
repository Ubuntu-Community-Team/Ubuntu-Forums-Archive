---
title: "how to install games"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by coolman121 on 2008-07-13
i am trying to install games any game 
games i have are: sims 2 deluxe , grid , nfs all, bf2,crysis, and many others but i have still to find a way to install them ......... even using wine

---

### Post by Tatty on 2008-07-13
Wine is not perfect at all, even though it is a 1.0 release it is still not fully compatible with all windows software.

If your games are windows games then wine or crossover(paid-for and tweaked version of wine) are usually your only options.  The only exception I can think of is if your games are powered by the SCUMM lucasarts engine (old adventure games only), in which case you can use scummvm.

I assume you are aware that winehq.org offers an application database which lets you know about wine compatibility for software.

If there is a linux game you are trying to install then post details of it on here and someone will be able to help you.

---

### Post by ChameleonDave on 2008-07-13
> **coolman121 said:**
> i am trying to install games any game 
games i have are: sims 2 deluxe , grid , nfs all, bf2,crysis, and many others but i have still to find a way to install them ......... even using wine
There is a separate forum here for [Linux games]("http://ubuntuforums.org/forumdisplay.php?f=93") and for [Wine]("http://ubuntuforums.org/forumdisplay.php?f=313").  You will indeed need Wine for any existing Windows games that you may have on CD.  Check out the [Wine Application Database]("http://appdb.winehq.org/") to see if they are listed as working.  You can get help with the problems associated with individual games by starting a thread in the appropriate forum.

Meanwhile, go to Synaptic and install any of the many cool games which are available for free.  I recommend OpenArena, Alien Arena, Scorched3D and Neverball.

---

### Post by coolman121 on 2008-07-13
well obviously hence y im posting... but none oof my games are compatible or if they say they are they dont work online ...... only grid is really what i want

---

### Post by ChameleonDave on 2008-07-14
> **coolman121 said:**
> well obviously hence y im posting... but none oof my games are compatible or if they say they are they dont work online ...... only grid is really what i want
Let's decipher that.

I can find a couple of games by that name.  I suppose you mean [Race Driver: GRID]("http://en.wikipedia.org/wiki/Race_Driver:_GRID")?  It is not listed in the Wine Application Database, so I don't hold high hopes for you being able to run it in Wine.  You might want to investigate [Cedega]("http://en.wikipedia.org/wiki/Cedega") or [Crossover]("http://en.wikipedia.org/wiki/CrossOver") (both Wine variants).

Again, if you seek help with installing a specific game, I advise you to start a thread on the specific issue, with full information, in the [Wine forum]("http://ubuntuforums.org/forumdisplay.php?f=313"). 

Another resource for you is [http://www.wine-reviews.net/](http://www.wine-reviews.net/).

If you cannot bear not to play certain games, and despite all your efforts they refuse to run via Wine, then you have three options:

[LIST]
[*]Run them on Windows inside VirtualBox inside Ubuntu;
[*]Run them on Windows by dual-booting with Ubuntu;
[*]Buy a game console (PlayStation, Wii or Xbox 360) and play on that instead.
[/LIST]

---

### Post by coolman121 on 2008-07-14
this is kinda why ubuntu sucks but imma still try it for a little longer until i decide to dual boot...........

---

### Post by WRDN on 2008-07-14
> **ChameleonDave said:**
> Let's decipher that.

I can find a couple of games by that name.  I suppose you mean [Race Driver: GRID]("http://en.wikipedia.org/wiki/Race_Driver:_GRID")?  It is not listed in the Wine Application Database, so I don't hold high hopes for you being able to run it in Wine.  You might want to investigate [Cedega]("http://en.wikipedia.org/wiki/Cedega") or [Crossover]("http://en.wikipedia.org/wiki/CrossOver") (both Wine variants).

Again, if you seek help with installing a specific game, I advise you to start a thread on the specific issue, with full information, in the [Wine forum]("http://ubuntuforums.org/forumdisplay.php?f=313"). 

Another resource for you is [http://www.wine-reviews.net/](http://www.wine-reviews.net/).

If you cannot bear not to play certain games, and despite all your efforts they refuse to run via Wine, then you have three options:

[LIST]
[*]Run them on Windows inside VirtualBox inside Ubuntu;
[*]Run them on Windows by dual-booting with Ubuntu;
[*]Buy a game console (PlayStation, Wii or Xbox 360) and play on that instead.
[/LIST]

You can't play *most* games in a virtual machine, because, as of today (14/7/2008.) they do not support Hardware Acceleration, so games won't work well.

---

### Post by lazyart on 2008-07-14
> **coolman121 said:**
> this is kinda why ubuntu sucks but imma still try it for a little longer until i decide to dual boot...........

:confused:

Yikes.  Let's make an analogy here:

Xbox360 must suck because it doesn't play PS3 games.
PS2 must suck because it's doesn't play Wii games.

Why do people keep expecting Windows games to work in Linux?  It's not that ubuntu sucks, it's these ridiculous expectations that suck.  Yeah, wine/crossover can make some stuff work, but Linux is not Windows and was not created to run Windows software.

Would you buy Mac software to run in Windows?  Probably not.

The best way to run windows games is to INSTALL THEM IN WINDOWS.  Period.

---

### Post by stchman on 2008-07-14
> **coolman121 said:**
> i am trying to install games any game 
games i have are: sims 2 deluxe , grid , nfs all, bf2,crysis, and many others but i have still to find a way to install them ......... even using wine

MY recommendation is to dual boot.  Windows XP or Vista for games and Ubuntu for everything else.  It works well for me.  Some of the older games work with WINE, but the newer games are usually a no go.

---

### Post by Joyfulbob on 2008-08-31
> **stchman said:**
> MY recommendation is to dual boot.  Windows XP or Vista for games and Ubuntu for everything else.  It works well for me.  Some of the older games work with WINE, but the newer games are usually a no go.

Thanks for the thread! I am new to Linux so please help me understand.

I share this concern - I bought GRID and have yet to play it because I needed a new video card (which made me upgrade my entire PC). I've just built a new PC and am considering whether to buy Vista or go to Linux. I have a Linux boot disk and have toyed around a bit in it.

So the best Linux can do is dual-boot? 

If Linux can't run Windows games, I still would have to buy Vista. I wanted to use Linux to avoid buying Vista. If I have to get Vista to run games ($100 just to play games), then I don't have a single OS solution. 

Plus, I (and my wife who is less PC-literate) would have to learn 2 new UI's. 

What's a user to do? I've checked out Wine and CodeWeaver's web sites and it doesn't look good for other Windows apps as well as games. 

Unfortunately, it seems my smoothest route is to buy Vista and everything runs; I don't have to learn Linux; no dual-booting; no learning 2 UI's, etc.

Thanks in advance! 
Bob

---

