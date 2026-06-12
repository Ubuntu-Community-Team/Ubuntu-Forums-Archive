---
title: "Ubuntu can't seem to do everything I want it to do"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by Rukaru on 2008-05-13
There's a couple things I did on windows that can't seem to be done on ubuntu.  For one, video chat.  I can't find away to use video with Pigin.  It makes my webcam useless.  The other thing is watching FOX.  There's a few shows I watch on FOX.com (which, incidentally, is my least favorite major network!), but I can't watch them here because you need to download something in order to watch them.  Also, i had yahoo widgets and vista sidebar before.  Anything that can replace that?

EDIT: Flash is not what you have to download.  You actually need to download the FOX video player.  I already have flash working.  When I tried to download it, it said I didn't have the right OS.  It's fin though.  I still have XP on the comp that I'll use for that and photoshop.  I don't want wine until it's more stable.

---

### Post by swankyfb on 2008-05-13
um.... im pretty sure u need macromedia flash to play videos on fox.com... open your synaptic package manager, and then type in flash or flash player. there should be a download.

---

### Post by zenwalker on 2008-05-13
1) There a few Apps which supports Video Chats, Kopete, Gyache, etc.
2) I wonder what has 2 be downloaded for watching FOX. U can make that software to work under linux using WINE (if supproting libs has been implemented) or else see if a linux ver of that package is avail from the vendor i.e FOX or some one else. If not, then blame FOX or who ever is developing that package for. Plus i dont know what u can watch on FOX. Is it via browser? 
3)Regarding widgets, u can get Google widgets on Linux desktops. Google up.

---

### Post by bjschuma on 2008-05-13
> **Rukaru said:**
>   Also, i had yahoo widgets and vista sidebar before.  Anything that can replace that?

Try screenlets (you should be able to find it in synaptic)

---

### Post by tjwoosta on 2008-05-13
yes for flash you will want to download flashplugin-nonfree

open a terminal and type this
```
sudo apt-get install flashplugin-nonfree
```

im not sure about the video chat because i dont use it, but i do believe i have heard of people using it before with ubuntu so dont give up yet

---

### Post by asrai on 2008-05-13
I don't know anything about video chat but I did a quick search and found a thread here: [http://ubuntuforums.org/showthread.php?t=788822](http://ubuntuforums.org/showthread.php?t=788822) that seems to have some info for you.  I got 10 pages of results searching for 'video chat' within these forums so a quick search may help if that particular thread doesn't assist you.

I'm not sure what you mean by "you need to download something in order to watch them"? Download what and have you tried to do this, if so what happened?

I'm not sure about widgets or vista sidebar but there are plenty of widgets and fancy things for ubuntu! This is not my area of expertise but take a look at the forum at [http://ubuntuforums.org/forumdisplay.php?f=330](http://ubuntuforums.org/forumdisplay.php?f=330) for more info about the different things you can do.

These forums and wikis are a great resource and I'm sure you'll find plenty of answers with a little searching.

---

### Post by bsharp on 2008-05-13
First, I would like to refer you to this: [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

To get flash videos working in firefox:
```
sudo apt-get install flashplugin-nonfree
```

As for a replacement for Vista sidebar, the closest thing I can think of is the widget plugin for compiz which is actually closer to the Mac OS 10.x widgets (where windows ripped the idea from in the first place), so you may want to take a look at that.

---

### Post by Mr A Mouse on 2008-05-13
Hi, Rukaru. No, I'm afraid that Yahoo widgets is not available for Linux. Yahoo has been talking about porting for quite a while, but they've (TTBOMK) not actually done anything about it that they've announced to the public.

As for FOX--what does it tell you that you need to download? That will help in seeing if there is an equivalent or a workaround.

---

### Post by tjwoosta on 2008-05-13
> EDIT: Flash is not what you have to download. You actually need to download the FOX video player. I already have flash working. When I tried to download it, it said I didn't have the right OS. It's fin though. I still have XP on the comp that I'll use for that and photoshop. I don't want wine until it's more stable.

well if you were interested you can make some versions of photoshop as well as the fox tv plugin w/ windows version of firefox2 in WINE

here is a link for the fox tv plugin (i think its the one your looking for)
[http://ubuntuforums.org/showthread.php?t=491153]("http://ubuntuforums.org/showthread.php?t=491153")

here is one for photoshop
[http://lifehacker.com/software/photoshop/how-to-install-photoshop-on-ubuntu-206827.php]("http://lifehacker.com/software/photoshop/how-to-install-photoshop-on-ubuntu-206827.php")

---

### Post by JoshuaRL on 2008-05-13
And Wine isn't going to be more stable for a long long time.  It works great, and since they have to reverse engineer a lot of what they do, it is in open beta in perpetuity.  But that doesn't mean it isn't great.

It is.

---

### Post by Rukaru on 2008-05-13
> **JoshuaRL said:**
> And Wine isn't going to be more stable for a long long time.  It works great, and since they have to reverse engineer a lot of what they do, it is in open beta in perpetuity.  But that doesn't mean it isn't great.

It is.

I'd imagine it puts the securitymore at risk for malware...since wine lets you use exe file types, right?

---

### Post by Mr A Mouse on 2008-05-13
Yes and no--yes, you can mess up your Windows DLLd and files, but no, you can't mess up your Linux system.

At least, that's the theory. :)

---

### Post by SunnyRabbiera on 2008-05-14
> **Mr A Mouse said:**
> Yes and no--yes, you can mess up your Windows DLLd and files, but no, you can't mess up your Linux system.

At least, that's the theory. :)

right, as the viruses and mallware will only infect the windows software.
But Linux has a lot of features if you give it time.
Personally I dont see why the widgets are all that important to you as I find most windows widgets memory hogs.
our screenlets will certainly do the job for you in this area.

---

### Post by JoshuaRL on 2008-05-14
Mr A Mouse is correct.  It may be possible to mess up Wine a little, but it's really hard to do since Wine doesn't exactly run the same as a full Windows OS.  But it can't mess up Linux.  And if you ever have any issue with Wine getting hosed, just reinstall and you should be fine.  That's the beauty of compatibility layers/emulators.

---

### Post by Rukaru on 2008-05-14
> **JoshuaRL said:**
> Mr A Mouse is correct.  It may be possible to mess up Wine a little, but it's really hard to do since Wine doesn't exactly run the same as a full Windows OS.  But it can't mess up Linux.  And if you ever have any issue with Wine getting hosed, just reinstall and you should be fine.  That's the beauty of compatibility layers/emulators.

But one person said it could mess up the dual booted XP dll's right? There's no way I'm doing it if it puts my precious XP at risk.  What I like about XP is how easy it is to download and install stuff from online. None of that code stuff.  All you need is the mouse :)

---

### Post by Mr A Mouse on 2008-05-14
> **JoshuaRL said:**
> Mr A Mouse is correct.  It may be possible to mess up Wine a little, but it's really hard to do since Wine doesn't exactly run the same as a full Windows OS.  But it can't mess up Linux.  And if you ever have any issue with Wine getting hosed, just reinstall and you should be fine.  That's the beauty of compatibility layers/emulators.
[snark]Wine Is Not an Emulator[/snark]

:D Sorry--I couldn't resist.

---

### Post by Rukaru on 2008-05-14
> **SunnyRabbiera said:**
> right, as the viruses and mallware will only infect the windows software.
But Linux has a lot of features if you give it time.
Personally I dont see why the widgets are all that important to you as I find most windows widgets memory hogs.
our screenlets will certainly do the job for you in this area.

Oh well i didn't mean to indicate that I want yahoo widgets.  i meant I wanted something like yahoo widgets.  If screenlets are similar, than they will do just fine.  How do I get them?

---

### Post by Mr A Mouse on 2008-05-14
> **Rukaru said:**
> But one person said it could mess up the dual booted XP dll's right? There's no way I'm doing it if it puts my precious XP at risk.  What I like about XP is how easy it is to download and install stuff from online. None of that code stuff.  All you need is the mouse :)
Not your Windows DLLs -- it can mess up the DLLs on your Wine install. Even if Wine picked up a virus, it wouldn't touch the Windows partition unless you deliberately copied the virus to the Windows side.

---

### Post by SunnyRabbiera on 2008-05-14
> **Rukaru said:**
> But one person said it could mess up the dual booted XP dll's right? There's no way I'm doing it if it puts my precious XP at risk.  What I like about XP is how easy it is to download and install stuff from online. None of that code stuff.  All you need is the mouse :)

Yes but look at how many issues you have under windows too.
Look you have to have patience with learning a new OS, it takes time too, and yes it is possible to simple install in linux if you know how to do it.
Look I know windows might look easy, but trust me its no better then linux in many ways...
Its just a matter of doing things differently, once you know how you will find linux to be perhaps easier then windows.

---

### Post by JoshuaRL on 2008-05-14
> **Rukaru said:**
> But one person said it could mess up the dual booted XP dll's right? There's no way I'm doing it if it puts my precious XP at risk.  What I like about XP is how easy it is to download and install stuff from online. None of that code stuff.  All you need is the mouse :)

**WILL NOT MESS WITH A WINDOWS PARTITION.**  You can feel safe about that.

> **Mr A Mouse said:**
> [snark]Wine Is Not an Emulator[/snark]

:D Sorry--I couldn't resist.

Man, you're busting my chops dude.  But I'm sure you know that a couple of years ago that changed when they added some functionality.  It actually is an emulator now.

Punk.  :p

> **Mr A Mouse said:**
> Not your Windows DLLs -- it can mess up the DLLs on your Wine install. Even if Wine picked up a virus, it wouldn't touch the Windows partition unless you deliberately copied the virus to the Windows side.

Exactamundo.  That's what's so great about Wine.

---

### Post by Rukaru on 2008-05-14
> **SunnyRabbiera said:**
> Yes but look at how many issues you have under windows too.
Look you have to have patience with learning a new OS, it takes time too, and yes it is possible to simple install in linux if you know how to do it.
Look I know windows might look easy, but trust me its no better then linux in many ways...
Its just a matter of doing things differently, once you know how you will find linux to be perhaps easier then windows.

Oh I know.  i am giving it time to learn.  I'm saying that right now...windows is much easier for me because I'm used to it.  I am aware that these things take some getting used to.

---

### Post by Mr A Mouse on 2008-05-14
> **JoshuaRL said:**
> Man, you're busting my chops dude.  

Hey, I'm equal opportunity obnoxious. :D

> But I'm sure you know that a couple of years ago that changed when they added some functionality.  It actually is an emulator now.

Punk.  :p

Ouch! I've been pwned! :lolflag:

Seriously, no I didn't know that Wine was now actually an emulator--thanks for the update. :)

---

### Post by SunnyRabbiera on 2008-05-14
still there are many things that are actually easier in linux then windows that I find:
5 times out of 10 hardware might actually work more out of the box then it does in windows, I had a digicam that I had to install a driver in for windows but linux surprisingly picked it up fast... linux is full of surprises sometimes, even with most hardware being made for windows only I have been faced with many surprises in my linux experience.
keeping software up to date and maintained in linux I find is easier in linux, as everything is kept in the repository and if a software needs updating the package manager comes in to handle it, as opposed to having to manually update each program under windows.
theming linux is also easier if you know how, in windows XP you had to use dangerous patches and third party software to do it.
plus intalling alternate interfaces in linux is easier, in XP you are almost stuck with the same old playskool theme.

---

### Post by Inxsible on 2008-05-14
You can use Skype for video chat...I am not sure if someone already mentioned that to you. I skipped a few posts ;)... Too lazy !!!

---

### Post by Rukaru on 2008-05-14
> **SunnyRabbiera said:**
> still there are many things that are actually easier in linux then windows that I find:
5 times out of 10 hardware might actually work more out of the box then it does in windows, I had a digicam that I had to install a driver in for windows but linux surprisingly picked it up fast... linux is full of surprises sometimes, even with most hardware being made for windows only I have been faced with many surprises in my linux experience.
keeping software up to date and maintained in linux I find is easier in linux, as everything is kept in the repository and if a software needs updating the package manager comes in to handle it, as opposed to having to manually update each program under windows.
theming linux is also easier if you know how, in windows XP you had to use dangerous patches and third party software to do it.
plus intalling alternate interfaces in linux is easier, in XP you are almost stuck with the same old playskool theme.

Don't talk to me about feelings you worm!  I can have a defibrillator in my house if I want to! 

Sorry, I needed to say something random.  As far as appearance and interface stuff, Ubuntu is better....and that's not even talking about the extra eye candy.  I always hated the default XP look, so I changed it a long time ago.  I got objectdock and hid the taskbar, so the desktop itself looked just fine.  For the windows, I had to do some patching and get some themes/visual styles.  So, it looked okay.  Still, it doesn't look as good as my vista and ubuntu.  I love the aero look (glass is awsome!) so I customized ubuntu (with emerald) to look just like it.  So now it looks like aero, but with way more awsome effects/animations and other eye candy stuff.  I mean...you can't beat the cube.

---

### Post by SunnyRabbiera on 2008-05-14
actually I dont think the aero theme is not much better, I dont like either one.
Actually the best OS with the best looks by default is OSX, though its hard to change the theme in it.

---

### Post by Rukaru on 2008-05-14
> **SunnyRabbiera said:**
> actually I dont think the aero theme is not much better, I dont like either one.
Actually the best OS with the best looks by default is OSX, though its hard to change the theme in it.

Well it is a matter of taste.  I don't like the metal look.  The glass can go with anything.  I don't like all aspects of the aero interface, but I like the glass window frames (whatever you call it). That's what I copied here on ubuntu. Some things on aero are just too glossy.  I just love the customization options in ubuntu.  it's dangerous because it has already used up about 3 hours of my time just making/editing themes in emerald!

---

### Post by nicedude on 2008-05-14
Help my Ubuntu won't mix my drinks or microwave my burritos ?

---

