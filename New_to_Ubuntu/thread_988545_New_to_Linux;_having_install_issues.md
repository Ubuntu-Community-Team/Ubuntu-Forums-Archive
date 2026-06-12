---
title: "New to Linux; having install issues"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by Shadow_2014 on 2008-11-20
I'm sure you get a million of these threads, so I'm sorry about making a new one, but I just want to get some assistance without sifting through the forum and resurrecting an old related one. With that said, here's my issue.

So I tried installing Kubuntu and then Ubuntu. With Kubuntu I first tried running off the CD without installing, just to see how it runs. It would boot up, I'd get my new desktop and be able to see things responding to my clicks for about 5 to 10 seconds, at which point everything would completely freeze. Although my mouse pointer was still perfectly responsive, my desktop and whatever folder I had managed to open became my new, unresponsive desktop. I figured this was probably just because Windows was still on there, slowing everything down, so I installed regardless, after doing both the kinds of checks available from the install screen. When I installed, I did a full install, leaving no Windows partition. It was the same problem. Boot up, freeze, retention of cursor control. I figured maybe my computer wasn't good enough (it's four or five years old. Pentium 4, half a gig of ram, probably not a very good graphics card) but since I don't have a Win XP install disc at the ready, I figured I'd try installing Ubuntu. This time, I didn't even make it to the log-in screen after installing. So, I went back to the install process for Ubuntu where the first step offered online assistance. Luckily Firefox is included in the install, so now I'm surfing off the install CD. A very short-term fix. I'd kind of like to have an OS. Any suggestions?

---

### Post by Shadow_2014 on 2008-11-20
I hope it's okay to bump this so it doesn't get lost on another page... Any suggestions would be appreciated. I think awhile before this I may have had a virus on Windows. For a time my registry was kind of messed up. Is there any chance that it damaged my hard drive too much for it to work properly?

---

### Post by bennachie on 2008-11-20
There's something quite odd going on here. There is some history of the cursor freezing if you move the mouse or touch the trackpad at the wrong point during the start-up process, but I haven't heard of exactly the symptoms that you are experiencing.

I take it that you are now using a Ubuntu LiveCD for your surfing, and that you are not suffering the freezing that you experienced on the Kubuntu LiveCD? If so, that might imply a problem with the latter disk. Have you tried a clean install with the actual disk you are using now?

It seems unlikely that the graphics card is the problem, since you have been able to complete the installation process, but you might like to check exactly what you have in your system.

The system you are using is not exactly a powerhouse, but should work OK. You'll see better performance if you bump the RAM, but 512K should be just about enough to keep things running OK. You could try turning any desktop graphical effects off - go to system>appearance - to see whether there is an issue there.

A Windows virus might well have screwed up the previous Windows file system, but that shouldn't affect a clean Ubuntu installation in any way.

---

### Post by Paqman on 2008-11-20
> **Shadow_2014 said:**
> I hope it's okay to bump this so it doesn't get lost on another page... Any suggestions would be appreciated. I think awhile before this I may have had a virus on Windows. For a time my registry was kind of messed up. Is there any chance that it damaged my hard drive too much for it to work properly?

Most likely is that your motherboard has issues with Linux. Do you know what model it is? Try searching here and Google for the model and see if others have fixed the issue on their machines.

In the meantime you could try booting with some options to disable some of the likely sources of trouble. When you start up and the Grub menu appears hit "e" to edit the Grub boot command and add:
```

noapic nolapic acpi=off

``` 
to the end of the longest line, then hit "b" to boot. You'll lose some power management features, but hopefully it'll give you a stable desktop. If it works, you'll need to add those options permanantly to your Grub menu by editing /boot/grub/menu.lst (scroll way down to the bottom to see the actual menu entries)

---

### Post by hyper_ch on 2008-11-20
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by Shadow_2014 on 2008-11-20
> **bennachie said:**
> I take it that you are now using a Ubuntu LiveCD for your surfing, and that you are not suffering the freezing that you experienced on the Kubuntu LiveCD? If so, that might imply a problem with the latter disk. Have you tried a clean install with the actual disk you are using now?

A friend burned Ubuntu and Kubuntu to CDs, so I would assume they are LiveCDs. I tried a clean install with both Kubuntu which was the one that froze and Ubuntu which is the one I'm surfing with atm but which will not load at all.

> **bennachie said:**
> You could try turning any desktop graphical effects off - go to system>appearance - to see whether there is an issue there.

I don't know how to access these options without loading the platform itself. Do I do this from the Grub menu?

> **Paqman said:**
> Most likely is that your motherboard has issues with Linux. Do you know what model it is?

No idea. As I say, I've had it for quite awhile, and I know next to nothing about hardware.

> **Paqman said:**
> In the meantime you could try booting with some options to disable some of the likely sources of trouble.

I'll try this now.

---

### Post by Eisenwinter on 2008-11-20
> **hyper_ch said:**
> Or in short terms: Help others to help you ;)
+1. This makes things easier for all of us :guitar:

---

### Post by Slug71 on 2008-11-20
System--Appearance is within the Desktop. 
Are you using the LiveCD to surf or are you using a different PC? I would download the ISO again yourself and burn it. Perhaps the CD your friend made has a corruption. Download both 8.04 and 8.10 and try both.

---

### Post by Shadow_2014 on 2008-11-20
I'm surfing off the LiveCD. I have no desktop, as it freezes when it loads. At this point, it freezes before then, actually. There's a screen which has desktop wallpaper in the background and four icons on it which I assume represent my internet connection, hard drive and whatnot, and it freezes there. I used to be able to click once and it would proceed to the desktop before locking up, but perhaps I'm just not clicking quick enough.

When I load the LiveCD, I have 5 or 6 options. These are to use (K)Ubuntu without installing, to install, to check the CD for problems, to check the CD for problems, and a couple other ones. I've checked the Kubuntu disc, but since it was a lengthy process I didn't check Ubuntu. I'll try that next. Anyway, when I go to install the platform, the first step is to choose the language to install in. On this screen, there's a link to read the Release Notes and this loads Firefox.

I technically have Kubuntu installed right now, but I'm using the Ubuntu LiveCD to get help here. I have no way of burning an iso as I have no software. At this point I'd prefer to get Ubuntu working, as opposed to Kubuntu as it runs a lot smoother, or so it seems having used Firefox alone on both platforms.

As for changing things at the Grub boot command, I haven't seen any prompt where I could type anything. I don't know what the Grub screen looks like, but I can assume, and I haven't seen it. I even tried pressing 'e' every single time the screen changed. Leaving the CD in is the only time I'm prompted to do anything.

---

### Post by Paqman on 2008-11-20
> **Shadow_2014 said:**
> 
As for changing things at the Grub boot command, I haven't seen any prompt where I could type anything. I don't know what the Grub screen looks like, but I can assume, and I haven't seen it. I even tried pressing 'e' every single time the screen changed. Leaving the CD in is the only time I'm prompted to do anything.

Sorry, I should have been a bit more descriptive.

Grub looks like this:
[IMG]http://i80.photobucket.com/albums/j180/brthomas503/grub.jpg[/IMG]

You'll only get it when you're booting into a fully installed copy of Ubuntu (ie: not the LiveCD). As you can see in that image, you can use the arrow keys and "e" to edit the actual command used to launch Ubuntu or other OSes.

That will take you to a screen like:
[IMG]http://www.linuxconfig.org/images/f/fa/Editgrubbootoption.gif[/IMG]

where you can add in those options to the end of line starting with "kernel" and have a go at booting. As mentioned earlier, to make those options permanent you'd also have to edit a config file.

---

### Post by handydan918 on 2008-11-20
Two thoughts:
1) The live cd is a neat piece of magic. Maybe it doesn't work on your system. There is an "alternative install" cd image that you can download and burn. It doesn't give you the nice GUI, but it isn't to bad, either. 
2)Windows, by virtue of it's memory (mis-)management, thrashes hard drives. if You had trouble with windows, and then you installed Ubu, and have trouble with that, too, well....
ESPECIALLY if the live cd works OK, you may just have a hard drive issue.

I'd consider stuffing a new one in there, and see what happens with another install attempt.

---

### Post by Jesan Fafon on 2008-11-20
If your problem is occurring when running your machine off the live CD then it may be a throughput issue on your CD drive.

However, it sounds like you continued to have this problem after installing Kubuntu/Ubuntu? That's interesting.

Is this issue still happening on your live CD? I'm assuming your story about opening Firefox from the install portion is to explain how you got around your problem?

I've had issues with Live CD's frequently, and its due to my CD drive's less than stellar parts... too slow etc. Live CD's hang up on me all the time.

Also, Ubuntu is much faster, but its the *same* as Kubuntu, if you've got one, you can install the GUI for the other at a later time. Install Ubuntu as it will use less resources.

---

### Post by Shadow_2014 on 2008-11-20
Okay, I definitely haven't seen the Grub screen. Is that supposed to come up every time you boot? Because it doesn't for me. Last time I tried loading up Ubuntu without the LiveCD after installing, it went through its loading screen and then to a solid beige background, at which point it played some brief sound through my speakers as if it was going to load, but did not load anything but the solid background colour. I checked the Ubuntu CD for issues, and it said there were no problems; tested memory, still no problems. Perhaps I'll just have to suck it up and buy a new hard drive. Would more ram help at all, or is the issue more complex than that? Because I hear a gig of ram is only about $30 over here.

---

### Post by Jesan Fafon on 2008-11-20
RAM may help, but i doubt it.

I install Ubuntu on old computers I find at thrift stores, upgrade them, and resell them as a hobby. Never seen this happen before.

I think its got to be your hardrive. Its the only thing I can come up with... but you said you had issues running the live CD? That would be due to RAM requirements and I remember reading somewhere that it took ?756mb? of RAM for the Live CD's to run well. So RAM might be your issue, but if you can install it from the splash screen, where the other options are, you should be fine if its only the RAM.

As for grub, it should be displayed when your machine is booting up, after the machine POST's and detects hardware, but before Ubuntu loads. I've had a lot of problems with Grub, and I'd be glad to help.

I'm assuming you only have one hardrive, correct>?

---

### Post by Paqman on 2008-11-20
> **Shadow_2014 said:**
> Okay, I definitely haven't seen the Grub screen. Is that supposed to come up every time you boot? 


Yes, it is, but no fear. We can do this by editing Grub's config file. Boot into recovery mode and type:
```

nano /boot/grub/menu.lst

```

Then scroll down to the bottom where you'll see an entry like the second image I posted. Add the options to the kernel line, Ctrl-X to save and reboot the machine.

> 
Perhaps I'll just have to suck it up and buy a new hard drive. Would more ram help at all, or is the issue more complex than that?

I highly doubt either hard drive or RAM faults are the problem here.

---

### Post by Shadow_2014 on 2008-11-20
I can't boot into recovery mode. I can't boot up at all. Where would I type that line of code if I could though? Grub doesn't open before Ubuntu attempts to load.

And yes, just one hard drive.

---

### Post by Paqman on 2008-11-20
> **Shadow_2014 said:**
> I can't boot into recovery mode. I can't boot up at all.

I thought your problem was that it would boot, but then later lock up?

---

### Post by Shadow_2014 on 2008-11-20
Well, it would in Kubuntu. But I'm trying to get Ubuntu up and running, which won't make it quite that far. I get the background colour, but no aspect of the desktop loads. Though it does make the start-up jungle kind of sounds which would indicate it's nearly loading up.

---

### Post by Paqman on 2008-11-20
What happens if you spam the Esc key while booting? Do you get Grub?

---

