---
title: "Can't Get Flash to Work in Any Browser - XUbuntu and LUbuntu 14.04"
date: 2014-05-26
forum: New to Ubuntu
---

### Post by lah-ca on 2014-05-26
Hi,

I have tried both X and L Ubuntu 14.04 on an older system, Athlon XP 2800+, 256 Mb ATI AGP card, 2 Gb DDR1.  Everything runs fine except Flash.  The browser plugins crash when I go to a website with Flash content.  I have tried Opera, Firefox and Chrome, all with the same result.

Any ideas?

Thx.

---

### Post by Vladlenin5000 on 2014-05-26
Your CPU doesn't support the newer flash versions.

---

### Post by monkeybrain20122 on 2014-05-26
Which flash websites do you use? You may find Viewtube useful as it supports many popular sites.[http://isebaro.com/viewtube/?ln=en](http://isebaro.com/viewtube/?ln=en) You need to install the greasemonkey addon for Firefox and gecko-mediaplayer from the repo. 

I would use Viewtube for supported sites even if flash works, mplayer uses a lot less resources for video playback than flash, so e.g if you can only watch videos in 360p/480p with flash on Youtube because of weak cpu you may be able watch some in 720p with Viewtube.

---

### Post by lah-ca on 2014-05-26
> **Vladlenin5000 said:**
> Your CPU doesn't support the newer flash versions.

Yes.  That may well be it.  The Athlon XP 2800+ at 2.083 GHz (real) is just below the bare minimum system requirements for the current version of Flash.  

[https://www.adobe.com/products/flashplayer/tech-specs.html](https://www.adobe.com/products/flashplayer/tech-specs.html)  "Linux: 2.33GHz or faster x86-compatible processor, or Intel Atom 1.6GHz or faster processor for netbooks."

I am just cleaning up old stuff out of storage: the Athlon XP box is a very nice, but very old, Shuttle XPC box, my daughter's old PC which used to run Dapper and then Lucid; it had intermittent stability issues and was shelved until I had the time to look at it - which was never - ;^).  

I have resolved the stability issues too late now it seems.  LOL.

It might make an attractive doorstop or Free BSD server or something else equally useful to me.  ;)

Thx.

---

### Post by lah-ca on 2014-05-26
> **monkeybrain20122 said:**
> Which flash websites do you use? You may find Viewtube useful as it supports many popular sites.[http://isebaro.com/viewtube/?ln=en](http://isebaro.com/viewtube/?ln=en) You need to install the greasemonkey addon for Firefox and gecko-mediaplayer from the repo. 

I would use Viewtube for supported sites even if flash works, mplayer uses a lot less resources for video playback than flash, so e.g if you can only watch videos in 360p/480p with flash on Youtube because of weak cpu you may be able watch some in 720p with Viewtube.

Well ... I am just experimenting with this old computer to see if it might be useful.  See the other reply above.  I do not use it to do anything, per se.  It is a very pretty little aluminum Shuttle XPC box.  It seems a shame to toss it, now that I have finally resolved its hardware issues.   

I will look at Greasemonkey and Viewtube, both of which are new to me.  

Thx.

---

### Post by squakie on 2014-05-26
You could try making it a home server or even a media center (see xbmcbuntu - but I don't know how well it works, there is other free media center software available as well).  Sounds like it still has enough "umph" to serve a purpose other than the doorstop ;) , although it would make an interesting conversation piece when people come to visit and ask "is that door THAT heavy??".  ;) ;)

EDIT:  I forgot to mention - you could always try to install something like 12.04 since it is still supported and then add XBMC via the package manager and use the PC as both a media center and whatever else at the same time.

---

### Post by lah-ca on 2014-06-13
Well the system here is pretty much useless as a desktop.

I have tried 14.04 32 bit, Ubuntu and Mint, on this system, the full versions, and everything works at a more or less acceptable speed.  The proc is definitely the bottle neck in the system, but things do work.  The system could still be useful as a PC for someone except for the demands of flash media.  

Grease Monkey and its dependencies work reasonably well.  (GNash does not - Nor does Light Spark - very choppy low res garbled performance.)  But there are so many sites for which Grease Monkey will not work - pretty much all major news sites for example.  Again, without working flash media support the Athlon XP PC here is pretty much useless as a desktop.

Adobe becomes the aribiter of computer obsolecense.  A dependency on the bloated technology of this single corporation basically disenfrachises a lot of the 3rd world from meaningful enjoyment of the web - very scary, boys and girls,very scary.   

Lucid was not that long ago, and this system worked just fine then.  Too bad the toxic 3rd world circuitboard smelting industry is not in Adobe's backyard, eh?

---

### Post by Yellow Pasque on 2014-06-14
Well, you can use an older Flash version, but be warned that it is insecure (and video playback still might bring your old CPU to its knees..).
[http://ubuntuforums.org/showthread.php?t=1953796&p=12362874#post12362874](http://ubuntuforums.org/showthread.php?t=1953796&p=12362874#post12362874)

---

### Post by claracc on 2014-06-14
I have a very old laptop PIII, CPU 1 GHZ, 512 Mb Ram, sys 630/730 graphics card with unsupported lubuntu 12.04.

I have an old flash player installed, I think is 11.2.202.297, see [http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html](http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html), and I can play flash video (the laptop doesn't support any flash plaayer above this release, and I can see flash videos, but in the slow motion way) or use viewtube in the supported web places. Firefox complains about the old outdated flash plugin but it lets you to run it.

So, I suggest to install an old flash player which your hardware can run (you can try what release your computer can run), but you have to be aware of the security risks.

Other posibility, which I haven't tried yet, is to install ubuntu 12.04 lxle which seems to work well in old computers. Certainly adobe flash is a resources hog which made old computers useless to play flash videos. I hope it will soon be replaced by a more efficient piece of software.

---

### Post by squakie on 2014-06-14
Yeah - when you consider Adobe stopped flash support for linux, then we are left with the newest "old" version that worked for linux.  The result is that many sites look at the version and won't run the flash player because it is not at a certain level - read "after support for linux ended".  So in this case it isn't even so much hardware obsolesence (though it is true for your CPU) as it is that we are "stuck" at a certain release of flash.

---

