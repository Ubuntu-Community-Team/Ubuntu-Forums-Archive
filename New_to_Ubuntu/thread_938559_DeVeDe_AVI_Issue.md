---
title: "DeVeDe AVI Issue"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by GarethA on 2008-10-05
I'm using DeVeDe (3.6) to create ISO images to burn to DVD.
Other formats work fine but whenever I create an ISO from an AVI the resulting DVD has a flickering image.
The audio is fine but the image seems to jump.

Getting fed up of throwing away DVDRs
:confused:


I'm running Hardy with the latest patches

---

### Post by sleepingdragon on 2008-10-05
The only issue I can think of is that DeVeDe is converting between NTSC and PAL (or vice versa). The change in framerate can throw up some unexpected flickering or jumping. 

Since most modern DVD players don't have a big issue playing both NTSC and PAL, try sticking to the original framereate the AVI came with and take it from there - NTSC is 29.97, PAL is 25.00. 

You could also try using Avidemux to set up the framerate. It will convert between them well enough.

Hope some of that helps. We're here if you need us!

---

### Post by GarethA on 2008-10-06
Thanks for that.
The framerate of the AVIs is 25FPS (according to avidemux) and I'm creating PAL ISOs so don't think DeVeDe should be changing the framerate.
The resulting ISO DVDs play fine on other PCs - (even windows ones!) - but on my normal DVD player they 'jump'.
Maybe I just have a dud DVD player - but it plays normal DVDs -
I've created plenty of DVDs that play fine.(using Kino to capture output of analog camcorder thru firewire card - then creating ISO with DeVeDe)
It's just AVI conversions that 'jump'
Any thoughts?

---

### Post by sleepingdragon on 2008-10-06
It does seem to be a dodgy DVD player if the resulting DVDs play fine on other machines... Some older machines can be a little funny with DVD-R(W)s. My old player wouldn't recognise DVD-RW at all. 

If you're thinking of a new player, then try one with DivX playback. [Toshiba do one at a reasonable price]("http://www.amazon.co.uk/Toshiba-SD280E-DVD-Player/dp/B0012Z1FME/ref=sr_1_1?ie=UTF8&s=electronics&qid=1223316575&sr=8-1") that's easily available. DivX conversion is so much easier than converting to DVD (fewer steps involved), and you can fit 2 hours of film onto a **CD-R**.

If you're planning to stick to DVD format, then do try another DVD creator, such as ManDVD. I've had plenty of success with that package, but I do find DeVeDe easier to run.

---

### Post by LowSky on 2008-10-06
I personally like ManDVD better than DeVeDe. Also if you are going to rip movies, rip them to Mpeg, not Avi. 
The issue being that DVD's are designed in Mpeg ten you rip the content to AVI and then you place it back onto a disc, which means it needs to be reconverted to Mpeg, You loose quality when this process.

And if you dont care about quality convert to Xvid or Divx and save some space.

---

### Post by GarethA on 2008-11-26
In case anyone else has this problem...
I have upgraded Devede to the latest version (3.11b)
This has solved the problem - I no longer get flickering on DVDs created from AVIs.

Latest version not available on synaptic. If you need it go here:
[http://www.rastersoft.com/programas/devede.html#download_section](http://www.rastersoft.com/programas/devede.html#download_section)

---

### Post by pmooney78 on 2008-12-05
I know your issue was solved, but I've run into another cause of this problem, in case anyone else stumbles across this thread ... sometimes using a different brand or make of blank DVDs will fix the problem. Recordable DVDs work slightly differently than "real" (professionally pressed) DVDs (they use dye to encode bits, rather than actual pits in the surface of the DVD), and some brands of DVD players (especially cheap ones) are sensitive to slight differences in reflectivity. :)

---

