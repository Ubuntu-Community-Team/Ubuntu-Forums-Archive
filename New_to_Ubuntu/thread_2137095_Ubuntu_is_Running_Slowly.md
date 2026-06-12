---
title: "Ubuntu is Running Slowly"
date: 2013-04-19
forum: New to Ubuntu
---

### Post by VicariousToast on 2013-04-19
Sorry if this is in the wrong section, I wasn't really sure where to put this.

I decided to try out Ubuntu because I heard it was faster than Windows XP, and since I have an old laptop, it was pretty slow (although, I uninstalled some of my old games that I stopped playing halfway through, and it's running faster now.). I downloaded Wubi, and it was set to 18 GB(I only have 42 GB of space available on my hard drive, it holds a total of around 70 GB), and let Ubuntu download overnight.

When I woke up, I found that my laptop had somehow been unplugged, and it had turned off. I turned it back on, selected Ubuntu, and waited while it installed (at least I think that's what it was doing.), and then I logged in. I left for a few minutes while it booted up. When I came back, it was sort of slow at first, but then it was going faster than XP unless I had more than one application open. After that, the speed started to fluctuate, firefox froze a few times, and I had to go on another computer to figure out how to kill a program when it freezes.

When I restarted and went to XP, it was much more stable, and it's average speed was faster, so I'm assuming that it's some sort of compatibility issue, or the way that I installed it.

Here are my system specs (this is all taken from dxdiag):

System Model: Toshiba Sattelite A40(this is strange, because this has never showed up as my system model. I did a google search and that is not my laptop.)
Processor: Intel(R) Pentium(R) M Processor 1.60GHz
Memory: 504MB RAM
Graphics: Mobile Intel(R) 915GM/GMS, 910GML Express


So is Ubuntu not going to run properly on my laptop?

Would I be better off with a different version(I've seen Lubuntu, Xubuntu, etc. and don't know if any of them would suit my needs better.)? I mainly use this computer for surfing the internet, and playing older games like Baldur's Gate, Star Wars: Knights of the Old Republic, and various DOS games through DOSBox. I'm also getting into programming, and now that I'm getting closer to finishing my C# course, I'm starting to think about learning some other programming languages. I plan on getting a career in video game design, and I would like to be able to design games so that they can be played on Ubuntu without having to use a special program to run windows applications. Besides that, from what I've heard, Ubuntu is a good OS for messing around with programming and such, so that could be fun.

What would be the best way to install Ubuntu? I would prefer to keep XP until I test out Wine to make sure all of the programs and games I have will work properly.

---

### Post by sudodus on 2013-04-19
Welcome to the Ubuntu Forums :-)

You need a flavour of Ubuntu with a lighter foot-print, Xubuntu 12.04 LTS or LXLE. Maybe it will be easier to install Xubuntu from the alternate iso file. See these links

[http://ubuntuforums.org/showthread.php?t=2130640](http://ubuntuforums.org/showthread.php?t=2130640)
[http://ubuntuforums.org/showthread.php?t=2135547](http://ubuntuforums.org/showthread.php?t=2135547)
[http://ubuntuforums.org/showthread.php?t=2125764](http://ubuntuforums.org/showthread.php?t=2125764)

---

### Post by Sef on 2013-04-19
<snip>

---

### Post by mörgæs on 2013-04-19
I'm not sure I understand the post completely. Have you only been using Wubi or also a real install in a dual boot?

Also, please run **sudo lshw > lshw.txt** and post lshw.txt in CODE tags.

---

### Post by Impavidus on 2013-04-19
With that amount of RAM don't use Ubuntu. Xubuntu will work better, you will be able to run a few programs simultaneously, or else Lubuntu.

When XP was still young Ubuntu was much faster, but a modern Ubuntu isn't faster than a ten year old XP. Well, that is when you forget about the virus scanner, that can still make XP slower than Ubuntu.

I never heard of laptops unplugging themselves during the night (would actually be a good way to save energy), but it may have damaged your system while installing updates. You gave it a night to do so, so I assume you don't have a very fast internet connection. Have you checked whether the package manager reports any errors?

---

### Post by VicariousToast on 2013-04-20
> [COLOR=#000000]I'm not sure I understand the post completely. Have you only been using Wubi or also a real install in a dual boot?[/COLOR]

[COLOR=#000000]Also, please run [/COLOR]**sudo lshw > lshw.txt and post lshw.txt in CODE tags.**

I used Wubi, but I un-installed Ubuntu yesterday because I was told that I needed a lighter version.
[COLOR=#000000]
> ...but it may have damaged your system while installing updates. You gave it a night to do so, so I assume you don't have a very fast internet connection.[/COLOR]

My download speed is only 90 kb/s max. It's usually around 70 kb/s unless the internet is being used on another computer. It was midnight by the time I installed it, otherwise it probably could have finished while I was awake.

> [COLOR=#000000]Have you checked whether the package manager reports any errors?[/COLOR]
No, I have no idea how to do that. I should have mentioned that I'm not too skilled with computers yet.

As soon as I find my blank cd-r discs I will install Xubuntu and see how it works, hopefully I won't have any issues.

---

### Post by Impavidus on 2013-04-20
Any system damage is irrelevant if you're reinstalling anyway. Power failures whilst downloading updates shouldn't really harm, the big trouble comes when the installation of updates is interrupted.

---

### Post by zrdc28 on 2013-04-20
You need to install lubuntu, I have a 1.6 gig tablet that is running lubuntu excellent, ubuntu on it was real slow. The better way to install it would be to put it on its own
partician. A  easy way to partician is with gparted that you can get from distro watch,

---

### Post by VicariousToast on 2013-04-21
I just finished installing Xubuntu, and it's working great. So far, it's a lot faster than XP, but I'm assuming it will slow down a bit with time like other OSes. Even then, I think it'll still be a lot faster. I also really like the UI.

I'm gonna wait until tomorrow to change the tag to "solved," just in case I start having issues of some sort when I start messing around with things.

Thank you for the help everyone!

---

