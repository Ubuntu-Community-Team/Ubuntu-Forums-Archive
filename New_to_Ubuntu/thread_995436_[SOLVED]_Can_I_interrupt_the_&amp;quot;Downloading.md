---
title: "[SOLVED] Can I interrupt the &amp;quot;Downloading Package Files&amp;quot;? and have partial install?"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by kyleryner on 2008-11-27
Hi all,

    Been a Linux user for only a few days with the new Ubuntu release and i'm loving it.

    Tested in Wubi with a 5gig space, found out i liked it, so i reinstalled in a bigger 10gig space (hope that's enough!) :)

    I have some questions on the Add/Remove programs...

    First of all, its like being in a candy store.. i sort of got carried away and clicked a bunch of programs I think i might like... turned out to to be 151 files.. ETA keeps fluctuating from 16 hours to 1 day plus. Anyway, i left the "Downloading Package Files" overnight and its been 10 hours now with still a long ways to go.

    If I CANCEL it now (126 of 151 as of this post), will it have kept/installed the first 126 files done already? Still 14 hrs to go and i may need to reboot to Vista before then. My mistake was including a bunch of 3D FPS games and Freeciv in the download.. w/c are rather large files. I hope i can just redownload them later and keep the smaller utils and apps i chose.

   Next question, is it normal for downloads to be slower in Linux than in windows? I get significantly lower speeds in the dls, even tried to dl a bittorrent file (I have yet to do a proper speedtest though.. no point doing it now with a download in progress). DOnt know if its Ubuntu or perhaps the driver for my wireless lan that's causing the slower speeds (maybe even my isp). 

   Lastly, with the "Add/Remove" functions, does that mean ALL AVAILABLE (or at least the significant) Linux software is made available there? How often are software added? Im thinking the rate im going trying to try them all, its possible to try all (well, most) of the apps in the list within a week or 2. :)  Is there any link or site to go to to get more cool linux software or is everything made available thru the "ADD/REMOVE" function?

   Dont get me wrong, Im not complaining about the speed or the number of software available.. its all FREE and lots of hard work had gone into it and i appreciate that SO much. Im just wondering, that's all :)

   Thanks for listening! :)

P.S. Sorry for the newbie questions,  I did try to search for some answers but i wasnt that successful...

---

### Post by Keen101 on 2008-11-27
You can cancel, and it will install most of what was downloaded.

The Add/Remove is kind of for beginners. It has a lot, but synaptic package manager is much better. Neither one will give you every open source program available for linux, but it will give you a lot. 

you can always install things from .run files, .deb files, and compiling from source. You can also add more repositories to your list of software sources and get even more in synaptic.

once you get confortable in the command line, you will use "sudo apt-get install" a lot. 

I don't know about the speed. Probably should not be slower. I've found 8.10 ubuntu a little slower than the 8.04 version.

---

### Post by Paqman on 2008-11-27
> **kyleryner said:**
> 
   Next question, is it normal for downloads to be slower in Linux than in windows? 

Nope. 

Make sure you're getting the packages from the best server you can. Go to System > Admin > Software Sources > Download from > Other > Select Best Server.

---

### Post by mkvnmtr on 2008-11-27
It is not a good idea to stop a download in progress. Maybe the files that are downloaded will cache on your system but you will have broken packages. Try just a few at a time. It is not normal to have slow downloads. You probably need to look for a faster repository or a closer one. I think this option is in software sources. Now while you are downloading is not the time to do it though. Go ahead and finish.
If you want to sample all the software it will probably take you several years. But heck try it you will have fun and learn a lot about Ubuntu and reinstalling.

---

### Post by kyleryner on 2008-11-27
WOW. that was FAST. 3 replies in a matter of minutes.

You guys are GREAT! and this forum is AWESOME! :-)

Thanks for the tips, guys..

Right now i think its done with most of the smaller apps and games, its currently downloading a 280mb openarena-data (i think thats for the 3d game). Hopefully IF i do cancel, it will not crash and keep the 120+ files already done..

darn speed keeps fluctuating from below 10kB/s to 28kB/s (i should be getting about 50kBs) and ETA from 1 plus hour to 8 hours.. LOL.. i could decide whether to wait or cancel now.. :-)  Ill probably wait a bit more and see (maybe after the 280mb file is done)

"if you want to sample all the software it will probably take you several years" -- yikes!!  :-)  I was referring to the list in the Add/Remove section.. seems a lot, but its a finite list.. unless they keep adding new stuff everyday (in w/c case i would imagine it to be MUCH longer than it is now, considering how many years Linux/Ubuntu has been around.

But I think Keen101 explained it with the Add/Remove being basially for beginners, and i should try Synaptic next time.

btw, i did try Kubuntu and its install method. I like the Ubuntu way better so far.. but will have to try Synaptic too (i dont think the Kubuntu method is Synaptic?)

---

### Post by slmouradian on 2008-11-27
> i dont think the Kubuntu method is Synaptic?

No, Synaptic is a package manager.

You can find it at:
System -> Administration -> Synaptic Package Manager

---

### Post by mkvnmtr on 2008-11-27
When you enable all software in add and remove you will see a lot more. I have always been like a kid in a candy store. My first couple of months I must have reinstalled 30 times. I kept adding software until something didn't work. It's fun. Good luck.

---

### Post by ByteJuggler on 2008-11-27
> **mkvnmtr said:**
> It is not a good idea to stop a download in progress. Maybe the files that are downloaded will cache on your system but you will have broken packages. Try just a few at a time. It is not normal to have slow downloads. You probably need to look for a faster repository or a closer one. I think this option is in software sources. Now while you are downloading is not the time to do it though. Go ahead and finish.
If you want to sample all the software it will probably take you several years. But heck try it you will have fun and learn a lot about Ubuntu and reinstalling.

Just a minor nit-pick/correction: Stopping downloading won't break your installed packages so feel free to stop that.  (However forcibly stopping a package instllation while half complete might rarely cause minor problems.  However such problems can be fixed fairly easily.  Personally I don't really worry too much about interrupting Synaptic or apt-get.)

---

### Post by ByteJuggler on 2008-11-27
> **slmouradian said:**
> No, Synaptic is a package manager.

You can find it at:
System -> Administration -> Synaptic Package Manager

Yes, but for **kubuntu** the package manager is not called "Synaptic", it's called "Adept", which is what the original poster was syaing I think.  However to the original poster: Both Synaptic (for the Gnome Ubuntu desktop) and Adept (for the KDE Kubuntu desktop) are in fact front-ends to the same underlying package management system.

---

### Post by kd420 on 2008-11-27
> **Paqman said:**
> Nope. 

Make sure you're getting the packages from the best server you can. Go to System > Admin > Software Sources > Download from > Other > Select Best Server.

Definitely do this! You can even look at the mirrored places and see if theres one close to you (the "Best Server" approach takes a while sometimes) and the speeds will greatly increase. I personally went from ~25 kb/s to over 250 by switching, and it greatly helps for updates and installing programs.

---

### Post by egalvan on 2008-11-27
> **ByteJuggler said:**
> Yes, but for **kubuntu** the package manager is not called "Synaptic", it's called "Adept", which is what the original poster was syaing I think.  However to the original poster: Both Synaptic (for the Gnome Ubuntu desktop) and Adept (for the KDE Kubuntu desktop) are in fact front-ends to the same underlying package management system.

Synaptic will work in KDE and Gnome.
I use it with both.

Aptitude used to be considered the "up-dated" apt-get.
Now-a-days, they are considered equal, and most long-time Linux users use 'apt-get'.

Again, it works with both KDE & Gnome.

to quote the Synaptic Web Site

[http://www.nongnu.org/synaptic/](http://www.nongnu.org/synaptic/)

*Synaptic is a graphical package management program for apt. It provides the same features as the apt-get command line utility with a GUI front-end based on Gtk+.*

---

### Post by ByteJuggler on 2008-11-27
> **egalvan said:**
> 
Again, it works with both KDE & Gnome.

Yes, correct, however the default GUI for Gnome is Synaptic, and the default for KDE is Adept.  By default, Adept is not installed on Gnome desktops and Synaptic is not installed Kubuntu desktops.  You would have to manually install the missing one if you wanted to use it on a desktop where it wasn't installed by default.  I did not mean to imply they're incompatible (indeed as I pointed out, they're both front-ends to the same underlying package management system!)

---

### Post by ByteJuggler on 2008-11-27
> **egalvan said:**
> 
Aptitude used to be considered the "up-dated" apt-get.
Now-a-days, they are considered equal, and most long-time Linux users use 'apt-get'.
[/i]

Just to add:  "aptitude" and "apt-get" are command line commands/interfaces to the package management system, being referred to here.  They're similar but independent text mode/command line based tools, as opposed to the previously mentioned Synaptic and Adept GUI tools.  (Get used to the feeling of choice you have for most things in Linux!)  :)

---

### Post by stevek123 on 2008-11-28
Just another quick note on seeing the available packages listed in add/remove (and probably applies to synaptic too) - make sure you've enabled 3rd party sources, universe, and multiverse - I did it (ubuntu) thru System->Admin->SoftwareSources... not sure your path in kubuntu...

---

### Post by kyleryner on 2008-11-28
thanks to everyone for all the helpful hints/replies!

I did stop the download and  most of the apps installed fine.

I changed to the Best server as suggested (would never have known about it otherwise) :)  Will test the speeds later..

Yes, I was referring to "Aptitude" in Kubuntu.. i understand now they are merely frontends and underneath its the same as Synaptic and the "Add/Remove" section in Ubuntu (whatever you call it).. i just thought (IMHO) that Ubuntu's user-interface is better. A total linux newbie like me managed to wade thru the basic stuff. For example, the Ranking feature in Ubuntu helps me decide what app to try.. did not see that in Kubuntu (although its possible there is such a feature but i just overlooked it).  Kind of surprising actually, based on some reviews I read and screenshots, I thought i would like KDE/Kubuntu better (talking about the overall user experience).. but turns out i liked Ubuntu better so i switched back. :)

Now on installing more goodies... (something tells me now that extra 5 gig i alloated to make it 10 gig still wouldnt be enough...)

thanks again

---

