---
title: "Linux &amp; Games for 64mb of Ram?  Possible?"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by NewRubberSoul on 2008-08-07
Hello,

I have a friend that has a very old computer she would like to use for games.  She has Windows 98 running on it now with a few card games, mahjong, memory games, etc.

She doesn't know anything about computers, but won't be using it for web browsing, text editing, or anything, besides the occasional game or to watch a VCD movie.

I've heard of linux distros that are good on old hardware and was wondering if I'd be able to put linux on this computer and load it with simple games.  

But the system is very old.  Here's what I'm working with:

[LIST]
[*]Panasonic CF-57 Computer
[*]Windows 98
[*]Intel Celeron Processor
[*]64 Mb of Ram
[*]5.98 GB Hard Drive
[*]CD-Rom, Floppy, and USB Drives
[/LIST]

So my question is this:  Is it even possible to get something working on this old machine?  And if so, is it even worth it? Her Windows 98 doesn't run too slowly and I wouldn't the linux distro to run too slow. Should I just leave Windows 98 and not bother or is there hope for this machine yet?

I've checked out some of the lightweight distro websites (Puppy, Xubuntu, DSL, Wolvix, etc.) but they recommend 128mb of Ram.

Any ideas would be gladly welcomed.

---

### Post by Rocket2DMn on 2008-08-07
With that little RAM it is unlikely that your friend will be able to play any kind of graphics intensive game, she would be limited to small things like card games and other little brain teasers and puzzle type games.  Xubuntu may even be a little heavy for that machine, Puppy or DSL would go better, but they are very limited out of the box (but they work!).
The machine should be ok for web browsing, text editing, email, and small stuff like that.  May run into problems trying to play videos that are highly compressed or just run at high kbit rates (like larger resolution videos), and I'm not sure how well flash would run (for stuff like youtube).  It would *work* but you won't notice any leaps and bounds improvements over the way it acts now.

---

### Post by JoshuaRL on 2008-08-07
I agree with Rocket.  DSL would be my suggestion, since it is based off of Debian (like Ubuntu) and so you can have APT.

---

### Post by Crafty Kisses on 2008-08-07
He could probably play Five or More.

---

### Post by snowpine on 2008-08-07
Unfortunately, nothing in the *buntu 8.04 Hardy family will currently install easily on 64mb of ram: [https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/202959](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/202959)

There is a bug in the installer. I was able to do a minimal install on a virtual machine with 64mb of ram, but it took TWO DAYS, and that was on a fast computer. :(

DSL is your best bet.

---

### Post by Tom--d on 2008-08-07
Quake 1!
You can play Quake! :D:D

Its amazing. And you can get it for Linux as well :D

---

### Post by halitech on 2008-08-07
I'm in the process of installing Zenwalk on a similiar machine (Thinkpad 1400i) that has a Pentium 300 processor, 64meg of ram, 12 gig drive, floppy, cd/dvd combo drive so once its done I'll let you know how it works out :)

may also try DSL-n and puppy just to see what I can get working.

---

### Post by doorknob60 on 2008-08-07
I installed Fluxbuntu on a laptop with 64 MB of RAM, 400 Mhz AMD K6 CPU, 4.5 GB Hard Drive before. I even put in a wifi card (PCMCIA) and was able to browse the web in Opera :lolflag: It was definately usable, although I didn't try nany games. I've since upgraded the RAM to 192 and installed Debian on it (with xfce, then I switched to Lxde). After the RAM upgrade, I can actually play Runescape and funorb.com and playable speeds :-) And SNES emulators.

---

### Post by snowpine on 2008-08-07
> **doorknob60 said:**
> I installed Fluxbuntu on a laptop with 64 MB of RAM, 400 Mhz AMD K6 CPU, 4.5 GB Hard Drive before. I even put in a wifi card (PCMCIA) and was able to browse the web in Opera :lolflag: It was definately usable, although I didn't try nany games. I've since upgraded the RAM to 192 and installed Debian on it (with xfce, then I switched to Lxde). After the RAM upgrade, I can actually play Runescape and funorb.com and playable speeds :-) And SNES emulators.

Hi Doorknob, I am having a problem with a 64mb Fluxbuntu install... since you were able to get it working, can you possibly check out my other thread... maybe you know the answer? [http://ubuntuforums.org/showthread.php?t=882096](http://ubuntuforums.org/showthread.php?t=882096)

Thanks! (and sorry to derail the thread)

---

### Post by halitech on 2008-08-07
update: well the install of zenwalk went fine, not too bad for time and it booted with no problems but when I go to log in my keyboard is not putting in what I am typing so not sure what happened there.

will try fluxbuntu as soon as I finsih downloading it and see what happens :D

---

### Post by mikjp on 2008-08-08
It is possible to install e.g. Debian or Slackware with X Windows on that computer. It should be fast enought to be able to play Mahjong or Patience, but not much else. 

Forget KDE and GNOME. Use IceWM or OpenBox. 

Playing videos? No way. 

> update: well the install of zenwalk went fine, not too bad for time and it booted with no problems but when I go to log in my keyboard is not putting in what I am typing so not sure what happened there.

Are you using a USB keyboard? Try  PS/2 kbd.

Greetings,

mikko

---

### Post by halitech on 2008-08-08
actually its a thinkpad laptop so no USB keyboard. Believe it or not, I could not get any distro to boot properly except Ubuntu 6.10 after adding another 64 meg of ram. Its not a speedster by any stretch but it does seem to be working.

---

### Post by JoshuaRL on 2008-08-10
> **halitech said:**
> actually its a thinkpad laptop so no USB keyboard. Believe it or not, I could not get any distro to boot properly except Ubuntu 6.10 after adding another 64 meg of ram. Its not a speedster by any stretch but it does seem to be working.

Try to install [Enlightenment (e17).](http://ubuntuforums.org/showthread.php?t=546746)  It's a lightweight desktop environment, and you might get a little better performance.  There's lots of cool themes out there too.

---

### Post by tjwoosta on 2008-08-10
i can play doom with only 32mb ram on damnsmalllinux

---

### Post by halitech on 2008-08-11
> **JoshuaRL said:**
> Try to install [Enlightenment (e17).](http://ubuntuforums.org/showthread.php?t=546746)  It's a lightweight desktop environment, and you might get a little better performance.  There's lots of cool themes out there too.

I've actually had to give up on getting Linux running on the thinkpad, couldn't get the xircom pcmcia card to work and with no net connection, setting up a network is miserable so its gotten win2k on it (and will be "donated" to my girlfriends oldest daughter for school work) and I've decided to put DSL on an older toshiba tecra 550cdt which to my amazement, installed perfectly. Had to modify the /opt/localboot.sh to get sound working on boot and set it up with a static ip but other then that, no problems running it on 96 meg of ram, 4gig hard drive, cd rom and the same xircom pcmcia card..

---

### Post by mikjp on 2008-08-16
There is one new possibility: Vector Linux Light:

[I]Light Edition

    * LXDE, JWM and Fluxbox
    * Abiword and Gnumeric
    * Galaxy
    * 64mb of RAM required
    * 2gb of HD required
[/I]

([http://vectorlinux.com/downloads](http://vectorlinux.com/downloads))

Mikko

---

### Post by Vivaldi Gloria on 2008-08-16
Play NetHack.

---

