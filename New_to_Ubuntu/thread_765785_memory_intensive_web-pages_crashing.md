---
title: "memory intensive web-pages crashing"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by warped0ne on 2008-04-24
Is there some kind of memory limit in 8.04 for web-pages, applications.  I've got 2GB of memory, P4 2.54Ghz processor and 80GB hard drive, and every time I open a program that requires a lot of memory (e.g. [www.seesmic.com](www.seesmic.com), Boson, SuperTux World) the program just closes.  I've only had Ubuntu for about 1 week, and I really enjoy it, but so far, it's not allowing me to do anything except go to some of my usual web-pages.

I've tried Firefox 2.0.0.14, Firefox 3 beta 5, and Konqueror in Hardy Heron, all with the same result.

I know it's not a problem with the web-page ([www.seesmic.com](www.seesmic.com)) as I can visit it on my WinXP partition and 2 laptops plus my work computer (seesmic generally requires about 120MB of RAM to run in FireFox 3 in WinXP).

[www.seesmic.com](www.seesmic.com) is a web-page designed as a mix between MSN messenger and Youtube (which reminds me, youtube.com, youku.com and tudou.com all work in 8.04).

Any suggestions, settings I'm missing, anything? :confused:

Also, got a 19 inch, widescreen HP monitor (w1907).  Version 7.04 (I think) or 7.10 had drivers for it and allowed me to have a screen resolution of 1440x900 (native), 8.04 doesn't seem to have a driver for this though.

---

### Post by st33med on 2008-04-24
hrm, does seesimic.com use flash? It is a ongoing bug that in Firefox it crashes 1/3 of the time (or, I think it is still ongoing). Try other flash sites for a while, see if they experience any problems.

---

### Post by warped0ne on 2008-04-24
Yes, the first time I went to Seesmic after the install it said I needed to download flash.  I have now done that through the built in Add/Remove Applications (1st) and directly from Adobe (2nd).

This isn't a 1/3 of the time crash though, this is 100% of the time crash.

---

### Post by warped0ne on 2008-04-24
Just tried the Flash Game Desktop Tower Defense ([http://www.handdrawngames.com/DesktopTD/Game.asp](http://www.handdrawngames.com/DesktopTD/Game.asp)) and it crashed the page, too.  

Any suggestions?

Any known fixes for this flash issue?

Off topic question - I've lost my monitor selection application under system, any ideas there?

---

### Post by warped0ne on 2008-04-25
Seesmic now works for me now.  Here's what I did.

I went into the Synaptic Package Manager and uninstalled everything that said Flash, Mozilla and or Firefox.  Then I reinstalled Firefox, through the Applications -> Add/Remove Applications and it now works.

I was just on Seesmic for over an hour without any crashes, but I'll post again tomorrow if I am able/unable to get in again.

Thanks to St33med for pointing me in the direction of the Flash plugin.

:KS

---

### Post by tiggsy on 2008-08-05
Unfortunately, after following these instructions, Seesmic still crashes my browser. I just avoid it when I can, but occasionally, I get a link that's been shortened (tinyurl or whatever), and I get caught.

Ed Dale often shortens links to seesmic, so I always take a lot of care when going to one of his links, and close the tab quick!

---

### Post by shatteredmindofbob on 2008-08-11
I realize I'm bumping up an old thread but this problem still exists and has gotten worse since many of the sites I read have started embedding Seesmic content, shutting down Firefox the second they load...anyone have ANY idea what the problem is?

---

### Post by shatteredmindofbob on 2008-08-11
So I just tried my roommate's computer (also running Hardy) and it works fine...so I'm guessing it's a plug-in or extension issue...now to play the disable plugins until I find the problem game....

---

### Post by shatteredmindofbob on 2008-08-11
Okay, disabled all extensions...no good. Clearly none of them are the culprit. On to plug-ins...

In the meantime, anyone else have any ideas?

All I learned from running Firefox in terminal is that Seesmic causes a segfault.

---

### Post by shatteredmindofbob on 2008-08-11
Okay, Shockwave Flash is DEFINITELY the culprit. But how do I FIX it?

---

### Post by gaspard.leon on 2008-08-11
I suggest trying different versions of flash.

I found the v9 Flash plug in crashes occasionally.

Try using the v10 beta plug in... I recommend the first beta as the second one slows to a crawl on some pages.

(the v10 betas don't crash as much, I've never had a crash with version 10 myself, but the second beta was so slow I had to downgrade to the first beta...)

DISCLAIMER: I use Hardy i386 32bit version, NOT 64bit... YMMV

---

### Post by shatteredmindofbob on 2008-08-11
Okay, this has gotten weird, I just checked my roommates computer, he's using the exact same version of Flash I am (9.0 r124) so now I'm really confused as to why his works fine and mine doesn't. I don't think it's a conflict with anything since I've got everything in Firefox but Flash disabled. 

Could this have something to do with Pulse Audio? ALSA stopped working for me a few days ago, so I had to switch over...

---

### Post by rockerphil on 2008-08-11
unfortunately Flash support for Linux is still pretty buggy, although i've been using the newest Beta release of Flash, and it works well for me. you can either try that or possibly try running it through another browser i.e. Opera, Netscape or possibly somthing else. hope the info helps,

Phil

---

### Post by shatteredmindofbob on 2008-08-11
> **gaspard.leon said:**
> I suggest trying different versions of flash.

I found the v9 Flash plug in crashes occasionally.

Try using the v10 beta plug in... I recommend the first beta as the second one slows to a crawl on some pages.

(the v10 betas don't crash as much, I've never had a crash with version 10 myself, but the second beta was so slow I had to downgrade to the first beta...)

DISCLAIMER: I use Hardy i386 32bit version, NOT 64bit... YMMV

Thanks, I'm also using 32 bit...though I'm weirded out by the fact that the same version of Flash runs fine on a different computer

---

### Post by shatteredmindofbob on 2008-08-11
> **shatteredmindofbob said:**
> Thanks, I'm also using 32 bit...though I'm weirded out by the fact that the same version of Flash runs fine on a different computer

Blah, alright, install Beta 2 and Firefox still shuts itself off.

---

### Post by shatteredmindofbob on 2008-08-11
Okay, Beta 2 just made things worse, now YouTube shuts off Firefox as well...

I hate to say it, but it's times like this when I'm tempted to go running back to Windows...

---

### Post by tuxxy on 2008-08-11
Running back? maybe you would prefer to access windows in virtualbox and never even have to reboot :)

---

### Post by shatteredmindofbob on 2008-08-11
> **tuxxy said:**
> Running back? maybe you would prefer to access windows in virtualbox and never even have to reboot :)

True, but one of the main reasons I like Ubuntu is how fast web browsing is (especially streaming videos) until it crashes...

So anyway, I disabled Flash 10 and now Flash 9 is gone. I figured I'd just go a Flash intensive site and wait for the pop-up to appear telling me I need flash...but it ain't popping up anymore. Argh!!

---

### Post by shatteredmindofbob on 2008-08-11
Alright, this makes NO SENSE...but, it seems to have fixed the issue. 

I reinstalled Flash 9 manually...the install went fine, but Flash didn't work in Firefox, period. Fed up, I went into the Package manager and deleted everything Flash related (well, I wussed out and didn't kill Restricted Drivers, because I didn't feel like fighting to get MP3 support back...) 

Went back into Firefox planning to reinstall Flash yet again except...everything worked. 

...makes...NO...SENSE...but it works. 

...HAH, before I hit Submit Reply I figured I'd test other stuff as well and now Amarok is completely messed up due to what I did. ...This is fun!

---

### Post by tuxxy on 2008-08-11
> True, but one of the main reasons I like Ubuntu is how fast web browsing is (especially streaming videos) until it crashes...

Yes me too, I meant instead of having to boot down to run windows you could quickly open virtualbox and browse that site which is the only reason you seem to want windows.  Maye you could have a look at ie4linux to display that site aswell.

---

### Post by shatteredmindofbob on 2008-08-11
> **tuxxy said:**
> Yes me too, I meant instead of having to boot down to run windows you could quickly open virtualbox and browse that site which is the only reason you seem to want windows.  Maye you could have a look at ie4linux to display that site aswell.

Ah yes, I actually did that before posting here...the sites in question run fine under Firefox in Windows. Unfortunately, so do all those stupid pop-up bubbles in the task bar that remind of why I was on a mission to purge Windows from my life in the first place. 

Anyway, update...since this gets weirder. ALSA is now working again (it stopped a few days ago, but switching to Pulseaudio made everything work fine, so I didn't worry...) Uninstalled and reinstalled Amarok and now I seem to be back in business all around. 

Total flashback to troubleshooting Windows 3.1...where the solution rarely made sense but as long as it worked, I wasn't going to complain.

---

