---
title: "[SOLVED] still having problems with wmv and other video files"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by anewguy on 2008-09-24
Prior to going to 8.04, I had wmv and other video files playing fine.  Since the upgrade last spring, I have been trying like crazy to get these things to work again.  I have tried many things, but will summarize where I am now.

With VLC, the video either doesn't start, shows only a frame or two, or shows 1 very distorted frame.  Movie player does the same unless I stop the playback, wait about 10 seconds, then play - it will play about 3 or 4 seconds tops before it goes bad again,

I have installed many things, but have backed it down now to having ubuntu-restricted, gstreamer good, bad and ugly, and the win32codecs.

If anyone can provide any insight into this it would be so greatly appreciated!

Thanks in advance!

Dave :)

---

### Post by sneeks on 2008-09-24
did you try the resticted extra's and also all the lib's for gstreamer.

---

### Post by knix on 2008-09-24
ubuntu-restricted-extras is a huge download, but it has all sorts of useful codecs, etc.

---

### Post by crjackson on 2008-09-24
> **anewguy said:**
> Prior to going to 8.04, I had wmv and other video files playing fine.  Since the upgrade last spring, I have been trying like crazy to get these things to work again.  I have tried many things, but will summarize where I am now.

With VLC, the video either doesn't start, shows only a frame or two, or shows 1 very distorted frame.  Movie player does the same unless I stop the playback, wait about 10 seconds, then play - it will play about 3 or 4 seconds tops before it goes bad again,

I have installed many things, but have backed it down now to having ubuntu-restricted, gstreamer good, bad and ugly, and the win32codecs.

If anyone can provide any insight into this it would be so greatly appreciated!

Thanks in advance!

Dave :)

Give this a try if you are on 32-bit Hardy.  It always works for me.  Don't worry if you already have some of this installed, it will skip over those items.

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2 libdvdnav4 gxine totem-xine xine-ui libdmx1 libxine1 libxine1-ffmpeg libxinerama1 libdvdread3
```

---

### Post by anewguy on 2008-09-24
As mentioned, I already had the gstreamer stuff I though I needed and also already had ubuntu-restricted-extras.

crjackson:  Thanks for the input.  I went ahead and copy/pasted your command line but the videos still don't work.  I noticed the downloads from the command line didn't get win32-codecs-2007, but I assume that is because I already had the newest ones installed.  Any more things for me to try?

Thanks!

Dave :)

---

### Post by crjackson on 2008-09-24
> **anewguy said:**
> As mentioned, I already had the gstreamer stuff I though I needed and also already had ubuntu-restricted-extras.

crjackson:  Thanks for the input.  I went ahead and copy/pasted your command line but the videos still don't work.  I noticed the downloads from the command line didn't get win32-codecs-2007, but I assume that is because I already had the newest ones installed.  Any more things for me to try?

Thanks!

Dave :)

crap!  I had my fingers crossed for you.  I've only EVER had 2 users report this didn't work for them.  This was MY ultimate solution for me, and I was hoping for you too...

This pretty much installs all codecs available so I'm not sure at this point what to try next.

If you already had the win32codecs installed, it shoud just skip them and indicate 0 packges removed, 0 installed, 0 updated.  Did you get something like that?

---

### Post by I wanted to leave on 2008-09-24
I have installed Hardy 3 times in the last 2 weeks (long story)
However, I use the default players Rhythmbox and totem without any pain.
In Rhythmbox just try to play mp3 and wma and you get a prompt to install missing codecs. Install both codecs. In synaptic, as mentioned, ensure you have restricted-extras installed. Thats the audio sorted inc streaming. 

For totem (movie player) to work, inc vcd, all I do is install libdvdcss via

/usr/share/doc/libdvdread3/install-css.sh

Thats it. Everything works! :popcorn:

I like a minimalist approach to my desk, but that's the simplest means I have found.
Good luck

anewguy you could also install libdvdcss to get vlc working, eventhough 'it comes with everything' it needs to play

---

### Post by anewguy on 2008-09-24
All of the libdvd* packages I already had installed, so that's not it.  As mentioned previously, the gstreamer good bad and ugly packages are installed.  I re-installed the win32-codecs just to be safe.

No difference.

---

### Post by crjackson on 2008-09-24
> **anewguy said:**
> All of the libdvd* packages I already had installed, so that's not it.  As mentioned previously, the gstreamer good bad and ugly packages are installed.  I re-installed the win32-codecs just to be safe.
No difference.

I've actually done hundreds of installs, and always use the code I posted above with perfect results :confused:

Is this a clean install, or was it an upgraded install from a previous version?

---

### Post by anewguy on 2008-09-24
I had been at 7.10 until last spring when 8.04 came out, then initially did an upgrade.  I then updated my video card and did a complete fresh install of 8.04 in May.

---

### Post by crjackson on 2008-09-24
> **anewguy said:**
> I had been at 7.10 until last spring when 8.04 came out, then initially did an upgrade.  I then updated my video card and did a complete fresh install of 8.04 in May.

I've actually had to tinker with video output modes in some of my players to get EVERYTHING working.  It's trial an error and I'm sure you've probably done all that.  X11 on some apps and I can't remember on some of the others.

I wish I had a better answer for you.  Messing with some flavors of flash and WinCodecs can be a test of your patients.  Keep banging away.  What video card are you using?

---

### Post by anewguy on 2008-09-25
Okay, may have found a hint as to what is going on.

Prior to 8.04, I was running a real antique video card - an old Diamond Viper with only 16mb memory.  It didn't do anything like compiz, etc., but I was able to play wmv files with no problems with the codecs and the gstreamer "extras".  I updated to 8.04, and very shortly afterwards updated to an ATI 9250 video card.  Compiz, etc., runs fine on it.

So, tonight I thought I'd try installing and running the Elisa Media Center package, and I think it gave me a hint:

It said I was running old video hardware and that video playback would be slow.  Hummmmm.....maybe like the problems I'm having?

So, I go looking at hardware manager and see my video card is listed as follows:

ATI Technologies RV280 (Radeon 9200 Pro) (secondary)

I thought I had installed a driver via ENVY, but when I think back I think it just worked when I installed 8.04 again.  In the hardware manager I see no driver listed, and there is nothing under system/administration/hardware drivers.

So......is it possible whatever default driver is being used (xorg.conf says "ATI") is screwing this up, and if so, is there another driver of some sort I should install instead?  Do I perhaps need some special xserver-xxxx-xxxx file?

I have to believe since that old Diamond Viper card still ran wmv files okay that it must be something with this card.  And since the hardware is more advanced than that old card, I would assume it therefore has to be with the driver.

Does anyone know if there is another driver besides what I got by default in Ubuntu 8.04 for this RV280 (Radeon 9200 Pro) card?

Also, what does (secondary) mean on the hardware manager description of this device - is that saying it has more than 1 output (which it does)?

Any help would be greatly appreciated!

Dave :)

EDIT:  I found a post on the internet from 2006 where somebody got this card working with Ubuntu using a driver of "radeon", not "ATI", in xorg.conf.  Does anyone know where I can get that driver and if it still applies for 8.04?

---

### Post by crjackson on 2008-09-25
Okay, so it seems you are running the 9250 if I understand correctly.  I have several ATI systems and I have to admit that although they work fine, they have each required a BUNCH of tinkering with the media players to find something that will work with all my video files.  I have to use different players for different file types.

On my systems that have nVidia cards I don't have this issue at all.  On one of my systems I too changed video cards on a perfectly working system but wanted an upgrade.  I never did get it all sorted out until I did a fresh install with new video card in place, and still I needed to adjust a few player settings.  I use the driver supplied with the Restricted Driver Manager for ATI with best results.  I have installed all the newer drivers but find too many glitches with them so far (for my taste anyway).

If it's feasible, I would back everything up and start with a fresh install with all the hardware in place.  Then the tinkering begins... :)

Oh, and BTW - MPlayer Movie Player and Totem Xine works the best for me on MOST files.

---

### Post by Teamgeist on 2008-09-25
Try to install the ATI driver by going to System--> Administration--> Hardware drivers.

This will (hopefully) install the proprietary ATI (fglrx) driver for you and will give you 3D support and hardware accelerated video support.

---

### Post by markbuntu on 2008-09-25
No no no, do not install fglrx from ati. It does not support your card. What you need is the latest Radeon open source driver.

---

### Post by anewguy on 2008-09-25
Well, I did a couple of things before I got back here to see your posts - wish I had seen them first! :)

I tried Envyng in the GUI format (GTK) but it said my card wasn't supported.  I then did the text-mode version and selected manually choose.  I somehow got a version of the driver installed that included the "radeon" driver, but it never worked through xorg - the log file didn't say anything was wrong, it just defaulted back to VESA.  So I restored my old xorg file, and now everything paints a little slower and paints from the bottom up instead of the top down!  How's that for screwing things up? :)

So, at any rate, I now have learned that the old fglrx driver with radeon support doesn't work for me.  Which leads to my next question:

Nothing currently shows in restricted drivers.  So, short of a re-install (I do have quite a bit of stuff to back up and right now can't afford any blank CDs to put it on), what would I have to do to enable the restricted driver?  Currently my xorg.conf is back to "ATI", but I'm familiar with changing xorg.  I would also assume there is a xserver-xorg-ATI file hanging around out there as well.

Any help would be appreciated!  Thanks for the help so far!

Dave :)

---

### Post by markbuntu on 2008-09-25
No restricted driver for that card so give it up. You can use the ati driver or the Radeon driver, both are open source.  You should have them both installed already by default. xserver-xorg-ati or xserver-xorg-radeon. You can use either one but I would suggest getting the latest stable release from radeon.org as it is a vast improvement over the one in the repos.

---

### Post by anewguy on 2008-09-25
I found another link from a Yahoo! search that had additional parameters to put in with the device in xorg.conf.  Did all that, still have the same problems but a little improved - it at least goes all the way through even though it is still like watching a slide show with all kinds of frames dropped.

xserver-xorg-radeon is not in the repositories according to Synaptic.  I am back at the ATI driver in xorg.conf with the tweaking parameters.  I have one more thing I can try, then I think I'm out of luck.  I have been unable to find open source radeon driver in a Yahoo! search, so I guess I'm stuck with what I have.  Not to mention, from the reading I've done, the ATI driver supplied in Ubuntu is supposed to know your card type and run the appropriate driver - in my case the radeon with full 3D and full acceleration.  I'm guessing that it isn't going to work, and with everything else I ****LOVE**** with Ubuntu, and Linux in general, this is a tough pill to swallow. I'm expecting to get a nice new computer in the next month or two if things work out, and I know it will come with Vista which is a requirement for the part time work from home job I'll be getting.  I guess I'll just leave it all Vista (and I can't tell you how much I **HATE** having to use it for the part time job) and leave Ubuntu on this old antique and go from there.

If I do stumble upon something that actually works, I'll post back.

Thanks, everyone!

Dave :)

---

### Post by anewguy on 2008-09-30
Guess what??  I get to mark this as SOLVED!!  The solution for my problem was to install the opera browser and use it.  The videos play fine right in it.  I for one have noticed a TERRIBLE slow-down in Firefox since the 3.0.2 and then 3.0.3 updates - it's extremely slow.  Opera is VERY fast!!

Dave :D

---

### Post by crjackson on 2008-09-30
> **anewguy said:**
> Guess what??  I get to mark this as SOLVED!!  The solution for my problem was to install the opera browser and use it.  The videos play fine right in it.  I for one have noticed a TERRIBLE slow-down in Firefox since the 3.0.2 and then 3.0.3 updates - it's extremely slow.  Opera is VERY fast!!

Dave :D

I'm glad you got this working to your satisfaction, but it's a shame that the answer is dumping firefox. This dosn't say much for them. Anyway, if you're good with it that's all that matters at the end of the day. :)

---

### Post by anewguy on 2008-09-30
> **crjackson said:**
> I'm glad you got this working to your satisfaction, but it's a shame that the answer is dumping firefox. This dosn't say much for them. Anyway, if you're good with it that's all that matters at the end of the day. :)


Thanks for your help on this, also!  

Dave :D

---

### Post by anewguy on 2008-10-06
Okay, I got this working with Firefox.  I was looking at the "hidden" menu entries under right-click applications/edit menus, and noticed 2 entries for mplayer - one was just plain mplayer and the other said mplayer (gstreamer).  So I thought I wonder how I know which Firefox is looking at, knowing that I needed the gstreamer mode.  Well, couldn't find an entry in the Firefox preferences that said anything other than just plain mplayer.  So, I changed the wmv entry by point to /usr/bin/mplayer and now it works.  I really don't understand why - maybe it's a difference in paths or something, and it bugs me that I don't understand why, but hey - it works!

Dave :)

---

