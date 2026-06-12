---
title: "Just installed Ubuntu, what now?"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by Phustus on 2008-05-12
I just got it installed on a fairly old pc and was wondering what to do next, I think I need to install drivers or something but dunno how the OS works. Please help.

---

### Post by ladr0n on 2008-05-12
There are quite a few drivers already built into the Linux kernel.  There's a good chance that all of your hardware will work "out of the box" (especially if it's an older machine).  I would suggest that you just try it out and figure out what isn't working, and then ask how to fix those things.  
Out of curiosity, which version did you install, and what are the specifications of your hardware?

---

### Post by nathansoz on 2008-05-12
Wow! Some more information would be nice. What do you plan to do with the computer? As for drivers, most of the drivers that you should need will be built into the kernel or supplied as modules. In plain english this means that almost any driver you should need is installed already. But you may have an exception so feel free to ask questions and give more details!

---

### Post by ugm6hr on 2008-05-12
Start using the computer.  Presumably that's why you installed an OS on it!

It will be obvious if something isn't working.

Then post back describing your problems (if any).

If you don't know what you want to use it for - decide that first....

---

### Post by steveneddy on 2008-05-12
> **Phustus said:**
> I just got it installed on a fairly old pc and was wondering what to do next, I think I need to install drivers or something but dunno how the OS works. Please help.

What did you do on your last PC?

Did you have a plan for a particular type of usage on this machine?

What doesn't work?

Can you connect to the internet? IM someone? watch DVD's?

---

### Post by Zerocool10482 on 2008-05-12
Try to run the Ubuntu Hardware Tester. It's somewhere in your menu. I don't remember. I'm at work using Windows.

[https://launchpad.net/hwtest/](https://launchpad.net/hwtest/)

---

### Post by Phustus on 2008-05-12
The things I'll be using it for are Starcraft, music, and playing around with the terminal and such.

I don't know much off the top of my head but the specs that I know are 1gb ddr ram, radeon 8500 graphics card (ancient I know), a 300 gb hard drive, 400w power supply, I don't know what motherboard, and the screen has a max resolution of 1280x1024.

After using it for a while I've noticed that the resolution is kind of off.. The right side of my screen cuts off about half the recycle bin icon and half of the power icon. Does this have to do with my hardware or ubuntu?

---

### Post by Hamchan on 2008-05-12
Wow, I just bought my computer and it's even older than yours.

To change your resolution, you can go into system>preferences>screen resolution. That should fix your problem with things being cut off.

---

### Post by ugm6hr on 2008-05-12
> **Phustus said:**
> After using it for a while I've noticed that the resolution is kind of off.. The right side of my screen cuts off about half the recycle bin icon and half of the power icon. Does this have to do with my hardware or ubuntu?

You can recentre most monitor pictures using the monitor hardware controls.

This is unlikely to be a problem with Ubuntu, since it sounds like the resolution is correct, but the picture is just bigger than the visible screen.

Is this a CRT or flatscreen monitor?  If the former - almost certainly a problem with centering and adjusting the screen from the monitor controls.

As for using the computer - don't worry about drivers etc.

Just start using it.

You may need to install mp3 codecs for music etc, but you should be prompted to do that automatically if you try and play an mp3 file (I think).  If not - just ask.

---

### Post by Phustus on 2008-05-12
My resolution problem was fixed by pressing auto-adjust on the monitor :P (should have thought of that earlier).

I can't seem to install Starcraft using my cds (is the windows version incompatible?), it doesn't do anything when I try to run the .exe's on the cd.

---

### Post by ugm6hr on 2008-05-12
> **Phustus said:**
> My resolution problem was fixed by pressing auto-adjust on the monitor :P (should have thought of that earlier).
Great :)
> I can't seem to install Starcraft using my cds (is the windows version incompatible?), it doesn't do anything when I try to run the .exe's on the cd.
Your hunch was right - Windows programs are not compatible (in general).

Not sure what Starcraft is, but some Windows programs can be run with a bit of effort, but that is probably not something to attempt on your first day of Ubuntu.

---

### Post by thisiam on 2008-05-12
you wont be able to run .exe in ubuntu. check out [Wine]("http://www.winehq.org/") for using windows software.

---

### Post by Zerocool10482 on 2008-05-12
Good luck using Wine. I've never used it for games. But I know it works.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=149](http://appdb.winehq.org/objectManager.php?sClass=version&iId=149)

---

### Post by Phustus on 2008-05-12
I just realized there was a 2nd page to the thread, I thought no one was posting replies lol. I'm currently installing wine now and will try to figure it out. Estimated download time on the ubuntu pc is around an hour though so you might not hear back from me till tomorrow. Thanks for all the help so far, ubuntu's seeming pretty fun :D.

---

### Post by apostate on 2008-05-12
> **ugm6hr said:**
> Great :)

Your hunch was right - Windows programs are not compatible (in general).

Not sure what Starcraft is, but some Windows programs can be run with a bit of effort, but that is probably not something to attempt on your first day of Ubuntu.

Hi,

Starcraft, as well as most Blizzard titles will run absolutely swimmingly in Ubuntu with your Graphics card.  You need either WINE which is free, or Cedega which is very cheap, and geared toward gaming. Both are variations of the Wine project which is an application compatibility layer for Windows programs in Linux.  To get the most enjoyment from your games, I would honestly suggest you go to transgaming.com and get Cedega. It is $5 a month for a subscription which gets you upgrades to the engine. The engine currently supports Starcraft %100 so you could just cancel whenever you got tired of paying for updates you don't care about, and the GUI for Cedega is stoopid easy. It will detect your game disc, set the Windows emulation settings to the optimal, and then you just launch your games from a nice little menu. Easy as hell.  If you don't want to get it, let me know and I'll walk you through installing StarCraft with vanilla Wine. If you do want to get Cedega, download the package called something like:

i386 debian,Ubuntu,MEPIS,etc   (i386cedega-small.deb) and let Firefox open it with your package installer.

Have fun.

---

### Post by ubuntu-freak on 2008-05-12
Have a look at my [how-to](http://ubuntuforums.org/showthread.php?t=766683), it will help with installing codecs for music and video, Flash, Java etc and give you a chance to play around with the Terminal. :-)
 
Nathan

---

