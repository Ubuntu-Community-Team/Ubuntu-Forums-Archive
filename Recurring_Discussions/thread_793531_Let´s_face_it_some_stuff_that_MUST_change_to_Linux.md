---
title: "Let´s face it: some stuff that MUST change to Linux (Ubuntu in special) reach the sky"
date: 2008-05-13
forum: Recurring Discussions
---

### Post by richterlevania3 on 2008-05-13
Hi there,

First of all, let me say I´m using Kubuntu Hardy Heron with KD4 and Virtual Boxing sloWindow$ XP (some games I just can´t live without...). So, I´m not a Windows Enthusiast (If that even exists) or a Linux flamer. Rather than that, I´m just listing all the stuff I find VERY HARD to do on Ubuntu and, if improved, enhanced, changed or what you want to call it, would, lacking more suitable word, ERASE sloWindow$ from the Earth´s face forever. Let´s get moving:

**1. Command Line**

Ok, ok. I know some of you will think this is ridiculous or plain talk, but follow my thought: the student who never did more than homework on his PC, the wife that just likes to chat with her friends on MSN, the father that just want to edit some text and images. They want something and Ubuntu offers what they want. But in the case of the boy that wants his ultra-powerful video card fully working, what´s the choice? Geez, not Ubuntu fault if the manufacturer don´t make a native driver for Ubuntu or any Linux flavor. But must the alternatives be that hard to do and get our video card working? I´m talking about the Command Line. Manually editing config files as I did is not for everyone, and even if someone know how to do it sometimes he/she just don´t want to do, ´cause it´s hard, time consuming doing so. 

**Idea:** how about a full GUI to configure every video setting? I mean, why is that not avaiable already?

More to come.

Meanwhile, I would enjoy some comments and thoughts about my words. Flames are accepted, of course.

---

### Post by darrenn on 2008-05-13
I think you should run ubuntu as a virtual machine and use windows as your main OS. You don't sound like your experienced enough to have ubuntu as your main OS.

---

### Post by Mateo on 2008-05-13
True, you are definitely right.  There is a video GUI app but it's not very good.  I think the problem is that they have tried to make it work for all the different cards.  But instead there should probably be separate apps for Nvidia and ATI cards at the very least, if not broken down even more.

---

### Post by Mateo on 2008-05-13
> **darrenn said:**
> I think you should run ubuntu as a virtual machine and use windows as your main OS. You don't sound like your experienced enough to have ubuntu as your main OS.

Uh, I don't think that's the right attitude to have at all.  Ubuntu should be accessible to all different types of users.

---

### Post by darrenn on 2008-05-13
I haven't always used linux. I was once a windows user. But as I grew more and more comfortable with linux, I slowly started booting into windows less and less. Im all for training wheels for linux. And if virtual box can do that all the better.

---

### Post by FuturePilot on 2008-05-13
> But in the case of the boy that wants his ultra-powerful video card fully working, what´s the choice? Geez, not Ubuntu fault if the manufacturer don´t make a native driver for Ubuntu or any Linux flavor. But must the alternatives be that hard to do and get our video card working? I´m talking about the Command Line. Manually editing config files as I did is not for everyone, and even if someone know how to do it sometimes he/she just don´t want to do, ´cause it´s hard, time consuming doing so.
And exactly how much easier would that be to get that same card working on Windows? I hope you would have a CD with drivers on it that are compatible with the latest version of Windows, or it's off to Google. And if that fails you're out of luck.
> Idea: how about a full GUI to configure every video setting? I mean, why is that not avaiable already?
If you have a Nvidia card this is already available.
```
nvidia-settings
```
Also in Hardy it now has a menu entry System&#8594;Administration&#8594;NVIDIA X Server Settings

---

### Post by |{urse on 2008-05-13
lol, if you think ubuntu is tough to figure out your foray into linux should stop here. Look at it like cars, windows is kinda like an automatic, no fun to drive and expensive to replace. Linux is like a manual, you have complete control but have to be willing to learn how to do it. GUI's and wizards are overrated, what takes "slow" users 12 mouse clicks to do, i can do with a single command.

---

### Post by justin whitaker on 2008-05-13
Don't fear the command line....it's often the fastest, and easiest, way to get something done. You just need to know the right commands. :)

---

### Post by chick on 2008-05-14
You are throwing out very general remarks. Tell us more details about your difficulties?

Even for a camera you would need to read the manual, but not so for an operating system?

But I do agree that the documentation on configuring X.org is inadequate, if that's what's you're talking about.

---

### Post by bufsabre666 on 2008-05-14
honestly play around with commands and everything, honestly for your average use they prolly wont ever even need to look at a command line, but the more familiar you are with it the less and less you fear using it, its a very good tool and i think windows should adopt something like it cause the command prompt is useless

---

### Post by fissionmailed on 2008-05-14
Linux isn't for everyone, if you want to be "different" but not do anything, there are always Macs....

---

### Post by Riffer on 2008-05-14
I think the people that you discribe would have trouble even in a windows enviroment, installing drivers and tweaking resolution can be daunting for alot of window users.

Installing drivers in the Linux enviroment is no harder then in windows and in some cases easier, its just a "different" way is all.

---

### Post by perce on 2008-05-14
The OP has a point: X.org is not plug and play, in the sense that a new mouse 
or a new screen wich are not configured yet won't work until X.org is reconfigured. This is quite unpleasant and is a point where Linux is really lagging behind Windows or Mac. However it's not as unpleasant as manually editing /etc/X11/xorg.conf: often dpkg-reconfigure is able to solve the problem almost automatically. 

Rumors say that this has been fixed in the new X.org (which should be shipped in Hardy) but I haven't upgraded yet.

---

### Post by SunnyRabbiera on 2008-05-14
> **richterlevania3 said:**
> Hi there,

First of all, let me say I´m using Kubuntu Hardy Heron with KD4 and Virtual Boxing sloWindow$ XP (some games I just can´t live without...). So, I´m not a Windows Enthusiast (If that even exists) or a Linux flamer. Rather than that, I´m just listing all the stuff I find VERY HARD to do on Ubuntu and, if improved, enhanced, changed or what you want to call it, would, lacking more suitable word, ERASE sloWindow$ from the Earth´s face forever. Let´s get moving:

**1. Command Line**

Ok, ok. I know some of you will think this is ridiculous or plain talk, but follow my thought: the student who never did more than homework on his PC, the wife that just likes to chat with her friends on MSN, the father that just want to edit some text and images. They want something and Ubuntu offers what they want. But in the case of the boy that wants his ultra-powerful video card fully working, what´s the choice? Geez, not Ubuntu fault if the manufacturer don´t make a native driver for Ubuntu or any Linux flavor. But must the alternatives be that hard to do and get our video card working? I´m talking about the Command Line. Manually editing config files as I did is not for everyone, and even if someone know how to do it sometimes he/she just don´t want to do, ´cause it´s hard, time consuming doing so. 

**Idea:** how about a full GUI to configure every video setting? I mean, why is that not avaiable already?

More to come.

Meanwhile, I would enjoy some comments and thoughts about my words. Flames are accepted, of course.

well if you think the command line is bad now, you should have seen things 10 years ago.

---

### Post by bufsabre666 on 2008-05-14
> **SunnyRabbiera said:**
> well if you think the command line is bad now, you should have seen things 10 years ago.

10 years? even 4 years ago it wasnt that great

---

### Post by SunnyRabbiera on 2008-05-14
> **bufsabre666 said:**
> 10 years? even 4 years ago it wasnt that great

perhaps, but its improved a lot even 4 years ago...
I started using linux 4 years ago I hope you know :D

---

### Post by bufsabre666 on 2008-05-14
> **SunnyRabbiera said:**
> perhaps, but its improved a lot even 4 years ago...
I started using linux 4 years ago I hope you know :D

thats when i started too, if anyone wants a comparison they should find a warty iso and compare it to hardy, trust me hardy is a cake walk in comparison

---

### Post by swoll1980 on 2008-05-14
> **richterlevania3 said:**
> Hi there,

First of all, let me say I´m using Kubuntu Hardy Heron with KD4 and Virtual Boxing sloWindow$ XP (some games I just can´t live without...). So, I´m not a Windows Enthusiast (If that even exists) or a Linux flamer. Rather than that, I´m just listing all the stuff I find VERY HARD to do on Ubuntu and, if improved, enhanced, changed or what you want to call it, would, lacking more suitable word, ERASE sloWindow$ from the Earth´s face forever. Let´s get moving:

**1. Command Line**

Ok, ok. I know some of you will think this is ridiculous or plain talk, but follow my thought: the student who never did more than homework on his PC, the wife that just likes to chat with her friends on MSN, the father that just want to edit some text and images. They want something and Ubuntu offers what they want. But in the case of the boy that wants his ultra-powerful video card fully working, what´s the choice? Geez, not Ubuntu fault if the manufacturer don´t make a native driver for Ubuntu or any Linux flavor. But must the alternatives be that hard to do and get our video card working? I´m talking about the Command Line. Manually editing config files as I did is not for everyone, and even if someone know how to do it sometimes he/she just don´t want to do, ´cause it´s hard, time consuming doing so. 

**Idea:** how about a full GUI to configure every video setting? I mean, why is that not avaiable already?

More to come.

Meanwhile, I would enjoy some comments and thoughts about my words. Flames are accepted, of course.

I don't get it. There is video guis for Nvidia and Ati the Nvidia settings for Linux is the same one I have for Windows

---

### Post by seshomaru samma on 2008-05-14
> **richterlevania3 said:**
> Hi there,


**1. Command Line**


In Suse Linux you don't need to use the command line at all.
I think that for most stuff you rarely use the command line in Ubuntu - unless you need to, especially if you buy/get a machine pre-installed with Linux ,the same way that most people get their Windows/Mac

---

### Post by seshomaru samma on 2008-05-14
> **richterlevania3 said:**
> Hi there,


**1. Command Line**


In Suse Linux you don't need to use the command line at all.
I think that for most stuff you rarely use the command line in Ubuntu - unless you need to, especially if you buy/get a machine pre-installed with Linux ,the same way that most people get their Windows/Mac

---

### Post by seshomaru samma on 2008-05-14
> **richterlevania3 said:**
> Hi there,


**1. Command Line**


In Suse Linux you don't hardly need to use the command line at all.
I think that for most stuff you rarely use the command line in Ubuntu - , especially if you buy/get a machine pre-installed with Linux ,the same way that most people get their Windows/Mac

---

### Post by bufsabre666 on 2008-05-14
> **seshomaru samma said:**
> In Suse Linux you don't hardly need to use the command line at all.
I think that for most stuff you rarely use the command line in Ubuntu - , especially if you buy/get a machine pre-installed with Linux ,the same way that most people get their Windows/Mac

well im a big fan of suse linux now, and alot of things i dont need to use the commandline for i use it cause it usually is a fair bit faster than the gui way

---

### Post by SupaSonic on 2008-05-14
This should really be in recurring discussions.

And by the way, you don't **need** the CLI to edit config files. Fire up root nautilus and edit them with gedit - it's all GUI. It's just simpler and faster for me to edit them from CLI, which kinda destroys the OP's point.

I'd take a config file over a registry edit any day.

---

### Post by UnknownElement on 2008-05-14
Regarding the command line, I think it can generally be avoided by the end user when things are working fine. If something breaks however, often the solution involves using the command line instead of a GUI-based tool as would often be the case with Windows. For this reason, if you don't want to bother with the command line, just hope that your problems are mostly trivial. ;)

---

### Post by 3rdalbum on 2008-05-14
> **richterlevania3 said:**
> But in the case of the boy that wants his ultra-powerful video card fully working, what´s the choice? Geez, not Ubuntu fault if the manufacturer don´t make a native driver for Ubuntu or any Linux flavor. But must the alternatives be that hard to do and get our video card working? I´m talking about the Command Line. Manually editing config files as I did is not for everyone, and even if someone know how to do it sometimes he/she just don´t want to do, ´cause it´s hard, time consuming doing so. 

**Idea:** how about a full GUI to configure every video setting? I mean, why is that not avaiable already?

Here's a better idea: How about Ubuntu comes with a special program that detects when the user has put in a new graphics card, and asks the user if they want to install the drivers? If the user says yes, the program can download and install the drivers, and next time you reboot the new graphics card drivers will be fully operational without you even needing to "configure" it.

We could call this program something obvious, like "Hardware Drivers", and put it under the System > Administration menu. It could also work with things other than graphics drivers - for instance, wireless or sound card drivers! And if you wanted to remove said drivers, just go back into the program and uncheck the box.

I believe such a program as I have proposed, will cause hoardes of disillusioned Windows users to immediately migrate over to Ubuntu. I think I'll start work on it immediately, and I'm sure the OP will volunteer his help in testing such a program.

---

### Post by K.Mandla on 2008-05-14
Yawn. Moved to Recurring Discussions.

---

### Post by |{urse on 2008-05-14
Just wanted you to know if you wanted to purchase a preconfigured ubuntu machine there are more and more places popping up where u can purchase them.. check out the link in my sig

---

### Post by LaRoza on 2008-05-14
> **richterlevania3 said:**
> Hi there,

**1. Command Line**

Ok, ok. I know some of you will think this is ridiculous or plain talk, but follow my thought: the student who never did more than homework on his PC, the wife that just likes to chat with her friends on MSN, the father that just want to edit some text and images. They want something and Ubuntu offers what they want. But in the case of the boy that wants his ultra-powerful video card fully working, what´s the choice? Geez, not Ubuntu fault if the manufacturer don´t make a native driver for Ubuntu or any Linux flavor. But must the alternatives be that hard to do and get our video card working? I´m talking about the Command Line. Manually editing config files as I did is not for everyone, and even if someone know how to do it sometimes he/she just don´t want to do, ´cause it´s hard, time consuming doing so. 

**Idea:** how about a full GUI to configure every video setting? I mean, why is that not avaiable already?


Obviously, you are not all that skilled with Windows. Vista requires the command line for some tasks that XP could do with a GUI. Both have tasks that require the command line. The average person doesn't need to use them. As for video settings, it does have a GUI.

---

### Post by gadget_hacker on 2008-05-14
you should try to not be so high and mighty.  Just because someone has constructive criticism for ubuntu, doesn´t mean in any way that they are too stupid to use it.  Don´t forget that there are plenty of people out there with enough linux experience to make you look like a noob.  I like the idea.  A GUI would be helpful for some that are still getting there feet wet.

---

### Post by LaRoza on 2008-05-14
> **gadget_hacker said:**
> you should try to not be so high and mighty.  Just because someone has constructive criticism for ubuntu, doesn´t mean in any way that they are too stupid to use it.  Don´t forget that there are plenty of people out there with enough linux experience to make you look like a noob.  I like the idea.  A GUI would be helpful for some that are still getting there feet wet.

If you are talking to me, I wasn't trying to be high and mighty.

It isn't constructive criticism, otherwise, it wouldn't be in the Recurring Discussions. 

I don't know how you know what my experience is, but I would prefer you not do personal attacks.

If a GUI would be helpful, there is nothing wrong with making one. I am working (actually, finished) a system restore program because people seemed to think Ubuntu needed one. I don't think Ubuntu needs one, but I programmed it because I thought I could be helpful. (I haven't released it) I did it because I chose to, not because someone told me to. It is futile to make demands.

---

### Post by |{urse on 2008-05-14
Laroza I'd love to see your system restore program, are you using something like partimage or all dd?

---

### Post by LaRoza on 2008-05-14
> **|{urse said:**
> Laroza I'd love to see your system restore program, are you using something like partimage or all dd?

No. It is just a local restore for settings.

Example of use:

All your video, grub, fstab and other system settings are working, so you make a restore point. You can make many restore points and they can have names. Their date and time of creation is recorded. You fiddle with a new video card/try to change the boot order/alter fstab/etc and something goes wrong. You can restore the system from that restore point.

It has a GUI and a CLI, and it can be extended by user rules (like if a user wants to add ~/.vimrc or ~/.bashrc or something). By default, it only does fstab, menu.lst, sources.list, and xorg.conf. Adding others as defaults would be a simple addition to the code.

I am not sure if I want to release it. It isn't the best coding and was mostly something I did at night when I was bored.

---

### Post by |{urse on 2008-05-14
oh cool, I have my own thing in the works using the above-mentioned programs unfortunately i cant post any of it here as there are too many naughty looking commands i don't want people to run, but basically it uses partimage for the partitions, a non open-source prog for recreating raidsets and dd for partition tables and mbr. Just cli menu in a case statement with a few nested loops atm but what else do you need lol? it has a "do it all" selection for speshul ppl. O and all running from a livecd of course ^^ I am proud to say that it's all built up off of minix (pretty proud of that) busybox was a pain though.

---

### Post by richterlevania3 on 2008-05-14
> **Mateo said:**
> True, you are definitely right.  There is a video GUI app but it's not very good.  I think the problem is that they have tried to make it work for all the different cards.  But instead there should probably be separate apps for Nvidia and ATI cards at the very least, if not broken down even more.

Your approach can be the right one. Wish the devs look deeper in this matter, or maybe someone who programms could make a GUI.

---

### Post by richterlevania3 on 2008-05-15
> And exactly how much easier would that be to get that same card working on Windows? I hope you would have a CD with drivers on it that are compatible with the latest version of Windows, or it's off to Google. And if that fails you're out of luck.

Don´t be like that: it´s just simplier (is this word correct?) find any video driver for any version of windows than a linux counterpart. I know the manufacturer don´t release a native driver for us, but I really can´t believe that nobody here cannot make a full GUI for the ATI and nVidia drivers avaliable. The point is just that: don´t eliminate the command line, just offer us an alternative to do things with the ol´n good mouse. It may be surprising to you, but the majority of the world want to do these things as easy as possible.

---

### Post by cardinals_fan on 2008-05-15
> **richterlevania3 said:**
> Don´t be like that: it´s just simplier (is this word correct?) find any video driver for any version of windows than a linux counterpart. I know the manufacturer don´t release a native driver for us, but I really can´t believe that nobody here cannot make a full GUI for the ATI and nVidia drivers avaliable. The point is just that: don´t eliminate the command line, just offer us an alternative to do things with the ol´n good mouse. It may be surprising to you, but the majority of the world want to do these things as easy as possible.
NVIDIA does provide a native Linux driver.

---

### Post by richterlevania3 on 2008-05-15
> **|{urse said:**
> lol, if you think ubuntu is tough to figure out your foray into linux should stop here. Look at it like cars, windows is kinda like an automatic, no fun to drive and expensive to replace. Linux is like a manual, you have complete control but have to be willing to learn how to do it. GUI's and wizards are overrated, what takes "slow" users 12 mouse clicks to do, i can do with a single command.

You are right: like in GT4, I prefer the manual shift than the auto one. But I drove a long time with auto shift before I changed to manual. 

Again, it´s slower to click a lot of windows and boxes, but it´s also waaayyy easier. And again, don´t eliminate the command line, instead just offer us, that part of people trying to move to linux as fast as possible, as easy as possible, an alternative to do these stuff.

---

### Post by richterlevania3 on 2008-05-15
> **UnknownElement said:**
> Regarding the command line, I think it can generally be avoided by the end user when things are working fine. If something breaks however, often the solution involves using the command line instead of a GUI-based tool as would often be the case with Windows. For this reason, if you don't want to bother with the command line, just hope that your problems are mostly trivial. ;)

Now I found someone who just got what I meant to tell. This is just what happens. Instead of accepting this like it is now, why don´t improve, enhance, offer an alternative? I took a week or so to get my system working. I did need to search how to install my video driver and configure it (even to change the resolution and refresh rate I did need to manually edit the config file), how to enable my wireless network (oh, and I had had to disable the WEP, ´cause nothing I tried, even some very good howto´s from these forums, worked) and so on. The same thing I can do in less than 2 hours, for sure, in Windows OR Mac, that is an OS based on Unix.

If they (Mac) managed to reach this point, why can´t we?

---

### Post by richterlevania3 on 2008-05-15
> **3rdalbum said:**
> Here's a better idea: How about Ubuntu comes with a special program that detects when the user has put in a new graphics card, and asks the user if they want to install the drivers? If the user says yes, the program can download and install the drivers, and next time you reboot the new graphics card drivers will be fully operational without you even needing to "configure" it.

We could call this program something obvious, like "Hardware Drivers", and put it under the System > Administration menu. It could also work with things other than graphics drivers - for instance, wireless or sound card drivers! And if you wanted to remove said drivers, just go back into the program and uncheck the box.

I believe such a program as I have proposed, will cause hoardes of disillusioned Windows users to immediately migrate over to Ubuntu. I think I'll start work on it immediately, and I'm sure the OP will volunteer his help in testing such a program.

This is just what I wanted to see here, someone who knows to programm getting the idea and trying to enhance this particularly "hard" part of installing and configuring the entire system. 

Of course I can help with everything you need! Testing and feedbacking, or maybe translating to portuguese (my native language).

---

### Post by richterlevania3 on 2008-05-15
> **LaRoza said:**
> If you are talking to me, I wasn't trying to be high and mighty.

It isn't constructive criticism, otherwise, it wouldn't be in the Recurring Discussions. 

I don't know how you know what my experience is, but I would prefer you not do personal attacks.

If a GUI would be helpful, there is nothing wrong with making one. I am working (actually, finished) a system restore program because people seemed to think Ubuntu needed one. I don't think Ubuntu needs one, but I programmed it because I thought I could be helpful. (I haven't released it) I did it because I chose to, not because someone told me to. It is futile to make demands.

Well, your "way" to do things don´t help Ubuntu or any linux flavor to reach the majority of people that uses a PC just for work or surf the web. Normal people, you could call it.

You probably did a good job creating such programm, but don´t think everyone knows a lot about PC´s and programms and CLI´s like you to not use it and, like you, prefer not using it ´cause think it´s pointless.

---

### Post by richterlevania3 on 2008-05-15
> **cardinals_fan said:**
> NVIDIA does provide a native Linux driver.

Native, yes, but we must go to CLI, shutdown the GDM or KDM manually (which is quite impossible to a normal person know without googling) and start the installer there. And that done, if everything went ok, we must configure the xorg file, ´cause something will always get wrong or misconfigured.

C´mon, man: it´s an outdated driver that is 30% or more less efficient than the Windows counterpart and still hard to install. 

Why not to make a full GUI for it, allowing easy instalation and configuration?

---

### Post by Kinst on 2008-05-15
I think ubuntu's the wrong distro for you. Ubuntu's very very awesome, but if you're looking for a strong control center for GUI configuration you're looking at openSUSE, Mandriva and PCLinuxOS. 

openSUSE uses YaST and Mandriva and PCLinuxOS use drakconf, both are great graphical tools for editing xorg.conf, grub, dual monitors, stuff like that. Hope this actually helps instead of pissing anyone off. ;)

---

### Post by Canis familiaris on 2008-05-15
Try Linux Mint. In Mint you rarely need to use the command line.

---

### Post by LaRoza on 2008-05-15
> **richterlevania3 said:**
> 
You probably did a good job creating such programm, but don´t think everyone knows a lot about PC´s and programms and CLI´s like you to not use it and, like you, prefer not using it ´cause think it´s pointless.

The problem with it is that it takes about a minute to get the concepts it hides. Do I really want to contribute to ignorance of the system?

> **richterlevania3 said:**
> 
Why not to make a full GUI for it, allowing easy instalation and configuration?

Why not? No one is stopping you.

---

### Post by madjr on 2008-05-15
> **Anurag_panda said:**
> Try Linux Mint. In Mint you rarely need to use the command line.

+1 and the new mint will include envyNG by default

[IMG]http://img11.nnm.ru/imagez/gallery/2/0/9/6/3/20963a3cd1f94f4cc83b5dfa249f33aa_full.jpg[/IMG]


nvidia-settings
[IMG]http://bp1.blogger.com/_Xc3ug-O4s-g/Rnf8lGbAURI/AAAAAAAAANs/kycMs0_2hWM/s1600/screenshot-nvidia-settings.png[/IMG]

---

### Post by whitefort on 2008-05-15
> **darrenn said:**
> You don't sound like your experienced enough to have ubuntu as your main OS.

Um... excuse me - I'm not experienced, and I'm running Ubuntu on 4 of my computers.  I disagree strongly with your comment, and if it were true it would be one of the most damning condemnations of Ubuntu I've heard.

No offense, but when I first tried Ubuntu and came here for help, I'm very grateful that the first answers I received were very different from yours.  Otherwise I'd probably have gone back to Windows.

---

### Post by aysiu on 2008-05-15
> **madjr said:**
> +1 and the new mint will include envyNG by default I think Envy's highly overrated. I tried it out with Linux Mint a while ago, and when I had a kernel update, my X configuration was completely broken and I was stuck in safe video mode no matter what I did.

I'd much rather use Restricted Drivers Manager.

---

### Post by Jadephyre on 2008-05-15
how about they fix the latest Kernel so that a good amount of users (like me) won't get stuck at a BusyBox Prompt.

Hardy has been the worst so far for me, and i'm sticking with Gutsy and it's derivates for the Moment (gOS Space 2.9).
I really hoped that Hardy would be better than the Original Gutsy, but i have been deeply disappointed with the Kernel they included as this one can't detect my Processor in either flavor (32bit & 64Bit).

---

### Post by |{urse on 2008-05-15
LOl people are going to be mad at me now. TO be perfectly honest I don't think linux users/developers/community need to retard (slow down) themselves just because of, how do i put this, slower kids in the classroom? Seems to me that if linux is going to be for the savvy (*which it should be) then the new users are better off learning things the hard way. PFF PFF PFFFFFF! @ point and click wizards.

That said, I don't believe myself to be smarter because I have shaped my career around *nix (which i have for the last 5 yrs) but i'll tell you one thing. Other OSes like Solaris, BSD were much easier to install because i kinda knew or could guess where things should be and how to properly configure them! lol, and that makes me money, I say the more minimal the gui, the more the user truly understands whats going on in the OS and the more apt they are to be able to do amazing things with the software.

---

### Post by LaRoza on 2008-05-15
> **Jadephyre said:**
> how about they fix the latest Kernel so that a good amount of users (like me) won't get stuck at a BusyBox Prompt.

Hardy has been the worst so far for me, and i'm sticking with Gutsy and it's derivates for the Moment (gOS Space 2.9).

I really hoped that Hardy would be better than the Original Gutsy, but i have been deeply disappointed with the Kernel they included as this one can't detect my Processor in either flavor (32bit & 64Bit).

Hardy doesn't use the lastest kernel.

What processor do you have that it can't detect? That is most weird. I do believe you have misdiagnosed the issue though.

---

### Post by darrenn on 2008-05-17
> Um... excuse me - I'm not experienced, and I'm running Ubuntu on 4 of my computers. I disagree strongly with your comment, and if it were true it would be one of the most damning condemnations of Ubuntu I've heard.

No offense, but when I first tried Ubuntu and came here for help, I'm very grateful that the first answers I received were very different from yours. Otherwise I'd probably have gone back to Windows.

Sorry. :( Did you read post number five?

---

