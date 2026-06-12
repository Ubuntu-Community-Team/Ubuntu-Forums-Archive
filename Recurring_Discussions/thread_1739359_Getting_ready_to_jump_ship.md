---
title: "Getting ready to jump ship?"
date: 2011-04-25
forum: Recurring Discussions
---

### Post by barthel on 2011-04-25
I've been using the Natty beta for a week now and trying really hard to like the Unity interface.

Aside from the hardware requirements for what I consider to be eye candy, I have two major issues.
[LIST=1]
[*]The global menu
[*]Focus-follows-mouse
[/LIST]
Before Linux came on the scene I was a Commodore/Amiga man. I really liked how having all the application menus in the screen titlebar saved precious screen real estate for actually doing something useful. I was really prepared to like this feature of Unity, BUT...

Screen resolutions are *much* larger now than they were in the 1980s. If I have a small application in the lower right of my screen, I have to make a major mouse movement (or click a keyboard sequence) to get to the new global menu. That's really not effective or efficient.

With the emphasis on touch devices that appears to be Unity's hallmark, most of the new features break focus-follows-mouse behaviors. Even Alt-TAB is broken: windows are raised but not focused unless the mouse is actually there. (I can't count the  number of times I've switched from an application to another window, say a terminal with a man page, and then switched back, happy to have my mouse cursor exactly where I left it.)

The bottom line of all of this is that I'm seriously considering switching distributions again. I had been a hard-core Slackware user since kernel 1.2 and switched to Ubuntu after Pat Volkerding's health issues brought Slackware to a standstill. I chose Ubuntu because of the wide community support and the fact that I'm getting older and rebuilding my system from scratch every 6 months was no longer as much fun as it used to be.

I've got a bit of breathing room since I can use "classic GNOME" for at least 11.04. But given that both GNOME and Ubuntu seem to be headed in the direction of limiting user choice instead of supporting it, I'm ready to start giving other options a look.

I'm seriously considering moving to Mint. I had looked at Gentoo, Arch, and Fedora (among others) the last time around. Are there any others I should be evaluating?

Or maybe I need to start my own distribution: "Old Dog Linux" for those of us who don't want to learn new tricks. :wink:

TIA!

P.S. Please keep it light and polite. It's really easy to get caught up in "Crusader mentality" when discussing distributions.

P.P.S. FWIW, I've been programming since 1978. I frequently use the command line -- and LIKE it! I've also been using focus-follows-mouse for over 25 years. Going back to clicking on each window feels like I'm being forced to be less productive. ](*,)

---

### Post by ikt on 2011-04-25
> **barthel said:**
> With the emphasis on touch devices that appears to be Unity's hallmark, most of the new features break focus-follows-mouse behaviors. Even Alt-TAB is broken: windows are raised but not focused unless the mouse is actually there. (I can't count the  number of times I've switched from an application to another window, say a terminal with a man page, and then switched back, happy to have my mouse cursor exactly where I left it.)

[https://bugs.launchpad.net/ubuntu/+filebug/?no-redirect](https://bugs.launchpad.net/ubuntu/+filebug/?no-redirect)

:)

---

### Post by wilee-nilee on 2011-04-25
I'm loading the paint gun when you jump do it slowly and give us a good shot at your backside to aim at.;)

Just giving you a hard time.

---

### Post by Dustin2128 on 2011-04-25
Why anyone would leave a distro due to default desktop environment is beyond me.

---

### Post by barthel on 2011-04-25
> **ikt said:**
> [https://bugs.launchpad.net/ubuntu/+filebug/?no-redirect](https://bugs.launchpad.net/ubuntu/+filebug/?no-redirect)

:)

My apologies. I failed to note that I was in the process of filing yet another bug when I found the comments that led me to considering switching.

Essentially, the developers aren't interested in fixing focus-follows-mouse in Unity. They may welcome patches, but there are so many aspects to the Unity design that break this functionality that I know I'm not competent to fix it, let alone maintain it.

Frankly, it would save more trouble if they simply decided to disallow focus-follows-mouse in the first place. Then those of us who use it wouldn't be surprised by the broken behaviors.

---

### Post by tgm4883 on 2011-04-25
> **dustin2128 said:**
> why anyone would leave a distro due to default desktop environment is beyond me.

+1

---

### Post by wojox on 2011-04-25
Maybe they don't care about FFM because it's X11 and their switching to Wayland soon.

---

### Post by NightwishFan on 2011-04-25
Abandon ship!

Why.. It is not sinking. :/

The Unity worries are over hyped I am thinking. If it is not for you it is not for you but please leave gracefully if that is the case. Gnome 2 will not be around any more (for any distro) I am not sorry to say.

I would not mind someone maintaining it but I doubt the gnome people will.

---

### Post by barthel on 2011-04-25
> **Dustin2128 said:**
> Why anyone would leave a distro due to default desktop environment is beyond me.

Because I can see the writing on the wall. (If you live long enough, it's easy to see the signs of history repeating itself.) Eventually, support for the "classic" environment will disappear. At which point I will be stuck running an unsupported distribution or being forced to change to either the new version or a new distribution.

If the user interface gets in the way of me being productive, I *will* choose something else.

Please note, that I'm not talking about a learning curve so much as new "features" that require me to perform more steps to achieve the same result.

Why leave the distro? Because Ubuntu is going to be tightly integrated into the new desktop environment. Removing Unity and replacing it with something else will break many more things which will have to be addressed. At that point I'm essentially creating my own Ubuntu based variant. I'd rather pool resources with another group than maintain it all myself. (Like I said, I'm getting older and it's not as much fun and I want to spend my time doing other things.)

---

### Post by tgm4883 on 2011-04-25
> **barthel said:**
> Because I can see the writing on the wall. (If you live long enough, it's easy to see the signs of history repeating itself.) Eventually, support for the "classic" environment will disappear. At which point I will be stuck running an unsupported distribution or being forced to change to either the new version or a new distribution.

If the user interface gets in the way of me being productive, I *will* choose something else.

Please note, that I'm not talking about a learning curve so much as new "features" that require me to perform more steps to achieve the same result.

Why leave the distro? Because Ubuntu is going to be tightly integrated into the new desktop environment. Removing Unity and replacing it with something else will break many more things which will have to be addressed. At that point I'm essentially creating my own Ubuntu based variant. I'd rather pool resources with another group than maintain it all myself. (Like I said, I'm getting older and it's not as much fun and I want to spend my time doing other things.)

I think more of the point of not switching distros over the DE is that you could easily use Xubuntu, which is still Ubuntu at it's base.

---

### Post by handy on 2011-04-25
Xfce4 is nice, its lighter & quicker than Gnome2 & modular, so you can use what you like. It also has GTK-2 underneath, which makes it easy for software written for Gnome to look good, as well as themes & such.

I'm sure someone will (if it doesn't already exist, write a step by step how-to for removing that which is unnecessary in Gnome/Unity whatever it is called, & make it easy to add Xfce4 (or whatever other desktop/window manager) instead.

Or you could go to Xubuntu, or Mint has (or at least used to anyway) a nice Xfce version.

Or you could install Arch & run Xfce on it. Which would make for a very light, quick, space efficient system that has only what you want on it. Being perfectly suitable for someone who is already comfortable with the command line.

The problem has many more solutions than the few I stated.

---

### Post by NormanFLinux on 2011-04-25
Ubuntu-based distro developers that take over Unity will do a much better job of integrating it into their distros than Ubuntu. Its open source software and any one should be able to fix and improve the code. Its not that big an issue.

---

### Post by Thewhistlingwind on 2011-04-25
> **barthel said:**
> Because I can see the writing on the wall. (If you live long enough, it's easy to see the signs of history repeating itself.) Eventually, support for the "classic" environment will disappear. At which point I will be stuck running an unsupported distribution or being forced to change to either the new version or a new distribution.

If the user interface gets in the way of me being productive, I *will* choose something else.

Hmmmmm. Methinks a veteran programmer needs to clone gnome-panels. (Or an ambitious young lad with no idea what he's getting into.) That wasn't necessarily me asking you to do it, but.......

I've always been pleased with debian (Though I haven't really used it enough to get pissed.), but my thoughts are that they will soon be switching to the gnome-shell. (As with fedora.) This leaves you with the problem of hacking something functional as the DE into a distro you like. :( (Or using one which has Xfce/Crunchbang/etc, EG. Xbuntu)

---

### Post by barthel on 2011-04-25
> **tgm4883 said:**
> I think more of the point of not switching distros over the DE is that you could easily use Xubuntu, which is still Ubuntu at it's base.

I did think about that. It has been a while since I test-drove XFCE.

My concern here is that with the push for Unity over both GNOME and KDE, that Xubutnu may also fall by the wayside.

Once Natty is finalized, I'll be able to use my Maverick partition to check out other options. I'll definitely put Xubuntu on my list along with Mint.

---

### Post by sammiev on 2011-04-25
Tried them all now. lol If you are looking at fedora, take the time to check out openSUSE while you are playing. GL :)

---

### Post by krapp on 2011-04-25
Debian Stable is an obvious alternative!

---

### Post by Learning Linux 2011 on 2011-04-25
10.04 is supported until April 2013, so you have plenty of time to decide.

---

### Post by zer010 on 2011-04-25
I figured I'd stick with 10.04 until it's time runs out, so in the mean time I've been doing some distro hopping.  I've tried a little Arch, some Bodhi and some Fedora.  Of all of them, I kinda like Fedora Xfce the best.  Of course I could've tried Xubuntu, but I figured if I was gonna try a new DE, I might as well try it on a new distro.

---

### Post by Perfect Storm on 2011-04-25
Moved to recurring Discussion.

---

### Post by Khakilang on 2011-04-25
That is why I still maintain 2 computer. 1 is my main computer and the other is for testing. Once I tested and I like it I will install into my main one.

---

### Post by Roasted on 2011-04-25
> **dustin2128 said:**
> why anyone would leave a distro due to default desktop environment is beyond me.

+11111111111111111111111111111111111111111111111

---

### Post by wolfen69 on 2011-04-26
> **barthel said:**
> Removing Unity and replacing it with something else will break many more things which will have to be addressed.

I had no problem installing gnome 3 on top of xfce in xubuntu 11.04. Gnome 3 does not conflict with xfce. No need to worry about removing unity. Btw, I'm really digging gnome 3.

---

### Post by barthel on 2011-04-26
> **wolfen69 said:**
> I had no problem installing gnome 3 on top of xfce in xubuntu 11.04. Gnome 3 does not conflict with xfce. No need to worry about removing unity. Btw, I'm really digging gnome 3.

That may be a viable way to go. Even switching to "classic" didn't get rid of Unity: unity-window-decorator was still being used. Since that appears to be the source of most of the focus-follows-mouse breakage, I chmod'ed it to 644, which forced metacity to be used instead.

Makes me wonder why gtk-window-decorator is even installed....

---

### Post by el_koraco on 2011-04-26
Right now, both Xubuntu and Kubuntu are more stable and you can expect to see less breakage than with Ubuntu. You can also do a minimal install and bring up only the packages you want. I mean, if you used Slack in the past, that shouldn't be too much of a problem.

---

### Post by robert shearer on 2011-04-26
While I am trying to get used to Unity I have found it easier to use both the gnome panels and unity and choose/experiment with navigation options.

This means I don't have to keep logging in and out and choosing different environments all the time.

Set up your panels as you want them whilst logged in to Ubuntu Classic. Then log out and log back in choosing Unity (I am running Unity2d but assume this holds true for 3d as well).
Then alt-F2 and type...    gnome-panel

Now you should have Unity **and** gnome panels to play with in the same desktop.

For anyone looking for the gnome system monitor this will show it if setup in the panel. :D

---

### Post by beew on 2011-04-26
> **robert shearer said:**
> While I am trying to get used to Unity I have found it easier to use both the gnome panels and unity and choose/experiment with navigation options.

This means I don't have to keep logging in and out and choosing different environments all the time.

Set up your panels as you want them whilst logged in to Ubuntu Classic. Then log out and log back in choosing Unity (I am running Unity2d but assume this holds true for 3d as well).
Then alt-F2 and type...    gnome-panel

Now you should have Unity **and** gnome panels to play with in the same desktop.

For anyone looking for the gnome system monitor this will show it if setup in the panel. :D


It works but max/min/close buttons for all maximized windows disappear. :)

I am not crazy about the panels per se, in 10.10 I run full Compiz and Cairo Dock and I hardly use the panel (so thanks but no thanks, gnome 3 "fall back mode" is not for me, I want a full 3d desktop). My complaint about Unity is that it is not very customizable and many functionalities are either missing or take more mouse clicks to accomplish. The worse part is these defects are  apparently by design (features rather than bugs

---

### Post by robert shearer on 2011-04-26
> **beew said:**
> It works but max/min/close buttons for all maximized windows disappear. :)

Try setting the top panel as your bottom panel and see if this helps.

My default setting for Gnome2 has been to always swap panel positions top for bottom etc. 
So with Unity and gnome-panel there are working buttons, sometimes right as per my theme and sometimes left as per Unity.

---

### Post by beew on 2011-04-26
> **robert shearer said:**
> Try setting the top panel as your bottom panel and see if this helps.

My default setting for Gnome2 has been to always swap panel positions top for bottom etc. 
So with Unity and gnome-panel there are working buttons, sometimes right as per my theme and sometimes left as per Unity.


How do you switch top and bottom panels?

I don't really care whether the buttons are on the left or on the right, as long as they are always on one side. Lately I am having a problem since there is an emerald theme I like which only has buttons on the right,--I was able to install emerald in Unity with some help from the forum,-- so when windows get maximized the buttons suddenly switch to the left, and unmaxized, buttons go right again. From your second paragraph I take it that using the gnome panel would not solve this problem?

---

### Post by el_koraco on 2011-04-26
> **beew said:**
> From your second paragraph I take it that using the gnome panel would not solve this problem?

There is a Gnome panel applet which puts the buttons for the running window into the top right of the panel. Couldn't tell you what it's called, because I just remember seeing it off-hand.

---

### Post by demosthene1 on 2011-04-26
Choice is  what I believe Linux is about. I am considering a rolling release that comes ready to use, light and free of the current desktop debates, familiar feel...

[http://blog.linuxmint.com/?p=1725](http://blog.linuxmint.com/?p=1725)

Linux Mint Xfce (201104) looks promising. I installed it to an external usb hard drive. High functionality minus the social networking and Ubuntu One stuff. Very fast and responsive on my low end computers. Always updated. Nice.

---

### Post by barthel on 2011-05-02
Well, I'm currently test-driving Linux Mint 10 on my alternate root partition. My biggest hassle was the loss of my wireless network on the initial install. It's a known issue with the initial kernel (2.6.35-22) in Maverick: the wireless card in my new desktop *is* supported with 2.6.35-27 and later. I just had to run a cable down the laundry chute to connect directly to my router in the basement until I downloaded the updates.

I know Mint 10 isn't much of a change from Ubuntu 10.10, but it will let me try out Mint's version of GNOME 3. I'm hoping that the only change I'd have to make there would be to replace gnome-screensaver: I was not happy to see that even more functionality was stripped away to protect users from themselves--AGAIN.

Unfortunately, over the past few days while I've been getting Mint up and running I discovered a new flaw-by-design in Unity that is definitely pushing me out. The new thin line scrollbars are impossible to find when scrolling through a highlighted list. Plus, the buttons never appear at the same place relative to the height of the scroll indicator: they're offset to avoid overlapping other decorations at the top and bottom of the "trough". Hard to see, hard to activate with a mouse (let alone a finger), I'm just not seeing how this is enhancing the user "experience". It seems more like design in search of a problem.

Supposedly GNOME 3 did a lot of research first. That's why I'm currently waiting for the "minty freshness" of Mint 11. But there's a good possibility that I'll be taking a closer look at a good KDE implementation or falling back to XFCE in the very near future.

---

