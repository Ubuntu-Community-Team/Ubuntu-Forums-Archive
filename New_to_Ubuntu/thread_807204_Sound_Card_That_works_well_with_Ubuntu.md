---
title: "Sound Card That works well with Ubuntu"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by jukingeo on 2008-05-25
Hello All,

I have been doing some research on regards to getting my Sound Blaster X-Fi to work, and I am currently working on getting issues resolved with that card.

I noticed quite a few sound cards that need to use OSS or ALSA.

However, I did get to wondering if there are sound cards that work perfectly with Ubuntu (directly).  So, in short, that is my question.  Are their sound cards that specifically have Linux drivers to facilitate a seamless install?

---

### Post by diablo75 on 2008-05-25
I have an Audigy 2 and it works just fine.  PulseAudio needs some work though so as to better take advantage of my surround sound speakers, and that's a problem that exists across all surround sound cards and not just Creative Labs cards.  The PulseAudio devs are currently working on a "glitch-free" version for their next update which will take care of the occasional sound-clipping that currently takes place.

I would tend to say that pretty much any card made by Creative Labs would be the way to go...  But I also know that a LOT of different cards work right out of the box.  It seems that Pulse Audio is the only drawback about audio right now, but it's just a temporary bump in the road.

---

### Post by forestpixie on 2008-05-25
I think the XFi creatives can still be a bit problematic from what I've read here, although there has been a driver released beta I think.

---

### Post by soxs on 2008-05-25
After years Creative got around that *opensource==evil* never was valid, as far as I know they send Xfi specs to the alsa devs, didn't watch the progress so far. The drivers they pushed out in that time were rather horrible (x86_64 bit only, oss only, wacky like hell)
I would suggest you a Soundblaster Audigy LS, plug in and listen to your music :-P (Note: tested last with 7.10, so it works perfectly with alsa, pulsaaudio *may* or may not require some additional setup, but I do not think so.)

---

### Post by tad1073 on 2008-05-25
I bought an X-Fi Extreme and had to return it because I could not get it to work. Does anyone know if a [Dynex® - 5.1-Channel PCI Sound Card](http://www.bestbuy.com/site/olspage.jsp?skuId=7180739&productCategoryId=abcat0507003&type=product&tab=2&id=1110267355627#productdetail) will work?

---

### Post by chiefci on 2008-05-27
Hello.
I need help.
I have a special sound card:
ProteusX with E-MU chip from Creative-
First, is there anybody who know this card.
Thanks

Chief

---

### Post by herbster on 2008-05-27
M-Audio Revolution series work beautifully, using a 7.1 here.

---

### Post by jukingeo on 2008-05-28
> **herbster said:**
> M-Audio Revolution series work beautifully, using a 7.1 here.

I should have been more clearer.  I meant a pro audio interface that requires a break out box with XLR connectors, gain controls and such.  A phono input would be nice too as I still do record transfers.

At any rate I DID get the X-Fi card to work...but only on two channels.  It is also a 7.1 card but apparently it isn't fully supported as of yet.

Geo

---

### Post by bobpur on 2008-05-28
The Diamond brand of soundcards work well for me. They are so linux friendly that they ship with Audacity. They come in a 5.1 version and a 7.1 version for between $20 and $50 depending on which one you get. 
You can check them out at [www.newegg.com](www.newegg.com) (Specs & Reviews)

---

### Post by kansasnoob on 2008-05-29
This isn't really an answer to your question, but I know when I set up my daughters computer I had to install "alsa-firmware" from the Medibuntu repository to get her Sound Blaster card working.

---

### Post by jukingeo on 2008-05-29
> **bobpur said:**
> The Diamond brand of soundcards work well for me. They are so linux friendly that they ship with Audacity. They come in a 5.1 version and a 7.1 version for between $20 and $50 depending on which one you get. 
You can check them out at [www.newegg.com](www.newegg.com) (Specs & Reviews)

These are almost exactly like the M-Audio cards that Herbster pointed out.  As I mentioned to him, I am looking at something that has a breakout box with XLR connectors inputs, etc.

To give you an idea of what I have for Windows, this is my current beast:

[http://www.alesis.jp/images/products/large/io26_front_large.jpg](http://www.alesis.jp/images/products/large/io26_front_large.jpg)

Pretty Phat, huh?  It took me a while to find a nice audio interface like that, sadly it doesn't work with Linux.

Geo

---

### Post by garyed on 2008-05-29
Since M-audios works well why not look into just adding an audio buddy
that has xlr to any of the Delta lines. I use the Delta 2496 with an external Mackie mixer & it works great. I'm sure the Delta 66 would do fine & it has balanced inputs for a pro sound with a breakout box though not xlr. Add an audio buddy & its still pretty cheap for a pro sound.

---

### Post by jukingeo on 2008-05-30
> **garyed said:**
> Since M-audios works well why not look into just adding an audio buddy
that has xlr to any of the Delta lines. I use the Delta 2496 with an external Mackie mixer & it works great. I'm sure the Delta 66 would do fine & it has balanced inputs for a pro sound with a breakout box though not xlr. Add an audio buddy & its still pretty cheap for a pro sound.

Hello Gary, I don't know how a box like that works, but if it has to go through those 1/8" jacks that is asking for trouble in terms of Loose connections.  These 1/8" jacks are notorious for developing bad connections as time goes on.

A good example of a PCI card type interface that would meet my standards is the EMU-1820M which has a PCI card and then a wired connection to a breakout box.

Here is the standard 1820:

[http://www.musiciansfriend.com/product/EMu-1820-Computer-Recording-System?sku=242511&src=3SOSWXXB](http://www.musiciansfriend.com/product/EMu-1820-Computer-Recording-System?sku=242511&src=3SOSWXXB)

Another issue is sampling frequency.  I will no longer accept 48k and 96k is just for 'passable work', but for high end recordings, I like 192k.  Both the Emu and Alesis units I presented here have that capability.

As a preference, USB and Firewire have a minimum of connections to be made to the machine and as such an external interface is my first pick.

I do remember a while back that there was a version of the Sound Blaster X-fi that offered a breakout box, but that was near impossible to find.  Since that was an option at the time, the connector for the box IS present on my X-Fi card.  But I am wondering if I should even pursue that issue because as of now only 1/5th of the true capabilites of the X-fi card are available to Ubuntu.

I know I am new to Ubuntu and I don't know what it's audio capabilities are in terms of studio level work.  However, I am getting the gist that most of the good audio interfaces are not supported and probably will not be for some time.  And this probably goes the same for USB keyboards and other studio devices.  So I would say at this point that Windows still has that market cornered (followed closely by Mac).

However, if the M-Audio or Diamond cards did have full capability in Ubuntu and they offered a direct connecting breakout box, then I would look into that possibility.  But I certainly don't want to use the 1/8" plugs for connection points.  Also the cards would need to be a bare minimum of 96k, but 192 preferred.

---

### Post by garyed on 2008-05-31
The M-audio Delta series breakout boxes take standard 1/4" balanced or unbalance cables. There's no 1/8" on them. I think they only run 24 bit/96k.
My theory is if I can't get a good enough sound at 24bit/96k then it's not the equipment wher the problem is. 
My 2496 uses rca cables which isn't as good but it still does fine for me. 
Do a search for the Delta 66 & check out the specs. Ardour & Audacity will definitely run at 96k.

---

### Post by jukingeo on 2008-06-03
> **garyed said:**
> The M-audio Delta series breakout boxes take standard 1/4" balanced or unbalance cables. There's no 1/8" on them. I think they only run 24 bit/96k.
My theory is if I can't get a good enough sound at 24bit/96k then it's not the equipment wher the problem is. 
My 2496 uses rca cables which isn't as good but it still does fine for me. 
Do a search for the Delta 66 & check out the specs. Ardour & Audacity will definitely run at 96k.

The Delta 66 is no where near like my Alesis IO26, BUT IF it works somewhat then I may give it a shot.  I can't argue with the purchase price, which looks to be pretty good.

Now the next question is this:  Is the card fully functional under Linux?  Does it have Linux drivers, or does it have to be "fudged in" with another program (Like ASLA)?


Thanx,

Geo

---

### Post by jukingeo on 2008-06-25
Hello,

Back again.  Still having sound problems.  Overall it looks like I am probably going to have to use a different sound device.  However, I am NOT going to pull out my X-Fi card because it works great in Windows XP.

I don't want to muck around the inside of my machine and install a second audio card.  Windows may alter my sound configuration if I do that and then maybe I will not have sound in either Windows or Ubuntu. 

So the next question I have is that what EXTERNAL USB or Firewire audio cards/interfaces are compliant with Linux/ALSA?

I would like to go this route because with a Firewire or USB sound device, I can always "pull the plug" on it, when I go into Windows.  You can't do that with an internal card.

So what's out there?

Thanx,
Geo

---

### Post by go_beep_yourself on 2008-10-08
Did you ever get that working?

---

### Post by jukingeo on 2008-10-13
> **go_beep_yourself said:**
> Did you ever get that working?


Yes, I did get the X-Fi to work.  I had posted a link to the procedure in my signature, but for some reason the signature is gone now.  I will have to fix that later on.

Just do a search here for X-Fi AMD 64 bit and you will find the procedure.  The procedure holds true for all systems Intel & 32 bit as well.  The topic was started in the AMD/64 forum but "drifted" to cover all.

There were limitations with the X-Fi in the fact that I couldn't use it in any other distribution other than Ubuntu.  So I pulled the card out anyway.  I had trouble finding a card that would work with everything, but I finally settled on the M-Audio Delta series of audio cards.  I bought a Delta 44 and thusfar everything is working fine.  The Delta 44 didn't need any kind of set up procedure at all.  It was automagically detected by Ubuntu AND all my other Linux distributions.  If you want a low hassle way to go...I highly recommend this card.  In fact I wouldn't use anything else for pro-audio work if you intend on switching between distributions.  If you are content with sticking with Ubuntu Gutsy or Hardy, then the X-Fi may be good enough.  However, my main worry was that I may end up going back to square 1 when Ubuntu Intrepid is released, which is another reason why I pulled the X-Fi.

If you don't mind investing some time and you are not considering upgrading to Intrepid for a while, then perhaps getting the X-Fi to work on your system may be a good alternative to yanking the card out right away.  At least you will be able to try out the applications in Ubuntu.

I don't know what your usage is in Ubuntu.  Mine is pretty much specifically for audio and video editing.  So I needed something that had audio and editing software built in.  I have Ubuntu Studio on my machine right now.  I also have Puppy Linux, and Dynebolic.  My machine is setup on a triple booth with those operating systems and Windows XP.

Gee, I wonder why my signature was erased!

Anyway, hope that helps.

Edit:  I don't get it, my signature is back!  Anyway, click on that link below and you should be good to go.

Geo

---

### Post by go_beep_yourself on 2008-10-14
I had tried the link in your signature about a week ago. Unfortunately the beta driver from Creative doesn't seem to support my X-fi model. My model is newer than that driver. I'm pretty sure that's why. I've also tried OSS4. I think my X-fi model is too new for the oss-sbxfi driver as well. I have the X-fi Titanium PCIe model. I'm about to RMA it. Even if I do manage to get it working, it will likely give me 2.1 sound with my 5.1 surround sound Logitech G51 speakers and sub. However my onboard HD Audio has a higher sample rate and works just great in Linux with full 5.1 sound.

---

### Post by markbuntu on 2008-10-14
M-audio and the RME Hammerfall cards are well supported in linux if you are looking for pro quality. You can look in the Multimedia Production form here to see what people are using and problem cards that you might want to avoid.

---

### Post by jukingeo on 2008-10-14
> **go_beep_yourself said:**
> I had tried the link in your signature about a week ago. Unfortunately the beta driver from Creative doesn't seem to support my X-fi model. My model is newer than that driver. I'm pretty sure that's why. I've also tried OSS4. I think my X-fi model is too new for the oss-sbxfi driver as well. I have the X-fi Titanium PCIe model. I'm about to RMA it. Even if I do manage to get it working, it will likely give me 2.1 sound with my 5.1 surround sound Logitech G51 speakers and sub. However my onboard HD Audio has a higher sample rate and works just great in Linux with full 5.1 sound.

Sorry to hear that.  Usually in most cases the fresh kernel build with the X-Fi drivers should work.  There was another caveat I forgot to mention earlier.  That Kernel rebuild for the X-Fi is for the standard Kernel..not the RT Kernel.  Everyone with an X-Fi is up the creek in that regards.  That was also another reason why I pulled it.

I will say that overall sound card support in Linux is a very very tough issue.  The ALSA site says so many cards are supported in Linux if you use their drivers, however, many of those drivers are not updated as I found out the hard way when I bought an Echo Mona device.

The best thing is to go with something that is automatically recognized that will require little or no intervention on your part.

Sad to say, as Markbuntu points out, the only two companies that have favorable results are M-Audio Delta line PCI only (not the USB or Firewire stuff) and RME Hammerfall.  The trouble here is that with only the two product mfgs supported there is a gap in price v.s. features v.s. quality.

I always considered M-Audio fairly lower end in the pro field.  RME I hold in high regard, but with their cards starting at $600 and going up from there, it is out of my reach as well as the reach of most just starting to get into working with Linux.  Unfortunately, there isn't a middle of the road card.

I caved in with all the trouble I had with audio devices and made the decision to go with an M-Audio Delta 44.  It is a basic 4 in 4 out card with no preamps, no XLR inputs, no digital inputs, no midi.  The good news is that it only cost me $130 and it works in ALL of my Linux distributions...automagically to boot!  Sure I am going to have to end up buying a pre-amp for mic control and I already have a M-Audio 4x4 interface on the way for midi (this is automatically detected as well).  So it is more work to do hardware wise, but on the OS front, much less configuring to do.  

So if you don't have the cash for the RME Hammerfall line, really your only option is go with an M-Audio Delta card.

As for internal computer sound devices...sometimes you may get lucky!  The Dell machines at my job have something called SoundMAX and it too is automagically detected.

Geo

---

