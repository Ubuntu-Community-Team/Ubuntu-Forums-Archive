---
title: "Dual Booting XP and Ubuntu"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by awseft on 2008-04-28
Tried Ubuntu a while ago and had some issues. I've been told they've been dealt with now by a friend so I thought I'd ask here. :)

I have a Dell E1505 w/ an 80G HD. Issues I had:

1) It did not recognize my dual core processors
2) It did not scale back my mobile processor (Computer ran burning hot)
3) Didn't have a way to have multiple wireless profiles (home/work/secured networks)
4) Never go the video card drivers correct (Dell 256MB ATI X1400)

If I install using the WUBI how hard will it be to remove from my computer and get just windows boot back? How large of a partition should I give Ubuntu (I have music/backups on my windows side)?

Edit: If you search my post history you'll see the video card fun. Maybe that can help get me to do it right the first time.

---

### Post by Helios1276 on 2008-04-28
well for 2 of that list ;)

1. the x1400 performs lovely on Hardy now

2. approx 15/20 gb for hardy is loads

3. try Wicd for multiple wireless profiles maybe

---

### Post by awseft on 2008-04-28
> **Helios1276 said:**
> well for 2 of that list ;)

1. the x1400 performs lovely on Hardy now

2. approx 15/20 gb for hardy is loads

I was thinking of giving it about 5-6GB. Would that be enough?

How do I do Hardy instead of Dapper that comes from the download page. 

<-- EXTREME NEWBIE!

---

### Post by Helios1276 on 2008-04-28
[http://ubuntuforums.org/showthread.php?t=764856](http://ubuntuforums.org/showthread.php?t=764856)

id go on the side of caution and push it to ten, if your pushed for space why nt try puppy linux or damn small linux?

---

### Post by awseft on 2008-04-28
> **Helios1276 said:**
> [http://ubuntuforums.org/showthread.php?t=764856](http://ubuntuforums.org/showthread.php?t=764856)

id go on the side of caution and push it to ten, if your pushed for space why nt try puppy linux or damn small linux?

Ok, 10GB it is. 

Well I'll be. I'm running Hardy. I guess I should just enable the video card in hardware then hu?

---

### Post by Helios1276 on 2008-04-28
> **awseft said:**
> Ok, 10GB it is. 

Well I'll be. I'm running Hardy. I guess I should just enable the video card in hardware then hu?

Well on Gutsy I needed Envy, however on Hardy the restricted drivers just needed a tick and I was good. (with x1400).

---

### Post by spacefreak86 on 2008-04-28
I'm not sure how to go about Wubi, but I'm also dual-booting with XP and Kubuntu 8.04. For your list of problems from previous editions:

1) Hardy does recognize dual-core, as did Gutsy

2) I'm pretty sure both Gutsy and Hardy had variable processing power. I know on both of my two cores, it claims I could max it at around 1620 MHz or so, but it was usually only around 1000 MHz unless it was running heavy programs.
I'm not sure how to check on that for Hardy, as I'm still working out the bugs on my own.

3) Ubuntu and Kubuntu come with NetworkManager and KNetworkManager, but due to my school wireless needing WPA encryption with TKIP / PEAP, I found Wicd much easier to navigate and setup than I did NetworkManager. To each their own I suppose.

4) I don't know much (or anything really about video cards), but I have heard that Linux in general has a problem with ATI graphics cards. I'm hoping that it would run in at the very least, the restricted hardware profile for you.


But yeah, Ubuntu / Kubuntu is actually pretty awesome. I had Gutsy for about a month, then this past weekend upgraded to Hardy. I had some installation problems while I was installing it via the package manager, which I suspect might be causing some problems for me now, but if you are going to upgrade, I'd recommend backing up files and then installing fresh from the .iso.

---

### Post by Helios1276 on 2008-04-28
> **spacefreak86 said:**
> 

4) I don't know much (or anything really about video cards), but I have heard that Linux in general has a problem with ATI graphics cards. I'm hoping that it would run in at the very least, the restricted hardware profile for you.



Sadly ya, there can be alot of issues with ATI cards at times, the x1400 I have is muck really..Hypermemory my ***

---

### Post by awseft on 2008-04-29
Got it up and running. Got the video card up but the resolution is still low. Oh well I guess.

---

### Post by Helios1276 on 2008-04-29
> **awseft said:**
> Got it up and running. Got the video card up but the resolution is still low. Oh well I guess.

Did u try changing the resolution? what options did you get?

System-Preferences-screen resolutions

---

### Post by awseft on 2008-04-29
> **Helios1276 said:**
> Did u try changing the resolution? what options did you get?

System-Preferences-screen resolutions

1280x800

---

### Post by Helios1276 on 2008-04-29
Where you getting higher resolutions with your comp before? 1280x800 is what I'm currently running on Hardy and what I had with xp before that.

---

### Post by awseft on 2008-04-29
> **Helios1276 said:**
> Where you getting higher resolutions with your comp before? 1280x800 is what I'm currently running on Hardy and what I had with xp before that.

That is what I used in Windows. I guess it just seems like fonts are larger. I'm playing with all those settings now. 

I notice it most in web pages even when I change the font sizes (CTRL + +/-).

Is there a way to get windows font set so web pages that use them can reference them? Like Microsoft Core Fonts

---

### Post by Helios38 on 2008-04-29
> **awseft said:**
> I was thinking of giving it about 5-6GB. Would that be enough?

How do I do Hardy instead of Dapper that comes from the download page. 

<-- EXTREME NEWBIE!



the ubuntu version should have in my opinion at least 10 gb due to swap, etc.


and omg theres another helios xD i thought i was unique:(

---

### Post by Helios1276 on 2008-04-29
> **awseft said:**
> That is what I used in Windows. I guess it just seems like fonts are larger. I'm playing with all those settings now. 

I notice it most in web pages even when I change the font sizes (CTRL + +/-).

Is there a way to get windows font set so web pages that use them can reference them? Like Microsoft Core Fonts

Well in firefox Edit-Preferences- Content does the job for me , I'm pretty sure CTRL + etc is only temporary in nature. Hope that helps a little , I have to get some sleep now lol good luck with the fine tuning and welcome to the forums :popcorn:

---

### Post by corevette on 2008-04-29
The proprietary drivers for my ATI X1300 are absolutely horrid; when I restart to complete installation of the proprietary drivers, a black screen appears and I have to uninstall the drivers...
I'm stuck with no 3d acceleration

---

### Post by Helios1276 on 2008-04-29
> **Helios38 said:**
> the ubuntu version should have in my opinion at least 10 gb due to swap, etc.


and omg theres another helios xD i thought i was unique:(

Ya that is annoying, what are you gonna change to? ;)

---

### Post by Helios38 on 2008-04-29
> **Helios1276 said:**
> Ya that is annoying, what are you gonna change to? ;)

Nou ;)


anyways, pointless spam.


i personally do not have experience with nvidia or ATI driver but i always hear ppl moan about them.


i think u might just be screwed on hardware acel, but try the restricted drivers, u may find a cure.

---

