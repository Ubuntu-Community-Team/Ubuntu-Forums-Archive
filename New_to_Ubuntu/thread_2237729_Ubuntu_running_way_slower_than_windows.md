---
title: "Ubuntu running way slower than windows?"
date: 2014-08-03
forum: New to Ubuntu
---

### Post by sebastian28 on 2014-08-03
So I've had windows 7 on my machine ever since it was released and it was working really well (faster responses than windows XP).. but recently I've had some performance issues and decided I should give Ubuntu a go since linux based OS are supposed to be less demanding and faster than the Windows OS, right?

First I tried something called "Ubuntu GNOME" since it was the first one I found but when I "tried" it from the bootable USB it was running really slowly (and by slowly I mean windows taking a long time to open and appearing on the screen frame by frame, text appearing on screen only 1 second after I've pressed the keyboard button and just a general feel of unresponsiveness) so I decided not to install it. Ultimately I tried ubuntu 14 from a bootable USB stick using unetbootin and the same problem occurred. I thought it was probably the USB stick slowing it down so decided to install it and see. Install went fine, everything's alright but the problem is not gone: it's running SO slow.. it boots relatively fast but again: windows are taking a long time to open, the opening/pop-up animations (or however you want to call them) are running at no more than a couple frames per second, everything seems delayed and unresponsive and I have to wait a couple of seconds inbetween my every action.

Why is this happening?.. I know for a fact that linux-based systems are less demanding than windows systems.

My specs are: Intel Premium Dual Core 1.80 GHz processor, 4GB of RAM and NVIDIA GeForce 7300 SE video card.

Should I try to install a different linux distribution?.. can somebody recommend me a lightweight distribution (which still has functionality such as a graphical interface (well, I guess I could install that myself later), connectivity to internet and all of that).

P.S: I have had some experience with linux-based systems before, I know basic commands and all that but, as you can probably tell from this post, I'm still relatively new to linux so.. if you can, please keep that in mind in your responses.

Thank you for reading and thanks in advance for your response :)

---

### Post by Vladlenin5000 on 2014-08-03
Hi, welcome.

Ubuntu isn't necessarily less demanding than Windows. The standard Ubuntu with its modern Unity is quite similar to Windows 7 in terms of system requirements (Ubuntu Gnome isn't much less demanding). There are other desktop environments which are lightweight: XFCE (Xubuntu) and LXDE (Lubuntu). That said your machine should be enough for Unity but just barely. The problem is most likely related with graphics drivers.

Graphics drivers:
By default the open source driver is used. You probably need the Nvidia's proprietary driver. First of all test the OS as it is now but with the proprietary driver: Go to System Settings > Software & Upadates; click on the rightmost tab - Additional Drivers - and select the one that says nvidia and "proprietary, tested"; allow it some minutes to download and install the driver and when done reboot and test (important note: The boot splash won't look as good as before - blame Nvidia, not Ubuntu - but, provided the OS is now responsive as it should, we can deal with that small annoyance later, if you want (most people just live with it).

---

### Post by Wouter_De_Winter on 2014-08-03
You probably have to install/upgrade your graphics driver manually. This is (in my experience) a common problem after a fresh Ubuntu install with Nvidia.

---

### Post by Mike_Walsh on 2014-08-03
Hi, Sebastian...and welcome to the forums.

Take it from me, I understand your predicament very well!

I'm relatively new to Linux myself, although I've been messing about with these things ever since the year dot (well, since the early 1980's, anyway).

I'm like you; a long-time Windows user. I'd been using XP ever since it came out, 13 years ago, and it's end-of-life status was the push that I needed to try Linux for myself. I have friends who've been using it for years, and swear by it (and sometimes AT it..!)

Anyway. I also tried several of the distros; some on CD or DVD, some on USB stick (via UNetbootin), and without exception, the LiveCDs DO run slow. And the reason is very simple. Because although they do temporarily load into RAM while you try them out, the actual O/S is running from the disc itself.....and the rate of data transfer from an optical disc (unless you have top-flight BluRay, and not many 'puters have those) is very much slower than that of a hard drive; something in the order of a ratio of 1:7, or even 1:8...or even more. My figures may well be way out, actually...but you get the idea.

Flash drives are a little bit faster; but you WILL find, as I have, that once you actually install the O/S, the response time goes off the scale. Not massively so, but the response time is certainly better than that of Windows.

If you want a lightweight distro, Lubuntu 14.04 is a good place to start...but your specs are similar to mine (AMD Athlon 64, 3 Gb RAM, and I've got integrated graphics...the old Radeon Xpress 200 series); and my system handles Ubuntu 14.04 LTS a treat. In case you weren't aware, LTS stands for "Long Term Support"; it won't be end of life until 2019.

There's nothing wrong with your specs; many Linux distros are specifically designed to work with very much older hardware!

Regards,

Mike.

BTW, I agree with the other two; you will find that the graphic card drivers will give you the majority of your headaches when first installing, and setting up the system..!

---

### Post by sebastian28 on 2014-08-03
> **Vladlenin5000 said:**
> Hi, welcome.

Ubuntu isn't necessarily less demanding than Windows. The standard Ubuntu with its modern Unity is quite similar to Windows 7 in terms of system requirements (Ubuntu Gnome isn't much less demanding). There are other desktop environments which are lightweight: XFCE (Xubuntu) and LXDE (Lubuntu). That said your machine should be enough for Unity but just barely. The problem is most likely related with graphics drivers.

Graphics drivers:
By default the open source driver is used. You probably need the Nvidia's proprietary driver. First of all test the OS as it is now but with the proprietary driver: Go to System Settings > Software & Upadates; click on the rightmost tab - Additional Drivers - and select the one that says nvidia and "proprietary, tested"; allow it some minutes to download and install the driver and when done reboot and test (important note: The boot splash won't look as good as before - blame Nvidia, not Ubuntu - but, provided the OS is now responsive as it should, we can deal with that small annoyance later, if you want (most people just live with it).

Thank you so much for the fast response! I've done all of that (and meanwhile 3 more responses have sprouted up, I'm amazed) and everything is working so, SO much better than before so thanks :).. however, it's still not as smooth as I'd hoped for, sadly.. that doesn't mean I won't stick with Ubuntu, just that I'd like to try out different, more lightweight distributions. Which one would you recommend between XFCE and LXDE? And what are the differences?.. what does standard Ubuntu have that these distros don't?.. I assume I could read documentation myself and I probably will but, if it isn't too much of a bother a 1 or two rows summary would be greatly appreciated :)

Also, as a side note, since I don't want to open another thread for this: I keep getting a red bubble saying "Disconnected - you are now offline" although my connection is stable (or seems stable anyway; and I never got disconnected on windows). I have a wired connection from an ISP provider and I used pppoeconf in the terminal to set up my connection. I also tried with just clicking the little button on the top and adding a connection that way but same result. I am connected to the internet constantly, if I stream a video for instance it doesn't stop for even a split second, however every 5 minutes or so (very variable time intervals) I keep getting this bubble.

---

### Post by Paulgirardin on 2014-08-03
Note that you can install other desktop environments from the software center.You do not need to re-install the OS.You then select the DE at  login.
Look for: lubuntu-desktop ; LXDE ; xubuntu-desktop in the software center

---

### Post by sandyd on 2014-08-03
Do note that your graphics card, NVIDIA GeForce 7300 SE, is already ~8 years old and the slowest card in the 7xxx series. The default graphical interface may be a bit too heavy for your card.

If you want to try a alternative, lighter desktop environment, I reccomend XFCE.

You can install XFCE from the Ubuntu Software Center by searching for 'xubuntu-desktop', and installing the first entry that comes up.

When it is completed, log out, and click on the small circle beside your username/login, and choose XFCE. Login, and you should now be in XFCE.

---

### Post by mastablasta on 2014-08-04
you assumptions abotu Ubutnu are all wrong. window 7 is from 2009 (5 years ago), Ubuntu is from 2014. A modern OS for modern PC. Windows 7 Works well on older hardware as long as you turn off all special effects. Windows 7 starter preloaded on netbooks has these effects disabled. and Works well on low powered system.  Ubutnu uses 3D hardware (the graphics card) to draw Windows it uses numerous special effects to make the desktop look more pleasant. for that it needs relatively high spec machine to run fluently. well those made in last 2 -4 years will run it very well. I believe a similar thing can be noticed in windows 8 - where you basically have to have a modern PC or it will be running slow or won't even install.

now what others suggested is to change the default desktop environment to something lighter. something that doesn't use GPU to draw windows and such. Of those lighter version the most complete desktops are offered by XFCE and LXDE (found Xubuntu and Lubuntu). the panels and such by default do not look as pretty. there won't be any wobbly windows, sliding panels, transparent menus etc. but it will work fast.

> **sebastian28 said:**
> , just that I'd like to try out different, more lightweight distributions. Which one would you recommend between XFCE and LXDE? .

I would recommend you look at xubuntu and it's xfce first. it is more mature and easy to configure. Mate i("old gnome") s another option. once you get it up you can add various things (for visual pleasure).

modular nature of Linux allows you to change only part of the system. such as desktop, windows manager etc, while leaving the rest intact.

you asked about the difference between LXDE and XFCE - XFCE is older, more mature. LXDE is younger and currently undergoing a transformation into LXQT (qt library based desktop). they are both similar but I think XFCE is easier to modify and has a bit less big bugs. 

---
another thing you said you had performance issues on windows 7. if the slowdown wasn't software related it could be hardware related. might be worth to run a few tests on disk just to be sure.
---

---

### Post by Mike_Walsh on 2014-08-04
Hi, mastablasta.

Quote:-

"you assumptions abotu Ubutnu are all wrong. window 7 is from 2009 (5  years ago), Ubuntu is from 2014. A modern OS for modern PC. Windows 7  Works well on older hardware as long as you turn off all special  effects. Windows 7 starter preloaded on netbooks has these effects  disabled. and Works well on low powered system.  Ubutnu uses 3D hardware  (the graphics card) to draw Windows it uses numerous special effects to  make the desktop look more pleasant. for that it needs relatively high  spec machine to run fluently. well those made in last 2 -4 years will  run it very well. I believe a similar thing can be noticed in windows 8 -  where you basically have to have a modern PC or it will be running slow  or won't even install."

Interesting.

My machine is a 10 year old HP/Compaq Presario desktop PC. AMD Athlon 64 3200+ CPU, 3 GB DDR1 RAM, ATI Radeon Xpress 200 integrated GPU (RS482 chipset-based), and a Western Digital Caviar 'Black' 160 GB HDD.

THIS INTEGRATED GPU DATES FROM 2004. For goodness sakes, it has a clock speed of just 300 MHz and uses system RAM becaause it has no dedicated memory of its own...

I've been running 64-bit 'Trusty Tahr' since the last week in April. To date, it has performed faultlessly; no glitches, no flashes and/or pixellation and/or lines or ANYTHING similar graphics-wise. Now, according to your theory, my machine, which was designed for Windows XP (itself released WAY back in 2001!), should barely be capable of running Unity properly, if at all.

Yet I have not ONCE had any graphics trouble .....of ANY kind. AND I'm running full 3D acceleration.

Comments?


Regards, 

Mike.

---

### Post by whitesmith on 2014-08-04
As others have pointed out, you have a choice of desktops in Linux. Not so in Windows, which limits you to explorer.exe; likewise, Mac comes with a take-it-or-leave-it desktop environment. With either operating system, DE modifiability is out of the question. Contrast that straitjacket with Linux, which offers almost limitless DEs; some nimble and fast, others feature-heavy and leaden. The point is this: Linux lets you choose. Here are 8 from which to experiment: [http://www.howtogeek.com/163154/linux-users-have-a-choice-8-linux-desktop-environments/?utm_source=newsletter&utm_medium=email&utm_campaign=180513&utm_content=emailsidebar](http://www.howtogeek.com/163154/linux-users-have-a-choice-8-linux-desktop-environments/?utm_source=newsletter&utm_medium=email&utm_campaign=180513&utm_content=emailsidebar) -- Be warned of this: Linux is addictive. Cheers.

---

### Post by dave131 on 2014-08-05
I would pay attention to what mastablasta is saying.  Just because they keep their bean count hidden is no indication of experience and knowledge - and mastablasta has both.  He/she also is mature enough not to get in an arguement with someone with obvious less experience.  I would try some of the suggestions that have been made and then post back.

---

### Post by mastablasta on 2014-08-05
> **Mike_Walsh said:**
> 

Yet I have not ONCE had any graphics trouble .....of ANY kind. AND I'm running full 3D acceleration.

Someone supported your chip well. patched drivers propperly in kernel etc. From similar age, i think maybe even same CPU and Radeon 9200 - can't get propper 3D using the chip. It is using the CPU instead. Now plenty of supported KDE special effects still work and desktop does work fluently, however try running some games (no the demanding one) and it will all start to crawl.  More RAM helps in speeding up the desktop (up to a point). most computer form that age have less RAM in them.


> 
Comments?


Age is a rule of thumb. I all depends how well the components are still supported. If you had a newish card (my other build AMD single core 3200 as well i think, 4GB ram, Radeon 3650)  when 13.04 came and a kernel update for 12.04 these chips lost propietary driver support for xserver i believe. at the same time the opensource drivers for these chips were a lot worse than proprietary drivers. so what happened is that people with this cards had a major slow down. desktop sort of work for the most part butother things just didn't work as well. so proprietarz drivers dropped and opensource not ready = slower performance on these older chips. let's not even start talking about rubish battery life on laptops with opensource drivers.

2 years later - 14.04 opensource drivers with the help of AMD got some major improvements for these chips. now they work almost as good as proprietary but graphic tests still show they are not as good (you can read more on this on Phoronix website).

In this case of OP (i do not know the nvidia chip line that well) it could well be that their equipment is old enough to have bad support or none from proprietary drivers and yet it is young enough (as those chip i wrote above) that opensource drivers are not that developed yet.

the issue here is likely drivers. so if they can install proprietary i would use those. if they can't then the only option is some PPA with newer opensoruce drivers or to wait until they improve them.

---

### Post by Mike_Walsh on 2014-08-05
Hi, mastablasta.

Fair comment.

You're probably right on that score...about the games & stuff.

I'm NOT a gamer. I'm in my mid-50s, and photography is my main passion these days. I do a lot of photo editing (I use GIMP, darktable, and I've started dabbling with LibreCAD, since I did a fair amount of technical drawing when I was younger, and I always promised myself that one of these days I WOULD look into CAD, and find out for myself how it works...)

The point being, of course, that this is all what I call 'static' computing; i. e., working on a single frame at a time. It's not fast moving, and it's not constantly changing. I have NO doubt at all that the Xpress 200 would struggle mightily at gaming. According to some old reviews I've found, even 2 years after it's introduction, it struggled like h**l with the then current games on the market... Unfortunately, I can't install a graphics card on this mobo; the single PCI-e x 16 bus on it has several damaged pins in the slot; and it's only 1.0a spec anyway. I'm considering a rebuild in a few months time (when funds permit); FM2-based Gigabyte board, AMD A6-6400k APU (with the built-in 7000-series HD Radeon GPU), and obviously, a larger quantity of DDR3 RAM.

But my system works for what I want it to do, so...I can't complain. 

I think I've 'hijacked' poor Sebastian's thread enough for now ( a point I've grumbled about other folk doing! ), so we'll let him get back to it!!

Regards,

Mike.

BTW; I WILL have a look on the Phoronix site... I was reading some of their stuff about the Gallium LLVMpipe drivers the other day, so that'll be interesting; thanks for that.

---

### Post by mastablasta on 2014-08-05
yes money is always involved with upgrade and then you can only wonder do I really really need it? and usually you can find out you can do without.

in your case I would use a lighter desktop - it would free up more the GPU power for other processes. I have this old notebook we got as a gift. 1,2 Ghz Athlon 64 (Single core) and only 256 MB ram. it has a 32Mb GPU. Ubutnu 10.04 worked nicely though later it got sluggish. so I put Debian remix (Chrunchbang) with XFCE desktop. A little bit of tweaking to use flat panels and such and this computer can work nicely one process at a time. you can surf the web (well as long as too many tabs are not open), edit documents on it, draw, even play some simple kids games. remarkable! and this is all because the desktop is tweaked in such a way as to use minimum CPU, GPU and RAM (it uses about 80-90 MB on boot I believe).

I too wish to upgrade the PC I have but then I always think "I can still use them, they are not dead", so I will continue to use them until they stop working. I then spend money on other more important things (/taking family on a trip or something like that).

If you plan on getting the APU, check for their support. Some of these have poor Linux support. Not sure which ones but I did read some threads from users where even proprietary drivers didn't help. My brother did some research at the time he though he might need to change the whole thing (also keeping the old one as long as he can) and found some interesting combo of cheap but good AMD CPU and Nvidia card. both together didn't use much electricity and seemed to be medium range and would hold for another 10 years or so. as I remember he told me that the power put together from both was greater than from these APU yet the price was almost if not the same. I can't remember all the details since it was about 8 months ago. all I am saying it pays off to investigate these things a bit. especially if you are tight on money and want them to last as long as possible or at least for the components to be upgradable.

---

### Post by Mike_Walsh on 2014-08-05
Agree with ALL that.I've always believed in doing my research when it comes to tech.

Sometimes I let stuff 'prove' itself in the marketplace SO long that it's nearly obsolete by the time I invest in it.

Take CDs. Marantz made the first commercial player in 1983. I didn't buy my first CD player until 2001...18 years later! CDs were already in decline, to be relaced in large part by solid state storage. I didn't buy my first MP3 player till 3 years ago...

So, yeah; I do like to research tech. I shall do precisely that with the A6. I don't think I shall take QUITE so long, though; I'm NOT getting any younger! :D

Regards,

Mike.

---

