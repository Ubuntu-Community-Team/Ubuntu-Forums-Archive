---
title: "oneiric daily builds out"
date: 2011-05-24
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by cpatrick08 on 2011-05-24
the oeirirc daily builds are out for 32 bit, 64 mac, and power5 at [http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)

---

### Post by cpatrick08 on 2011-05-24
> **cpatrick08 said:**
> the oeirirc daily builds are out for 32 bit, 64 mac, and power5 at [http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)

i would not install it from the daily build i would wait till June 2 to get alpha 1 when you login you just get a blue screen

---

### Post by dext on 2011-05-25
> **cpatrick08 said:**
> i would not install it from the daily build i would wait till June 2 to get alpha 1 when you login you just get a blue screen

you sure you werent using Windows? :p

---

### Post by meborc on 2011-05-25
time to fire up virtualbox at work and flash the laptop at home :D

---

### Post by kansasnoob on 2011-05-25
> **meborc said:**
> time to fire up virtualbox at work and flash the laptop at home :D

I was just going to say about the same thing. I generally use testdrive w/VB before I start burning discs.

But I renamed a Natty final and I'm using zsync now to bring it up to date, it was 49% complete :)

Also makes me think ............ I haven't even tried VirtualBox in Natty yet, I guess I'll soon find out what kind of a host a narwhal is :lolflag:

---

### Post by cpatrick08 on 2011-05-25
> **kansasnoob said:**
> I was just going to say about the same thing. I generally use testdrive w/VB before I start burning discs.

But I renamed a Natty final and I'm using zsync now to bring it up to date, it was 49% complete :)

Also makes me think ............ I haven't even tried VirtualBox in Natty yet, I guess I'll soon find out what kind of a host a narwhal is :lolflag:
i did not burn a disk i used a usb drive

---

### Post by jerrylamos on 2011-05-25
> **dext said:**
> you sure you werent using Windows? :p

Ocelot daily build USB boots to blue screen with cursor.

Ctrl-Alt-F1 gets usual command line.  Then try:

sudo service gdm restart

same blue screen.
used to work on Natty daily builds sometimes.

Right mouse button does not get a menu.

Dead On Arrival...

Jerry

p.s. This is Natty.  Runs Unity 3D fine but I run Unity 2D mostly.

---

### Post by williejones on 2011-05-25
> **jerrylamos said:**
> Ocelot daily build USB boots to blue screen with cursor.

Ctrl-Alt-F1 gets usual command line.  Then try:

sudo service gdm restart

same blue screen.
used to work on Natty daily builds sometimes.

Right mouse button does not get a menu.

Dead On Arrival...

Jerry

p.s. This is Natty.  Runs Unity 3D fine but I run Unity 2D mostly.

Jerry since you can get to a TTY, sudo apt-get update, sudo apt-get upgrade.  My system was booting to a blue screen yesterday.  This is what I did today and it has fixed it.

---

### Post by mc4man on 2011-05-26
you can boot up to the daily-live/current, use it and  likely install from, though no good reason atm other than a curiosity. (didn't try an install - the installer is in the Desktop folder though not visible on the desktop and shows up in the unity launcher

The fallback is to some semi-functional gnome2-panel, the unity login on the live session (nvidia/mesa 3d) is nothing different than natty other than a lack of a usable desktop (the ~/Desktop folder is usable

Of more interest here was how nautilus 3 has no 'use a custom command' available from the context menu or in Fm > Media, though it will add the .desktop(s) if one creates

The live cd's should be  more interesting down the road a bit

---

### Post by An Sanct on 2011-05-26
I get a blue screen with nautilus v3 (something) after I close it, I see a few menu items, amongst them is System, which has "Install Ubuntu 11.10" somewhere. This also crashes :}

ps. This result was produced in VirtualBox, 64b host, 64b guest

---

### Post by jerrylamos on 2011-05-26
> **williejones said:**
> Jerry since you can get to a TTY, sudo apt-get update, sudo apt-get upgrade.  My system was booting to a blue screen yesterday.  This is what I did today and it has fixed it.

williejones,

It worked.  I checked daily build with zsync, and my copy of .iso was current.  

Blue screen on boot.

I did 
sudo dhclient
sudo apt-get update
sudo apt-get upgrade
sudo service gdm stop
sudo service gdm start

and it did indeed get some kind of Unity, and Firefox even worked.

Now I'm booting from a Partition-Live, let's see if it will install to a USB hard drive....

Thanks, Jerry

---

### Post by jerrylamos on 2011-05-26
Running sort of from daily build plus sudo apt-get update and sudo apt-get upgrade on a .iso image which is mounted in a disk partition:

DISTRIB_DESCRIPTION="Ubuntu oneiric (development branch)"
Linux USBHD2 2.6.39-3-generic #9-Ubuntu SMP Sat May 21 10:22:23 UTC 2011 i686 i686 i386 GNU/Linux

The daily build booted to blue screen and cursor.  
Ctrl-Alt-F1 got a command line.
As suggested above, did sudo apt-get update and sudo apt-get upgrade.  Not sure why the daily build is so far back level.
sudo service gdm restart
did get a somewhat usable desktop.

Installed on a usb hard drive as sdc6.  Do note I forgot to see where it was going to put grub which went onto sda.  Oops.

Coupe reboots with various other partitions finally got grub on sda back to pointing to Narwhal, and grub on sdc pointed to sdc6 Ocelot.

Note!  Grub on Ocelot is deadly slow, really really slow on install and really slow after installed.

Now I expect breakage any time as more Ocelot updates hit me...

Now do remember I volunteered for this...

Jerry

---

### Post by VMC on 2011-05-26
The desktop amd64 iso is now also available, as of May26th.

---

### Post by kansasnoob on 2011-05-26
I just tried todays image in VirtualBox and it's basically the same as what I'm running from the toolchain/upload so I think the (oversized) iso at least works.

Remember this will be an Alpha 1 :)

I consider that equivalent to a rough draft of a finished manuscript. IMHO they seem to be coming into this with every intent to provide a decent experience for everyone - maybe not by default, but with only a few minor tweaks.

I've been reading a lot of the conversations at Ayatana regarding Unity and I'm close to having a personal plan .................. maybe :rolleyes:

I think my success rate at Ayatana is about 50% so I need to get my proposal right before trying :cool:

---

### Post by Quadunit404 on 2011-05-26
Just installed the latest Live CD to a VM in VirtualBox. I got Unity working through installing the Guest Additions. Just about as smooth as Unity on my actual hardware :D

This is what I have noticed so far:

- Cannot change panel colors, or window control borders for that matter, so therefore I'm stuck with an ugly Windows 2000ish theme :|
- GNOME 3 apps (e.g. Nautilus, Totem, File Roller) do not use the Global Menu.
- Unless you change the wallpaper, Unity is buggier than Windows Me, and until now I didn't think it was possible to get buggier than that AWFUL pile of s... I think I'll stop there :oops:
- Ships with GNOME 2.32 for some reason. I thought that Oneiric is supposed to be the big Unity G3 rewrite (the not-as-big season 2 of rewriting Unity) not one of the few remaining G2 distros.

Gonna try out [s]Unity[/s] *Ubuntu* 2D on this VM now.

---

### Post by silex89 on 2011-05-26
Nice! thanks for the info :D, time to give it a try

---

### Post by Quadunit404 on 2011-05-26
Oh yeah... one last observation.

Apparently none of the default software changes have been made yet. Deja Dup has not yet replaced Computer [s]Breaker[/s] Janitor and PiTiVi is still installed by default. I'm guessing these changes won't be made until Alpha 1.

---

### Post by VMC on 2011-05-27
Surprisingly, todays daily build (05/27/2011), I was able to boot to the default 2d unity desktop. 
Later today I plan to install on one of my spare partitions. This is the earliest that I have been able to get a desktop. Usually its after the first alpha. I wanted to see how the 2d unity worked anyway, since I didn't try any of the 2d stuff on natty.

---

### Post by An Sanct on 2011-05-27
Where can I download that version, that boots normally?

I mean - there are no torrent links ... this kinda sux for people with a bad internet connection.

PS. I have a 6mbit down/1Mbit up link, that goes down to 64kbit down for no apparent reason, if I use anything, but port 80 (and other limitations...) - and I cannot do anything about it...

PS2. Also - This is a know ISSUE ... I HAVE to use Windows XP (and above) and a piece of AV software, that my ISP sells, or else the link goes down to extreme minimum ... for anybody from Slovenia, here is the link to a story, that I am telling .... The ['Who knows about "advanced viruses" and telemach' - story]("http://mojmikro.si/center/v_precepu/telemach_napredni_virusi_in_windows_xp").

---

### Post by kansasnoob on 2011-05-27
> **An Sanct said:**
> Where can I download that version, that boots normally?

I mean - there are no torrent links ... this kinda sux for people with a bad internet connection.

PS. I have a 6mbit down/1Mbit up link, that goes down to 64kbit down for no apparent reason, if I use anything, but port 80 (and other limitations...) - and I cannot do anything about it...

PS2. Also - This is a know ISSUE ... I HAVE to use Windows XP (and above) and a piece of AV software, that my ISP sells, or else the link goes down to extreme minimum ... for anybody from Slovenia, here is the link to a story, that I am telling .... The ['Who knows about "advanced viruses" and telemach' - story]("http://mojmikro.si/center/v_precepu/telemach_napredni_virusi_in_windows_xp").

Have you ever tried zsync? If you look at the DL page:

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

You'll see the whateverversion.iso.zsync images also.

I started out with a Natty final image and renamed it, the name of the existing image must match the name of the image you're going to download, eg; oneiric-desktop-amd64.iso.

For example, when I zsynced the first Oneiric image I started with a Natty final image and just renamed it and zsync found it was 49% complete.

After renaming the existing image using zsync is very easy, just install the package 'zsync'. Then open a terminal and if the image is in /home just type zsync, space, and on that DL page locate the proper "iso.zsync" link, right click, and select Copy link location, then back in terminal just right click and select paste.

If the image is in a different directory then you must "cd" to that directory in terminal before running zsync. I made some more complete notes here:

[http://ubuntuforums.org/showpost.php?p=10483784&postcount=21](http://ubuntuforums.org/showpost.php?p=10483784&postcount=21)

Zsync is great at repairing damaged or incomplete images too :D

---

### Post by PaulW2U on 2011-05-28
Today's **Kubuntu** build from [http://cdimage.ubuntu.com/kubuntu/daily-live/current/](http://cdimage.ubuntu.com/kubuntu/daily-live/current/) is running well, posting with it now in fact. Seems faster than Natty on this old PC of mine. The fonts that many of us seemed to have problems with also seem to have improved with Oneiric.

---

### Post by VMC on 2011-05-28
> **PaulW2U said:**
> Today's **Kubuntu** build from [http://cdimage.ubuntu.com/kubuntu/daily-live/current/](http://cdimage.ubuntu.com/kubuntu/daily-live/current/) is running well, posting with it now in fact. Seems faster than Natty on this old PC of mine. The fonts that many of us seemed to have problems with also seem to have improved with Oneiric.

May28th daily-live works well also. No Ubuntu yet, but Kubuntu boots fast on a Try basis. 

Its still using KDE 4.6. Hopefully it will switch to 4.7 during the release cycle. I've read some info on devboot and it was inconclusive.

---

### Post by An Sanct on 2011-05-30
> **kansasnoob said:**
> Have you ever tried zsync? If you look at the DL page:
...
Zsync is great at repairing damaged or incomplete images too :D

No I didn't try zsync until now, its great! I did notice the ".zsync" files, but didn't know what to think of them, so I didn't poke them.

Wow :) every day something new. Thanx!

---

### Post by novatillasku on 2011-05-30
Daily builds .iso don't work for me.I try Usb and DVD too but only a blue screen show me ;-)

---

### Post by PaulW2U on 2011-05-30
> **VMC said:**
> Its still using KDE 4.6. Hopefully it will switch to 4.7 during the release cycle.
I'm sure it won't be too long. Meanwhile it looks like we'll be starting the alpha phase with KDE 4.6.3 which seems to be filtering through in bits and pieces today.

---

### Post by tlcstat on 2011-05-30
Greetings, I'm using Oneiric full install on this B120 Dell in Unity 2D with no problems. But yesterday (May 29) I tried to install the daily May 29 Oneiric on my Toshiba L305 and the install aborted in the middle of the software install. It gave me a list of options to manually finish the install. I chose to install the grub boot loader and finished the installation. The install would not boot. I know that all I have to do is wait this out and it will be fixed but anyone have the same experience? I am full installing, not upgrading.
Just checking.
Tlcstat

---

### Post by kansasnoob on 2011-05-30
So far I've only tested using VirtualBox. I'm waiting for the official iso-testing build to burn a disc.

I'm penny pinching so I can get a decent router and a KVM switch :D

Being able to use two boxes at once will be great come iso-testing time, and I'm also going to add a Roku box.

---

### Post by rtalcott on 2011-05-30
Today's build = Blue Screen for me in vbox....any ideas on how to fix this?
rt

---

### Post by tlcstat on 2011-05-30
Greetings,
Hey kansasnoob! Thats a lot of beans for a noob! I can hot swap my HD in my Toshiba in less than 30 sec, so no problem testing here. Also, I can get new 500Gig SATA HD's on Amazon.com for 50 bucks. No sense going the poor route for that kind of money. You can also get a SATA usb adapter for 2 bucks if you want to plug-in you extra to a usb port.
FYI
tlcstat

Greetings,
Well! I just got my daily (May 30) to install on my usb 160Gig drive. 
1. Remove all existing partitions from the drive. 
2. Remove resident/local hard drive from computer. 
3. Boot from the Oneiric DVD
4. When the install gets to the partitioning menu choose "Guided". It will install a Swap Partition and a the remainder as a root/Boot partition. The May 27 disc gave the option to multipartition as boot, root, var, usr, home. but that is gone for now, so don't bother with the manual partition, it will abort in the middle anyway. 
5. If the installation boots to a black screen. Just reboot and it should come up. 
tlcstat

---

### Post by PaulW2U on 2011-05-30
I thought I would see how Unity is coming along now that I seem to have migrated to Kubuntu for the time being. Booting directly from an ISO of today's build (30th May) on the hard-drive seems to be working fine. I have to set the wallpaper manually as the desktop seems to be blue by default and a few crash notifications appear just once shortly after the desktop has been displayed but not bad for a pre-alpha. It seemed quite stable for the 30 minutes or so that I was using it. I'm posting with it now. :D

---

### Post by tlcstat on 2011-05-30
Greetings,
I have been running a full install since May 27th with Unity 2D. Software that I have functioning properly is. 
1. Moneydance
2. Nero4 Linux (used gdebi to install). 
3. Claws Mail with plug-ins. 
4. Kompozer
5. Medibuntu
6. DVD95

All of the default installed programs seem to be working properly. 

My problems seem to revolve around the updating process and support for Unity 3D. I also don't like the bookmarks display that I am getting in Firefox. 

Thing is, it is working so well that I think I will just go with it for the duration. I always have my Natty on a different HD to fall back on. 
tlcstat

---

### Post by JRV on 2011-05-30
> **cpatrick08 said:**
> i would not install it from the daily build i would wait till June 2 to get alpha 1 when you login you just get a blue screen

Once you install a wallpaper it works.

---

### Post by mdurham on 2011-05-30
> **JRV said:**
> Once you install a wallpaper it works.

Yes, but how do I install it from a blue screen?
Cheers, Mike

---

### Post by JRV on 2011-05-30
The only way I found was to login in Classic Gnome.

---

### Post by mdurham on 2011-05-30
> **JRV said:**
> The only way I found was to login in Classic Gnome.

Sorry, what I meant was, how do you install to hdd from a blue screen on a live usb?
Cheers, Mike

---

### Post by jerrylamos on 2011-05-30
> **mdurham said:**
> Sorry, what I meant was, how do you install to hdd from a blue screen on a live usb?
Cheers, Mike
What I had to do from a blue screen with cursor, from memory:
Ctrl-Alt-F1
sudo apt-get update
sudo apt-get upgrade
sudo service gdm restart

Now this is going to take a while since the daily builds are behind.  

Anyway that got me a desktop where I could choose install.

Do use the latest daily build you can get from:
[http://cdimage.ubuntu.com/cdimage/daily-live/current/](http://cdimage.ubuntu.com/cdimage/daily-live/current/)

Once you have a daily build, you can update it like so:

zsync [http://cdimage.ubuntu.com/daily-live/current/oneiric-desktop-i386.iso.zsync](http://cdimage.ubuntu.com/daily-live/current/oneiric-desktop-i386.iso.zsync)

Now this early software breaks crash often (!).  Back up everything.  I always install to an additional partition so hopefully there is something to boot when Ocelot won't.  The reason I attempt to run this early software is to learn about linux and find bugs for the developers.

Good luck...

Jerry

---

### Post by VMC on 2011-05-30
Regarding the Blue screens everone is seeing. I also get it it I leave the "man + keyboard" keep going (see my avatar :) ), but if you hit return when you see the "man", then Try Ubuntu will get you to a desktop - at least it has for me.

---

### Post by mdurham on 2011-05-31
Thanks jerrylamos and VMC I'll give those ideas a try.
Cheers, Mike

---

