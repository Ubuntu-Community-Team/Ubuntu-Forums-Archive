---
title: "emulation on ubuntu"
date: 2014-10-30
forum: New to Ubuntu
---

### Post by martins2 on 2014-10-30
Hello!
Im thinking about using ubuntu as my main operating system and have some questions regarding emulating windows apps

Whats quality of emulation possibilitys on emulating specific windows apps... For example newest games, bluestacks apps, and so on... Can I fully depend on ubuntu as only os or I will have to use dualboot?

---

### Post by JazzPotato on 2014-10-30
It depends on the app you are looking to use.
For alot of windows applications, there are open-source, ubuntu-compatible replacements, (gimp -> photoshop, pitivi -> sony vegas, etc).
But, for some apps that you can't live without, there are a few options.

There is a program called **wine **that acts as a layer between the windows program and the linux os and makes the windows program think it's on windows (it's not an emulator, by the way). This doesn't work for all applications, and the ones it does work for often have bugs, however older versions or less complex windows programs usually work fine and wine is always being updated. You can find which windows programs work well here [https://appdb.winehq.org/](https://appdb.winehq.org/)
Wine is not recommended for games as you take serious performance hits and alot of games are large and complex, and therefore don't work well under wine. However, some games have been proven to work semi-well

Your other option is to run a windows virtual machine in virtualbox, as I do. Depending on how much ram your machine has, this can have mixed results. With virtualbox you essentially run a virtual instance of windows over the top of ubuntu as a "guest" machine, (called a virtual machine). I use a virtual machine for testing programs I write in a windows environment and the occasional photoshop job, because my machine has 6 gigabytes of ram and can handle two operating systems running at once. Again, this is not recommended for games because of rendering issues between the vm and the host os, but I think that the guys who work on virtualbox are working on getting a gpu passthrough working like some vmware software uses, though I may be wrong. You also take performance hits because the virtual machine does not operate on your hardware with 100% efficiency. The guys over at the "virtualisation" sub-forum can help you out more.

The last option is to dual-boot, in which you get the full performance of both operating systems, but you have to share the hard drive. This is what most people do for gaming, because windows is running natively and you get the full performance of the operating system. The only problem is that you have to split the hard drive and figure out how much space you want both operating systems to use. They cannot share. It is recommended that you install windows first, because the ubuntu installer is much smarter figuring out what it should do with the hard drive partitions and you will find it easier to install both operating systems side by side, though things are possible the other way, just a little harder. 

I hope I've given you a good run-down of your options martins2! Just remember, everything windows can do ubuntu can do better, so where as now you may be struggling getting used to using new software, once you learn more about linux and ubuntu you will be able to bend it to your will by writing your own programs, and scripts, and by using the command line, and you will be far more productive and flexible than you have ever been using any windows program! :-)

Good luck!

---

### Post by grahammechanical on 2014-10-30
I fully depend on Ubuntu as the only OS. But then I do not need or desire to run Windows applications. Well, there is one Windows app. It is not a game and wine runs it very well.

You may also find that the Windows app store will not let you download apps because it is not detecting a version of Windows.  If you have already paid for Windows why not keep and dual boot with Ubuntu. You will be surprised at the number of people who post here saying that they deleted Windows and can they now have it back, please? Without install discs once it is gone, it is gone. 

Regards.

---

### Post by martins2 on 2014-10-30
Thank you for responses.
I know about virtual machines and that they do bad about performance.

Im talking more about applications you cant find alternative. Like newest games...
I dont rly wanna do the dualboot.

I have knowlage about it and what I wanna do is get linux on my laptop - it have limited hdd capability. Aswell I beleave its best to have 1os at one physical hdd. So dualboot is bad idea for me.

---

### Post by pfeiffep on 2014-10-30
> **martins2 said:**
> Thank you for responses.
I know about virtual machines and that they do bad about performance.

Im talking more about applications you cant find alternative. Like newest games...
I dont rly wanna do the dualboot.

I have knowlage about it and what I wanna do is get linux on my laptop - it have limited hdd capability. Aswell I beleave its best to have 1os at one physical hdd. So dualboot is bad idea for me.Obviously the choice is totally yours. 
I have 2 machines with dual boot (Windows 7 and Ubuntu 14) and I've never experienced and issue because of multiple OSes on the same machine. 
IMO no dual boot and latest games restricts your options to staying with Windows.

---

### Post by Mark Phelps on 2014-10-30
> Im talking more about applications you cant find alternative. Like newest games...
I dont rly wanna do the dualboot.

Then, you're backing yourself into a corner.  Windows gaming, in general, works poorly on Linux.  You need to check the WineHQ link you were provided to see the ratings for the games you want to run.  Anything rated lower than Gold is going to be a waste of your time.

Also, it's fairly common for Linux video drivers to lag behind Windows video drivers -- and Games tend to be the most demanding of those drivers.

Seriously, if you're going to rely heavily on using Linux for Windows games, you're setting yourself up for a disappointing experience.

---

### Post by Impavidus on 2014-10-30
I've got one computer that has dual booted Windows and Ubuntu for the past 8 years from a single 200GB hard drive without any problems. The drive is slowly filling up now, but a major clean-up should fix that. How big is your hard drive? I don't really know how much Windows wants nowadays, but most laptop drives should be big enough. If you want the latest Windows games, dual booting is the only option.

---

### Post by whitesmith on 2014-10-30
+1 to Mark Phelps. Gaming is not for emulated OSes, including those that use a software virtualization layer, like Wine. The sole exception is middleware--Facebook games, for example--that run on APIs exposed by your browser. I caution you in no uncertain terms to avoid dual boot systems. They are harder to set up, for one thing. But the user is the major problem. Say you know more about Windows than *nix, a common situation. So, instead of facing some impediment-of-the-day as a learning experience, you just boot Windows and do your thing there. This will happen time and time again, until, 6 months down the road, you won't even be thinking of this box as a dual boot machine. Thanks to the effects of human nature and time, it will have transformed itself into a Windows machine. Read the webpage included first on my sig line. Ask yourself, "Do I genuinely enjoy solving old problems in new ways?" If so, and if learning doesn't intimidate you--by all means go the Linux route. Wild horses couldn't drag me back to the blandness and bloat of Windows. But I know many lured by Redmond's siren song. That old shoe has proven too comfortable for many!

---

