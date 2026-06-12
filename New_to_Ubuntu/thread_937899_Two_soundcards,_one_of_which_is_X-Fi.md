---
title: "Two soundcards, one of which is X-Fi"
date: 2008-10-04
forum: New to Ubuntu
---

### Post by TheDesertDragon on 2008-10-04
Hello Ubuntu users! Nice to be here, this seems like a nice operating system and I'd like to learn a lot more about it but... I'm being severely halted.

I'm in sounddriver hell... :/

I have a Realtek AC97 and a SoundBlaster X-Fi Fatality Pro.
On Windows I have the Realtek one turned off, since I can't remove it physically as it is built in and, under Windows, would conflict.

Well, conflict's back and I haven't got a clue how to solve it. I've been trying for weeks now but no dice.

I have both the OSS drivers and the ALSA drivers. The OSS drivers immediately found my Realtek card but not my SoudBlaster card, unfortunately, and the Realtek card is disabled. I tried enabling it but not even that works. Ubuntu seems to ignore BIOS settings, amirite?

Any nice tech-gurus out there who can help me get my sound working? It's becoming rather annoying not having sound and I am *this* close to switch back to Windows and wait for ALSA's upcoming driver, which (hopefully, anyway) work. :S

And yes, I have searched a ton on the subject and tried the official drivers. No dice, still. I guess I'm just doing something simple wrong.

Thanks
 - A new user

---

### Post by terry_gardener on 2008-10-04
i also have a x-fi card and onboard soundcard. 

i couldn't get the x-fi card to work with some of my apps, and had to disable the onboard card in bios because ubuntu and windows just didn't like both drivers installed. 

i dont use the x-fi card now because i couldn't get it to work properly with all my programs. 

what i did was install ubuntu with onboard card enabled. ubuntu automatically installed the drivers for this as they are included by default and i didn't install the drivers for the x-fi card due to compatibility problems i experienced. 

sorry this doesn't solve your problems but just wanted to share my experience with the x-fi card and how i worked around the issue. 

if you dont mind using the onboard sound then might be worth reinstalling ubuntu and not installing the ossv4 for the x-fi card

---

### Post by TheDesertDragon on 2008-10-04
Actually it just might solve them!

I never thought of reinstalling whilst the card was enabled... >.<
I always thought I could make it detect it afterwards.

Haha, silly me!:rolleyes:

---

### Post by oldsoundguy on 2008-10-04
Due to the lack of co-operation from Creative in the creation and adaptation of drivers, most front panel sound cards (from the 5.1 live and up) do not WORK completely.  The front panels, which is what most use as the reason for BUYING the card in the first place, just are non functional.  The digital surround signal (digital out) works, but only in various programs.  The master control for the systems sounds on the desktop is stuck at 80% and can not be changed.

I would NOT wait for Linux to get these cards working 100%.  With as many chip iterations as has come out of Creative, reverse engineering is a nightmare for the developers. 

Creative MAY co-operate once Linux has a full 10% share of the OS market, but don't hold your breath.

I have 5 machines with such cards .. my mistake!  Seriously considering switching over to Turtle Beach when I can afford to. They, at least, acknowledge the existence of Linux!

---

### Post by jimbean on 2008-10-04
some bios`s have more than 1 option for disabling onboard sound

some have jumpers on the mobo that you have to jump or unjump

you might have to read your system board manual

if you dont have 1 you might be able to download off internet

or go into bios an read every option carefully

if it  has anything about sound try disabling that also

make sure to save bios settings before exit

---

### Post by bobpur on 2008-10-04
Another buyer of Hi-end Creative Labs cards here.

My workaround involves leaving the X-Fi card installed in Windows and using the onboard sound in Ubuntu. I just have to reach around and, physically, unplug the jack from one to the other and back.

This computer uses an ASUS M2NPV-VM mobo. I left the onboard sound set to "AUTO" in the BIOS.

A fairly cheap fix is the Diamond make of soundcards. Either the 5.1 or the 7.1 cards. I have a couple in service and they are linux friendly. You can get them from [www.newegg.com](www.newegg.com) for about $20 for the 5.1 and about $30 for the 7.1. These cards compared favorably with the Creative cards in a soundcard shootout done in Maximum PC a while back. The article said the Diamond cards lost out to the Creative only on top end (not by much).

Good luck.

---

### Post by TheDesertDragon on 2008-10-04
Thanks for the immensily helpful replies! :D

Well, I'm attempting what you've said, but rather than going with Ubuntu this time, I'm trying Fedora.

Turns out my father is a complete fanboi of Fedora and he's practically ORDERED me to try it now that he found out I'm trying to get into Linux. (I asked him about the problem, too)

I'll keep your advice in mind here. I suppose I'll need to do the same thing.

Again, thanks! :)

EDIT: I'll propably have to go back to Ubuntu again anyway. My future school uses it exclusively. (DTU in Denmark)

---

