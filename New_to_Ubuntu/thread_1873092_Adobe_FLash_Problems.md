---
title: "Adobe FLash Problems"
date: 2011-10-31
forum: New to Ubuntu
---

### Post by Malt Frisky on 2011-10-31
Hi there

I'm doing an update on this post but I've had problems with flash for awhile now.

I've tried downloading flash-aid and adobe 10 from Ubuntu software centre.

When I've played videos I've had crashes, screen freezes and video freezes.

This normally occurs when I'm selecting another video or selecting a particular part of the video when the screen freezes though the audio is still working fine.

I have no idea if it's the settings or if it's just adobe in general.

Jonny

---

### Post by oldsoundguy on 2011-10-31
What is your set up?  Processor/Memory and video set up?  Those are big factors.

---

### Post by Malt Frisky on 2011-10-31
Okay, my system settings are

Memory: 2.0GiB
Processor: Intel Core 2 Duo CPU T7500 @ 2.20GHz x 2
Graphics: GeForce 8600 GS/PCI/SSE2
OS Type: 32 Bit
Disk: 293GB

On VLC everything is fine, I can play HD films, move them back and forth and everything is fine.

It's only using something with flash that things go wrong.  I've had this problem for awhile now but it's been getting worse as time's gone on.

---

### Post by Sef on 2011-10-31
Have you tried to install flash from the repositories?

---

### Post by anewguy on 2011-10-31
I have an open post (it says solved, but the problems returned) regarding flash as well, so I'll be keeping an eye on this one and let you know if a solution is found for my problem in case it is helpful for yours.

Dave ;)

---

### Post by Malt Frisky on 2011-11-01
@ Sef: How do I go about installing it from the  repositories?

@ Dave: That would be brilliant.  The problem just seems to be getting worse with me at the stage were I can't even stop a video and go to another one without forcing to shut down.

---

### Post by DapperMe17 on 2011-11-02
If you are using Firefox, simply install an add-on called "flash-aid"...it provides an easy quick wizard to install the latest "beta" version of Flash. 

Once you run it, terminal will open and follow the on-screen directions to install the best version of Flash, as well as remove any old versions that may conflict. 

Easy solution & good luck!
:popcorn:

---

### Post by rushikesh988 on 2011-11-02
> **Malt Frisky said:**
> Hi there

I'm doing an update on this post but I've had problems with flash for awhile now.

I've tried downloading flash-aid and adobe 10 from Ubuntu software centre.

When I've played videos I've had crashes, screen freezes and video freezes.

This normally occurs when I'm selecting another video or selecting a particular part of the video when the screen freezes though the audio is still working fine.

I have no idea if it's the settings or if it's just adobe in general.

Jonny
why don't you try to install flash player from adobe's website


or simple install other plugins like swf player ..firefox finds it but you will have to remove adobe flash plugin first..

---

### Post by LowSky on 2011-11-02
delete all copies of the libflashplayer.so from your pc

then download the newest version directly from adobes website.
download the version that says "Flash Player 11 for other Linux (.tar.gz)" 32 or 64 bit depending on your Ubuntu version. 

then open the file and extract it to 

/home/*username*/.mozilla/plugins/

*note change username to your user's name. you may also need to create the plugins folder.

---

### Post by beew on 2011-11-02
> **rushikesh988 said:**
> why don't you try to install flash player from adobe's website


or simple install other plugins like swf player ..firefox finds it but you will have to remove adobe flash plugin first..

Because you then have to update it manually and OP may have other versions of flash installed due to trial and errors.
@OP 

Use flash-aid.

---

### Post by Malt Frisky on 2011-11-02
> **LowSky said:**
> delete all copies of the libflashplayer.so from your pc

then download the newest version directly from adobes website.
download the version that says "Flash Player 11 for other Linux (.tar.gz)" 32 or 64 bit depending on your Ubuntu version. 

then open the file and extract it to 

/home/*username*/.mozilla/plugins/

*note change username to your user's name. you may also need to create the plugins folder.

I've managed to get to the extract part on home/username/ but can't find file with mozilla plugins?  Do I have to create this as a file?

Not fully versed in Linux command lines yet ](*,)

---

### Post by xaegis on 2011-11-02
I was having a similar issue today. I solved it by disabling the multiple copies of  "Shockwave Flash" I had installed on my computer by going to:***  Tools>Add-ons>Plugins*** In the Firefox Top/context bar.

HTH

---

### Post by Malt Frisky on 2011-11-02
> **xaegis said:**
> I was having a similar issue today. I solved it by disabling the multiple copies of  "Shockwave Flash" I had installed on my computer by going to:***  Tools>Add-ons>Plugins*** In the Firefox Top/context bar.

HTH

I tried this, there was only the one in my extensions and if I disabled that videos don't work.  I have removed Flash Aid and left Adobe 11 in, but still having the same problems.

Do you skip your video forward?  In my case the audio still runs but the screen freezes.

---

### Post by Malt Frisky on 2011-11-02
As a side note I'll mention my plug ins I've currently got running within Firefox if that helps.

Gnome Shell Integration
IcedTea-Web Plugin
iTunes Application Detector
Shockwave Flash
Xine Plugin

---

### Post by TunaCanTommy on 2011-11-02
I've been experiencing similar problems.

I'm on a AMD64 installation of 11.10, my graphics card is an older AGP GeForce with the nvidia-current driver from the repos.

I used flash-aid to install the latest version of flash . . . but flash still kept crashing.  What fixed it for me was to un-tick the option in the flash-aid script that offered 'hardware-acceleration' (vdpau).

Been stable since then.

---

