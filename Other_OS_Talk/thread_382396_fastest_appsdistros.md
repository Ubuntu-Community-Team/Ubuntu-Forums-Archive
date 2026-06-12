---
title: "fastest apps/distros?"
date: 2007-03-12
forum: Other OS Talk
---

### Post by billdotson on 2007-03-12
I am using XP SP2 and Ubuntu currently.  I am on a slower PC right now as my newer system is down for maintenance (4 month old MB and PSU started acting funny so i am waiting to get replacements back) 

The system specs on this Dell are 512MB RAM, 1.6GHz P4 processor, 40GB IDE HDD (I am guessing 5400RPM.. :confused: since the PC is 5 years old.)
I think this XP install has been running for 3 years and is only restarted when something locks up or when an update or some soft of software is installed.

XP is running a bit slow on this PC and when using my PC before it had to get replacement parts Ubuntu was running pretty slow.. which is odd cause I have a Core 2 Duo system w/ 2GB Corsair 800MHz RAM.  Ubuntu is loaded onto my external USB HDD- [http://www.newegg.com/Product/Product.asp?Item=N82E16822144079]("http://www.newegg.com/Product/Product.asp?Item=N82E16822144079") although mine is 300GB not 320GB (actually only like 279GB technically.. you know how HDD space is..)

I do not know if my external HDD is really that much of a bottleneck to slow Ubuntu down like that.  The external is the same RPM as my internal and I do not know how much USB 2.0 can bottleneck a HDD.

Anyway, I was wondering what are the fastest OSes out there that would be suitable for desktop use.  I have heard that Xubuntu is pretty quick because it uses Xfce instead of Gnome.  I have also heard that the BSD flavors specifically for desktop use are pretty quick.  I have also heard that (once you get it set up and running) Gentoo is the quickest Linux distro.

So.. what would be the quickest desktop OS that has a GUI (one that is actually useful i.e. not just a toy)?
Also, what would you say are the fastest GUI apps (that are also useful) within these categories:
   web browser
   word processor
   spreadsheet
   slideshow app
   video editor
   video player
   video transcoder/encoder
   music player
   sound recorder
   image editor
   image viewer

Also, as CLI apps are clearly always going to be faster and easier on system resources than GUI apps what CLI apps would you recommend for those categories above (apart from the obvious things like a video editor or image editor where a GUI is required)

I would like to get a really fast distro and get it setup w/ the fastest apps for general purposes such as the categories mentioned above.  Even though my system is capable of running the resource hog apps like firefox, openoffice and others if I had programs that opened faster I could get more stuff done as I would be waiting less for programs to open, etc.

Also, if I ever got my hands on an older PC or someone had an old PC that they felt was too old to be useful I would have an OS and apps that would be able to make the PC useful again.

---

### Post by fuscia on 2007-03-12
dillo is pretty fast, but not full featured. opera is faster and lighter than firefox and is pretty full featured. xine-ui would take care of both video and audio. a window manager will be faster than a DE. the fastest i've found are openbox, icewm and e17. feh is great image viewer and can set your wallpaper, as well.

---

### Post by billdotson on 2007-03-12
I have not been w/ Linux for very long at all.. only about 5-6 weeks or so so could you please tune me in as to what a window manager is vs. a desktop environement?

Yeah when I have firefox on here (running it from a USB flash drive) it gets really slow when I add extensions to it.. the extensions/themes I am using in firefox are:
stumbleupon
forecast fox
foxytunes
tabmix plus
talkback
blueice(theme)
reminderfox
adblock plus
password hasher
answers (alt-click)
and then I have about 25 search engines loaded from the mycroft project for the search toolbar

and it is so SLOW.  Without the add-ons firefox = nothing IMO, and I would use Firefox over Opera all the time if it wasn't such a slow resource hog.  Opera doesn't have as much functionality (I really miss the the alt+click features for answers.com) but I have found many widgets that do some pretty useful things.  The good point about the widgets is they don't take up browser space unless you launch them where as add-ons for firefox tend to be put in toolbars and clunk up firefox a bit.

---

### Post by fuscia on 2007-03-12
> **billdotson said:**
> I have not been w/ Linux for very long at all.. only about 5-6 weeks or so so could you please tune me in as to what a window manager is vs. a desktop environement?

i really don't know. i know which are which, but i don't know what distinguishes them, really, other than DEs do more. the three DEs each have window managers: kde has kwin, gnome has metacity (though you can substitute others) and xfce has whatever tf it has. i think the idea of the DEs is to have more intergration between the apps and appearance than one would find in a wm. a window manager supposedly just manages the placement of windows, though many do more than just that (i still think e17 is more of a DE than a wm). if a DE were a burger, it would be a 'chopped sirloin' with the freshest veggies, mouth watering aged cheddar and 'our special sauce'. with a wm, it's "here's your burger. there's ketchup."

---

### Post by igknighted on 2007-03-12
> **fuscia said:**
> i really don't know. i know which are which, but i don't know what distinguishes them, really, other than DEs do more. the three DEs each have window managers: kde has kwin, gnome has metacity (though you can substitute others) and xfce has whatever tf it has. i think the idea of the DEs is to have more intergration between the apps and appearance than one would find in a wm. a window manager supposedly just manages the placement of windows, though many do more than just that (i still think e17 is more of a DE than a wm). if a DE were a burger, it would be a 'chopped sirloin' with the freshest veggies, mouth watering aged cheddar and 'our special sauce'. with a wm, it's "here's your burger. there's ketchup."

Haha, i suppose a fair analysis.  How about this analogy:  A wm is like a burger, it's your primary course in a meal.  It is the important part.  A DE is like your whole dinner.  There is a wm (your burger) but also default apps, config tools, services, a display manager (gdm or kdm) that is more feature rich and other such nicities.  Of course, to get this nicer dinner it costs you.  In relation to your computer, it costs you resources.  The real question it boils down to is how much of your system resources do you want to donate to a pretty desktop and extra features, and how much do you want to go to your apps.  High end PCs really don't show much difference, but older PCs with less ram and slower processors will show signs of slowing with a full DE like KDE or Gnome.  Using just a wm like fluxbox would reduce the eye-candy, but increase system response time and let apps run quicker.

---

### Post by fuscia on 2007-03-12
KDM or GDM = valet parking.

---

### Post by tigerpants on 2007-03-12
> **billdotson said:**
> 
I would like to get a really fast distro and get it setup w/ the fastest apps for general purposes such as the categories mentioned above.  Even though my system is capable of running the resource hog apps like firefox, openoffice and others if I had programs that opened faster I could get more stuff done as I would be waiting less for programs to open, etc.


For net stuff, BSD running Opera = lightening fast.
For all other apps, slackware or a bespoke install of gentoo (set aside a few days) :) 


I've tried about 20 different distro's so far, and Slackware is by far the quickest on my system, for opening apps and general doodling around with day to day things. I've not tried Gentoo properly (just distro's based on gentoo) and found them a little bloated. But I understand a clean install of pure Gentoo is very quick.

BSD wins hands down for internet stuff. Web pages load in milliseconds. The speed difference is incredible. Its fast in Linux, but BSD is just amazing.

TBH, install apps from source and building them yourself will generally get you a faster more stable set up. Depends on how much spare time you have to do this. And if you use E17, Flux, IceWM or Openbox as a window manager, you'll have an even quicker system.

---

### Post by billdotson on 2007-03-12
well I have a Core 2 Duo system w/ 2 GB DDR2 800MHz RAM and an nVidia 7800GT and Ubuntu gets too slow for me to deem acceptable sometimes.  It sometimes takes 3-5 seconds to show the dropdown menu when I click on the applications button on the panel.  Not acceptable.

---

### Post by Crashmaxx on 2007-03-12
> **billdotson said:**
> well I have a Core 2 Duo system w/ 2 GB DDR2 800MHz RAM and an nVidia 7800GT and Ubuntu gets too slow for me to deem acceptable sometimes.  It sometimes takes 3-5 seconds to show the dropdown menu when I click on the applications button on the panel.  Not acceptable.

Do you have the nvidia driver installed? And enabled in xorg.conf?

---

### Post by Tipo on 2007-03-12
Zenwalk has been the fastest distro that I've tried. It uses the XFCE environment...

However, I've found that upgrading it, especially the kernel, results in quite a few problems for me.

---

### Post by chippy99 on 2007-03-12
The fastest distro I have used (and still do) is Gentoo. The trade off is it will take at least 3 days to get everything you want to use installed due to all apps having to be compiled on your system whereas Ubuntu just installs  precompiled binaries. Also the learning curve is very steep but it does have excellent documentation and is a good way of getting a deeper understanding of Linux.

---

### Post by billdotson on 2007-03-12
yes I have the nvidia driver installed and I am pretty sure it is configured in the xorg.conf or otherwise i wouldn't have been able to run beryl.

---

### Post by zubrug on 2007-03-12
Try an ubuntu server install and then add xfce (not xubuntu-desktop, got this idea from pricechild) and your app's and menu's will open so fast you can hear the screen crackle.

---

### Post by RAV TUX on 2007-03-12
moving to the other OS forum

---

### Post by TheRingmaster on 2007-03-12
If you like emulators, Zsnes is the fastest app you will ever use. This is because it is written in pure machine language.

---

### Post by igknighted on 2007-03-13
> **billdotson said:**
> yes I have the nvidia driver installed and I am pretty sure it is configured in the xorg.conf or otherwise i wouldn't have been able to run beryl.

Try disabling Gnome compositing.  This causes all kinds of hell when gnome and beryl both try to do stuff to the windows (like shadows or what not).  This is probably where some of your mess is coming from.  Also, in beryl you might quicken the animations (or remove them) that occur when a menu is clicked.  Look at my specs in my sig, my comp is nothing compared to yours and I don't notice anything like this at all.  Even with beryl my menus open instantaneously.  Try running "top" in the terminal to see if anything is eating lots of resources.  Also, leave top running when you click the menu to see if something freaks out and causes the delay.

---

