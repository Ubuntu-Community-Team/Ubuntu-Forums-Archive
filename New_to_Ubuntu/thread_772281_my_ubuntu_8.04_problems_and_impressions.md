---
title: "my ubuntu 8.04 problems and impressions"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by bitchain on 2008-04-28
Hi All,

First time Ubuntu user, on the whole I like the experience though I can't shake the feeling it needs still more polish and performance (graphics in particular seem more sluggish than Vista), but from last time I tried Linux with Mandrake 8 it's a *vast* improvement and I'll keep using it for now in dual boot and see how it goes.

Do have a couple of niggling issues:

- When I close my laptop lid my laptop fans remain on. They don't in Vista. I changed my Power Management settings from Blank Screen to Hibernate in both AC/on and battery, but the fans just don't shut down, and in fact, when I reopen the lid now, I cannot get back into Ubuntu at all! not with mouse movement, power button nor key pressing. Seems a little more than broken. In vista it all works as expected so not a laptop issue I think (brand new MSI GX-700 Extreme laptop).

- I can't remember the exact message but when I boot into Ubuntu it stops on a black screen (before the Ubuntu logo shows) with a text msg at the top. To paraphrase it says something to the effect "can't find linux on disk 0" but after about 1 minute it starts up. Not really a problem but seems like an unnecessary long wait. I installed with Wubi onto my D: partition (I have 2 partitions c: and d:). I figured it could not find it on c: but takes an age to find it on D: I can dig out the exact message if it helps more.

- Brightness is uncessarily dark by default if you ask me. I have to manually turn it up each boot.

- I still just don't buy into the complexity of the linux file structure, all these folders like var, usr, lib, etc and the way an app throws files into all these places. But that's not an Ubuntu issue, but it's damn confusing :) Program Files in Windows is just way better, even though a couple of DLL files may go to Windows/System. And I don't like that compiling and making source often results in *not* being told what the hell it's done with the result (like I was builing a JAR the other day and it didn't tell me where it put it). I eventually found it in /share/java with the find command.

Overall, am liking Ubuntu, just can't see a compelling reason to get away from Windows though. For all those who don't like MS for whatever reason, it's still a more comprehesively usable windowing OS than gnome.

Cheers.

---

### Post by Cypher on 2008-04-28
Let me preface my response with Linux != Windows. :)

> **bitchain said:**
> Hi All,

First time Ubuntu user, on the whole I like the experience though I can't shake the feeling it needs still more polish and performance (graphics in particular seem more sluggish than Vista), but from last time I tried Linux with Mandrake 8 it's a *vast* improvement and I'll keep using it for now in dual boot and see how it goes.

Do have a couple of niggling issues:

- When I close my laptop lid my laptop fans remain on. They don't in Vista. I changed my Power Management settings from Blank Screen to Hibernate in both AC/on and battery, but the fans just don't shut down, and in fact, when I reopen the lid now, I cannot get back into Ubuntu at all! not with mouse movement, power button nor key pressing. Seems a little more than broken. In vista it all works as expected so not a laptop issue I think (brand new MSI GX-700 Extreme laptop).

Laptop support is something that's a little lacking on Linux in all aspects..from hibernation, temporary suspending and other things. A lot of things work really well in Windows partly because the manufacturers work closely with MS with various functionality. That isn't the case with Linux and in time the Kernel will have good support for it..
> 
- I can't remember the exact message but when I boot into Ubuntu it stops on a black screen (before the Ubuntu logo shows) with a text msg at the top. To paraphrase it says something to the effect "can't find linux on disk 0" but after about 1 minute it starts up. Not really a problem but seems like an unnecessary long wait. I installed with Wubi onto my D: partition (I have 2 partitions c: and d:). I figured it could not find it on c: but takes an age to find it on D: I can dig out the exact message if it helps more.

I haven't used Wubi, I primarily use Linux and have XP installed just the in the off chance I need it for something..so I have nothing helpful for this error. But I do agree, there shouldn't be a minute long wait before it logs in. Do you notice any sudden  slowness after booting up, or is this just once before login?
> 
- Brightness is uncessarily dark by default if you ask me. I have to manually turn it up each boot.

- I still just don't buy into the complexity of the linux file structure, all these folders like var, usr, lib, etc and the way an app throws files into all these places. But that's not an Ubuntu issue, but it's damn confusing :) Program Files in Windows is just way better, even though a couple of DLL files may go to Windows/System. And I don't like that compiling and making source often results in *not* being told what the hell it's done with the result (like I was builing a JAR the other day and it didn't tell me where it put it). I eventually found it in /share/java with the find command.

If you think all the files in Windows end up primarily in "Program Files", you are mistaken. :) With Ubuntu's DPKG and DEBs you can easily see which directory contain all the files from a package and when you remove it, it's truly gone.

Now as far as the directory structure, once you start working with it you'll find that it actually makes a lot of sense. Besides, this is more of a Unix thing than a Linux thing..

With the majority of applications that are needed by the regular Ubuntu user, there are pre-compiled DEBs available in a repo that can be safely installed. If you are going the route of compiling an application, there is an expectation that you'd learn a little about what's going on there while you compile the application. The amount of information being given out by the compile process is entirely dependent on the application creator. This isn't necessary a Linux distro thing.
> 

Overall, am liking Ubuntu, just can't see a compelling reason to get away from Windows though. For all those who don't like MS for whatever reason, it's still a more comprehesively usable windowing OS than gnome.

Cheers.
The saying, "To each their own" seems appropriate here. Just as you can comfortable with Windows and prefer to stay with it, there are those who find Linux suits them better..so no harm, no foul..

---

### Post by Nano Geek on 2008-04-28
Hi, welcome to Ubuntu.

> - When I close my laptop lid my laptop fans remain on. They don't in Vista. I changed my Power Management settings from Blank Screen to Hibernate in both AC/on and battery, but the fans just don't shut down, and in fact, when I reopen the lid now, I cannot get back into Ubuntu at all! not with mouse movement, power button nor key pressing. Seems a little more than broken. In vista it all works as expected so not a laptop issue I think (brand new MSI GX-700 Extreme laptop).
 
 - I can't remember the exact message but when I boot into Ubuntu it stops on a black screen (before the Ubuntu logo shows) with a text msg at the top. To paraphrase it says something to the effect "can't find linux on disk 0" but after about 1 minute it starts up. Not really a problem but seems like an unnecessary long wait. I installed with Wubi onto my D: partition (I have 2 partitions c: and d:smile:. I figured it could not find it on c: but takes an age to find it on D: I can dig out the exact message if it helps more.
 
- Brightness is uncessarily dark by default if you ask me. I have to manually turn it up each boot.That first problem affects most Linux users. 
The problem with Hibernation is the fact that every laptop maker does it differently, but since the hardware makers only provide Windows with the correct drivers, Linux users have to try to do it themselves. And it doesn't always work. 

Problem 2 could be due to the fact that Wubi is still new and it probably still has bugs that need to be worked out. 

Problem 3 probably could be fixed in a setting somewhere, but I'm not sure where.
 
 > - I still just don't buy into the complexity of the linux file structure, all these folders like var, usr, lib, etc and the way an app throws files into all these places. But that's not an Ubuntu issue, but it's damn confusing :smile: Program Files in Windows is just way better, even though a couple of DLL files may go to Windows/System. And I don't like that compiling and making source often results in *not* being told what the hell it's done with the result (like I was builing a JAR the other day and it didn't tell me where it put it). I eventually found it in /share/java with the find command.Yes it can be somewhat confusing, but don't forget, Linux doesn't have the Regestry. :)
 
 > Overall, am liking Ubuntu, just can't see a compelling reason to get away from Windows though. For all those who don't like MS for whatever reason, it's still a more comprehesively usable windowing OS than gnome.Well, that's personal opinion. I personally believe that Ubuntu is better than Windows, but every one has a different opinion.

Enjoy using Ubuntu. ;)

---

### Post by bitchain on 2008-04-28
thanks for the replies.

1) Shame about hibernation, I always use hibernate to avoid booting up and ubuntu doesn't boot too fast on my brand new laptop :(

2) Got the exact error now: "Try (hd0,0) NTFS5 : No wubildr"

3) I just use my laptop function keys but yeah if I can do it in a setting that would be good.

Cheers

---

### Post by Cypher on 2008-04-28
It's strange that Ubuntu should take that long to boot up. But perhaps that has something to do with working from within WUBI? My on Core2 desktop, Ubuntu usually only takes about 30-40 seconds before I'm staring at the login prompt.

The error in #2 seems to be related to WUBI, perhaps their support forums have a better answer for you on that.

---

### Post by Raistlinbuntu on 2008-04-28
> **bitchain said:**
> thanks for the replies.

3) I just use my laptop function keys but yeah if I can do it in a setting that would be good.

Cheers

Error number 3: maybe it reads the default that you set up in your laptop-bios. In my bios I find that setting in the power-management section.

---

### Post by Joeb454 on 2008-04-28
For the brightness check your power management settings (right click the battery icon in the top right - select preferences)

And disable "Dim screen when on battery" (it reads something like that anyway :p) As most laptops seem to dim when on battery anyway :)

Hope that helps

---

### Post by mwf on 2008-04-28
I just have a little to say here as a Linux newbie. I have tried Ubuntu in every version since 5.> xx (?) and have not been satisfied at all to use it full time. However, with 8.04, I am happily surprised at how good it really is this time.

As others have stated, Linux is not Windows just as MacOS is not Windows. Yeah, I used UNIX for quite a while in the old days so I might have a small advantage over you. But the directory structure, at least the parts the end user would ever have to deal with, are simple enough. Forget about all the other folders, they don't concern you! More than likely, as with Windows, it will be out of sight, out of mind.

I have also used Wubi to install 8.04 onto an XP desktop. It takes the same amount of time to boot up that XP does. Once booted, it runs much much faster than Vista and even a bit faster than XP. That's on a P4 with 1/2 Gig of memory compared to Vista on my dual core, 2G of memory. Something else is going on with your laptop, I don't think it's Ubuntu's fault. I must agree, however, that Linux on laptops is sometimes hit and miss.

Fancy GUIs are a personal choice. On Vista, I have Aero shut off. But there are fancy UIs for Ubuntu as well if that's what you like. Install and try a few.

Right now, my plan is to move 8.04 to my desktop full time and install the XP Pro disk (retail) to my Vista laptop. This is the very first time in Linux history I have felt it was good enough to use all the time. Give it some time, you may grow to like it. Worst case, you still have Windows which is not really as bad as so many people here claim it to be!

---

### Post by thorgal on 2008-04-28
I don't know about Gnome, I am a KDE user and you have a little app called kPowersave, where you can set your powersaving options, a bit like the windows power conf applet.

I have an old laptop (Dell Latitude D800 with an NVidia chip, GeForce FX 5200 Go IIRC) and all this powersaving stuff works great (I use a package called uswsusp which includes s2ram, s2disk and some conf files). It is supported by the power daemon powersaved, whose behavior can be configured in kpowersave (docked to your task panel so you can easily access all the power stuff).

OK, it did not work OOB but a little digging and a few attempts later, I got it to work exactly the way I want. It is also paramount that the graphics driver (the binary package from nvidia) supports all these power features. If you use the open-source nv driver (no 3D acc), you might get undesired effects ... YMMV :)

I forgot to mention, I am originally a debian user and maintain a few debian boxes at home. I don't really like how ubuntu degraded certain things compared to the original debian but for newcomers, that is understandable because debian is way too hard to handle if you know nothing about linux. This said, by all means, ubuntu is great :)
My laptop is actually a triple boot system : Ubuntu Hardy, WinXP and OSX86 10.5.2 (yeah, you can run OSX on non mac platforms ;)
I installed winXP and OSX AFTER ubuntu, no sweat here but you have to know about filesystems, partitioning, mbr and grub before any attempt at doing so :D

---

### Post by rustutzman on 2008-04-28
For the brightness issue you can put the "Brightness Applet" in one of your panels and adjust it from there. After setting the level there it stayed after reboot for me. Do the right click and add to panel.

Russ

---

### Post by jim3240 on 2008-06-03
As far as the looks goes, i use 'ubuntu studio', modified with the 'overglossed' theme, both from the GNOME-look site.... have a look around, hope you find something you like

---

