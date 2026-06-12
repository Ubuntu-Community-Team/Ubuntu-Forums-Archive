---
title: "Is ubuntu getting fat?"
date: 2010-07-28
forum: Recurring Discussions
---

### Post by justinsn95 on 2010-07-28
One of the main reasons I want to switch to Ubuntu from windows, is the fact that it uses less system resources. Well, at least I thought it used to. Here is a screenshot of my system, running a simple stock market trading program, that I must always leave open. This isn't even with FireFox, or Limewire, or Rythmbox music player, or anything else. This is just one program, that only uses about 17Mb of RAM. 

Now, if you looked at the pic, you can see what I am talking about here. I have trimmed down Windows 7 to only run the necessary parts. Parts that any user might want running, really. I disabled much of Microsoft's infamous bloat, and now I have windows 7 (64 bit) running at 908Mb with the same program open. Now of course, windows is still running roughly 100Mb more than Ubuntu. But the gap is closing. Back when I tried out Ubuntu Gutsy 7.10 when it first came out, the idle (with FF and Limewire running) was about 330Mb. 

I know that was an older version, and I know that 10.04 likely has some goodies that the older stuff didn't have. But man, if this continues on like this, I will see the loss of 1 more reason to use Ubuntu instead of windows. Is there anything that you guys can think of, that I could do to get my RAM usage down? I haven't messed with it too awful much, all I have been doing is installing some necessary software and getting it to look pretty. It seems to me like it should be using 400Mb of RAM at most, not twice that amount.

---

### Post by justinsn95 on 2010-07-28
The pic:

---

### Post by prodigy_ on 2010-07-28
Ubuntu 10.04 (64-bit) uses 640MiB of my RAM (right now with FF running). Windows 7 (64-bit) uses 1.5GiB+.

Not that it make any difference to me...

---

### Post by borth92 on 2010-07-28
You have to realize that as Ubuntu gets newer, they count on the average computer getting better. These days most software companies count on the user having about 1GB RAM. With 1gb, the little amount your program is taking is hardly anything (you could run 50 of them before you need to dip into your HDD). So yes, Ubuntu is fatter than it was, but if you look at the features and RAM usage in the competition (Windows and Mac), It is not getting any more resource hungry than other OS's and in fact is getting faster than the other two, showing that it's RAM usage is not increasing as fast as the competition.

---

### Post by howefield on 2010-07-28
What does it use after booting, and are you using 32 bit or 64 bit ?

---

### Post by Mike'sHardLinux on 2010-07-28
ummmm. Don't forget. Windows generally will run to the swap file well before you ever really need it. Ubuntu...and any Linux distro I've ever used.....on the other hand, takes advantage of the RAM you have. That is to improve performance. Not necessarily because of "fatness".

Plus, you still got over 3Gigs free! What's the point of having it if you don't use it?

---

### Post by kerry_s on 2010-07-28
i think it's not fair to blame ubuntu for a programs resource use.

would you blame your car if you use bad tires?

---

### Post by dreamsR4living on 2010-07-28
My Ubuntu 10.04 just uses 315 MB ram, with Firefox on which is in turn using 64 MB ram. Ubuntu (with visual effects by the way) just takes about 250 MB ram on my machine (which is still not as good as my Debian - Fluxbox install which takes only 65 MB ram in total). 

Really check your systems monitor for programs eating up ram, because Ubuntu just using over 800 MB is far from normal.

---

### Post by ve3tru on 2010-07-28
That's not really fair, if you have an older computer or one with limited resources there is
Xubuntu for you. If thats too much, you can even go dam small linux its all about choice.
I want more things not less, I'm greedy that way, if you don't like it, you have choices don't try taking mine away. Why not try going into the kernal and turn stuff off you don't need, I did, little things like blue tooth (i never use it) takes cpu and battery power.

---

### Post by justinsn95 on 2010-07-28
> **Mike'sHardLinux said:**
> ummmm. Don't forget. Windows generally will run to the swap file well before you ever really need it. Ubuntu...and any Linux distro I've ever used.....on the other hand, takes advantage of the RAM you have. That is to improve performance. Not necessarily because of "fatness".

Plus, you still got over 3Gigs free! What's the point of having it if you don't use it?

I still use it when gaming. And when gaming, the less RAM used by everything else, the faster you go. I mean, the better your game runs. So I like to have it as low as I can. 

> **dreamsR4living said:**
> My Ubuntu 10.04 just uses 315 MB ram, with Firefox on which is in turn using 64 MB ram. Ubuntu (with visual effects by the way) just takes about 250 MB ram on my machine (which is still not as good as my Debian - Fluxbox install which takes only 65 MB ram in total). 

Really check your systems monitor for programs eating up ram, because Ubuntu just using over 800 MB is far from normal.

Now *that* sounds like the Ubuntu that I remember. Very low system resource usage. I have checked what I have going, and everything that is running, is stuff that sounds like it needs to be running. Where do you go to check your stuff? Maybe I am looking in the wrong place.

---

### Post by clhsharky on 2010-07-28
justinsn95

At start up my memory use is around 400MB. After chromium with a hand full of tabs, terminal, text editor, default background apps including compiz, I end up with this
> free -m
             total       used       free     shared    buffers     cached
Mem:          3962        661       3300          0         31        225
-/+ buffers/cache:        404       3557
Swap:         4596          0       4596

I think its good for a modern OS.

Ubuntu and Kubuntu is a little heave but full featured.
There are lighter distros like Lubuntu.

Sharky

used 661

---

### Post by justinsn95 on 2010-07-28
Well I narrowed it down to the stock trading program that is causing all the trouble. Sort of. When I boot, and don't run anything but the resource monitor, I am running a nice 315Mib (don't know what the "i" is for in mib) of RAM. Then, when I start the trading program, it skyrockets up to around 675Mb of RAM. Well, once I close the program, it doesn't do what it is supposed to, and go back down to 315Mb of RAM. It only goes down to 455Mb of RAM. 

What is going on there? How can I fix that? I need it to go right back down to 315Mb of RAM at idle. I have to figure all this out, if I ever want to be able to run Ubuntu on a tablet. I want to learn how to best run it on a tablet like the ipad. Doesn't necessarily have to be an Ipad, but you get the idea.

---

### Post by clhsharky on 2010-07-28
Ubuntu was designed for desktop not a tablet, try a lighter distro.

> try a lighter distro
Is incorrect.
Tablets use a arm architecture and will probably need a special distro for the tablet form factor to look, work correctly.

---

### Post by kerry_s on 2010-07-28
> **justinsn95 said:**
> Well I narrowed it down to the stock trading program that is causing all the trouble. Sort of. When I boot, and don't run anything but the resource monitor, I am running a nice 315Mib (don't know what the "i" is for in mib) of RAM. Then, when I start the trading program, it skyrockets up to around 675Mb of RAM. Well, once I close the program, it doesn't do what it is supposed to, and go back down to 315Mb of RAM. It only goes down to 455Mb of RAM. 

What is going on there? How can I fix that? I need it to go right back down to 315Mb of RAM at idle. I have to figure all this out, if I ever want to be able to run Ubuntu on a tablet. I want to learn how to best run it on a tablet like the ipad. Doesn't necessarily have to be an Ipad, but you get the idea.

thats normal, the program is cached. when the ram is needed by something else it will be released. it may also be released after a period of time.

what i tell people is don't worry about it, let the memory do what it's suppose to do. just use your computer.

---

### Post by Iowan on 2010-07-28
Not really a support request - moved to Community Cafe.

---

### Post by Chronon on 2010-07-28
> **clhsharky said:**
> Ubuntu was designed for desktop not a tablet, try a lighter distro.


Is incorrect.
Tablets use a arm architecture and will probably need a special distro for the tablet form factor to look, work correctly.

It's not that huge of a deal.  You can always use cross-compilers to convert ELF to ARM, for example.

---

### Post by Zorgoth on 2010-07-28
My very flashy Ubuntu desktop with compiz (and like 30 key bindings), cairo-dock, firefox, skype, nautilus, and emacs all going uses 600-900 MB of ram.  That is a lot less than I have ever seen Windows 7 do.  Maybe if you bought a boxed copy for $200 or spent a week cleaning out all the bloatware.

When I was using 1GB of RAM and a USB stick based installation and was going for efficiency I only use 250 MB of ram.

---

### Post by Version Dependency on 2010-07-28
> **justinsn95 said:**
> The pic:

So you're using 1 gig of your 4 gigs.  I'm going to file this under "not an issue."

But for comparison, just opened up my system monitor and I'm using just under 2 gigs right now out of my 6 gigs.  Should I be worried?  No...I have 4 gigs of RAM left!  Why buy a bunch of RAM if you're not going to ever use it?

---

### Post by NightwishFan on 2010-07-28
Ram usage is of no concern. If you notice a definite droop in responsiveness or performance it is then you should be concerned. I find that when you have less RAM it uses less, so it has to depend on how it is measured/allocated. As for gaming, I find Linux really is amazing for that. I have my system set for vm.swappiness=100, so if I run near the brink, it will swap out all my inactive stuff such as nautilus, gnome-panel, etc.

---

### Post by justinsn95 on 2010-07-28
> **kerry_s said:**
> thats normal, the program is cached. when the ram is needed by something else it will be released. it may also be released after a period of time.

what i tell people is don't worry about it, let the memory do what it's suppose to do. just use your computer.

Well as I said earlier, I am trying to learn Ubuntu well enough that I can use it (or some linux distro) on a tablet PC similar to the Ipad. HP canceled their "Slate" tablet which was competition for the Ipad, because Windows 7 drained the battery in about 30 minutes. *But,* if you had an OS that had very low RAM usage, then it wouldn't drain the battery so fast. I am thinking that Ubuntu could be perfect for this task. So do you think that there is a way that I can keep the program from being cached? There must be some way...

> **Version Dependency said:**
> So you're using 1 gig of your 4 gigs.  I'm going to file this under "not an issue."

But for comparison, just opened up my system monitor and I'm using just under 2 gigs right now out of my 6 gigs.  Should I be worried?  No...I have 4 gigs of RAM left!  Why buy a bunch of RAM if you're not going to ever use it?

Well one reason is my other reply in this post. Another is that I simply like the challenge of trying to get it low so the system runs as fast as it can, for daily usage. Its nice to have your computer be as fast as it can be at all times. The last reason is Gaming. The more RAM you have cleared out for gaming, the better the gaming experience because you can set your settings higher without your framerate dropping quite as low. Its just kind of a nice thing to have low/very low RAM usage. So as yall can see from my replies here, I have multiple reasons for wanting low RAM usage.

---

### Post by NightwishFan on 2010-07-28
Really it depends how low you need it. You can install a core Ubuntu system and build it from the ground up with different packages. The standard Ubuntu desktop edition is just that, for desktops/laptops.

---

### Post by SunnyRabbiera on 2010-07-28
Well there are ways around high ram usage, like using LXDE and not using firefox as the main browser.

---

### Post by Joe Ker1086 on 2010-07-28
You could always do a minimal install of ubuntu, and maybe using xfce ore ldxe (as mentioned above). You would notice a pretty big difference. Check it out here --> [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by Nick_Jinn on 2010-07-28
I have 4gb of ram. I prefer a more full featured OS to a lighter one on THIS computer. If my PC cant handle it, I would use something different.

I think Ubuntu should be efficient, but shouldnt sacrifice looks or functionality for being lightweight. They have Lubuntu and Xubuntu for that.

---

### Post by justinsn95 on 2010-07-28
> **NightwishFan said:**
> Really it depends how low you need it. You can install a core Ubuntu system and build it from the ground up with different packages. The standard Ubuntu desktop edition is just that, for desktops/laptops.

> **SunnyRabbiera said:**
> Well there are ways around high ram usage, like using LXDE and not using firefox as the main browser.

Well then at this time, I'd like draw upon yall's far greater experience. 

I'll list off the things that I want the linux OS to be able to do, and perhaps yall can make a ballpark guess of how much RAM it would be using. If I built the OS from the ground up, like a lego set. Only including what I *had* to have. Such an OS would likely be much smaller than ubuntu 10.04. 

This hypothetical linux OS for the tablet would need to have:

1. Touchscreen support. Wouldn't be much good without it. 

2. Wifi support. I guess this would mean some kind of driver for the wifi card. 

3. FireFox. And everything that goes with it, like Flash and java. 

4. A basic desktop environment that I could use to build on. 

5. And here is the clincher... 3G support. The hardware will have it, but can linux supply the driver? Gotta be able to connect anywhere or I really don't need the tablet. 

6. Probly already included in the kernal, but all your basics like USB support. Gotta be able to plug in devices. 

7. A little music player like rhythmbox. Just so I can listen to a few mp3's here and there. 

8. Bluetooth support if it isn't too much of a hog. If it is, I'll just use the USB port instead. 

9.The software center and the synaptic package manager. Just in case I want to add some more stuff, but I'll likely be trying to keep it small. 

10. The updates center. I need to be able to update all the stuff that I already have. 

Ok. That is the list. To reiterate, what is the smallest linux I can use that fits that bill? The less activity and system resources the OS uses, the longer my battery lives. Windows failed, I am hoping linux can succeed.

---

### Post by Joe Ker1086 on 2010-07-28
You could also try Crunch Bang linux. Based on ubuntu but uses openbox window manager and is **preconfigured **(I tried using openbox once but has a lot of trouble setting it up). I have been meaning to try crunchbang but just havent had the time :( but a couple friends swear by it.

EDIT:

Just saw your last post, not sure if crunchbang has touch screen and 3g support. Is the 3g built in or is it a 3g card? Also, have you looked into Arch linux. Dont know how experienced you are but you can build a pretty minimal system and configure it exatcly how you want it and even run a more full featured desktop environment if you so desire...KDE uses more resources BUT with KDE 4 it became modular so you can install ONLY the parts that you want

---

### Post by Legendary_Bibo on 2010-07-28
Mine takes about 600-750mb of RAM with just Firefox open, and empathy constantly going. I also use Compiz, and Cairo-dock.

Oh and I wouldn't trust the system monitor that thing isn't very accurate. use htop for the actual results.

---

### Post by mkendall on 2010-07-29
[quote=justinsn95]Is ubuntu getting fat?[/quote]
No, it's just the dress.

---

### Post by linux18 on 2010-07-29
I think I win, 370MB with firefox, compiz, avant-window-navigator (i intentionally crased a few applets to save a few mb's):

[http://img3.imageshack.us/img3/6354/screenshotiev.png](http://img3.imageshack.us/img3/6354/screenshotiev.png)

the key is in my own distro (check sig)

---

### Post by cariboo on 2010-07-29
> **linux18 said:**
> I think I win, 370MB with firefox, compiz, avant-window-navigator (i intentionally crased a few applets to save a few mb's):

[http://img3.imageshack.us/img3/6354/screenshotiev.png](http://img3.imageshack.us/img3/6354/screenshotiev.png)

the key is in my own distro (check sig)

You could have saved even more ram usage if you used:

```
free -m
```

in a terminal, as the system-monitor can use up to 12Mb all by itself.

BTW my netbook running Maverick Unity and chromium with several tabs open comes in at just over 200Mb, and it includes most of the bells and whistles of a full desktop install. See this [post]("http://ubuntuforums.org/showpost.php?p=9650763&postcount=55").

---

### Post by Joe Ker1086 on 2010-07-29
ok, so i finally installed crunchbang linux........ currently only using 188mb. and none of my swap file. and i am running pidgin, firefox and gimp (just to see how it would run) only uses about 140mb with firefox open. oh and compositioning is enabled too

---

### Post by Stefanie on 2010-07-29
I'm at 830 MB, with firefox, thunderbird, gnome-do/docky, rhythmbox and a java app running. 
I don't see where the problem is - unused RAM is wasted RAM.

---

### Post by handy on 2010-07-29
It happens to most of us as we get older...

---

### Post by Nick_Jinn on 2010-07-29
Got to eat your ginseng.


Maybe there should be a program called ginseng that will speed up your computer by temporarily allocating most ram functions to swap....things you dont need that run in the background, so that you can have more ram dedicated to a primary task like gaming or media conversion....put the libido back in your system.

---

### Post by Frogs Hair on 2010-07-29
Memory use in W7 home premium and Ubuntu 10.04 are about the same for me . It is disk usage is that differs. W7 uses 54 gb and Ubuntu uses 3.5 gb. One of the big memory users on Ubuntu is X-Org , but I think it is because I use Nvidia drivers.

---

### Post by Old Marcus on 2010-07-29
I don't see the point in moaning that your OS won't run on 4 bytes of RAM, so is bloated. Unless you experience slowdowns, let the RAM do its job i.e. be used. If you are so fanatical about keeping RAM usage low, then sell the RAM that isn't being used and make a little money in the process. Or just use it like everyone else does.

---

### Post by endotherm on 2010-07-29
no

---

### Post by keithpeter on 2010-07-29
Hello All

Both of these computers do everything I need them to. I've only ever slowed the desktop down seriously once - using imagemagic to batch convert and rotate a lot of images. I tend to just work away anyway... #! Statler is ace on my netbook...

Asus desktop, fresh boot, includes dropbox and Ubuntu One

```
keith@pundit:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           874        548        326          0         59        211
-/+ buffers/cache:        277        597
Swap:         1951          0       1951
```

Asus desktop with Chrome running a couple of tabs

```
keith@pundit:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           874        719        155          0         64        304
-/+ buffers/cache:        350        524
Swap:         1951          0       1951
```

Thinkpad T42 with minimal iso + gnome-core (see sig, Lighter Gnome Install) fresh boot including dropbox

```
keith@thinkpad:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1001        248        753          0         15        112
-/+ buffers/cache:        120        881
Swap:          839          0        839

```

Thinkpad with Firefox running bbc news

```
keith@thinkpad:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1001        331        670          0         16        151
-/+ buffers/cache:        163        838
Swap:          839          0        839
```

---

### Post by Legendary_Bibo on 2010-07-29
The only time I've gotten a slowdown is with GIMP, but my GIMP is a bit heavier then most people's (GIMP loads all your brushes, and gradients into RAM, and I have about a gig of brushes). Also some Script-fu scripts can be heavy when it's working on several layers. Other than that as long as Ubuntu doesn't slow down for me then it can be as fat as it wants to.

---

### Post by justinsn95 on 2010-07-30
I can't believe no one has suggested Damn Small Linux.

---

### Post by RiceMonster on 2010-07-30
OP: You have 4GB of ram and you're still have 3+GB left. Why are you so concerned?

---

### Post by TheStroj on 2010-07-30
Ubuntu?...Fat??

I'm using Gnome which is more bloated than some other desktop environments and my results are still very nice:

---

### Post by justinsn95 on 2010-07-30
When windows XP came out I ran it on 128Mb of RAM. Just throwing that out there.

---

### Post by linux18 on 2010-07-30
but windows xp always uses at least 80MB of swap just starting up.

Ok EVERYONE use this logic,
FORGET ABOUT RAM USAGE, IF THE COMPUTER RUNS FASTER THAN WINDOWS, WHATS THE POINT OF COMPLAINING? IF ITS WORKING DON'T SCREW WITH IT! I have my own command line distro (see sig) and total hard disk usage is 800 MB buit im using 700MB of ram, problem? NO i have half of the hard disk cached and thats a good thing if you need speed. stop worring about ram.

---

### Post by WRDN on 2010-07-30
> **justinsn95 said:**
> When windows XP came out I ran it on 128Mb of RAM. Just throwing that out there.

Without antivirus etc, XP runs in that for a base install, but its relatively easy to get it running in around 60Mb.

---

### Post by murderslastcrow on 2010-07-30
If you use Xfce or lighter (e17, for example, which is much better looking than Windows XP), you can have lower than XP's minimum requirements when it was released NINE YEARS AGO.

Also, if you get the right combination, you can run Linux faster than Windows 98, which is over a decade old.

So yeah, considering the fact that the cheapest computers you can buy on eBay could run KDE 4 comfortably, I don't think Ubuntu's getting fat. There are plenty of options, and KDE and Gnome are always optimizing their code to squeeze as much speed out of it as they can during maintenance releases.

So really, get a nice fluxbox theme and use rounded corners if you're concerned about memory use but still want a slick look. Unless you plan on using Windows 95 or the old MacOS for everything, Linux is basically the best  you've got to work with. I mean, there's only so much functionality you can squeeze out of these megabtyes of RAM, and our community's done an amazing job.

Try Arch if you're really concerned with being lightweight with daemons and stuff.

---

### Post by Nick_Jinn on 2010-07-30
The thing with windows is this....it gets slower and slower the longer you use it. Even if you keep it clean and degragmented and use anti-virus, the way windows is built it just gets bent out of shape the longer you use it until a clean install is needed.....Windows 7 may be more stable than XP, but that is an absurdly low standard. Its not stable like linux is stable.

I am by no means a linux guru, but I know from end user experience that windows will get slower and slower and use more and more resources as time goes on, while Ubuntu will stay the same unless you pile on a lot of startup processes which is always voluntary. Ubuntu will 'keep its shape' if left alone, which is not something you can say for Windows. 

But yeah, if you are running a PC from 2001 and you were able to run Ubuntu 7.04 ok but 10.04 is a little sluggish.....thats a progression we will have to learn to deal with Its growing much much slower than the competition while giving us more in return. We are coming out ahead.

But if you cant run it, try E17 or XFCE. 


How is Mints implementation of XFCE vs Xubuntu?

---

### Post by Grifulkin on 2010-07-30
> **Nick_Jinn said:**
> The thing with windows is this....it gets slower and slower the longer you use it. Even if you keep it clean and degragmented and use anti-virus, the way windows is built it just gets bent out of shape the longer you use it until a clean install is needed.....Windows 7 may be more stable than XP, but that is an absurdly low standard. Its not stable like linux is stable.

I am by no means a linux guru, but I know from end user experience that windows will get slower and slower and use more and more resources as time goes on, while Ubuntu will stay the same unless you pile on a lot of startup processes which is always voluntary. Ubuntu will 'keep its shape' if left alone, which is not something you can say for Windows. 

But yeah, if you are running a PC from 2001 and you were able to run Ubuntu 7.04 ok but 10.04 is a little sluggish.....thats a progression we will have to learn to deal with Its growing much much slower than the competition while giving us more in return. We are coming out ahead.

But if you cant run it, try E17 or XFCE. 


How is Mints implementation of XFCE vs Xubuntu?


What, if you aren't doing stupid stuff you will never have to reinstall windows, I have never had to do it, even with XP.  My install never got slower, never became sluggish.  And people saying that Windows uses 1.5 GB or RAM at start up that is because it loads all your favorite apps into RAM when it starts that way you don't have to wait the first time you try to use it after turning it on.

Also Xubuntu is a **** poor implementation of XFCE, my XFCE on Slackware64 13.1 uses 150 mb or RAM after start up, I would love to see Xubuntu do that.

One more thing you can also manage your start up apps/services in Windows as well, msconfig controls all your start up processes.

---

### Post by Joe Ker1086 on 2010-07-30
Why would someone suggest damn small linux to you when your system has 4 gigs of ram.....that would just be a waste....

---

### Post by K.Mandla on 2010-07-30
Ubuntu is very fat.

[http://kmandla.wordpress.com/2010/03/14/thats-not-bloated-thats-clinically-obese/](http://kmandla.wordpress.com/2010/03/14/thats-not-bloated-thats-clinically-obese/)

It has gotten fatter over time.

[http://kmandla.wordpress.com/2010/05/03/its-the-fat-that-makes-you-look-fat/](http://kmandla.wordpress.com/2010/05/03/its-the-fat-that-makes-you-look-fat/)

It is possible to use a Gnome desktop without all the fat.

[http://kmandla.wordpress.com/2010/03/19/a-clarification-gnome-on-arch/](http://kmandla.wordpress.com/2010/03/19/a-clarification-gnome-on-arch/)

If you don't like the fat, learn to build your own lighter Gnome system. 

[http://kmandla.wordpress.com/2010/03/22/build-a-lighter-gnome-in-ubuntu/](http://kmandla.wordpress.com/2010/03/22/build-a-lighter-gnome-in-ubuntu/)

Or better, avoid Gnome altogether.

[http://kmandla.wordpress.com/2010/03/21/build-a-lightweight-graphical-system-in-ubuntu/](http://kmandla.wordpress.com/2010/03/21/build-a-lightweight-graphical-system-in-ubuntu/)

This is the principle that separates Linux from Windows. With Linux, you have the freedom to make your system faster. With Windows ... you have to buy a new computer. ;)

---

### Post by Nick_Jinn on 2010-07-31
> **Grifulkin said:**
> What, if you aren't doing stupid stuff you will never have to reinstall windows

I disagree. Even basic installing and removing programs requires matenaince like fragmenting and registry cleaning to stay fit. After a while its just going to be a mess, and while you dont NEED to reinstall, it would run faster if you did. 


> **Grifulkin said:**
> I have never had to do it, even with XP.

Possible, but that is still an argument from personal incredulity. Anyone can claim anything in a debate like this. However, there is documentation supporting the claim that windows systems tend to slow down with typical use.

> **Grifulkin said:**
> Also Xubuntu is a **** poor implementation of XFCE, my XFCE on Slackware64 13.1 uses 150 mb or RAM after start up, I would love to see Xubuntu do that.

Slackware sounds difficult to use if you are not an expert, but easy to develop for....probably a good hackers OS if its designed for ease of development rather than ease on the end user side. 

I wouldnt think that using more system resources would mean that its a poor distro. I think bugs and crashes would be more indicative than that. I would be willing to sacrifice a little more ram for a little more polish. However, I hear its still buggy.

---

### Post by Spice Weasel on 2010-07-31
Join the dark side - switch to Debian.

---

### Post by NightwishFan on 2010-07-31
I like Xubuntu better than Fedora XFCE Remix, though if you really want a lightweight system, start from scratch and add what you need. At least you CAN do that. :)

As for Ubuntu being fat, why don't we work on finding the fat and getting out the trimmers, and putting our data up to Canonical for review?

---

### Post by CuXe on 2010-07-31
I dunno what u guys have got going on but my ubuntu installation with compiz enabled is currently using 174 mb to run.

In the second screenshot I am running the SMPlayer and Chromium with 3 tabs, one of them being videos from SouthparkStudios ... and still sitting at 346.8Mib of used RAM ;)

---

### Post by NightwishFan on 2010-07-31
On a similar note, here is Ubuntu 10.04 on my laptop running a virtual machine of maverick which is doing updates, and installing The Elder Scrolls: Oblivion (which probably will not run..) :)

Try installing a CLI Ubuntu in Virtualbox using the Alternate installer and then install Xorg and fluxbox, I bet you can get it running in 64mb of ram. As for the default install, I do find it sluggish at times, but I am not sure it has to do with ram. I have been playing with the IDLE priority for ionice, and it seems to work wonders.

---

### Post by linux18 on 2010-07-31
yay TES:Oblivion, tell me if you get it working, Ive been wanting to play it for a while, but was unsure about it's wine compatibility

---

### Post by TNT1 on 2010-07-31
Dunno... I am... Gotta cut down on the beer...

---

### Post by Nick_Jinn on 2010-08-01
> **linux18 said:**
> yay TES:Oblivion, tell me if you get it working, Ive been wanting to play it for a while, but was unsure about it's wine compatibility

I got it working in Karmic but Ive had trouble with Lucid.

---

### Post by justinsn95 on 2010-08-01
> **Zorgoth said:**
> My very flashy Ubuntu desktop with compiz (and like 30 key bindings), cairo-dock, firefox, skype, nautilus, and emacs all going uses 600-900 MB of ram.  That is a lot less than I have ever seen Windows 7 do.  Maybe if you bought a boxed copy for $200 or spent a week cleaning out all the bloatware.

When I was using 1GB of RAM and a USB stick based installation and was going for efficiency I only use 250 MB of ram.

I'm not trying to be argumentative, but I find this to be just plain false. I know for a *fact* I can keep windows Xp, Vista, and 7 in tip top shape over a span of... I'll say 10 years. Well beyond their usefulness. I won't argue that you shouldn't have to do it, cause you're right you shouldn't. But I know the OS doesn't just "degrade" down so much that it can't be polished back up to brand new quality, without a reinstall. 

> **WRDN said:**
> Without antivirus etc, XP runs in that for a base install, but its relatively easy to get it running in around 60Mb.

I haven't whittled XP down as low is it'll go yet, but after seeing this post I might try. If this is in fact true, I hate to say it but windows XP might be the OS I need to go with on my tablet. It does have its advantages, being part of the 800lb gorilla. And if it can be made that light, I'd do well to make use of those advantages. Although, with all updates installed and SP3, I'm a little skeptical that it can be made to run on 60Mb of RAM. Although I don't need to have my antivirus running constantly, cause I know how to keep myself out of harm's way. Not to toot my own horn or anything, but I dare say I've gotten pretty good at it over the years. 

> **linux18 said:**
> but windows xp always uses at least 80MB of swap just starting up.

Ok EVERYONE use this logic,
FORGET ABOUT RAM USAGE, IF THE COMPUTER RUNS FASTER THAN WINDOWS, WHATS THE POINT OF COMPLAINING? IF ITS WORKING DON'T SCREW WITH IT! I have my own command line distro (see sig) and total hard disk usage is 800 MB buit im using 700MB of ram, problem? NO i have half of the hard disk cached and thats a good thing if you need speed. stop worring about ram.

To avoid all the posts in this thread asking this question or commenting on this, I guess I should have said that all of this is for battery life purposes. And as we all know, the less RAM usage you have at any given time, the longer your battery life will be. A computer that is using 1.5Gb of its RAM is going to be using more power than when that same computer is only using 300Mb of its RAM. 

> **murderslastcrow said:**
> If you use Xfce or lighter (e17, for example, which is much better looking than Windows XP), you can have lower than XP's minimum requirements when it was released NINE YEARS AGO.

Try Arch if you're really concerned with being lightweight with daemons and stuff.

Could you please elaborate a little on what XFCE is, or e17? I am such a noob that I don't even know what a daemon is. Please forgive my noob ignorance. 


> **K.Mandla said:**
> 
This is the principle that separates Linux from Windows. With Linux, you have the freedom to make your system faster. With Windows ... you have to buy a new computer. ;)

Agreed. But to all the guys around here saying that their W7 or Vista is running 1Gb or 1.5Gb or RAM at idle, you need to optimize your OS. If you care to, anyway. I have the GF's vista install running at 605Mb RAM usage at idle, and my W7 install running at 650MB. (mine is more cause I have all manner of gadgets going at startup. It would be less than the vista otherwise.) Now I'm not a windows fanboy or anything, I kept an open mind and I have decided that I actually like linux a lot better. I am however, an accuracy fanboy and I have noticed a lot of windows hate placed in areas where its unjustified. Some areas, yeah its justified. Other areas, not so much. 


> **Spice Weasel said:**
> Join the dark side - switch to Debian.

I thought that Ubuntu had something to do with Debian cause you use .deb packages?

---

### Post by Nick_Jinn on 2010-08-01
Xp without the service packs is going to be really vulnerable. It will get attacked by viruses. It also might not be as useful or functional as you would expect it to be.


You could try a light weight version of Linux....something XFCE, LXDE or maybe puppy linux.





You could also try installing Android.

---

### Post by s3a on 2010-08-01
I think this is mostly a GNOME issue rather than a Ubuntu one. Does anyone have any way to take a Ubuntu installation and slim it down? (because my mother's computer has 384MB of RAM and runs very slowly once it reaches swap and it reaches it easily) (as opposed to starting from scratch and adding things)

Are people comparing 64 bit RAM usage to 32 bit? I think that could bias results. Also, I'm curious as to whether the "weight gain" is due to bad coding or extra features and programs installed in the background that many of us are not aware of.

---

### Post by linux18 on 2010-08-01
> **s3a said:**
> I think this is mostly a GNOME issue rather than a Ubuntu one. Does anyone have any way to take a Ubuntu installation and slim it down? (because my mother's computer has 384MB of RAM and runs very slowly once it reaches swap and it reaches it easily) (as opposed to starting from scratch and adding things)

Are people comparing 64 bit RAM usage to 32 bit? I think that could bias results. Also, I'm curious as to whether the "weight gain" is due to bad coding or extra features and programs installed in the background that many of us are not aware of.
If you want it slimmed down check my sig, I've got my own ubuntu based distro. just install it plug in an ethernet cable and install lxde. ram usage will be about 180MB, message me if you need any help.

---

### Post by Legendary_Bibo on 2010-08-01
> **justinsn95 said:**
> I'm not trying to be argumentative, but I find this to be just plain false. I know for a *fact* I can keep windows Xp, Vista, and 7 in tip top shape over a span of... I'll say 10 years. Well beyond their usefulness. I won't argue that you shouldn't have to do it, cause you're right you shouldn't. But I know the OS doesn't just "degrade" down so much that it can't be polished back up to brand new quality, without a reinstall. 

*[COLOR=Red]It's because parts of the registry becomes corrupted which causes slowdowns and issues. Also because of Windows' choice of filesystem (I think) you also have to defragment your hard drive to fix things like sectors of your hard drive not fully recognizing parts that no longer have data written to it.[/COLOR]* 

I haven't whittled XP down as low is it'll go yet, but after seeing this post I might try. If this is in fact true, I hate to say it but windows XP might be the OS I need to go with on my tablet. It does have its advantages, being part of the 800lb gorilla. And if it can be made that light, I'd do well to make use of those advantages. Although, with all updates installed and SP3, I'm a little skeptical that it can be made to run on 60Mb of RAM. Although I don't need to have my antivirus running constantly, cause I know how to keep myself out of harm's way. Not to toot my own horn or anything, but I dare say I've gotten pretty good at it over the years. 

[COLOR=Red]*That's great then. Most people who use Windows don't have that knowledge, and refuse to learn how to properly keep their system secure, which in turn leads to a lot of frustrations.*[/COLOR]

To avoid all the posts in this thread asking this question or commenting on this, I guess I should have said that all of this is for battery life purposes. And as we all know, the less RAM usage you have at any given time, the longer your battery life will be. A computer that is using 1.5Gb of its RAM is going to be using more power than when that same computer is only using 300Mb of its RAM. 

[COLOR=Red]*Yes. Also if it doesn't have to use the CPU a lot.*[/COLOR]

Could you please elaborate a little on what XFCE is, or e17? I am such a noob that I don't even know what a daemon is. Please forgive my noob ignorance. 

*[COLOR=Red]XFCE, e17, GNOME, KDE, Openbox, Blackbox, Icebox, Roxo (correct spelling?), etc. are all desktop environments. They're kind of an abstract idea. Think of it this way, an OS lets your applications tie themselves to your hardware. Well a desktop environment is what an application ties itself to so it can be tied to the OS to be tied to the hardware. This is at least how I understand it.[/COLOR]*


Agreed. But to all the guys around here saying that their W7 or Vista is running 1Gb or 1.5Gb or RAM at idle, you need to optimize your OS. If you care to, anyway. I have the GF's vista install running at 605Mb RAM usage at idle, and my W7 install running at 650MB. (mine is more cause I have all manner of gadgets going at startup. It would be less than the vista otherwise.) Now I'm not a windows fanboy or anything, I kept an open mind and I have decided that I actually like linux a lot better. I am however, an accuracy fanboy and I have noticed a lot of windows hate placed in areas where its unjustified. Some areas, yeah its justified. Other areas, not so much. 

*[COLOR=Red]I didn't have to optimize my Ubuntu OS and it runs at 350mb of RAM on a fresh install. Although now it's at 650mb idle with Compiz, Cairo-Dock, and Gnomenu[/COLOR]*. [COLOR=Red]*1.2GB with empathy running in the background, Firefox running, Evolution open, and Rythmbox going using Pulse Audio on top of the previous stuff. I could strip it down, but I have 4GB of RAM and I don't really open up a lot of programs at a time. GIMP is my heaviest, it takes about 800mb of RAM because it's pretty loaded for me.*[/COLOR]


I thought that Ubuntu had something to do with Debian cause you use .deb packages?

[COLOR=Red]*Ubuntu is based off of Debian. It's a fork, which means they took the Debian OS and changed some things, most of which were to make it more user friendly for the end user.*[/COLOR]


I addressed your points individually. :D

---

### Post by linux18 on 2010-08-01
> **Legendary_Bibo said:**
> I addressed your points individually. :D
sort of what you said, but I wanted to go farther

1) how do you know you you can keep an os 10 years? xp came out 9 years  ago and every service pack made major changes to the os, effectively  resetting your clock.

2) with ubuntu, you dont have to keep such constant maintenace on the  computer to keep it working, it like a post in another forum i read  written by a microsoft fanboy: "NTFS is the best filesystem ever, I  defrag it 3 times a week and its always fast" --this guy was posting in a  forum for server maintenance and got many "well when you grow up and  get a server, have fun trying to defrag it 3 times a week" posts. the  point is when we choose linux, we are doing it because we don't want to  do constant maintenance. For many of us computer maintenance is our job,  we don't want to come home to it.

3) less ram = less battery drain, hardly. ram sips a watt or two at the  most. you'll save as much turning off sound, wifi, and bluetooth or you  could turn down your brightness and save loads. Even better, you could  have turned off your computer completely and not posted, saving all of  your battery power and some of mine.

4) noob ignorance? so you are here at the ubuntu forums asking how you  can cut down your ram usage and after all these posts you don't like the  answer and decide to say how much better xp is. that is the definition  of noob, but i think you meant newb in either case you acted like a  noob.

5) " Now I'm not a windows fanboy or anything" if you have to say that,  then you are a fanboy. Anyway, your bragging about w7 only taking 650MB?  my distro (see sig) takes 60MB and 74 with fluxbox and its 2 years  newer than w7.

6) JFGI seriously its not that hard to use wikipedia or google and it  would have required less time and typing than putting it in your post.

also here are some random facts:

 the windows xp release matrix:
 [http://upload.wikimedia.org/wikipedia/commons/thumb/b/b0/XP-Editions.svg/2000px-XP-Editions.svg.png](http://upload.wikimedia.org/wikipedia/commons/thumb/b/b0/XP-Editions.svg/2000px-XP-Editions.svg.png)

and the ubuntu release matrix:
desktop and server in [IA-32]("http://en.wikipedia.org/wiki/IA-32"), [x86-64]("http://en.wikipedia.org/wiki/X86-64"), lpia, [SPARC]("http://en.wikipedia.org/wiki/SPARC"), [PowerPC]("http://en.wikipedia.org/wiki/PowerPC"), [ARM]("http://en.wikipedia.org/wiki/ARM_architecture"), [IA-64]("http://en.wikipedia.org/wiki/IA-64") 

windows vista starter has a physical memory limit of 1GB

linux with pae kernel has a physical memory limit of up to 64GB on 32-bit hardware

windows 7 starter has a physical memory limit of 2 GB in BOTH 32-bit AND  64-bit. with a minimum requirement of 2GB for the 64-bit editions

ubuntu, has a minimun requirement of 64MB of ram for the 64-bit edition   

windows = simple?  I laugh at that.

---

### Post by keithpeter on 2010-08-02
> **linux18 said:**
> 
3) less ram = less battery drain, hardly. ram sips a watt or two at the  most. you'll save as much turning off sound, wifi, and bluetooth or you  could turn down your brightness and save loads. 

I thought so, being as this recycled thinkpad uses about 12% of the battery being suspended to ram for 12 hours. 

What I'm interested in is using MORE ram to cut down hard drive activity on battery. The screen brightness only seems to change the power consumption by three watts from dim to bright.

---

### Post by justinsn95 on 2010-08-02
[COLOR="White"]edited post[/COLOR]

---

### Post by linux18 on 2010-08-02
sorry, I was sort of venting that night and managed to alienate a few forum members. I'm going to reread the ubuntu philosophy and take a few days off from the forums.

---

### Post by darkstarbyte on 2010-08-02
I think ubuntu is starting to get fat from when I first used it from karmic to lucid ubuntu is getting pretty

big its a 668 meg download correct me if I wrong but it is increasing in hard drive space, but the 

spinoffs are a little smaller. ps. If anyone knows of a ubuntu spin off that uses window maker let me 

know. please

---

### Post by darkstarbyte on 2010-08-02
> **s3a said:**
> I think this is mostly a GNOME issue rather than a Ubuntu one. Does anyone have any way to take a Ubuntu installation and slim it down? (because my mother's computer has 384MB of RAM and runs very slowly once it reaches swap and it reaches it easily) (as opposed to starting from scratch and adding things)

Are people comparing 64 bit RAM usage to 32 bit? I think that could bias results. Also, I'm curious as to whether the "weight gain" is due to bad coding or extra features and programs installed in the background that many of us are not aware of.

Well I might know the solution use ubuntu spin off Lubuntu which uses lxde window manager but to be sure i have a pentium three laptop that has about 128 megs of ram but it might take a while to download burn and install on that old machine.

You would be right about the 64 bit thing to 32 bit because from my understanding is 64 bit handles more information at once than a 32 bit which breaks it up into smaller peaces correct me if am wrong not just  the spelling or the grammar.

---

### Post by NightwishFan on 2010-08-02
Ram usage is better when more is used. Laptop or not.

---

### Post by justinsn95 on 2010-08-08
> **linux18 said:**
> sorry, I was sort of venting that night and managed to alienate a few forum members. I'm going to reread the ubuntu philosophy and take a few days off from the forums.

Well, now I feel like a #$@%. Lets just forget the whole argument.

---

### Post by linux18 on 2010-08-08
> **justinsn95 said:**
> Well, now I feel like a #$@%. Lets just forget the whole argument.

Thanks for accepting my apology, we all should remember that the only enemy in the ubuntu forums is misunderstanding and maybe slow servers.

---

### Post by phredbull on 2010-11-25
Related question:
Is the Linux kernel getting fat?

---

### Post by Spice Weasel on 2010-11-27
> **phredbull said:**
> Related question:
Is the Linux kernel getting fat?

Yes. Well, Linus seems to think so and I agree with him. Old features (such as Windows 98- filesystem support) need to be forked to a separate legacy kernel and removed from the main version.

---

