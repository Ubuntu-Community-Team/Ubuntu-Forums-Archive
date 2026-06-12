---
title: "The Easy Way Out"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by geoman on 2008-07-09
Hi kids,been using ubuntu for a year now,couldn't get my head around installing hardware cos I relied on windows doing it for me in the past.After many many many problems with XP ( things just suddenly not working, many many many re-installs/formats) , I was quite familiar with the routine but was scared of the limited automated help with ubuntu, so left the remnants of XP on my second hard drive. Then my mouse packed up and was replaced with a cheapo wired generic optical mouse (ps2) which just sat comatosed in the middle of the screen. OK, rant ,rave , bl***y ubuntu etc etc. Searched forums for weeks on end, all to no avail ,no easy answers so kept plugging away with the knackered trackball mouse. Then one day I needed to check out a windows cd rom for a mate & booted up XP. After the usual 30 min wait it was running, and well, why not try the optical mouse again.OK that works ah blissful smooth operation, all buttons working, just like a real one! Job done,reboot to ubuntu but forgot to swap back to the crappy old mouse.Ubuntu running, optical mouse running , me happy ! Don't know what happened there but who's complaining. All you other computer (linux) illiterates with hardware problems might wantto try it too !:lolflag:

---

### Post by WonderStivi on 2008-07-09
You have to boot up *after* connecting a PS2-mouse. If your computer's already on when you connect it, it won't work until next reboot. This might have been you problem, it might not have been. At least it works now :)

---

### Post by ibuclaw on 2008-07-09
To load devices/modules while Linux is running, use **modprobe** ;)

ie: to enable your PS2 Mouse

```
sudo modprobe psmouse
```

The same goes for **rmmod** (or "modprobe -r") too.
I could save power on my laptop by disabling bluetooth and webcam modules.
```
sudo rmmod bluetooth
sudo rmmod uvcvideo

```
This means that any applications that wishes to use the devices won't function anymore until they're re-enabled. (ie: webcam and cheese)

Then reenable them later on when I plug back into the AC.
```
sudo modprobe bluetooth
sudo modprobe uvcvideo

```
And it works again! :popcorn:

Regards
Iain

---

### Post by geoman on 2008-07-09
Tried a zillion times, all possible combinations ( before,during,after,standing on one leg facing magnetic North etc.)  when coming out of/ rebooting to ubuntu,it never worked. Seems that XP saved config to bios which ubuntu could then detect ( thats my theory & I'm sticking to it ). Glad to see that Microsoft did something for ME for a change,after years of filling their bank account!

---

### Post by ibuclaw on 2008-07-09
> **geoman said:**
> Tried a zillion times, all possible combinations ( before,during,after,standing on one leg facing magnetic North etc.)  
Don't forget the blindfold and patting your head while rubbing your belly :D

Perhaps you didn't modprobe the right device?

To display the list of currently loaded modules on your system, run this semi-one-liner command.
```
for i in `find /sys/ -name modalias -exec cat {} \; 2>/dev/null`; do /sbin/modprobe --config /dev/null --show-depends $i 2>/dev/null; done | rev | cut -f 1 -d '/' | rev | sort | uniq | sed 's/\.ko//g'
```

Scroll up and down looking for the word "mouse" (or something that may hint the word).
And with a bit of luck, to modprobe the device it should be using that name **minus** the .ko bit on the end.

ie: With my computer
**psmouse.ko**
```
sudo modprobe **psmouse**
```

[EDIT]
updated the command to remove the ".ko" bit. Try it now.

Regards
Iain

---

### Post by geoman on 2008-07-09
Seems to me that the greatest bugbear of linux still seems to be the automation aspect. Lotsa people (like myself ) suffer from TECHNOFEAR !, & simply don't need the hassle of relearning skills when an easier ( though more expensive/ potentially insecure) option is available off the shelf .Sad but true, not everyone can afford the time to sit plugging away at a computer when all they want is to surf or have fun .So to all you out there who find this stuff an end in itself, get busy, automate & take over the (computer)world. OK, gotta go to work now...

---

### Post by geoman on 2008-07-09
How rude of me ! Thanks a lot guys ( & gals)

---

### Post by ibuclaw on 2008-07-09
No probs geoman.

Just remember, you are never alone. And there is a large community of people here who are very enthusiastic to help you with almost all problems (and to ease your transition to learning to administer your system).

Regards
Iain

---

