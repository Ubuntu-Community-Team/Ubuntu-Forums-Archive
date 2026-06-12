---
title: "Help me find the right Buntu for me! (I Don't want to give up yet)"
date: 2013-03-27
forum: New to Ubuntu
---

### Post by charlieigg on 2013-03-27
Hello!

For many years I've heard about the wonders of the different Buntu distros. 
However it is until now that I decided to try it. What I did is download the regular Ubuntu 12.04 distro and installed it on a partition alongside my current OS (Windows 8).
Headaches until dawn. It just runs incredibly slow. Sometimes it will run OK, but then I want to launch a menu or app and it just freezes and hangs there for MINUTES. I tried changing the kernel's swappiness, and I logged using Classic Gnome (with no extras). Nothing. Compared to Windows 8 (which works seamlessly in my Netbook, but it's Windows and I hate Microsofts restrictive environment) this thing is crawling if anything.

My specs are:
-Acer Aspire One Netbook
-Intel Atom 1.6 GHz processor
-Intel Chipset graphics card
-2GB RAM
-I gave the Linux Partition System 30GB dedicated HDD space

Now I Know that often great stuff like this takes some time and work to get it just right, so that is why I don't want to quit just yet. But I am clueless, that's why I started this thread.
My best guess right now is that I should try a different distro of Buntu (or generally of linux) but I just don't know which is the right for me and my limited Specs.

What I'm looking for:
-An OS that is highly customizable
-An OS that can match Windows 8 in speed and performance on my netbook (I don't really care about boot times, just general performance/smoothness)
-Something that looks good (as in graphics) and not like if it was brought from the 90's

I REALLY appreciate your guidance.

---

### Post by MG&amp;TL on 2013-03-27
Unity's interface might lag a little on that laptop, but GNOME classic should be fine. That said, Lubuntu ([http://lubuntu.net](http://lubuntu.net)) is the lightest *buntu at the moment.

Welcome to open source, your attitude is certainly refreshing. :)

---

### Post by El Tito on 2013-03-27
I would go for Kubuntu. I suppose it should run smoothly in your laptop, although my experience with atoms says otherwise :)
I was told the latest gnome is very good (3.8), and also, if your laptop is suffering, you can change to the gnome fork (included) that looks like gnome 2 (lightweight).
I suppose the best looking are kde and gnome IMHO.

---

### Post by HermanAB on 2013-03-27
Xubuntu will work nicely on that machine.  I run it on one of my netbooks.

---

### Post by charlieigg on 2013-03-27
Thank you all guys for your responses. I think that I'm going to try with either Xubuntu or Lubuntu after reading a bit more on the web (there are some excellent Performance comparisons such as this one: [http://mylinuxexplore.blogspot.mx/2012/04/ubuntu-1204-vs-xubuntu-1204-vs-kubuntu.html](http://mylinuxexplore.blogspot.mx/2012/04/ubuntu-1204-vs-xubuntu-1204-vs-kubuntu.html))

Anybody know how much more limited are X- and Lubuntu compared to Ubuntu as in regards of customization?

---

### Post by Impavidus on 2013-03-27
I don't know about Lubuntu but it seems Xubuntu is easier to customise than Ubuntu.

---

### Post by ShadesOfGreen on 2013-03-27
If you want a fancy transparent minimized taskbar that shows up if you hover over it's spot with your mouse, than better take Xubuntu, because in Lubuntu it's not really transparant.. 
For example, in Lubuntu, when you're in your browser and mouse over the spot where the (minimized) taskbar would show, then the taskbar's backgroundcolor has the color of your wallpaper, so it isn't really transparant. (i hope you understand what i mean, because i don't really know how to explain it)

It's not a big deal however, and lubuntu is allot more lightweight as Xubuntu. (i use Lubuntu on my 10 year old Athlon64 with 512 mb ram and it runs great)

If you go for Xubuntu, i would recommend 12.10 because it looks better then 12.04 LTS :D

---

### Post by charlieigg on 2013-03-27
> **ShadesOfGreen said:**
> If you want a fancy transparent minimized taskbar that shows up if you hover over it's spot with your mouse, than better take Xubuntu, because in Lubuntu it's not really transparant.. 
For example, in Lubuntu, when you're in your browser and mouse over the spot where the (minimized) taskbar would show, then the taskbar's backgroundcolor has the color of your wallpaper, so it isn't really transparant. (i hope you understand what i mean, because i don't really know how to explanate it)

It's not a big deal however, and lubuntu is allot more lightweight as Xubuntu. (i use Lubuntu on my 10 year old Athlon64 with 512 mb ram and it runs great)

If you go for Xubuntu, i would recommend 12.10 because it looks better then 12.04 LTS :D

Yeah that's what I've read, however the strangest thing is happening right now, I downloaded the Xubuntu 12.10 iso, but as I'm Installing it, it says it's doing the 12.04... What the...!?

---

### Post by ShadesOfGreen on 2013-03-27
i don't think there is a xubuntu 12.10 with wubi ?
There seems to be a workaround, [http://ubuntu-with-wubi.blogspot.be/2012/10/tricking-wubi-installing-xubuntu.html](http://ubuntu-with-wubi.blogspot.be/2012/10/tricking-wubi-installing-xubuntu.html)

but if you are sure you want a specific distro i guess it is better to download the ISO file , make a mountable USB or CD, and install it that way.. 
Because from what i read the wubi installer is more like a thing to try out ubuntu, if you want to stick with it it's better to do a clean install the 'normal' way

---

### Post by 3rdalbum on 2013-03-27
Changing the whole desktop because of unusual slowness in Ubuntu seems rather extreme.

I have the same netbook with half the RAM running 12.04 and, while it is not a snappy performer, it is tolerable.

My thought is that there may be a program running in the background that is crashing and using up massive amounts of CPU time or RAM (causing the system to swap programs from memory to disk). If you can use System Monitor to find that program, you can kill it.

If you want lots of customisation, you might want to use KDE. Lubuntu, Xubuntu and Gnome Classic are configurable as you want, but have more than a whiff of the 1990s about them.

---

### Post by mastablasta on 2013-03-28
my thought on all this is -  you are using wubi which installs inside a virtual file in windows. so if you have problems with windows you will have issues here. additionally wubi is not necesserily as fast as dedicated install. furthermore wubi is only ment to test and as a chance to give users to easilly try out the system withouth any major system changes.

so i suggest you try again and this time with propper side by side dual boot. or only linux if you htink you can handle it.

and one more thing - there is no need to download xubuntu, reformat, reisntall... to see how a different desktop looks/behaves. you could have just searched for xubuntu-desktop in software center and install it. that would install Xubuntu to your computer. note that you might get some services doubled - e.g. network monitor form gnome and network monitor form xfce and such. but you can see hwo it looks like and behaves and oyu can later remove the gnome if you wish by copying a few commands into the terminal (very fast mehtod) or finding packages in package manager and uninstall those one by one.

---

### Post by Zill on 2013-03-28
> **charlieigg said:**
> ...What I'm looking for:
-An OS that is highly customizable
-An OS that can match Windows 8 in speed and performance on my netbook (I don't really care about boot times, just general performance/smoothness)
-Something that looks good (as in graphics) and not like if it was brought from the 90's...
I have installed [CrunchBang Linux (Waldorf)]("http://crunchbang.org/") on a similar AspireOne netbook to yours (but with only 1GB RAM!) and it really flies along. :-)

CrunchBang is certainly *very* customizable but as it is based on Debian, rather than Ubuntu, a lot of the advice on Ubuntu Forums is not totally relevant to the OpenBox Window Manager.

Boot times and general performance are excellent, although the limitations of the AspireOne graphics chipset reduce the ability to use "Ubuntu-like" eye-candy.

Although a lot of stuff "just works" with CrunchBang (including multimedia), it *can* give the appearance of a "techie" distro.  I will leave you to decide if this looks too 90's for you but I just view it as a very lean and efficient, first-class, distro. ;-)

---

### Post by kyalami321 on 2013-03-28
i wouldve gone with Xubuntu as a single install on the drive, as its the closest you can get to GNOME w/out its system reqs, though i guess it depends on your desire to DUMP windows. 

now this might sound noobish ... but HOW does win8 run faster than ubuntu 12.

---

### Post by MG&amp;TL on 2013-03-29
> **kyalami321 said:**
> 
now this might sound noobish ... but HOW does win8 run faster than ubuntu 12.

Reasons could be one of two:

[LIST=1]
[*]Microsoft's product does not use as much processing power as ubuntu does. Past experience says I should doubt this, but windows 8 is a big improvement. 
[*]Better driver support for one or more pieces of your hardware. If ubuntu cannot take advantage of, say, your graphics card, then performance will be reduced. 
[/LIST]

---

