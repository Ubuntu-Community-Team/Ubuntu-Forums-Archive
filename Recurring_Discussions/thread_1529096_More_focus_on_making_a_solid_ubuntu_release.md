---
title: "More focus on making a solid ubuntu release?"
date: 2010-07-11
forum: Recurring Discussions
---

### Post by geirknappen on 2010-07-11
I look at this list of [ubuntu releases]("http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline"), and I think: they always build ubuntu from scratch in 6 months, and after another 6 months a lot of bugs get fixed. And then you have less than a year before the release is no longer supported (except of lts) , and when the support end, it is still buggy.

So... I wonder. Why always start from scratch? Two releases per year, isn't that too much? How bout less releases, and more focus on making something solid? Which linux distro has the longest support time? If I want to keep one release for 20 years, which one should I choose?

---

### Post by Bachstelze on 2010-07-11
> **geirknappen said:**
> I look at this list of [ubuntu releases]("http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline"), and I think: they always build ubuntu from scratch in 6 months

No they don't. Each Ubuntu release is built from a snapshot of Debian testing or unstable.

---

### Post by geirknappen on 2010-07-12
> **Bachstelze said:**
> No they don't. Each Ubuntu release is built from a snapshot of Debian testing or unstable.

Almost then.

---

### Post by overdrank on 2010-07-12
Moved to Recurring Discussions :)

---

### Post by cr4321 on 2010-07-12
> **geirknappen said:**
> I look at this list of [ubuntu releases]("http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline"), and I think: they always build ubuntu from scratch in 6 months, and after another 6 months a lot of bugs get fixed. And then you have less than a year before the release is no longer supported (except of lts) , and when the support end, it is still buggy.

So... I wonder. Why always start from scratch? Two releases per year, isn't that too much? How bout less releases, and more focus on making something solid? Which linux distro has the longest support time? If I want to keep one release for 20 years, which one should I choose?
Yes, I believe there is some weight in that arguement. (It took many long years for WinXP to stabilise) To rebuild something like Ubuntu every 6 months must be a herculean effort - and then starts the bug fixes. One year looks reasonable to keep things current.

Then, 20 years support for a distro certainly seems too high.. with the pace of change in hardware and technology. However, depending on the scope, it is a worthwhile point for discussion.

---

### Post by geirknappen on 2010-07-13
> **cr4321 said:**
> 20 years support for a distro certainly seems too high..

Ok, I may have exaggerated a little. A computer would last for less than half that amount of time. Maybe they should make just 1 release per year, and double the time of support for LTS. If a such long support release were made, then maybe It would be possible to buy laptops and computers with ubuntu in the electronics stores.

---

### Post by snowpine on 2010-07-13
The great thing about Linux and Open Source software is that people work on the projects they feel motivated to work on. So if you desire to work on a distro that will be supported 20 years, get to work! ;)

The correlary of this, of course, is that the people making Ubuntu do it every 6 months because that's what *they* want to do, so you can't really tell them to change course and start working on a project they have no interest in; that's not a recipe for success in this competitive world. :)

FYI Ubuntu is built from a very stable distro called Debian that releases roughly every 2 years. If you are looking for a more stable alternative to Ubuntu, that is where I would recommend starting. Another really stable distro is Red Hat Enterprise Linux (or its free cousin, CentOS). I believe they are the longest-supported Linux distro at 7 years. You do realize, however, that the most stable distros, by definition, also have the oldest applications? :D

---

### Post by XubuRoxMySox on 2010-07-13
The OP's observations are one of the reasons I generally suggest that [COLOR="Blue"]X[/COLOR]/[COLOR="RoyalBlue"]K[/COLOR]/[COLOR="Purple"]U[/COLOR]buntu users remain "one release behind" the current one unless they're only using the LTS versions. There is still plenty of support left in Karmic while Lucid matures and gets bugs worked out, and by the time the next one is out, Lucid will be "more stable," having had time to work out bug fixes and stuff.

Still enjoying Karmic Xubuntu,
Robin

---

### Post by geirknappen on 2010-07-14
Hmmm... 
My linux history: started to use linux first time with ubuntu 9.04, then i tried ubuntu 9.10, but deleted it when i realized that 9.04 worked better on my laptop. S-video, printer, everything works. Then i tried ubuntu 10.04, even the boot screen looks like it's not working properly, so I deleted 10.04 too, 9.04 still works better. 

Ubuntu 9.04, I think has everything I will ever need. Opera 10.60 is as fast enough for me. Maybe I should just keep ubuntu 9.04 until my computer dies one day.

---

### Post by vandorjw on 2010-07-14
Ubuntu is not at all like Windows where only 1 company produces the entire OS.

The base of the system, or the kernel, comes from here.
[www.kernel.org](www.kernel.org)
The Ubuntu Engineers / Techichians make some changes and patches when they need to, but the bulk of it is done by others.

The display, xorg is produced by yet again, some other people. see [www.x.org](www.x.org)

On top of Xorg, Ubuntu runs Gnome, Kubuntu runs KDE, Xubuntu runs XFCE.
All these are again produced by another team of people, who focus on making it more solid and usable with each release / update.

Basically what they Ubuntu Engineers have to do, is collect all the programs and their source code, compile it, and if it produces conflicts with other software, edit it a bit. (The language I am using might make it seem simple but this takes a lot of effort)

Anyways, this point I want to make is, if they just take one release of the software, and make it "solid" or "stable" and take it from there, they would lose a lot of man-power and the Ubuntu project might fall behind.

I guess Ubuntu could just wait 2 years for everyone to develop their software some more, and then make a release...but it is much more beneficial for the developers of the software if the User use their latest versions so bugs can be found faster, and hopefully fixed quicker.

And even then, you would likely have a buggy initial release and only after a couple weeks/months would it get better again. The difference is the same, except that the time you stick with older software is longer...

Anyways, hope this will be usefull to someone,
and if its not, or I have it completely wrong...at least I felt like I did something for 5 minutes :)

Cheers - CC7

EDIT: You have the opportunity to stick with the LTS releases, I know some guys that still used 6.06 servers till recently :)

---

### Post by geirknappen on 2010-07-15
It is almost 100% certain that I will try ubuntu 10.10 when it comes, and if it does not work after 3 months I'll delete it an wait for the next one, ubuntu 11.04. 

Arch linux have a different system, you install once. Does that have disadvantages?  I would never install it, because I would never make it past the installation process and still be able keep vista and ubuntu, but the idea of only one time install, is that bad?

---

### Post by vandorjw on 2010-07-22
A rolling release has its own advantages and disadvantages.
In my opinion it needs a lot more bandwidth to keep it up to date.
I used Arch for a couple years and learned a lot from it. I found the way it was set up a bit more simple than Ubuntu. (Ubuntu is very easy to install but more difficult to customize afterward)

When it comes to computers and OS i seem to have ADD or ADHD.

As soon as I notice a new version of Ubuntu, Fedora, Suse, etc is out, I backup my data and try it out :)

To each his own. Currently I use Ubuntu, and have Windows Server R2 on my 2nd system.

PS: if you want to try arch linux, it is actually quite easy to set up. Much like Windows XP :)

After it is done just run this command.
sudo pacman -Syu
Sudo pacman -S xorg gstreamer0.10-good gstreamer0.10-plugins pulse firefox (and whatever else....) kde / gnome etc

Cheers - CC7

---

### Post by geirknappen on 2010-08-05
Ok... I've heard that it's best to have ubuntu because it supports a lot of different hardware compared other distros. A also think that ubuntu work better than other distros on a laptop, but I am not sure of this. I know i have i386 computer architecture + I know that I would want a distro that can run opera browser, and that reduces the number of distros that could be an alternative.

What I like about ubuntu 9.04 is the boot time of less than 20 seconds, compared to 50 sec with windows. I liked having the maximize minimize buttons on the left, and the black boot screen with the ubuntu logo, to me it gave professional feeling, compared to 10.04 with the dots that gives to me a feeling that this was made in haste. The 9.04 login screen also look nice. 


I would have given arch linux a chance, if someone had installed it and  customized everything for me, with a guarantee that it would work with my hardware. I don't want to spend time on making something work. I know very little about linux, but I know they use it on the supercomputers because it is 5 times as effective as windows. With linux on my computer, my computer is 5 times as effective? Maybe not that much.

---

### Post by Shining Arcanine on 2010-08-05
> **geirknappen said:**
> I look at this list of [ubuntu releases]("http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline"), and I think: they always build ubuntu from scratch in 6 months, and after another 6 months a lot of bugs get fixed. And then you have less than a year before the release is no longer supported (except of lts) , and when the support end, it is still buggy.

So... I wonder. Why always start from scratch? Two releases per year, isn't that too much? How bout less releases, and more focus on making something solid? Which linux distro has the longest support time? If I want to keep one release for 20 years, which one should I choose?

Open source software evolves at such a rate that 6 months is usually too slow to keep up with all of the changes.

Anyway, you likely want to try either RedHat Enterprise Linux or CentOS. A rolling distribution would probably be even better. With a rolling distribution, there is only one version, with a ton of updates, and it is always relatively up to date. Of course, that is stretching the notion of using a single release for years, because after several years, your OS would be significantly different than what it was when you started with it.


> **geirknappen said:**
> Ok... I've heard that it's best to have ubuntu because it supports a lot of different hardware compared other distros. A also think that ubuntu work better than other distros on a laptop, but I am not sure of this. I know i have i386 computer architecture + I know that I would want a distro that can run opera browser, and that reduces the number of distros that could be an alternative.

What I like about ubuntu 9.04 is the boot time of less than 20 seconds, compared to 50 sec with windows. I liked having the maximize minimize buttons on the left, and the black boot screen with the ubuntu logo, to me it gave professional feeling, compared to 10.04 with the dots that gives to me a feeling that this was made in haste. The 9.04 login screen also look nice. 


I would have given arch linux a chance, if someone had installed it and  customized everything for me, with a guarantee that it would work with my hardware. I don't want to spend time on making something work. I know very little about linux, but I know they use it on the supercomputers because it is 5 times as effective as windows. With linux on my computer, my computer is 5 times as effective? Maybe not that much.

How is it 5 times more effective? What is it 5 times more effective at doing? Your statement about its effectiveness makes no logical sense.

---

### Post by geirknappen on 2010-08-06
> **Shining Arcanine said:**
> 
How is it 5 times more effective? What is it 5 times more effective at doing? Your statement about its effectiveness makes no logical sense.

I don't know. Calculating peta flops per second something. Could not find it on the Internet,I only found that 90 % of top 500 supercomputers use linux. Maybe it was wrong.

---

### Post by zer010 on 2010-08-06
I was introduced to Ubuntu with the 8.04LTS. It was pretty good, but around that time 9.04 had come out and I just HAD to try it out. I was VERY pleased with it. All my hardware (old at the time) was supported right away and I had very few, if any, problems. With 9.04, I was hooked on Ubuntu! When 9.10 came out, I was excited to try it out. I finally got a copy burnt and then the problems started. First, it didn't want to install properly. I figured it might have been a bad copy, so I tried again. Success! Then I started to notice small things here and there were buggy. I was spending more time tracking bugs than actually USING my computer!  I went back to 9.04 while I waited for 10.04LTS.  I started hearing so much of how much more buggy 10.04 was compared to 9.10. needless to say, I was heartbroken. I gave 10.04 about a month before I finally tried it. To my surprise, I have had very few problems with it.  I am VERY satisfied with 10.04.  With the help of the great folks here in ubuntuforums, whatever tiny problems that arise are quickly and easily fixed.  With the advent of 10.10 on the horizon, I am reluctant to make a change anytime soon.  I might try it out one day.  I'll definitely give it time to mature, especially with all the new changes I hear are coming.  I can already tell it's going to be a couple months, after release, before it finds a home on my PC.  
Keep up the great work on Ubuntu!

---

### Post by geirknappen on 2010-12-08
> **dixiedancer said:**
> The OP's observations are one of the reasons I generally suggest that [COLOR="Blue"]X[/COLOR]/[COLOR="RoyalBlue"]K[/COLOR]/[COLOR="Purple"]U[/COLOR]buntu users remain "one release behind" the current one unless they're only using the LTS versions. ... Lucid will be "more stable," having had time to work out bug fixes and stuff.




I know it's an old tread, but I think I understand better Ubuntu now... There was in my opinion quite a big difference between ubuntu 10.04 and 10.04.1. With all updates per today, everything works a lot better than it would, if I had stayed with an old, unsupported ubuntu.

---

