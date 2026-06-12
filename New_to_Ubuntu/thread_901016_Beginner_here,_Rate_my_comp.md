---
title: "Beginner here, Rate my comp?"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by mrtasan on 2008-08-26
Hey,

I've posted before but I have a couple of questions now. I just finishd building my computer and I'm waiting to finish downloading Ubuntu. My initial plan was to build an energy efficient Shuttle for moderate personal use for around $300. here are my specs:

Shuttle SN68SG2 Barebones PC
AMD Athlon X2 BE-2400 2.3Ghz 45W Dual Core
NVIDIA GeForce 7025(onboard)
WD Caviar Green Power 500GB SATA Internal Hard Drive 
OCZ SLI-Ready Edition 4GB (2 x 2GB) DDR2 800
Samsung 22X Serial ATA DVD+/-RW/RAM Burner 

What do you think? I got it all for just over $300

Also, Is there an anti-virus program for Ubuntu? I read somewhere that Linux doesn't need Anti-virus programs? Is that true?

Do I need to know programming to be able to use Ubuntu?

Any help would be greatly appreciated! Thanks!

---

### Post by iaculallad on 2008-08-26
> **mrtasan said:**
> Hey,

I've posted before but I have a couple of questions now. I just finishd building my computer and I'm waiting to finish downloading Ubuntu. My initial plan was to build an energy efficient Shuttle for moderate personal use for around $300. here are my specs:

Shuttle SN68SG2 Barebones PC
AMD Athlon X2 BE-2400 2.3Ghz 45W Dual Core
NVIDIA GeForce 7025(onboard)
WD Caviar Green Power 500GB SATA Internal Hard Drive 
OCZ SLI-Ready Edition 4GB (2 x 2GB) DDR2 800
Samsung 22X Serial ATA DVD+/-RW/RAM Burner 

What do you think? I got it all for just over $300

Also, Is there an anti-virus program for Ubuntu? I read somewhere that Linux doesn't need Anti-virus programs? Is that true?

Do I need to know programming to be able to use Ubuntu?

Any help would be greatly appreciated! Thanks!

Not bad for a unit work $300, better yet if you included your monitor type so we could have assessed it. (But, with that specs, I could have paid $250 for that).
You can install Clamav AV in your Ubuntu but "sure" it's not recommended as you don't really need it.
You don't have to have a knowledge in programming to learn to use Ubuntu.

---

### Post by crispy_420 on 2008-08-26
Well you got me beat on my Ubuntu machine:

P4 2.0GHz
1024 DDR
200GB IDE + 80GB IDE (200GB is in swappable cage)
Logitech Elite Keyboard + Logitech MX510 Mouse
ATI x850 Pro
Leadtek WinFast TV Tuner
OEM Case
Intel 845 Chipset Mobo
LG DVD-RAM + Lite-On DVD-ROM

---

### Post by mrtasan on 2008-08-26
HELP!!!!

THE LIVE CD WONT INSTALL ON MY COMPUTER!!!

The screen shows up and it asks what to do, so I select "Install Ubuntu" and then it goes "loading Linux Kernal...100%" and then it stalls forever!!!!

What to do!??!?!
Please Help!!!

---

### Post by iaculallad on 2008-08-26
> **mrtasan said:**
> HELP!!!!

THE LIVE CD WONT INSTALL ON MY COMPUTER!!!

The screen shows up and it asks what to do, so I select "Install Ubuntu" and then it goes "loading Linux Kernal...100%" and then it stalls forever!!!!

What to do!??!?!
Please Help!!!

Did you download and burned the Ubuntu Desktop LiveCD ISO file yourself? If so, had you checked it for errors (MD5 hash) prior to burning?

Here, try reading this Ubuntu Community [page]("https://wiki.ubuntu.com/BurningIsoHowto") on how to properly burn an ISO.

---

### Post by Fondor1 on 2008-08-26
How long is "forever"?  It should be *fairly* quick, but it may take up to 5 minutes before you see anything.  Let it run for a bit first.

If you already waiting for a few minutes, have you tried the failsafe boot option?

---

### Post by mrtasan on 2008-08-26
There aren't any boot options on my computer? at least I dont see any. I'm new to a shuttle as well to ubuntu/linux.

I'll try verifying my cd. Thats the first option i chose when i installed and it just didn't work. I'm burning another cd at the slowest speed. If this doesn't work then I dunno what will.

---

### Post by RequinB4 on 2008-08-26
Remember, as a last resort you can install the text-based (non-pretty, but more stable) alternative installer - it's useless for "demoing" ubuntu, but it'll install it to your specifications.

As with any install - make sure you set up your partitions correctly so you don't accidently delete any other OS's on your comp.  If you need help, just ask here.

---

### Post by mrtasan on 2008-08-26
I really hope that it is the CD and not my computer. I dont want to go through the hassle of returning everything. What is this alternative installer?

Also what are "nolapic" or whatever?

---

### Post by crispy_420 on 2008-08-26
I also recommend the alternate install ISO if you having install issues. It seems to work better with more stubborn machines and also low-end ones (not implying yours is the second of course).

---

### Post by Michael.Godawski on 2008-08-26
the alternate installer is a text based installation of ubuntu

it helped me out a lot of times

for more information about this installation have a look at hermans site:

[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

---

### Post by RequinB4 on 2008-08-26
> **mrtasan said:**
> I really hope that it is the CD and not my computer. I dont want to go through the hassle of returning everything. What is this alternative installer?



Yep - The alternate installaer is an ISO image (CD) just like the LiveCD - but it just doesn't have most of the "gizmos and whizbangs" that let you try out the OS before you install it - which means that it will basically install on anything that looks like a computer :guitar:
You can get it the same place you did the other ISO - [www.ubuntu.com](www.ubuntu.com) - just either check the "alternate installer" box, or download the hardy i386 iso that says installer on it.

But really, if you say the cd check failed on the first cd, you should just redownload ([check the md5sum]("https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20Windows")) and re-burn at a slower speed the regular livecd.  Not only is it a lot prettier, it automatically does a few useful things on install.

> 
Also what are "nolapic" or whatever?

Those are boot options that tell whatever you are booting from exactly what programs to load or whatever.  it's best not to mess around with those unless someone knows what they are doing.  I forgot how to acess them on a livecd because it's been so long, but with an alt cd (or a re-burned regular cd) you shouldnt need it.

---

