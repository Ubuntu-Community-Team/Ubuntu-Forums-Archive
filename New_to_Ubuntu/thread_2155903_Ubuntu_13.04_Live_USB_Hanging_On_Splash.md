---
title: "Ubuntu 13.04 Live USB Hanging On Splash"
date: 2013-06-19
forum: New to Ubuntu
---

### Post by Gnawnsense on 2013-06-19
Greetings!

I recently made the hop from Windows 8 to Ubuntu and have been loving it so far. I originally decided to try out the 12.04 LTS release when I was first stepping into all of this, and things worked out great with 12.04 and my hardware. I was able to get my AMD drivers running great, was feeling comfortable in the migration, and was having no issues. Earlier today, I decided I'd try updating to 13.04 to see how thew newer releases were looking.

I originally tried to update via the update manager by going 12.04 => 12.10 => 13.04. However, when I upgraded from 12.04 => 12.10 and was prompted to reboot after downloading files, I got a flashing purple screen of death that I absolutely could not find a solution for. After reading a bit, it seems the update tools is infamous for causing problems at times, so I opted to go the Live USB route, just due to not having any blank DVDs at the house.

So I downloaded the 13.04 ISO, threw it on a USB, and tested the Live USB out on my Windows laptop before throwing it into my machine running 12.04. The Live USB worked flawlessly with the laptop, so I figured it was good to go. I plugged it into here, set my boot options to USB, and got prepared for the upgrade.. and that's where I ran into my brick wall.

Basically, what's happening is I will boot from the USB, and everything appears fine. I get to the purple screen with the white* Ubuntu* logo with the white/orange dots below it. And it hangs on this screen from this point on. It doesn't freeze, the dots will keep cycling from orange to white and back again, but the screen never updates and the Live CD never finishes booting.

I did a quick Google search and found a few suggestions advising to start off the USB, go into the boot options included on the Live CD, and try a few of the options including booting with the *"nomodeset"* option. I tried every option available on the list and still had no success. The Live CD will attempt to boot, and then never take me to the desktop. I also tried just using the Live CD without installing with no success, and going straight to installation, and still no success.

Any assistance would be greatly appreciated!

**TL;DR:** Already have 12.04 installed. Made Live USB for 13.04 and it hangs on the purple Ubuntu splash screen. Tested Live USB on Windows laptop, no issues. Tried options such as *"nomodeset"* to no success as advised from Google searches. Feeling completely lost.

---

### Post by Gnawnsense on 2013-06-20
Quite an interesting issue.

I tested the USB on my laptop and it booted up flawlessly and very quick. I finally attempted the USB on my desktop again and had walked out of the house for a bit, came back about an hour later and it had finally started up. The entire session was extremely slow, tho. Much moreso than I had experienced before. I did, however, get 13.04 installed properly. 

I just wish I knew why a Live USB of 12.04 started instantly on my desktop, the Live USB of 13.04 started instantly on my laptop, but the same 13.04 Live USB was a snail.

---

### Post by MidnightGrey on 2013-06-20
Your USB port may be at fault,
your laptop may have been using a USB3.0 connection,
while your PC was plugged into a USB2.0? or lower?

---

### Post by Gnawnsense on 2013-06-20
> **MidnightGrey said:**
> Your USB port may be at fault,
your laptop may have been using a USB3.0 connection,
while your PC was plugged into a USB2.0? or lower?

I had tried 4 different ports on the desktop. Both the laptop and desktop are using 2.0. But it might of honestly just been some random fluke, if those exists.

---

### Post by sudodus on 2013-06-20
I think it is a driver issue. You wrote

> I was able to get my AMD drivers running great

and there are well-known issues with AMD hardware. Is it AMD graphics? Have you tried proprietary drivers yet? If so, does it make a difference?

---

### Post by Gnawnsense on 2013-06-20
> **sudodus said:**
> 

and there are well-known issues with AMD hardware. Is it AMD graphics? Have you tried proprietary drivers yet? If so, does it make a difference?

While there are well-known issues with AMD hardware, I can't help but feel whatever was done was a step backwards with some changes in 13.04, tho I don't know what they are. I've never encountered an issue with a Live CD (up to 12.10) due to hardware or driver issues. After the Live CD installed and going to the first boot I always ran into display issues with an AMD, but never during the live CD.

I do think you're right, though.

When I finally got 13.04 installed and I tried selecting my drivers in the additional drivers tool I was having difficulty even having the computer register my selection. The entire experience as an AMD user on 13.04 is miserable, when on 12.04 there are no display issues before using restricted drivers, and then it's only a click away to get my proper drivers working, and then one command in terminal to enable hardware acceleration. 

I imagine if I wasn't such a complete noob to all of this I could of dinked around and got it working. But my aim coming to Linux is to try and do it from the perspective of your average computer user, and how "out of the box" the experience is. 12.04, with my setup, is completely out of the box. 13.04 was a headache, and I do think it was all driver related.

---

### Post by sudodus on 2013-06-20
Ubuntu 12.04 has LTS, long time support. LTS versions are released in April even years, and are better debugged and polished than the other versions. LTS versions are also recommended for production platforms, unless you need some new driver or program version.

I use 12.04.2 (point release 2) as my main system, but I am also helping to test Saucy (13.10). Since I am also interesting in keeping old hardware running, I have seen many cases, where working drivers have been dropped in new versions, and my recommendation is to use LTS versions particularly for old hardware, and not upgrade until it is necessary (near the end of the support).

If you want to play around and still have a stable system, you can dual boot the LTS version and the newest version.

---

