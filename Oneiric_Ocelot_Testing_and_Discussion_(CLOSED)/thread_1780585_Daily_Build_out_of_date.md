---
title: "Daily Build out of date?"
date: 2011-06-12
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by jerrylamos on 2011-06-12
It's 12 June now, daily build says 10 June but crucial Lightdm  is way older than that??

To run 10 June build Live I have to boot in recovery mode, do a huge fat update before I can get Oneiric & Lightdm to run without crashing.  As it is on the download, Lightdm crashes then crashreport says it cannot file a report because lightdm is out of date.

More of a bother is 10 June wireless is busted with this netbook so I have to hunt down a wired connection, boot in recovery mode, big fat update in persistent mode.  Then I can get wireless up.

Now I'm used to daily builds stopping a couple days before a release, but Alpha 2 is way out at 30 June??

Since 10 June daily build was down level on 10 June to start with, and getting way more behind as days go by, updating the Live is getting pretty massive.

"Ankle biter."  Can someone take mercy on us testers and put out an up-to-date daily build?

Jerry

---

### Post by jocko on 2011-06-12
> **jerrylamos said:**
> "Ankle biter."  Can someone take mercy on us testers and put out an up-to-date daily build?

Jerry
The daily builds are built automatically, probably following a set schedule, so there is nothing anyone will do to make a new daily build. It will be built and uploaded to the servers when it is scheduled to happen...
Perhaps it is not set to be built on weekends?
Or perhaps some change in the avaliable packages in the repos have prevented it from being built, in which case someone will need to make some change in the cd build process, which will probably not happen during a weekend...

---

### Post by stoneguy on 2011-06-12
After loading up with Alpha1 on June 2, I decided to set things aside for a while and pick up later with a heap of upgrades. However, seeing as how you can't get a consistent apt update today nor a current daily, I'd guess things are a bit borked.

while (builddate != today())
     sleep;

---

### Post by fjgaude on 2011-06-12
> **stoneguy said:**
> After loading up with Alpha1 on June 2, I decided to set things aside for a while and pick up later with a heap of upgrades. However, seeing as how you can't get a consistent apt update today nor a current daily, I'd guess things are a bit borked.

while (builddate != today())
     sleep;

You can say that again! Borked!

---

### Post by jerrylamos on 2011-06-12
Finally got there with quite a bit of a thrash.  
10 June daily build lightdm so down level crash couldn't even file a report.  
Wireless wouldn't work nohow.
With Live and 1 GB persistent did update & upgrade on 11 June.
Wireless now working.
On 12 June did another update, massive, I'm surprised it fit on the persistent.
Installed on USB hard drive specifying USB hard drive for 
Grub.  It is first in the boot order for my setup.
On booting the USB hard drive Grub said file not found, so booted the installed hard drive and updated & installed grub on the USB hard drive.
Booted, no wireless "The system network servcies are not compatible with this version".
Unplugged internet from desktop in the next room, with a very long cable got internet up.
Did yet another update & upgrade on the install mind I'd already done an update upgrade on the Live that did the install
Finally, wireless running....typically, Alpha updates bork me sooner or later, so bring on tomorrow's updates..
I much prefer looking for bugs using an up-to-date daily build live, one heck of a lot faster than all the thrash preceding.

Jerry

---

### Post by jerrylamos on 2011-06-13
13 June and daily build still stuck at 10 June with a lightdm that was already downlevel at 10 June,

?

Are the developers interested in us testers helping find bugs? Apparently not?

Jerry

---

### Post by ronacc on 2011-06-13
didn't the daily's "stall" for about a week during maverick ?I'm sure they'll get going again .

---

### Post by kansasnoob on 2011-06-13
It's not uncommon to have daily builds stall from time to time. Just be patient :)

---

### Post by jerrylamos on 2011-06-13
> **kansasnoob said:**
> It's not uncommon to have daily builds stall from time to time. Just be patient :)

If I can take a 10 June daily build, update the Live to 12 June and get it running, so could "they".  Pretty hard to shoehorn all those updates into a Live but it worked.  It even did an install usual thrashing around to get going, updated to 13 June and running.

10 June lightdm crashes and crash report says it is too far downlevel to even report on.
10 June doesn't do wireless on this pc.

12 June updates lightdm hasn't crashed
12 June updates wireless works, although I had to used wired to do the updates.

I'd be more sympathetic if 10 June daily build wasn't DOA for me.

Jerry

---

### Post by coffeecat on 2011-06-13
Newer daily lives are beginning to filter through. A 13th June i386 desktop ISO is there but not yet an amd64 which is still 10th June at the time of posting. Looking  in the i386 manifest reveals what the delay **may** have been about. It comes with the 3.0.0 kernel which only appeared in routine updates a few hours ago. Possibly  they delayed the dailies until the new version of the kernel was ready.

---

### Post by cariboo on 2011-06-13
The Live CD build system was changed over the weekend, so that may be why there weren't any new images:

> I've moved Ubuntu's live filesystem build process over from our original
custom shell script in livecd-rootfs to the newer live-build system from
Debian (formerly called live-helper).  Thanks in particular to Daniel
Baumann for guidance and for speedy upstream patch integration, and to
LaMont Jones for deployment assistance.

This only affects Oneiric and later releases.  Live filesystem builds
for previous releases will continue to use livecd-rootfs.

Developers who have not needed to modify livecd-rootfs in the past
should have no more need to modify it now than before; it still uses
tasks in much the same way to decide which packages should be installed.
However, people working on Ubuntu live filesystems will need to know how
the new build process is laid out.  I needed to have somewhere to put
configuration anyway, so I repurposed the livecd-rootfs package for
that, using auto/* files along the lines of
[http://live.debian.net/manual/en/html/managing-a-configuration.html](http://live.debian.net/manual/en/html/managing-a-configuration.html).  I
expect that the exact details may change here as we gain more experience
with live-build.  Briefly, the current way to reproduce an Ubuntu live
filesystem build is to do this in a scratch directory:

  Once only:
    $ mkdir -p auto
    $ ln -sf /usr/share/livecd-rootfs/live-build/auto/* auto/

  Each time:
    $ export PROJECT=ubuntu SUITE=oneiric ARCH=i386
    $ sudo lb clean
    $ lb config
    $ sudo lb build

There were a handful of changes in ubiquity 2.7.6 to cope with slight
differences in manifest files and sources.list generation.  These only
make a difference if you're producing installable live CDs.

If you are modifying the live build process for Ubuntu, please remember
that we are now working with an upstream codebase: the days of hacking a
couple of special-purpose lines into livecd-rootfs are over.  While we
do have three outstanding patches against upstream right now, they have
all been submitted as Debian bug reports (if it's any guide, there were
seven outstanding when I started drafting this mail!), and my goal is,
if at all possible, to be using an unpatched version of live-build from
Debian by the time we release Oneiric.  Instead of perpetrating
Ubuntu-specific hacks, please consider these alternatives:

 * live-build has lots and lots of options, and in many cases you can do
   what you need by tweaking those.

 * Patch live-build to do what you need, send your patch as a Debian
   bug, and engage in upstream discussion if necessary.  Note that, if
   need be, you can guard your code with [ "${LB_MODE}" = ubuntu ].

 * If necessary, there are various hook script facilities that you can
   use: for example, scripts in config/chroot_local-hooks/ are run in
   the chroot near the end of the chroot build process.  Try to keep
   this to a minimum, though; I'm trying to avoid using hook scripts in
   builds for Ubuntu proper, as it would be better for live-build to do
   the right thing out of the box without the need for hooks.  Right
   now, the only hook script I'm using is one to remove icon-theme.cache
   from Kubuntu images.

If you have any questions about the Ubuntu integration here, please ask.

Cheers,

-- Colin Watson 

---

### Post by jerrylamos on 2011-06-13
Thanks, Cariboo, I just saw the new builds.  I'll give the standard desktop a whirl.
This is from a 10 June updated install, updated, and is working.  On a USB hard drive hopefully avoiding Grub fumbles.

Jerry

---

### Post by jerrylamos on 2011-06-13
13 June 32 bit Live up and running here, wired internet.

I'll try wireless tomorrow on my netbook.

Famous last word, no crashes yet....

Jerry

---

### Post by arpanaut on 2011-06-13
> **cariboo907 said:**
> The Live CD build system was changed over the weekend, so that may be why there weren't any new images:

That, the newest kernel, and 45% new files: Yup might have taken some time to get that ready...

Thanks to all that work  to bring us fresh images.

---

### Post by jerrylamos on 2011-06-14
14 June daily build live up and running.  It's 3.0-0-generic 32 bit.

Attempt to connect to wireless and nm applet disappears.

In terminal sudo ifconfig wlan0 crashes lightdm

sudo service lightdm stop, sudo service lightdm start

log in again, with BFB select Network, connect to wireless O.K.

Up and running.  Yes, there's a launchpad bug I'll look up the #.

Jerry

---

### Post by ranch hand on 2011-06-15
It is important to remember, too, that when update/upgrades are coming fast that the Live image may not build well enough to work.

There is no sense in putting them out if there is little chance of them working,

There are a lot of complaints about Dailies not working anyway.  No point in fueling the fire.

---

### Post by jerrylamos on 2011-06-15
> **ranch hand said:**
> It is important to remember, too, that when update/upgrades are coming fast that the Live image may not build well enough to work.

There is no sense in putting them out if there is little chance of them working,

There are a lot of complaints about Dailies not working anyway.  No point in fueling the fire.

Looks like the real answer is post #11 above.

My grumble was I could take the daily build that wouldn't work, boot in recovery, do a massive update at which point it did work but that's a really hard stretch for "live" boot.  I couldn't figure out why the developers didn't do the update for us.

Answer is they were busy doing something else, see #11 above.

FYI, daily build 14 June here running O.K. except for the usual lightdm crashes etc. etc.

Tried daily build 15 June and got black screen.  Stop & start lightdm no help.  Oh, well, zsync keeps the back level so I boot that.

Let me try booting 15 June and doing an update later today.

Daily builds back on usual track.

Jerry

---

### Post by sparker256 on 2011-06-15
> **jerrylamos said:**
> Looks like the real answer is post #11 above.

My grumble was I could take the daily build that wouldn't work, boot in recovery, do a massive update at which point it did work but that's a really hard stretch for "live" boot.  I couldn't figure out why the developers didn't do the update for us.

Answer is they were busy doing something else, see #11 above.

FYI, daily build 14 June here running O.K. except for the usual lightdm crashes etc. etc.

Tried daily build 15 June and got black screen.  Stop & start lightdm no help.  Oh, well, zsync keeps the back level so I boot that.

Let me try booting 15 June and doing an update later today.

Daily builds back on usual track.

Jerry
Made a live usb with build 15 June 32 bit and 64 bit and booted fine. What is even better is the 2d fall back worked. By default lightdm is set to ubuntu and since my system will not run unity3d without extra drivers it did a fall back automatically.  :D

Bill

---

