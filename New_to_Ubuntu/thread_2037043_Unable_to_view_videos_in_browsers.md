---
title: "Unable to view videos in browsers"
date: 2012-08-03
forum: New to Ubuntu
---

### Post by Pharoahphx on 2012-08-03
I have recently upgraded to Ubuntu 12.04, and since then I am unable to view videos or anything flash related in my current browser. I use Firefox. I have tried all solutions that I have found, and even tried two different browsers, Opera and Chrome. I have tried flash aid and still no luck. In Firefox, the video will not even load, and in Opera and Chrome they both give me the "Shockwave Player has crashed" message. All of this worked fine in 10.04. So I am unsure at what I need to do to fix this. Please help.

Thanks,

Pharoahphx

---

### Post by 1204 on 2012-08-03
What does this page show for you? [www.mozilla.org/plugincheck/]("http://www.mozilla.org/plugincheck/")

---

### Post by Pharoahphx on 2012-08-03
[IMG]http://www.mozilla.org/img/covehead/plugincheck/icon-flip.png[/IMG] 						**[Windows Media Player Plug-in]("http://www.google.com/search?q=current%20version%20plugin%20Windows%20Media%20Player%20Plug-in")**

[Gecko Media Player]("http://kdekorte.googlepages.com/gecko-mediaplayer") 1.0.4

Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using [MPlayer]("http://mplayerhq.hu") 					 					Unknown plugin 					[Research]("http://www.google.com/search?q=current%20version%20plugin%20Windows%20Media%20Player%20Plug-in") 				 					 						[IMG]http://www.mozilla.org/img/covehead/plugincheck/icon-quicktime.png[/IMG] 						**[QuickTime Plug-in 7.6.9]("http://www.apple.com/quicktime/download/")**

[Gecko Media Player]("http://kdekorte.googlepages.com/gecko-mediaplayer") 1.0.4

Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using [MPlayer]("http://mplayerhq.hu") 					 					Outdated Version 					[Update]("http://www.apple.com/quicktime/download/") 				 					 						[IMG]http://www.mozilla.org/img/covehead/plugincheck/icon-flash.png[/IMG] 						**[Shockwave Flash]("http://www.adobe.com/go/getflashplayer")**

Shockwave Flash 11.2 r202 					 					11.2.202.0 					[Up to Date]("http://www.adobe.com/go/getflashplayer") 				 					 						[IMG]http://www.mozilla.org/img/covehead/plugincheck/icon-divx.png[/IMG] 						**[DivX Browser Plug-In]("http://www.google.com/search?q=current%20version%20plugin%20DivX%20Browser%20Plug-In")**

[Gecko Media Player]("http://kdekorte.googlepages.com/gecko-mediaplayer") 1.0.4

Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using [MPlayer]("http://mplayerhq.hu") 					 					Unknown plugin 					[Research]("http://www.google.com/search?q=current%20version%20plugin%20DivX%20Browser%20Plug-In") 				 					 						[IMG]http://www.mozilla.org/img/covehead/plugincheck/icon-real.png[/IMG] 						**[RealPlayer 9]("http://www.google.com/search?q=current%20version%20plugin%20RealPlayer%209")**

[Gecko Media Player]("http://kdekorte.googlepages.com/gecko-mediaplayer") 1.0.4

Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using [MPlayer]("http://mplayerhq.hu") 					 					Unknown plugin 					[Research]("http://www.google.com/search?q=current%20version%20plugin%20RealPlayer%209") 				 					 						Thanks for the response, here is what the page said.


[IMG]http://www.mozilla.org/img/covehead/plugincheck/icon-flip.png[/IMG] 						**[mplayerplug-in is now gecko-mediaplayer 1.0.4]("http://www.google.com/search?q=current%20version%20plugin%20mplayerplug-in%20is%20now%20gecko-mediaplayer%201.0.4")**

[Gecko Media Player]("http://kdekorte.googlepages.com/gecko-mediaplayer") 1.0.4

Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using [MPlayer]("http://mplayerhq.hu") 					 					Unknown plugin 					[Research]("http://www.google.com/search?q=current%20version%20plugin%20mplayerplug-in%20is%20now%20gecko-mediaplayer%201.0.4")

---

### Post by 1204 on 2012-08-03
Well everything seems to be alright. Close Firefox and open Terminal. Then commands:
[I]
cd
cd .macromedia
rm -rf Flash_Player[/I]

Now flash player files removed. Open Firefox and try Youtube or something. Does it work?

---

### Post by Pharoahphx on 2012-08-04
I tried those commands, and still no luck. Just as before the space where the video is suppose to be is blank, not even an outlined box.

Pharoahphx

---

### Post by cwsnyder on 2012-08-04
Do you have any plug-ins for Firefox which block javascript or flash objects from automatically running when you enter a webpage, such as NoScript or and ad blocking program?  These can also block video playback.

---

### Post by Pharoahphx on 2012-08-04
These are the plug ins and extensions that are installed:

Extensions:
Global Menu Bar Integration 3.2.5
Quick Java 1.8.0
Ubuntu Firefox Modification 2.1.1
Flash Aid 2.23
Flash Video Replacer 2.1.15
Java Script Debugger 0.9.89

Plug-ins:
DivX Browser Plug-in
itunes Application Detector
mplayer plug-in is now gecko media player 1.0.4
Quicktime Plug-in 7.6.9

All are enabled.

Thanks,
Pharoahphx
Real Player 9
Shockwave Flash 11.2r202
Windows Media Player Plug-in

---

### Post by cwsnyder on 2012-08-05
Javascript debugger has known and listed problems with some versions of Firefox and is not being developed as of August 2012.

QuickJava is can block any Flash video.

There may be other problem with your other extensions.

Have you run Firefox with all your extensions disabled and see if your problem recurs?

---

### Post by cwsnyder on 2012-08-05
Have you tried running Firefox without extensions except Shockwave Flash?

---

### Post by Pharoahphx on 2012-08-06
I have tried running it with all extensions blocked except Shockwave. Still no luck. The load box is still missing. I checked Opera too, because it is still installed, Opera does not have any extensions installed. I am not committed to firefox. I have used it in the past, but if another browser will fix this I am open to that as well. Is it something that was not installed and placed correctly during the upgrade of 12.04?

Thank you,

Pharoahphx

---

### Post by sid0972 on 2012-08-06
you might have tried this but try chromium web browser, if it doesnt play any video, type following

> sudo apt-get install ubuntu-restricted-extras

and see if it works..........

---

### Post by Pharoahphx on 2012-08-07
I just tried both  chromium web browser and the other command. Just as before the box for the video will not load. I see the video that is suppose to play on the previous screen. When I choose a video, that is when the problem comes. The next page will load everything for the page except the main box where the video is suppose to be. In Chromium as well as Opera I get the Shockwave has crashed message. In Firefox I get just an empty space where the video is suppose to be. This one has got me stumped.

Pharoahphx

---

### Post by Autodave on 2012-08-07
> **Pharoahphx said:**
> I just tried both  chromium web browser and the other command. Just as before the box for the video will not load. I see the video that is suppose to play on the previous screen. When I choose a video, that is when the problem comes. The next page will load everything for the page except the main box where the video is suppose to be. In Chromium as well as Opera I get the Shockwave has crashed message. In Firefox I get just an empty space where the video is suppose to be. This one has got me stumped.

Pharoahphx


I am having the same problem, too.  Exactly what you are saying.  Had 2 of 4 machines all of a sudden develop this problem: both were working until about a week ago.  Both running Xubuntu 12.04.  I have tried soooo many things on this machine that I just wiped it and re-nstalled fresh copy.  Still no Youtube videos.

---

### Post by Kalanac on 2012-08-07
YouTube doesn't run on flash anymore, it uses HTML5

---

### Post by Autodave on 2012-08-07
> **Kalanac said:**
> YouTube doesn't run on flash anymore, it uses HTML5

How do I get / install / activate that?

---

### Post by Kalanac on 2012-08-08
It's a new web standard.  Modern browsers should automatically support it in the same way they support HTML 4.

Make sure you don't have plugins that might be interfering with YouTube like ad or media blockers.  If you've tried it with two browsers and the problem is in both, the only thing I can think at is possibly a codec issue.  I think YouTube uses .mp4 format, so double check your codec for that.  The player is HTML5 but it will still call on your systems codec.  Maybe try purging your ubuntu-restricted-extra package, browser and any other codec packages you think could be involved.

```
sudo apt-get purge ubuntu-restricted-extras firefox chromium opera
```

Then re-install the restricted extras package, then your preferred browser.  That's the nuke everything and start again approach so just be a bit cautious, it shouldn't loose any personal data or anything like that, but especially be aware of other packages that might get selected for removal and don't go through with it if it tries to remove ubuntu-desktop or any other core package.  The simulation run I've just done suggests this won't happen.  If you want to check what will be removed first you can run

```
sudo apt-get purge **-s** ubuntu-restricted-extras firefox chromium opera
```

To do a simulation run.  This will tell you everything that will happen when you do it for real.  One thing that could possibly vanish is bookmarks, so maybe back those up before hand.

---

### Post by Curtis6767 on 2012-08-08
> **Autodave said:**
> How do I get / install / activate that?

[https://www.youtube.com/html5](https://www.youtube.com/html5)

opt in for the trial then go to one or more youtube videos and see if that works.

I just played several videos with adobe flash with no problems.

Using another system, one on which I have opted in to the HTML5 trial, I played a couple of videos. One played in HTML5 and the other played in Flash. 

I know youtube is moving to HTML5 but if I can play videos in both formats, then HTML5 is not yet default. .

---

### Post by Pharoahphx on 2012-08-09
> **Kalanac said:**
> It's a new web standard.  Modern browsers should automatically support it in the same way they support HTML 4.

Make sure you don't have plugins that might be interfering with YouTube like ad or media blockers.  If you've tried it with two browsers and the problem is in both, the only thing I can think at is possibly a codec issue.  I think YouTube uses .mp4 format, so double check your codec for that.  The player is HTML5 but it will still call on your systems codec.  Maybe try purging your ubuntu-restricted-extra package, browser and any other codec packages you think could be involved.

```
sudo apt-get purge ubuntu-restricted-extras firefox chromium opera
```Then re-install the restricted extras package, then your preferred browser.  That's the nuke everything and start again approach so just be a bit cautious, it shouldn't loose any personal data or anything like that, but especially be aware of other packages that might get selected for removal and don't go through with it if it tries to remove ubuntu-desktop or any other core package.  The simulation run I've just done suggests this won't happen.  If you want to check what will be removed first you can run

```
sudo apt-get purge **-s** ubuntu-restricted-extras firefox chromium opera
```To do a simulation run.  This will tell you everything that will happen when you do it for real.  One thing that could possibly vanish is bookmarks, so maybe back those up before hand.

I gave that a shot, and I am still at square one. Would starting at the beginning and working through different solutions work? I have tried so many I am not sure where to begin to try and resolve this. I don't want to downgrade back to 10.04, but I didn't have these issues until the upgrade. I like other aspects of the recent upgrade, just this issue. 

Pharoahphx

---

### Post by Kalanac on 2012-08-09
I'm running 12.04 with no flash related trouble.

I guess the final option would be to backup your none replaceable files (ideally your entire home directory) and re-install your Ubuntu installation from the ground up.  If you save your entire home directory check the browsers are working BEFORE you restore all the files therein.  That way if there is an error in one of your personal config files you'll at least know :)

---

