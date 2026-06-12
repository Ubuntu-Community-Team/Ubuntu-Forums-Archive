---
title: "workspace automatically switches to active window"
date: 2012-08-06
forum: New to Ubuntu
---

### Post by bebops_lost on 2012-08-06
I use workspaces a lot and love it. 
I recently upgraded to ubuntu 12.04, and after some updates, workspaces started behaving differently. For example, suppose I have a Firefox window already open in Workspace 1, but I'm currently in workspace 2 and I decide I want to use a new Firefox window in _this_ workspace. 

If I click on the Firefox launcher it will automatically take me back to workspace 1. I hate this feature with the fiery heat of a thousand suns. How do I disable it ?  (i.e. I want to be able to click on the launcher to launch a window of that program in the current workspace and *_always_* stay in the current workspace no matter what other windows might be open in other workspaces.) 

The only other suggestion I've read on the forums was to open compiz-config and "play around with the settings" -but that wasn't too helpful. I know generally how to use compiz-config manager, but I don't even know what this feature is called or how to disable it.

Any help would be appreciated.
thanks

---

### Post by mcduck on 2012-08-06
There is no easy setting for that, but if you middle-click a launcher in the Unity panel it behaves like you want to, opening a new window instead of switching to the already open window...

---

### Post by sid0972 on 2012-08-06
i use chrome, and in a different workspace i right click on it, and select "open new window", it opens there itself

---

### Post by gifford on 2012-08-06
Didn't know about using the middle click of a unity launcher item..works great. Thanks mcduck!

---

### Post by bebops_lost on 2012-08-06
> **mcduck said:**
> There is no easy setting for that, but if you middle-click a launcher in the Unity panel it behaves like you want to, opening a new window instead of switching to the already open window...

ok, well that's a pretty decent work-around. Thanks McDuck.

/As an aside though, this little feature (automatically moving you to the other workspace) is really more of the "Apple" mentality -i.e. "we do things for you our way whether you like it or not"  -and this sorta thing is the reason I removed OSX and installed ubuntu on my macbook -because I want my computer to do just what I tell it to do.

---

### Post by sid0972 on 2012-08-07
> **mcduck said:**
> There is no easy setting for that, but if you middle-click a launcher in the Unity panel it behaves like you want to, opening a new window instead of switching to the already open window...

even i didnt know that, seems its an alternate of right click
thanks

---

### Post by markbl on 2012-08-07
> **mcduck said:**
> if you middle-click a launcher in the Unity panel it behaves like you want to, opening a new window instead of switching to the already open window...
Gnome shell provides the same shortcut with ctrl+left-click. Gnome shell also provides middle-click which opens a new window in a **new** workspace. This is quite handy and is something Canonical should add to Unity although it is a pity that these shortcuts have diverged between Gnome shell and Unity.

---

### Post by bebops_lost on 2012-08-07
Just as an aside though,
> **mcduck said:**
> There is no easy setting for that, ...
 there should be.
Not that I'm faulting anyone here for the behaviour, but if there happen to be developpers out there reading this, I want to point out something:

It can be frustrating when your computer won't automatically do something that you want it to do. BUT, it's *way more frustrating* when your computer is doing something automatically without being asked and you can't stop it. The first kind of problem can be disappointing, but the second kind of problem is infuriating. 

Hence, unless it's totally obvious that everyone would always want something done a certain way, the computer's default should be "Don't do anything extra until told to do so."

---

### Post by mcduck on 2012-08-07
> **bebops_lost said:**
> Just as an aside though,

 there should be.
Not that I'm faulting anyone here for the behaviour, but if there happen to be developpers out there reading this, I want to point out something:

It can be frustrating when your computer won't automatically do something that you want it to do. BUT, it's *way more frustrating* when your computer is doing something automatically without being asked and you can't stop it. The first kind of problem can be disappointing, but the second kind of problem is infuriating. 

Hence, unless it's totally obvious that everyone would always want something done a certain way, the computer's default should be "Don't do anything extra until told to do so."

It's not really a question of doing "anything extra", actually it could be argued that it's exactly the opposite, not doing anything extra. Instead of opening an extra window of the same program it's simply changing to the one you already ahve running. (in most cases and with most programs, you'd sually only need one window open and opening a new one automatically every time you click the icon could very well be considered as "doing something extra", and quite often also pretty annoying... ;))

That being said, I'm not against having configuration option for this. But I still see the current behaviour as a good default. :)

---

### Post by bebops_lost on 2012-08-07
> **mcduck said:**
> It's not really a question of doing "anything extra", actually it could be argued that it's exactly the opposite, not doing anything extra. Instead of opening an extra window of the same program it's simply changing to the one you already ahve running. 

I suppose that's one way of looking at it. The reason I disagree is because I like to look at workspaces as modular -in the sense that when I'm in workspace 1, that should be my entire "computer universe" for the moment. 

This way I can write code, google papers, and do everything I need to do to get work done (when I'm in the 'work' universe), and when I switch to workspace 2, then I can peruse pictures, play Amarok songs, and surf youtube (when I'm in 'fun' mode). 

When I go back to working in workspace 1, and I decide to open wikipedia to look something up, I don't want to go back to the youtube videos of cats with their heads stuck in boxes that I have open in workspace 2.

> 
That being said, I'm not against having configuration option for this. But I still see the current behaviour as a good default. :)

I respectfully disagree as to what the default should be, but at least we agree it should be something that can be configured.

---

### Post by bebops_lost on 2012-08-27
Actually, it's worse than I described.
Not only is the above behaviour a problem. But there are times when I click on a program in the bar on the left and nothing happens.... click again, nothing happens. I start to think the computer is frozen because I'm clicking repeatedly and nothing is happening.

'Turns out, Unbeknownst to me, the program I want to relaunch is already open in another workspace and is just opening new tabs which I *couldn't possibly know about* from what I'm seeing on screen. This never happened in Ubuntu 10.04; I loved everything about the behaviour in 10.04, and now my whole system is screwed up.

As pointed out above, some people like the new default behaviour in 12.04. Good for them -whatever floats your boat- but personally, I find the current behaviour intolerably frustrating. Dividing things into *seperate* workspaces (which is what convinced me to start using linux instead of Windows) has gone from being a pleasure to be being a constant irritation. and there really needs to be at least the *option* of restoring the old behaviour from 10.04

And I will just add that I really do appreciate all the hard work that the developpers out there put into Ubuntu. I'm sure it can be hard keeping everyone happy. I'm just sayin' that this is one thing that's kinda driving me bonkers.

---

### Post by sid0972 on 2012-08-28
i tried several options but none of them seems to be the solution for your problem
you can switch to 10.04 again if you want
or can try other distribution

---

### Post by bergspyder on 2012-11-24
Got to agree with bepos_lost. And that, right there, is a good example: I wanted to make this post in one workspace while switching to another with the thread so I could scroll through but cannot. So I'm going back to 10.04 -- which converted me from Windows to Linux -- but is 12.04 progress? And how long will 10.04 be supported? OK, Linux is free but a massive success; I hope it will always stay ahead (in areas I need) of the costly alternatives. Come on, guys, there's got to be a way to add option for the 12.04 user to select 10.04 workspace behaviour, surely?

---

### Post by mcduck on 2012-11-24
> **bergspyder said:**
> Got to agree with bepos_lost. And that, right there, is a good example: I wanted to make this post in one workspace while switching to another with the thread so I could scroll through but cannot. So I'm going back to 10.04 -- which converted me from Windows to Linux -- but is 12.04 progress? And how long will 10.04 be supported? OK, Linux is free but a massive success; I hope it will always stay ahead (in areas I need) of the costly alternatives. Come on, guys, there's got to be a way to add option for the 12.04 user to select 10.04 workspace behaviour, surely?
Ubuntu offers you a large selection of various desktop environmets which you can install and use if you don't like the default Unity setup. So that is no reason to downgrade to an older release. Just use default Gnome, Gnome's fallback session, XFCE, KDE, LXDE or some other envrionment instead.

And to clarify things a bit, Gnome 2 desktop, which you seem to be missing, is not an option any more because it's developers stopped working on it and moved to Gnome 3 instead. So there is no way Ubuntu's (or any other distro's) developers could keep on giving you that exact desktop any more.

---

### Post by benhansenslc on 2013-06-09
I completely agree with the OP here and would love to see an option to disable automatic switching.

---

