---
title: "Installing on Pentium 3"
date: 2013-11-27
forum: New to Ubuntu
---

### Post by handysmurf on 2013-11-27
I have a number of salvaged desktops that refuse to install xfe.  I've tried different configurations in gparted from half the 16g drive, to no partitions, and everything in between.  I get a "operation fail, cannot inform kernal of changes to drive(?) reboot before continue." or something along those lines.  That is about the extent of any feedback i get from the install program... It appears to be "working" (even left it running overnight twice) have no idea as to cause.  xp was working on each before install attempts.

   "try ubuntu", and internet access is sucessful running from cd, (i guess that means "live"?) as are all the programs, albeit very slow response which is not unexpected.

---

### Post by mikewhatever on 2013-11-29
Well, P5 is too old. Ubuntu supports P7 onward. :)

You've probably meant Pentium4, for which Xubuntu 12.04 would be a better option. It's more lightweight, and runs XFCE by default.

---

### Post by handysmurf on 2013-11-29
been a while since i did anything on these old things...And apparently I have my details wrong... the one I'm trying to install on at the moment is a pentium 3 (not 5) clocked at 450 Mhz.  I am trying to install xubuntu 12.04, and I've tried the install so many different ways, i'm bout ready to throw in the towel.  I got a dell vostro 2420 with ubuntu preinstalled a year ago, and absolutely love it, but I was hoping to squeeze some more life out of these old desktops because of the line-in on the sound cards that the laptop lacks.

---

### Post by mikewhatever on 2013-11-30
The amount of RAM is usually the bottleneck on old machines. 12 years back, 256MB of RAM was acceptable, and XP was designed to run on that. In my experience, the Ubuntu live installer will not finish its job with less then 384MB of unshared RAM. If that's the problem, you can try [Xubuntu 12.04 Alternate ISO]("http://old-releases.ubuntu.com/releases/xubuntu/releases/precise/release/xubuntu-12.04.2-alternate-i386.iso"), which uses a text based installer. Here is a good walk-through: [http://members.iinet.net.au/~herman546/p2.html](http://members.iinet.net.au/~herman546/p2.html).

---

### Post by DuckHook on 2013-11-30
On machines that old, even Xubuntu is often too much. There are so many bottlenecks that modern distros will choke. Let us know some basic specs: RAM, video chipset, VRAM.

It also helps to know your own facility/familiarity with Linux and what you want to do.

I've got a soft spot for really old machines. Friends and family know that they can dump their old stuff off to me and I will reposition most for some kind of use. But it depends on how far you want to go getting into the more arcane and obscure parts of the OS.

Here are some ideas:

1. Install a minimal command-line system and run these old warhorses as servers. Once its just on the command line, even a Pentium III acts like it's on steroids. I have one such machine acting as a multiple server for network time, torrenting, mail server, print server and VPN server. Not bad for a rustbucket that would otherwise have long since gone to the great junk heap in the sky. Additional uses are: gateway/firewall, router/dhcp server, webserver, fileserver/NAS. This is, in my opinion, the best sort of use for ancient computers.

2. If you must run it as a desktop, then consider going completely outside the Ubuntu family. If =< 256MB, then consider distros like: Puppy, Vector, Slitaz, Damn Small, Tiny Core. Such distros cannot be considered even remotely as "full-featured", but they are surprisingly useful. Many are still on the 2.4.x kernel, which is ideal for the Pentium III. None use up any more than ~50MB for the OS footprint and their app selection is based almost entirely on resource minimalization, often (it must be admitted) at the cost of functionality.

3. If you are really into exploring, geekiness and masochism, then run it as a command line desktop. It's actually amazing the sort of things you can do on the command line from modern day necessities like surfing and e-mailing to: music-playing, videos, chatting, spreadsheets, word-editing, viewing images, pdf, the list is almost endless. This last is not a really serious consideration for new users, but it's nice to know that it's at least possible.

---

### Post by handysmurf on 2013-11-30
wow! thanks guys! I remember reading about the alternate installer somewhere, but I must'uv had a brain glitch.  it worked great, not a hitch during the entire install, now if the desktop works...  i'll have to try that tomorrow.  to answer your question tho'...  256M ram, don't know about the rest of the specs.

      I'm the guy that brings more stuff home from the dump than what i take...  I hate to see any useful thing discarded, and besides, it is recycling in it's purest form.

      mainly i want to record sound, the line-in on the desktop sound card gives me way better padding / flexibility than the mic jack on my laptop.  ubuntu laptop has been a dream, the programs are top-notch, audacity has advanced features that take all the "fun" out of editing marginal recordings, and whatnot.  I don't really care if the dinosauars are a little stressed,  anything i can do to distance myself from microsoft is freedom, and i'll take it!  i'll post more once i've gotten in some miles on the new OS,

Again...  muy gracis for all you'all's time.

---

### Post by DuckHook on 2013-12-01
I really hate to throw water on your heart-warming enthusiasm, but unfortunately, it doesn't work that way. The OS cannot read your mind. It won't know that you want to favour audio processes in preference to anything else, even if this means frozen graphics, etc. Therefore, your audio editing, which requires real-time precision to be anywhere close to workable, just won't work. Big modern graphical OSes will eat up so much of your resources just running their own overhead that they will have nothing left to run your audio apps. You are, of course, welcome to try, but I'm betting dollars to donuts that your desktop experience on a 450MHz Pentium III and 256MB RAM will be just awful no matter which Ubuntu flavour you install.

That was the whole point behind my original post: that the more proper distro in your case might be something like Tiny Core.

The alternate installer gives you a command line interface to start with, so your experience right after install will naturally be great. The system is not remotely stressed at this point. If you continue to use it only as a command line server, then for most server uses, it is likely to remain unstressed and continue to give you good results. However, the moment you install Lubuntu or Xubuntu on it, the system will slow to a crawl. It might even hang. A heavy-duty DE like Ubuntu or Kubuntu likely won't even load. This has been my experience with more than half-a-dozen of Pentium IIIs.

You do have my curiosity piqued though. Please do let us know how it goes.

---

### Post by handysmurf on 2013-12-15
gotcha, tiny core,  did get jaunty installed, and it boots okay, most apps okay, but "sound recorder" won't record, and since it is obsolete, no updates are available.  Tried ubuntustudio, but it kept asking for me to insert the ubuntustudio 9.04 dvd (20090421) which (i think) is in the drive.  That was the one i really wanted, but let me try tiny core.

     Waoh!  Man! Tiny is blazing fast!  I gotta do a bunch of research on this OS.  I wanna set it up to boot from the Hd just to simplify operation for a classroom.

    Yeah, I knew enough about the MS products to be dangerous, and even less about linux, but I love the philosophy, flexability, and the potential.  I'm a 59 yo truck mechanic, self taught in computers.  I have written a few filter programs in c++ related to lottery stats.  the knowledge is hard to hold on to because I am a single parent, and don't have the time to make daily use of many concepts, so by the time I need a skill the 2nd time, or try to build the knowledge, i have likely forgotten, and have to restart, so it is quite a struggle to learn.

---

### Post by MButterman on 2013-12-15
After skimming several answers, I wondered if boooting off a usb stick with knoppix would be an option. The usb might be faster than the old PATA drives. If you can put 1Gg in memory, it should suffice. If I am not mistaken Pentium mobos had that capacity, I could be mistaken. best of luck.

---

### Post by DuckHook on 2013-12-16
Knoppix is a full-fledged distro and will be as slow as the 'buntu flavours. Moreover, the age of the MOBO for a Pentium III will make it at most USB 1.0 which was slow as treacle. Last but not least, many of those old BIOSes could not boot from USB—only CD/DVD. Even if bootable, the USB speed and full-sized distro will be deal-killers.

@OP

You should not be resurrecting 9.04, as it is long dead and buried. If you want to keep using 'buntu, then no further back than 12.04 which remains supported and gives you updates that keep your system safe and secure. However, you've discovered for youself the speed difference between a bloated distro like any of the 'buntus (including Knoppix) versus super-light distros like Tiny Core. It's pointless to hanker after the bells and whistles when your HW just cannot handle it. Far better to go for functionality over eye-candy.

Tiny Core installation instructions are [here]("http://tinycorelinux.net/install_manual.html"). Because it's designed to run from a USB/CD, it requires some monkeying with the command line to install to HDD. But since you've done some work in C++ you won't be put off by the command line.

If you are exploring super-light distros, you may also want to give SliTaz a try. I like it's interface more than Tiny Core's and both end up using about the same amount of resources once installed. No matter which distro you settle on, make sure that it is the latest supported version.

Good Luck!

---

### Post by MButterman on 2013-12-18
Thanks for for the info. I wasn't sure if the combination would work so it's better to ask those with experience in it.

---

### Post by ajbozdar on 2013-12-18
In 2008, I used Ubuntu 8 version along with XP on Pentium 3 and it worked very well. But, one important thing my PC had 512MB RAM. It'd be better if you do not use a live cd. As live cd shares good amount of MBs of RAM to work very well. I used live CD on a Pentium 4 for test purposes, and it was quite slower. An other possible solution is that you can install Ubuntu 12.04 LTS version using installer (if you want to keep XP). Slow response is because of RAM. _Increase RAM and slowness of live cd will decrease itself_. -Best Wises

---

### Post by shabuboy on 2013-12-18
You need a distro that will support old old CPUs, specially one with non PAE support.

Check Bodhi and/or Zorin lite. Those worked for me on two 10yr old laptops. Running 521RAM on one of them and Zorin works fine

Just do not forget about PAE...

---

### Post by mörgæs on 2013-12-18
> **shabuboy said:**
> 

Just do not forget about PAE...

Please do forget about PAE. This is a Pentium 3, so it supports PAE (just like the Pentium 2 and 4).

There's so much unnecessary babble in the fora about PAE. Please don't make it worse.

---

### Post by ajbozdar on 2013-12-19
> **mörgæs said:**
>  There's so much unnecessary babble in the fora about PAE. Please don't make it worse.

It's already worse. Let's recover it. :)

---

