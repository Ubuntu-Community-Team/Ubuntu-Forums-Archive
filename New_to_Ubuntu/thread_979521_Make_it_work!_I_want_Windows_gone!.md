---
title: "Make it work! I want Windows gone!"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by HiltonJ on 2008-11-12
I'm desperately trying to switch my family computers from Windows to Linux. These computers are used by 6 separate adults and 4 children, none of whom have a bloody clue besides myself. So whatever is on here needs to work, needs to be simple, and needs to not break.

Ubuntu is supposed to fit that bill.

Unfortunately I've been caught in the whole Radeon 9600 thing going on, plus some other issues...

The basic specs of the problem system:
AMD Athlon XP 2400+ on an ASUS A7N8X board, 1.00 GB RAM.
ATI Radeon 9600 Pro (I think it's a Pro, anyway)

FGLRX refuses to acknowledge my card. The open source drivers work, but if desktop effects are turned on, the system freezes at some random point 1-10 minutes after login.

However, even with desktop effects turned off, I have STILL had freezes.
- One was seemingly random, other than a moderate amount of screen activity: a window being moved, and accidentally hit a menu key so a menu was fading in - froze halfway through the fade.
- Another freeze (twice in fact) was while someone was playing an online Java-based MMORPG. The applet in question handles a fair amount of graphics, but all in 2D.
- Two other freezes that I don't have details on, as I wasn't here.

Every time the freeze-up type is the same (including the freezes that happened with Desktop Effects turned on): A complete halt of all on-screen movement; any animations, fades, etc in progress halt completely. However, the mouse cursor still moves. I understand this is typical of a GPU freeze on ATI cards.

Now this same system runs Windows XP most of the time, and has ZERO stability issues. Never had a freeze or lockup, no crashes, nothing. Even plays high-end 3D games that it has no right running. So unfortunately, it's not the hardware. It's Ubuntu or the display drivers.


Please help me to correct these issues so I can drop Windows, which is causing nothing but grief. Yes, it's stable, but its causing other issues that I'm tired of dealing with.

---

### Post by tuxulin on 2008-11-12
what version of ubuntu are you using ?
is your g/card supported ? (bunty 8.10 might not support your model)
how did you install the g/card drivers ?
have you tried Envy-ng ? (thats if you are running bunty 8.04)
have you tried turning all desktop and other effects off then test to see
if you can recreate the problems?
have you got the latest updates ?
what type of monitor do you have ?

maybe if you are a little less demanding, then just maybe you will
attract more responses... than stating 
> Make it work! I want Windows gone!

Good Luck
Tux

---

### Post by jaytek13 on 2008-11-12
I've heard people with radeon cards have had good success in using the program Envy to install the drivers, but I don't have any experience with this myself.

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by HiltonJ on 2008-11-12
I apologize for the topic. It wasn't intended that way; and I was tired and frustrated.

Ubuntu 8.10 has apparently dropped R300 support (including my Radeon 9600), and FGLRX also does not seem to support the card. Where does that leave the many users with R300 video cards? What are we to do? There seem to be numerous bug reports and threads on this, with no resolution that I've found.

Is it possible, perhaps, to force-install the open source drivers from an older version of Ubuntu which did work?

Or else, can someone *don't hit me!* suggest a different distro with which I might have better luck? (Keep in mind the absolute required user-friendliness for the other 8 illiterates in the house)

---

### Post by sharkster2007 on 2008-11-12
I briefly defected to "Mandriva Linux One 2009" (Dont confuse with "Mandriva Linux Free" as it is different). Before I returned to Ubuntu 8.10 (I was trying 8.04LTS but 8.10 was a week away from being released at the time) 

This Linux Distribution automatically set my drivers up for me without having to do anything, it is also free to download. (It is based on .rpm files though "Red Hats package manager", ubuntu is based on .deb files "Debian's Package Manager")   

I do not know whether this would support your graphics card though, but does a lot of the work for you. :-)

Or you could try Ubuntu 8.04LTS (the previous one), this may still support your card, though you would probably have to use older Nvidia driver's i don't know how to set them up for 8.04LTS either, Sorry.

---

### Post by zombiepig on 2008-11-13
> **HiltonJ said:**
> 
Ubuntu 8.10 has apparently dropped R300 support (including my Radeon 9600), and FGLRX also does not seem to support the card. Where does that leave the many users with R300 video cards? What are we to do? There seem to be numerous bug reports and threads on this, with no resolution that I've found.


That's definitely not true - I'm using a laptop with a radeon 9600 in it with 8.10 and the open source drivers, and everything works perfectly. IMO, the R300 is probably the best supported card in linux - even working better than the intel 965. My advice is to drop the fglrx driver and stick with the open source one. 

Anyway, I don't think it's the video driver causing problems - it must be something else in your machine!

---

### Post by HiltonJ on 2008-11-14
I doubt the machine accusation. This machine runs Windows XP stably, handles 3D games that it has no business running.

The only other times I've ever had GPU lockups when I test-installed Vista; the Aero interface would cause lockups after a few minutes (much like Ubuntu's Desktop Effects does).
:confused:

---

### Post by Vadi on 2008-11-14
When you're just booting, you have an option to boot either ubuntu, xp, or other stuff. Select the "memtest" entry there, and leave it running for the night.

If you come back in the morning with errors listed, your RAM is corrupted, and this could be one of the reasons.

---

### Post by LowSky on 2008-11-14
Do you really need desktop effects? You're running a rather "old" computer, those effect will just slow things down. And games and things like flash and GoogleEarth will not run properly without making a lot of small system changes

You also said you need the computer to "just work" and from my own knowledge Compiz is going to cause a few headaches rather than smiles.

Just stick with a basic desktop, or switch back to 8.04 which has 3 years of updates and might support your hardware better.

---

### Post by sdowney717 on 2008-11-14
Zoombiepig,
Can you run google earth with your 9600 on the open source drivers?
And I mean run it well.

---

### Post by HiltonJ on 2008-11-14
I can handle not having desktop effects just fine.

My actual problem, if you re-read the post, is that I have **continued** to have crashes with Desktop Effects disabled, albeit less often. Two crashes I was present for were apparently graphics related: one while someone was playing a Java-based (not Flash) online game w/ lots of little 2D graphics, and the other while a lot of little things were happening on screen (moving window, menu fade in, animations, etc all at once).

Hence why I think there are problems with the drivers; still problems even with DE disabled.

---

### Post by eternalnewbee on 2008-11-14
Hi there HiltonJ.
I've read in these forums that Linux Mint comes highly recommended for absolute newbees, who who know nothing about linux. That could be a great alternative for you. It's based on Ubuntu.
Check it out: [http://www.linuxmint.com/rel_felicia_whatsnew.php](http://www.linuxmint.com/rel_felicia_whatsnew.php)
Good luck to you. And welcome to the Ubuntu community):P

---

### Post by Vadi on 2008-11-14
I uh highly doubt that issue is solved there.

---

### Post by eternalnewbee on 2008-11-14
> I uh highly doubt that issue is solved there.
You're right Vadi. But I was thinking about all those family members
> I'm desperately trying to switch my family computers from Windows to Linux. These computers are used by 6 separate adults and 4 children, none of whom have a bloody clue besides myself. So whatever is on here needs to work, needs to be simple, and needs to not break.

Once again you're right though.

---

### Post by Victormd on 2008-11-14
I would give envy-ng a try (you can get it in synaptic - search envyng). I've used it both with ATI (had to) and NVIDIA (wanted to) cards and it worked great with both.

---

