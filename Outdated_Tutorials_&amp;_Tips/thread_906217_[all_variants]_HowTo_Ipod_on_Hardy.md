---
title: "[all variants] HowTo Ipod on Hardy"
date: 2008-08-31
forum: Outdated Tutorials &amp; Tips
---

### Post by dentaku65 on 2008-08-31
[SIZE="2"]**Ipod Models list and status**[/SIZE]

**1st and 2nd Gen.                    **Works out of the box
**3rd Gen. 	                    **Works out of the box
**4th Gen. Greyscale 	            **Works out of the box
**4th Gen. Photo/Color 	            **Works out of the box
**Mini 1st Gen. 	                    **Works out of the box
**Mini 2nd Gen. 	                    **Works out of the box
**Nano 1st Gen. 	                    **Works out of the box
**Nano 2nd Gen. 	                    **Needs hack
**Nano 3rd Gen. 	                    **Needs hack
**5th Gen. (Video) 	            **Works out of the box
**5.5th Gen. 30 GB (Late 2006 Video)  **Works out of the box
**5.5th Gen. 80 GB (Late 2006 Video)  **Works out of the box
**6th Gen Classic 	            **Works out of the box
**Shuffle 	                    **Unknown (info needed)

[SIZE="2"]**Update your sources**[/SIZE]
Download the file [COLOR="Red"]sources.txt[/COLOR] located at the end of this topic on your desktop.

Open a terminal window and type:
```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.ORIGINAL
```
```
sudo mv ~/Desktop/sources.txt /etc/apt/sources.list
```
Then do:
```
sudo apt-get update && sudo apt-get dist-upgrade
```
(accept the updates if any)

Add now the Medibuntu (Media & Distractions) sources:
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```
You may be asked to accept this package even though it cannot be authenticated. This is normal; typing "Yes" means you trust Medibuntu.

Then do again:
```
sudo apt-get update && sudo apt-get dist-upgrade
```
(accept the updates if any)

Your sources now are complete and the system is full upgraded.

[SIZE="2"]**Hack Ipod (see your model from the list at the top)**[/SIZE]
Plug and mount (usually automounting) the ipod to your box, then do:
```
sudo lsusb -v | grep -i Serial
```
The output should be something like:
```
iSerial [COLOR="Red"]000A2700133125F5[/COLOR]
```

Edit (or create) this file on your ipod:
```
nano [COLOR="Red"]/media/IPOD[/COLOR]/iPod_Control/Device/SysInfo
```

* note: the [COLOR="Red"]/media/IPOD[/COLOR] is the default mounting point of Ipod in Ubuntu (change with yours if different)

Add to SysInfo file the following line and save the file (ctrl+x using nano):
```
FirewireGuid: 0x[COLOR="Red"]ffffffffffffffff[/COLOR]
```

* change the [COLOR="Red"]ffffffffffffffff[/COLOR] value with the value grabbed above with the lsusb (iSerial) command

Unmount the ipod (right click on Ipod icon on desktop choose: safely remove).

Good. Ipod is "hacked".

[SIZE="2"]**Install the software**[/SIZE]
```
sudo apt-get install amarok libgpod3 gtkpod-aac
```
Note: I suggest to use Amarok as audio player/ipod manager (is for KDE env but works good in Gnome too), but if you wish you can use also or instead:
- rhythmbox
- exaile
- banshee

Plug back your Ipod, now you can use it with your favourite program or, for a quick check you can try gtkpod, so in a terminal window type:
```
gtkpod
```

Enjoy you Ipod on Ubuntu Hardy.

Update 18/10/2008
6th Gen Works out of the box

Update 20/10/2008
**Quick trick for Amarok annoyance**
If you have the problem to see the Ipod under Amarok, you should follow these steps:

   1. Mount ipod
   2. Open Amarok and configure the Ipod manually under menu Options
   3. Close (quit) Amarok
   4. Umount the Ipod
   5. Mount the Ipod again
   6. Open Amarok... you should see the Ipod under devices

---

### Post by bvanaerde on 2008-09-01
For now, I'm still using iTunes on Windows for managing my music, as I'm a bit scared of using another program.

I know music playback works, but is it also possible to add files to the iPod using this HowTo?

---

### Post by dentaku65 on 2008-09-01
> **bvanaerde said:**
> For now, I'm still using iTunes on Windows for managing my music, as I'm a bit scared of using another program.

I know music playback works, but is it also possible to add files to the iPod using this HowTo?

Yes, is it possible. I'm using Amarok and it works pretty good (Ipod Nano 3rd gen silver):
- adding songs
- adding playlists
- adding/manage podcasts

And besides all these features can be used on any pc running Amarok (or any other application mentioned above), not mono-managed like Itunes

For video and pictures I'm using gtkpod (can be used for music/playst as well)

Only the updates of the firmware are not available (just possible via Itunes, at least with my Ipod)

---

### Post by bvanaerde on 2008-09-01
Thanks for the quick answer.
> **dentaku65 said:**
> Only the updates of the firmware are not available (just possible via Itunes, at least with my Ipod)
This is something I can live with. It is important though, that automatic syncing is turned off in iTunes: this way your iPod doesn't get synchronised with iTunes when trying update the firmware.

---

### Post by dentaku65 on 2008-09-01
Anyway I think Itunes is too limited as player and as manager; I just installed for the firmware update and that's it.

But I did not understood why you didn't tried Amarok or Exaile for your Ipod... there is no reason to be scared for loosing collection or configuration, the "hack" descibed in #1 (if your Ipod model needed) take care of the switch back to Itunes if one decide to do so.

---

### Post by bvanaerde on 2008-09-01
When I plugged my iPod (classic, 160GB) in, Rhythmbox automatically found it, and I could play the music that was already on it. But I couldn't find a way to copy more music onto the iPod. For some reason, it messed up the album art too (probably because I switched between Ubuntu and WindowsXP).

But that was a while ago. I'm definitely going to try it again, using this howto. I'm already using the Medibuntu repositories, so all I need to do is the little "hack" :)

---

### Post by luchop on 2008-09-07
I followed the how-to, but I can't get amarok to detect the ipod. Any ideas on how to get it working? I have an Ipod nano 2g

---

### Post by luchop on 2008-09-07
I tried to load music into the ipod through rythmbox, but after I unplug the ipod there appears nothing in it, though opening the ipod icon in the desktop shows the music folders. any idea why is this?

---

### Post by Jamie Jackson on 2008-09-07
> **dentaku65 said:**
> [SIZE="2"]**Ipod Models list and status**[/SIZE]
**Nano 3rd Gen. 	                    **Needs hack


It's a new Nano, so I guess it's 3rd Gen.
> 
Unmount the ipod (right click on Ipod icon on desktop choose: safely remove).

I don't have that option. Is "eject" equivalent?
> 
Plug back your Ipod, now you can use it with your favourite program or, for a quick check you can try gtkpod, so in a terminal window type:
```
gtkpod
```


gtkpod shows > Could not find iPod directory structure at '/media/IPOD'.
If you are sure that the iPod is properly mounted at '/media/IPOD', gtkpod can create the directory structure for you.

Do you want to create the directory structure now?

How do I answer this?

Also, blindly following your recommendation to use Amarok. Two questions about that:

[LIST=1]
[*]Amarok asks me to configure my media devices when I hit the device tab. If I try "Autodetect Devices," it comes up with nothing. If I try to manually set up: Plugin="Apple iPod Media Device", name="JamieNano", mount point="/media/IPOD", and then try to "connect" I get a blank set of Pre and Post-connect commands in a dialog box. Did I do something wrong?
[*]When I plug in the iPod, Rhythmbox opens. How do I change that to Amarok?
[/LIST]

Update: Oh, and one more thing: What do you suggest I do with my sources list after following your howto?

---

### Post by kpkeerthi on 2008-09-08
I just tried SongBird. I was stumped by the way it handled my iPod. If you are having trouble syncing file to you iPod, give Songbord a try. Its by far the best I have used so far in linux. The sync wizard resembles that of iTunes's.

---

### Post by dentaku65 on 2008-09-10
> **Jamie Jackson said:**
> It's a new Nano, so I guess it's 3rd Gen.

I don't have that option. Is "eject" equivalent?

gtkpod shows 

How do I answer this?

Also, blindly following your recommendation to use Amarok. Two questions about that:

[LIST=1]
[*]Amarok asks me to configure my media devices when I hit the device tab. If I try "Autodetect Devices," it comes up with nothing. If I try to manually set up: Plugin="Apple iPod Media Device", name="JamieNano", mount point="/media/IPOD", and then try to "connect" I get a blank set of Pre and Post-connect commands in a dialog box. Did I do something wrong?
[*]When I plug in the iPod, Rhythmbox opens. How do I change that to Amarok?
[/LIST]

Update: Oh, and one more thing: What do you suggest I do with my sources list after following your howto?

Ok.
eject it is the equivalent of safely remove, maybe is different name/command in KDE (in my case) 

When you connect with the cable your IPOD is the IPOD automounted? You can see on the desktop as icon if you choose to mount it from the pop-up window (like open in nautilus)... if so you can see where your IPOD is mounted /media/<something> (usually /media/IPOD)... from what you post about gtkpod it seems that you launched the apps without IPOD connected.

For Amarok, did you tried to configure it manually? Try to configure it manually under Configure amarok -> Media devices -> Add device...
Choose Apple ipod media device and choose your mounting point (/media/IPOD)

If you get blank situation on Amarok and that error on gtkpod means: your IPOD is not mounted.

You can switch back your original source.list doing:
```
sudo rm /etc/apt/sources.list 
```
```
sudo cp /etc/apt/sources.list.ORIGINAL /etc/apt/sources.list
```
```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by Jamie Jackson on 2008-09-10
> **dentaku65 said:**
> Ok.
eject it is the equivalent of safely remove, maybe is different name/command in KDE (in my case) 

When you connect with the cable your IPOD is the IPOD automounted? You can see on the desktop as icon if you choose to mount it from the pop-up window (like open in nautilus)... if so you can see where your IPOD is mounted /media/<something> (usually /media/IPOD)... from what you post about gtkpod it seems that you launched the apps without IPOD connected.


Yes, the iPod is automounted, and a shortcut shows on the desktop. Further, Rythmbox opens automatically when it's plugged in. The mount point is /media/IPOD
> 

For Amarok, did you tried to configure it manually? Try to configure it manually under Configure amarok -> Media devices -> Add device...
Choose Apple ipod media device and choose your mounting point (/media/IPOD)

I have tried to configure Amarok manually. (I'm pasting from my original post.)
[INDENT]Amarok asks me to configure my media devices when I hit the device tab. If I try "Autodetect Devices," it comes up with nothing. If I try to manually set up: Plugin="Apple iPod Media Device", name="JamieNano", mount point="/media/IPOD", and then try to "connect" I get a blank set of Pre and Post-connect commands in a dialog box. Did I do something wrong?[/INDENT]
> 
If you get blank situation on Amarok and that error on gtkpod means: your IPOD is not mounted.

I don't think that's the case. I know that the iPod is mounted, as I can browse its contents, etc. Further, I was able to write the file to it, as described in the hack in the post that starts this thread.

I can try it all again, but I'm not hopeful that my results will be any different.

By the way, might I have to sync it with iTunes to format the iPod? This is a brand new iPod, and it's never been connected to a Windows box.

---

### Post by dentaku65 on 2008-09-11
> **Jamie Jackson said:**
> Yes, the iPod is automounted, and a shortcut shows on the desktop. Further, Rythmbox opens automatically when it's plugged in. The mount point is /media/IPOD

I have tried to configure Amarok manually. (I'm pasting from my original post.)
[INDENT]Amarok asks me to configure my media devices when I hit the device tab. If I try "Autodetect Devices," it comes up with nothing. If I try to manually set up: Plugin="Apple iPod Media Device", name="JamieNano", mount point="/media/IPOD", and then try to "connect" I get a blank set of Pre and Post-connect commands in a dialog box. Did I do something wrong?[/INDENT]

I don't think that's the case. I know that the iPod is mounted, as I can browse its contents, etc. Further, I was able to write the file to it, as described in the hack in the post that starts this thread.

I can try it all again, but I'm not hopeful that my results will be any different.

By the way, might I have to sync it with iTunes to format the iPod? This is a brand new iPod, and it's never been connected to a Windows box.

Ok.
Try in this way: do the operation manually in Amarok once, then exit Amarok, then umount and mount again the Ipod, then reopen Amarok, the Ipod should be listed in the device section.

I used only Itunes for upgrading the firmware; I'm pretty sure that synch Ipod with Itunes is wrong or it's not needed at all. I have the same Ipod model and I never used Itunes as manager.

---

### Post by timbosity on 2008-09-11
just a question here. Does ipod have to be configured in windows? can a mac configured ipod be used in way described?

---

### Post by dentaku65 on 2008-09-11
> **timbosity said:**
> just a question here. Does ipod have to be configured in windows? can a mac configured ipod be used in way described?
I did not understand very well your question.
In win and/or mac you can use Itunes and so you don't need to make any tricks; beside that if you are in wir or mac and you don't want to use Itunes but other software (Yamipod for example) simply I don't know.

---

### Post by hcaleman on 2008-09-12
Thanks for this Howto, finally managed to get my 6g Classic working (which has been frustrating me for a week).  

However, I can only get it to work in GTKpod.  Amarok is still not able to see or control my ipod.  The error I'm receiving in amarok is I need to have the dbus and HAL daemon running.  Any idea where I'm going wrong on that one?

---

### Post by Jamie Jackson on 2008-09-12
> **dentaku65 said:**
> Ok.
Try in this way: do the operation manually in Amarok once, then exit Amarok, then umount and mount again the Ipod, then reopen Amarok, the Ipod should be listed in the device section.

I used only Itunes for upgrading the firmware; I'm pretty sure that synch Ipod with Itunes is wrong or it's not needed at all. I have the same Ipod model and I never used Itunes as manager.

That worked, thanks.

---

### Post by anotherdisciple on 2008-09-12
To all of you who are using iTunes.... have you tried banshee yet? I tried the latest version of banshee... it worked flawlessly! I was very surprised.

---

### Post by dentaku65 on 2008-09-12
> **hcaleman said:**
> Thanks for this Howto, finally managed to get my 6g Classic working (which has been frustrating me for a week).  

However, I can only get it to work in GTKpod.  Amarok is still not able to see or control my ipod.  The error I'm receiving in amarok is I need to have the dbus and HAL daemon running.  Any idea where I'm going wrong on that one?

We discussed above about the trick to manage the ipod under Amarok, briefly:
[I]
Try in this way: do the operation manually in Amarok once, then exit Amarok, then umount and mount again the Ipod, then reopen Amarok, the Ipod should be listed in the device section.[/I]

---

### Post by hcaleman on 2008-09-12
Yes, have done the manual operation in amarok, but still get a No media device found error.  It's just a mild annoyance since I'm going back and forth between two apps to do the job of 1.

At least I have something for the time being though with gtkpod running.

---

### Post by dentaku65 on 2008-09-12
> **hcaleman said:**
> Yes, have done the manual operation in amarok, but still get a No media device found error.  It's just a mild annoyance since I'm going back and forth between two apps to do the job of 1.

At least I have something for the time being though with gtkpod running.

Can you post what you see under Device in Amarok options?
I know that Amarok seems that cannot autodiscover the device but if you configure the ipod manually, exit Amarok, umount and mount again ipod and reopen Amarok, the Ipod should be there.

---

### Post by ztirffritz on 2008-09-12
> **timbosity said:**
> just a question here. Does ipod have to be configured in windows? can a mac configured ipod be used in way described?

The iPod must be formatted as a FAT device.  On a Mac they are formatted as HFS+ I believe.  You'll be able to read an HFS+ iPod, but not write to it.  If you connect it to a Windows machine and restore the iPod using iTunes for Windows it will change the format to FAT, then you can use Linux to read AND write the files.  This is frustrating to me because if you want to update the iPod when new firmware is released you must use Windows to do it.  I only have Windows at work, so I can't update my iPod.

---

### Post by dentaku65 on 2008-09-13
> **ztirffritz said:**
> The iPod must be formatted as a FAT device.  On a Mac they are formatted as HFS+ I believe.  You'll be able to read an HFS+ iPod, but not write to it.  If you connect it to a Windows machine and restore the iPod using iTunes for Windows it will change the format to FAT, then you can use Linux to read AND write the files.  This is frustrating to me because if you want to update the iPod when new firmware is released you must use Windows to do it.  I only have Windows at work, so I can't update my iPod.

Is this true for the new gen. Ipod too?
I suspect that the latest version of them are released only in FAT with a "strange" table partition, but I'm not sure...

---

### Post by hcaleman on 2008-09-13
Tried again, removed and reinstalled the ipod manually in amarok.  Seems to pick it up now, and all working great.  Thanks again.  

Is the cover art transferring properly for your setup?  That is one thing that won't go on mine, the screen always says "12 songs" despite having a couple thousand songs on it now, no covers in coverflow.  Amarok has most of my covers though.

---

### Post by dentaku65 on 2008-09-13
> **hcaleman said:**
> Tried again, removed and reinstalled the ipod manually in amarok.  Seems to pick it up now, and all working great.  Thanks again.  

Is the cover art transferring properly for your setup?  That is one thing that won't go on mine, the screen always says "12 songs" despite having a couple thousand songs on it now, no covers in coverflow.  Amarok has most of my covers though.

It works ok here for the cover.
Did you try the icon "ipod" under the menus of Amarok? That icon have a sub-menu (there is an arrow by side) where you can choose "Update artwork"

---

### Post by hcaleman on 2008-09-14
Yep, click that one (furiously) and don't seem to get any activity.  Used cover manager and picked up all the album covers I needed from amazon, so I'm stocked on that side.  I have a feeling it will just start to work eventually like everything else did (I hope).  

Will the model number I have set in my sysinfo ModelNumStr line effect this?  I am not using the standard xb147 for the black classic, instead am using a1238 (the model number listed on the back of my ipod in small print).

edit:  Scratch that, my suspicion above was right, I went ahead and set my model number in amarok to one it recognized for the black classic, and now artwork transfer works fine.  Great, I can finally dump that remaining XP partition on my 2nd hard drive, the iPod was the only thing that had me hesitant.

---

### Post by dentaku65 on 2008-09-18
> **hcaleman said:**
> 
edit:  Scratch that, my suspicion above was right, I went ahead and set my model number in amarok to one it recognized for the black classic, and now artwork transfer works fine.  Great, I can finally dump that remaining XP partition on my 2nd hard drive, the iPod was the only thing that had me hesitant.

Good to know. Another point toward the solution of [bug nr. 1]("https://launchpad.net/ubuntu/+bug/1")
:lolflag:

---

### Post by TuneLovinJacket on 2008-09-19
I've tried all the tricks listed above and nothing is working.
I am brand new to Ubuntu 8.04

I am running Amarok 1.4.9.1
My iPod is a 80 GB 5G Video
In the devices tab it say IPod (mounted at /media/ipod)
When I click Connect I get : Media Device: No mounted iPod found
I cannot find the ipod mounted in the media folder, desktop or anywhere else

Tried loading gtkpod and got the following:
libgpod3 is already the newest version.
E: Couldn't find package gtkpod-aac

Can somebody help me out?

Nothing I've tried in the forums has worked yet.

---

### Post by dentaku65 on 2008-09-20
> **TuneLovinJacket said:**
> I've tried all the tricks listed above and nothing is working.
I am brand new to Ubuntu 8.04

I am running Amarok 1.4.9.1
My iPod is a 80 GB 5G Video
In the devices tab it say IPod (mounted at /media/ipod)
When I click Connect I get : Media Device: No mounted iPod found
I cannot find the ipod mounted in the media folder, desktop or anywhere else

Tried loading gtkpod and got the following:
libgpod3 is already the newest version.
E: Couldn't find package gtkpod-aac

Can somebody help me out?

Nothing I've tried in the forums has worked yet.

I don't understand if the problem is Amarok or Ipod in general.

First of all the fact that you don't find the package gtkpod-aac means that you don't have enabled the Medibuntu repositories as I mentioned on #1.

If the problem is Amarok, you should follow these steps:
[LIST=1]
[*]Mount ipod
[*]Open Amarok and configure the Ipod manually under menu Options
[*]Close (quit) Amarok
[*]Umount the Ipod
[*]Mount the Ipod again
[*]Open Amarok... you should see the Ipod under devices
[/LIST]

---

### Post by TuneLovinJacket on 2008-09-20
> **dentaku65 said:**
> I don't understand if the problem is Amarok or Ipod in general.

First of all the fact that you don't find the package gtkpod-aac means that you don't have enabled the Medibuntu repositories as I mentioned on #1.

If the problem is Amarok, you should follow these steps:
[LIST=1]
[*]Mount ipod
[*]Open Amarok and configure the Ipod manually under menu Options
[*]Close (quit) Amarok
[*]Umount the Ipod  [COLOR="Navy"]**How do I unmount it when I can't find it anywhere?**[/COLOR]
[*]Mount the Ipod again
[*]Open Amarok... you should see the Ipod under devices
[/LIST]

[COLOR="Navy"]**What I tried was shutting the computer off, that's the only way I could make the ipod stop saying "Do Not Disconnect"**[/COLOR]

[COLOR="Navy"]**I tried unsuccessfult to do this in V!$t@ before that beast destroyed my computer. I wonder if it damaged the ipod as well**[/COLOR]

---

### Post by dentaku65 on 2008-09-20
> **TuneLovinJacket said:**
> [COLOR="Navy"]**What I tried was shutting the computer off, that's the only way I could make the ipod stop saying "Do Not Disconnect"**[/COLOR]

[COLOR="Navy"]**I tried unsuccessfult to do this in V!$t@ before that beast destroyed my computer. I wonder if it damaged the ipod as well**[/COLOR]

Well... you're saying two different things: you don't know where is but if the Ipod display that is connected, means: is connected. Where? Post the output (with ipod connected) of these two commands i terminal window:
```
ls -al /media
```
```
df
```
Beside this when you attached the ipod you should see the ipod icon on desktop, to unmount right click on it and choose eject or safely remove...

---

### Post by solaris_wiz on 2008-09-23
I may just be missing something in this thread, but I'm sure I've tried most everything in here.

when I connect my iPod I get this
[IMG]http://img.photobucket.com/albums/v718/Fok_N_Gon/Screenshot-gnome-mount-1.png[/IMG]

when I try to load the ipod in gtkpod I get this
[IMG]http://img.photobucket.com/albums/v718/Fok_N_Gon/Screenshot-Warning.png[/IMG]

I can mount the ipod via command line no problems.  However when I go to save music to the device I get permission problems. as shown below.
[IMG]http://img.photobucket.com/albums/v718/Fok_N_Gon/Screenshot-Warning-1.png[/IMG]


Please advise.

Thanks,
Jimmie

---

### Post by dentaku65 on 2008-09-24
> **solaris_wiz said:**
> I may just be missing something in this thread, but I'm sure I've tried most everything in here.

when I connect my iPod I get this
[IMG]http://img.photobucket.com/albums/v718/Fok_N_Gon/Screenshot-gnome-mount-1.png[/IMG]

when I try to load the ipod in gtkpod I get this
[IMG]http://img.photobucket.com/albums/v718/Fok_N_Gon/Screenshot-Warning.png[/IMG]

I can mount the ipod via command line no problems.  However when I go to save music to the device I get permission problems. as shown below.
[IMG]http://img.photobucket.com/albums/v718/Fok_N_Gon/Screenshot-Warning-1.png[/IMG]


Please advise.

Thanks,
Jimmie

mmm, pls post the output of your fstab:
```
cat /etc/fstab
```

---

### Post by juustokissa on 2008-09-25
Has anyone tried the new nano in ubuntu? I am able to mount it and to transfer songs with amarok, but I am not able to get any coverart onto the device. Is there a player that already supports the 4th gen nano and has an as easy-to-use coverart solution as the Amarok player, or should I just wait for Amarok to start supporting it?

---

### Post by solaris_wiz on 2008-09-26
device is /dev/sdc1

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d2915ccc-c623-42b7-aa7c-d8484e37e1a4 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=23a703b3-40d9-4acb-b34f-a4026ed56934 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
b
```

---

### Post by dentaku65 on 2008-09-26
> **solaris_wiz said:**
> device is /dev/sdc1

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d2915ccc-c623-42b7-aa7c-d8484e37e1a4 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=23a703b3-40d9-4acb-b34f-a4026ed56934 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
b
```

Nothing here, correct... now with the inserted ipod post the output of this:
```
ls -al /dev/sdc1

```
From the error posted few posts ago it seems that your ipod has been owned by another user... or maybe your user has no permissions to write on external device, see also in your user manager applet.

---

### Post by dentaku65 on 2008-09-26
> **juustokissa said:**
> Has anyone tried the new nano in ubuntu? I am able to mount it and to transfer songs with amarok, but I am not able to get any coverart onto the device. Is there a player that already supports the 4th gen nano and has an as easy-to-use coverart solution as the Amarok player, or should I just wait for Amarok to start supporting it?

I really don't know, maybe Amarok cannot manage the images for 4th yet... but I suspect that the job of this is done by libgpod; I suggest to try a specific app for ipod images like tripod [http://kde-apps.org/content/show.php/Tripod?content=48484]("http://kde-apps.org/content/show.php/Tripod?content=48484")

---

### Post by solaris_wiz on 2008-09-26
> **dentaku65 said:**
> Nothing here, correct... now with the inserted ipod post the output of this:
```
ls -al /dev/sdc1

```
From the error posted few posts ago it seems that your ipod has been owned by another user... or maybe your user has no permissions to write on external device, see also in your user manager applet.

listing output
```
brw-rw---- 1 root disk 8, 33 2008-09-26 10:46 /dev/sdc1

```


forgive me, but where in the user manager would I be looking?
this is for MY account, also the account trying (to my knowledge) to access the iPod through gtkpod...and amarok.

[IMG]http://img.photobucket.com/albums/v718/Fok_N_Gon/Screenshot-AccountjimmieProperties.png[/IMG]

---

### Post by dentaku65 on 2008-09-26
> **solaris_wiz said:**
> listing output
```
brw-rw---- 1 root disk 8, 33 2008-09-26 10:46 /dev/sdc1

```


forgive me, but where in the user manager would I be looking?
this is for MY account, also the account trying (to my knowledge) to access the iPod through gtkpod...and amarok.

[IMG]http://img.photobucket.com/albums/v718/Fok_N_Gon/Screenshot-AccountjimmieProperties.png[/IMG]

I meant if you are in the group disk as listed above with ls -al result, I don't know where to see this in Gnome. Btw you can try to load gtkpod as sudo and see if you are able to retrieve data from ipod; open a terminal:
```
sudo gtkpod

```
Then try to access the ipod

---

### Post by solaris_wiz on 2008-09-27
> **dentaku65 said:**
> I meant if you are in the group disk as listed above with ls -al result, I don't know where to see this in Gnome. Btw you can try to load gtkpod as sudo and see if you are able to retrieve data from ipod; open a terminal:
```
sudo gtkpod

```
Then try to access the ipod

sudo gtkpod worked.  THANK YOU!  I've been dying without my ipod. lol.  Thank you much!!!!

---

### Post by dentaku65 on 2008-09-28
> **solaris_wiz said:**
> sudo gtkpod worked.  THANK YOU!  I've been dying without my ipod. lol.  Thank you much!!!!

I'm glad that worked.
This means that you don't have permissions on external drives with your username, check that in gnome :-)

---

### Post by juustokissa on 2008-10-02
> **dentaku65 said:**
> I really don't know, maybe Amarok cannot manage the images for 4th yet... but I suspect that the job of this is done by libgpod; I suggest to try a specific app for ipod images like tripod [http://kde-apps.org/content/show.php/Tripod?content=48484]("http://kde-apps.org/content/show.php/Tripod?content=48484")

Ok, so now I got it working partially. By adding the songs through the Amarok collection to my iPod, it also transferred the cover-art. For some reason it did not do this when I dragged-and-dropped the folders with the music directly onto the Device through Amarok, it had to be done through the Collection. One problem still remains; when I tilt the nano sideways and enter the cover-flow mode, it shows the covers. But when I turn it back up into play-mode, the cover disappears and is replaced by a note image. The same applies when I'm in the main menu, and highlight the music alternative, at the bottom of the screens it shows some weird looking images, not the covers. Any ideas on how to fix this glitch? :) Thank you dentaku for your help so far!

---

### Post by dentaku65 on 2008-10-05
> **juustokissa said:**
> Ok, so now I got it working partially. By adding the songs through the Amarok collection to my iPod, it also transferred the cover-art. For some reason it did not do this when I dragged-and-dropped the folders with the music directly onto the Device through Amarok, it had to be done through the Collection. One problem still remains; when I tilt the nano sideways and enter the cover-flow mode, it shows the covers. But when I turn it back up into play-mode, the cover disappears and is replaced by a note image. The same applies when I'm in the main menu, and highlight the music alternative, at the bottom of the screens it shows some weird looking images, not the covers. Any ideas on how to fix this glitch? :) Thank you dentaku for your help so far!

Hi,
because your model is newer one (not present on the list of post #1), I suggest to build/use libpod of svn version:
[http://www.gtkpod.org/libgpod.html]("http://www.gtkpod.org/libgpod.html")
For my experience I'm using Amarok only trough the collection (mp3/cover) and not trough drag-n-drop.

---

### Post by u18b on 2008-10-07
Hi,  I need help connecting my Nano.  I've read tutorial and tried all kinds of steps, so I'm missing something.

I'm fairly new to Ubuntu.

Here's the info:

running Hardy
Nano 2 gen 8 gig black model A1199

When I plug into a USB port, the Nano comes on and starts charging.
And I can see a song page.

But that is it.

The Nano does not mount.  No icon on the desktop or in the Nautilus file manager.

when I run DMESG, there are no lines with the word APPLE in them.

I'm stuck, any help would be appreciated.

Ohhhh.  And the Nano was not new but obtained from a friend with songs already on it.  Is this possibly the problem?  Will it have to be reset and cleared before it can automounted in Linux?  (I don't see what difference it would make).

---

### Post by dentaku65 on 2008-10-08
> **u18b said:**
> Hi,  I need help connecting my Nano.  I've read tutorial and tried all kinds of steps, so I'm missing something.

I'm fairly new to Ubuntu.

Here's the info:

running Hardy
Nano 2 gen 8 gig black model A1199

When I plug into a USB port, the Nano comes on and starts charging.
And I can see a song page.

But that is it.

The Nano does not mount.  No icon on the desktop or in the Nautilus file manager.

when I run DMESG, there are no lines with the word APPLE in them.

I'm stuck, any help would be appreciated.

Ohhhh.  And the Nano was not new but obtained from a friend with songs already on it.  Is this possibly the problem?  Will it have to be reset and cleared before it can automounted in Linux?  (I don't see what difference it would make).

I'm afraid that in this situation your Ipod is not seen under Ubuntu, first of all on the display of Ipod you must see "connected" and you shouldn't be able to see anything else on the device... btw, how do you use your Ipod? I meant on which system you are able to use it (Mac, XP....)?

---

### Post by u18b on 2008-10-08
dentaku65, Thank you for responding.

Actually, the Ipod has NOT been connected to either Mac or Windows yet (it probably was by the previous owner- but I don't know who that was).

My daughter's Mac has (I think) OS 10.3 on it and she got a message saying that she had to have at least the next version up (10.4, or something like that).

OK, well, we have not connected to XP yet, but I can.  We figured, when we did that, the used Ipod would be wiped.  Before we did that, we just thought we would try to connect to Linux first.

So is it possible that this is the problem?  Since this is a used Ipod,  do we need to connect to XP first, download Itunes, reset the Ipod, and THEN try to see if Hardy will recognise it?

Is that the plan?

Thanks for your patience with a newbie.

---

### Post by bvanaerde on 2008-10-09
u18b: Maybe it's good to upgrade the iPod firmware (if it's not already the latest version). This can be only be done with iTunes.

---

### Post by dentaku65 on 2008-10-11
> **u18b said:**
> dentaku65, Thank you for responding.

Actually, the Ipod has NOT been connected to either Mac or Windows yet (it probably was by the previous owner- but I don't know who that was).

My daughter's Mac has (I think) OS 10.3 on it and she got a message saying that she had to have at least the next version up (10.4, or something like that).

OK, well, we have not connected to XP yet, but I can.  We figured, when we did that, the used Ipod would be wiped.  Before we did that, we just thought we would try to connect to Linux first.

So is it possible that this is the problem?  Since this is a used Ipod,  do we need to connect to XP first, download Itunes, reset the Ipod, and THEN try to see if Hardy will recognise it?

Is that the plan?

Thanks for your patience with a newbie.

I think on what you post before the ipod is not seen by your system (Ubuntu) at the drive level; I suggest, if you can, to see if this ipod is seen under XP or Mac... maybe this ipod has been formatted by your friend before to give it to you, if so, you must recreate the partitions on it...

---

### Post by tictactoe on 2008-10-11
wen i pressed 

sudo lsusb -v | grep -i Serial

i got this....
  iSerial                 3 000A27001C1088BE
  iSerial                 1 0000:00:13.2
  iSerial                 1 0000:00:13.1
  iSerial                 0 
  iSerial                 1 0000:00:13.0

 i just now....4hrs ago bought an ipod shuffle 1GB...which looks like a clip.When i put the USB connection inside the port..i could just see orange light glowing..in reality it should just be plain orange,indicating tht it is getting charged.Its also not getting detected,nor mounting...tried gparted ..no use..pls help me out!!!!:confused:

---

### Post by dentaku65 on 2008-10-11
> **tictactoe said:**
> wen i pressed 

sudo lsusb -v | grep -i Serial

i got this....
  iSerial                 3 000A27001C1088BE
  iSerial                 1 0000:00:13.2
  iSerial                 1 0000:00:13.1
  iSerial                 0 
  iSerial                 1 0000:00:13.0

 i just now....4hrs ago bought an ipod shuffle 1GB...which looks like a clip.When i put the USB connection inside the port..i could just see orange light glowing..in reality it should just be plain orange,indicating tht it is getting charged.Its also not getting detected,nor mounting...tried gparted ..no use..pls help me out!!!!:confused:

Can u post the output of this command
```
dmesg |tail 
```
just right after u plug in the ipod in the usb port?

---

### Post by maxxum on 2008-10-12
This solution did not work for my 6th gen 160gb ipod. I placed the
FirewireGuid: 0x000A270015503D2C
 line in the file as you mentioned. Gtkpod transfers the files to the ipod but it plays one song and never plays any other songs after that. When you select a song and play it it shows as 'playing' but the progress bar does not go further and song is not played. Some newer encryption?

---

### Post by finite9 on 2008-10-12
what does the hack do??

I have an iPod Nano 3g silver and hardy heron 64-bit.  I have tried a bit with Rhythmbox with limited success.  Even with latest WinAMP on WindowsXP at work, it's very unstable, and my ipod constantly looses album art or crashes and refuses to play songs that 5 minutes earlier played ok.  Only complete success I have had is with iTunes.

I have firmware 1.0.2 at the moment, where 1.0.1 was the original firmware.  Will this still wotk with the hack or does your hack assume original firmware?

At the moment, I seem to be able to transfer my OGG files to the iPod and get them converted to aac or mp3 on the fly, but when I unplug the ipod they disappear.

---

### Post by finite9 on 2008-10-12
what does the hack do??

I have an iPod Nano 3g silver and hardy heron 64-bit.  I have tried a bit with Rhythmbox with limited success.  Even with latest WinAMP on WindowsXP at work, it's very unstable, and my ipod constantly looses album art or crashes and refuses to play songs that 5 minutes earlier played ok.  Only complete success I have had is with iTunes.

I have firmware 1.0.2 at the moment, where 1.0.1 was the original firmware.  Will this still wotk with the hack or does your hack assume original firmware?

At the moment, I seem to be able to transfer my OGG files to the iPod and get them converted to aac or mp3 on the fly, but when I unplug the ipod they disappear.

---

### Post by dentaku65 on 2008-10-13
> **finite9 said:**
> what does the hack do??

I have an iPod Nano 3g silver and hardy heron 64-bit.  I have tried a bit with Rhythmbox with limited success.  Even with latest WinAMP on WindowsXP at work, it's very unstable, and my ipod constantly looses album art or crashes and refuses to play songs that 5 minutes earlier played ok.  Only complete success I have had is with iTunes.

I have firmware 1.0.2 at the moment, where 1.0.1 was the original firmware.  Will this still wotk with the hack or does your hack assume original firmware?

At the moment, I seem to be able to transfer my OGG files to the iPod and get them converted to aac or mp3 on the fly, but when I unplug the ipod they disappear.

Sorry finite9, but I do not understood if you have applied the iSerial number as indicated in post #1 or not.
You have my same ipod model (silver 3rd 4gb) and it works really good here (I'm using mostly Amarok and sometimes gtkpod), I have the last firmware on my ipod placed with iTunes (I did not found other way...) 20 days ago.

---

### Post by dentaku65 on 2008-10-13
> **maxxum said:**
> This solution did not work for my 6th gen 160gb ipod. I placed the
FirewireGuid: 0x000A270015503D2C
 line in the file as you mentioned. Gtkpod transfers the files to the ipod but it plays one song and never plays any other songs after that. When you select a song and play it it shows as 'playing' but the progress bar does not go further and song is not played. Some newer encryption?

Did you update libgpod to the version of Medibuntu?
[https://bugs.launchpad.net/gutsy-backports/+bug/178926](https://bugs.launchpad.net/gutsy-backports/+bug/178926)

---

### Post by knowitman on 2008-10-16
> **dentaku65 said:**
> Did you update libgpod to the version of Medibuntu?
[https://bugs.launchpad.net/gutsy-backports/+bug/178926](https://bugs.launchpad.net/gutsy-backports/+bug/178926)

I am having the same problem with my new 120 GB Classic.  Can you please elaborate on this suggestion?

---

### Post by dentaku65 on 2008-10-17
> **knowitman said:**
> I am having the same problem with my new 120 GB Classic.  Can you please elaborate on this suggestion?

Sorry, it is very difficult to understand; can you please say at least if you did the steps on post #1?
This strange behaviour, if I'm correct, seems depending on the version of libgpod, the correct one (to me) is the one present of Medibuntu repository, or the SVN one present on gtkpod site.

---

### Post by xdeathwishx on 2008-10-17
> **dentaku65 said:**
> 
Edit (or create) this file on your ipod:
```
nano [COLOR="Red"]/media/IPOD[/COLOR]/iPod_Control/Device/SysInfo
```

I can't perform this step because the Ipod (6 gen, 80gb classic) won't mount correctly in the first place.  It seems to try and mount to sdb1, but I get the invalid option when trying to mount error.  I used to use this on my windows xp computer.

I get the same exact error when trying to mount my 300gb external hard drive.

Check out some of the output for various commands I've seen people ask for:

```

sean@sean-laptop:~$ sudo blkid
/dev/sda1: UUID="3b14f55e-49e0-4fcf-8b64-c06bc1a5ad37" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="c38fa59d-4239-456c-bbbd-190b84062f93" 
/dev/sdb1: LABEL="SEAN'S IPOD" UUID="3141-5926" TYPE="vfat" 

sean@sean-laptop:~$ dmesg |tail
[ 3617.206286] printk: 1 messages suppressed.
[ 3617.206295] wlan0: CTS protection disabled (BSSID=00:1d:7e:20:04:da)
[ 3617.962771] printk: 3 messages suppressed.
[ 3617.962780] wlan0: CTS protection disabled (BSSID=00:1d:7e:20:04:da)
[ 3619.074664] printk: 3 messages suppressed.
[ 3619.074673] wlan0: CTS protection disabled (BSSID=00:1d:7e:20:04:da)
[ 3620.617411] printk: 1 messages suppressed.
[ 3620.617421] wlan0: CTS protection enabled (BSSID=00:1d:7e:20:04:da)
[ 3620.617425] wlan0: switched to long barker preamble (BSSID=00:1d:7e:20:04:da)
[ 3621.447706] wlan0: CTS protection disabled (BSSID=00:1d:7e:20:04:da)

sean@sean-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=3b14f55e-49e0-4fcf-8b64-c06bc1a5ad37 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=c38fa59d-4239-456c-bbbd-190b84062f93 none swap sw 0 0
/dev/sdb1 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/scd0 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0

sean@sean-laptop:~$ sudo lsusb -v | grep -i Serial
  iSerial                 3 000A270015596E98
  iSerial                 1 0000:00:1d.7
  iSerial                 0 
  iSerial                 1 0000:00:1d.3
  iSerial                 1 0000:00:1d.2
  iSerial                 1 0000:00:1d.1
  iSerial                 1 0000:00:1d.0


```

There are no errors when running 
```
sudo mount -a
```

The ipod says it is connected, and it shows up in the "Places" menu.  However, if I look in the /media/sdb1 folder, there is nothing.  

Any ideas?

---

### Post by xdeathwishx on 2008-10-17
OK I got it working.  Basically all I did was
```

mkdir /media/ipod
mount /dev/sda1 /media/ipod

```
Then a box came up and asked what kind of ipod it was and all that.  I think the box originated from gtkpod, which I have installed.

If this helps anyone else, I also performed all of the steps in the first entry, up to the one where you actually hack the ipod.  Instead of doing that, I just installed some packages that have to do with ipods.  I just searched my repositories and there was one called ipod or something, I installed it and it worked fine.

---

### Post by dentaku65 on 2008-10-18
> **xdeathwishx said:**
> OK I got it working.  Basically all I did was
```

mkdir /media/ipod
mount /dev/sda1 /media/ipod

```
Then a box came up and asked what kind of ipod it was and all that.  I think the box originated from gtkpod, which I have installed.

If this helps anyone else, I also performed all of the steps in the first entry, up to the one where you actually hack the ipod.  Instead of doing that, I just installed some packages that have to do with ipods.  I just searched my repositories and there was one called ipod or something, I installed it and it worked fine.

xdeathwishx, can you confirm that your 6th gen classic ipod works out of the box and does not need the iSerial?

---

### Post by swisscow on 2008-10-18
> **dentaku65 said:**
> xdeathwishx, can you confirm that your 6th gen classic ipod works out of the box and does not need the iSerial?

Mine did. New 120GB Classic, just plugged it in.

Worked with Amarok and gtkpod

---

### Post by dentaku65 on 2008-10-18
> **swisscow said:**
> Mine did. New 120GB Classic, just plugged it in.

Worked with Amarok and gtkpod

Thx. Post #1 updated!

---

### Post by finite9 on 2008-10-18
I cannot get my ipod nano 3rd gen to work with 1.1.3 firmware.  I applied the hack, and I can transfer my albums from OGG format to ipod using Rhythmbox, but artwork does not get synced and songs will not play on ipod after ejection.

artwork in Rhythmbox is downloaded into gnome hidden folder when i play it in rhythmbox, as i do not have artwork in each album folder.  when I try to play the songs on the ipod, it just returns me to the song list.  syncing in WinAMP on XP works fine.

I have not applied your sources.list.  It seems like it just enables all the canonical repos.  I do not have partner or backports enabled.  Can you specify more exactly which software is needed rather than having to swap out my entire source.list file?  Is this why it does not work?

---

### Post by Kotjze on 2008-10-18
I have a 4th gen iPod nano, but it's not listed in the guide. I tried the guide anyway and it works and shows up in Banshee. I sync my music to it, and it says how much space is left (therefore the files are actually on it), but the iPod itself says 0 songs, but also says that a few gigabytes are used. I searched/read through the thread, but I don't think I saw a fix for this?

---

### Post by dentaku65 on 2008-10-18
> **finite9 said:**
> I cannot get my ipod nano 3rd gen to work with 1.1.3 firmware.  I applied the hack, and I can transfer my albums from OGG format to ipod using Rhythmbox, but artwork does not get synced and songs will not play on ipod after ejection.

artwork in Rhythmbox is downloaded into gnome hidden folder when i play it in rhythmbox, as i do not have artwork in each album folder.  when I try to play the songs on the ipod, it just returns me to the song list.  syncing in WinAMP on XP works fine.

I have not applied your sources.list.  It seems like it just enables all the canonical repos.  I do not have partner or backports enabled.  Can you specify more exactly which software is needed rather than having to swap out my entire source.list file?  Is this why it does not work?

Basically you need libgpod, amarok and gtkpod presents in the medibuntu repos or, for libgpod, you need to compile by yourself.

---

### Post by dentaku65 on 2008-10-18
> **Kotjze said:**
> I have a 4th gen iPod nano, but it's not listed in the guide. I tried the guide anyway and it works and shows up in Banshee. I sync my music to it, and it says how much space is left (therefore the files are actually on it), but the iPod itself says 0 songs, but also says that a few gigabytes are used. I searched/read through the thread, but I don't think I saw a fix for this?

Did you tried gtkpod?
I think that gtkpod (gtkpod-aac) is the most important app to test (and if you like it to use) for ipod.

---

### Post by Kotjze on 2008-10-18
> **dentaku65 said:**
> Did you tried gtkpod?
I think that gtkpod (gtkpod-aac) is the most important app to test (and if you like it to use) for ipod.

gtkpod works, but the album art doesn't seem to get copied, and also, the new feature on the 4th gen iPod nano "Genius" doesn't work unless I connect it to iTunes :(

---

### Post by Tarmalo on 2008-10-21
I'm having some problems as well. My Ipod is a 16GB Silver Nano. GTKpod has it in the module selection but right next to it is --->[Nano 16GB (Read Only)]
I cant delete or add any music on. I want to just Format the whole thing... I thought that might be the simplest thing to do but I cant do that either. I tried following the "hack" direction but I'm not getting anywhere. Help would be nice.

---

### Post by dentaku65 on 2008-10-22
> **Tarmalo said:**
> I'm having some problems as well. My Ipod is a 16GB Silver Nano. GTKpod has it in the module selection but right next to it is --->[Nano 16GB (Read Only)]
I cant delete or add any music on. I want to just Format the whole thing... I thought that might be the simplest thing to do but I cant do that either. I tried following the "hack" direction but I'm not getting anywhere. Help would be nice.

Have you the permissions to read/write external drives? If
```
sudo gtkpod
```
works, you dont have that permissions.

---

### Post by Ity1982 on 2008-10-22
Does anyone try this with an iPod Touch?

---

### Post by Rodney9 on 2008-11-26
sudo lsusb -v | grep -i Serial
  iSerial                 3 000A270012A66943
  iSerial                 0 
  iSerial                 1 0000:00:1d.7
  iSerial                 2 812822227722
  iSerial                 1 0000:00:1a.7
  iSerial                 1 0000:00:1d.2
  iSerial                 0 
  iSerial                 1 0000:00:1d.1
  iSerial                 1 0000:00:1d.0
  iSerial                 1 0000:00:1a.2
  iSerial                 1 0000:00:1a.1
  iSerial                 1 0000:00:1a.0

Which one should I use ?

3 000A270012A66943

or

2 812822227722

well I tried 3 000A270012A66943
then 
bash: FirewireGuid:: command not found

---

### Post by Rodney9 on 2008-11-26
> **Rodney9 said:**
> sudo lsusb -v | grep -i Serial
  iSerial                 3 000A270012A66943
  iSerial                 0 
  iSerial                 1 0000:00:1d.7
  iSerial                 2 812822227722
  iSerial                 1 0000:00:1a.7
  iSerial                 1 0000:00:1d.2
  iSerial                 0 
  iSerial                 1 0000:00:1d.1
  iSerial                 1 0000:00:1d.0
  iSerial                 1 0000:00:1a.2
  iSerial                 1 0000:00:1a.1
  iSerial                 1 0000:00:1a.0

Which one should I use ?

3 000A270012A66943

or

2 812822227722

well I tried 3 000A270012A66943
then 
bash: FirewireGuid:: command not found

I guess the is only for Hardy and will not work in Ubuntu 8.10 64bit Intrepid Ibex :confused:

Does anyone know how to get my iPod Nano 2nd or  3rd Gen working in Ubuntu 8.10 64bit Intrepid Ibex ?

Rodney.

---

### Post by erikag on 2008-12-04
Okay. Major difficulties here. I have the 4th gen Nano, and want to use amarok, but it is not registering that my ipod is there. I was using rhythmbox, and that works great, but I want to be able to make play lists, a feature not offered through rhythmbox. I am a beginner when it comes to codes, so I have been reluctant to try too many things. I have gtkpod already. So, what should I do?

---

### Post by nicklikesfire on 2008-12-09
> **erikag said:**
> Okay. Major difficulties here. I have the 4th gen Nano, and want to use amarok, but it is not registering that my ipod is there. I was using rhythmbox, and that works great, but I want to be able to make play lists, a feature not offered through rhythmbox. I am a beginner when it comes to codes, so I have been reluctant to try too many things. I have gtkpod already. So, what should I do?

My nano shows up in rythmbox, but it will not tronsfer songs onto it. Any ideas on how to fix that? Did you have to do anything to get yours to work? I'm using intrepid, with rythmbox, and a 4th generation (4g) 16 gb ipod nano.

---

### Post by nlz on 2008-12-22
1.
Is there a script/program/function which can scan (and remove) double entries on my IPOD? I know songbird can do this, but it doesn't recognize my IPOD

2.
Does anyone know how to proceed with songbird if it doesn't recognize your IPOD (even after you installed the IPOD add-on)?

3.
Has anyone got good experience with Rockbox on your Ipod? The installer doesn't recognize my Ipod automatically..

(4th generation greyscale ubuntu 8.04 hardy)

---

### Post by nlz on 2008-12-22
I didn't wait for an answer and installed rockbox manually and it's AMAZING! You can just copy files and folders into the player and organize your music like that! 

No more 'only itunes knows what's goin' on' and 'itunes messes everything up'!

(Now you can even manage your ipod from a terminal *YES* :guitar: )

---

### Post by SneakPeak on 2008-12-23
I followed these instructions for my shuffle.  I can see all the files on the iPod in Amarok and in various other file browsers but my shuffle doesn't work.  When I press play I get alternate green and orange lights indicating no songs!!!

Ahhhhhhhhh  I have been working on this for about 8 hours now and nothing!!!!!

Does anybody know how to get the shuffle working???

---

### Post by joshmuffin on 2008-12-23
If you need GUI the fusion-icon (sudo apt-get install fusion icon, or you could get it from synaptic) You can see which one, change it or reload the current one.

---

### Post by t2hot on 2009-01-03
Try Resetting your iPod, SneakPeak.

---

### Post by devehf on 2009-01-04
> **SneakPeak said:**
> 
Does anybody know how to get the shuffle working???

I first synced my daughter's shuffle on a WinXP notebook with iTunes and a few songs. Then I followed these instructions and got syncing to work with Amarok. Some notes:

1) I had to create the Device directory and SysInfo file manually. I couldn't get the nano command to work correctly in Terminal. Maybe because the name of the iPod Shuffle had a single quote (apostrophe) and a space? I tried doing a few searches on how to get control nano with special characters in an iPod name, but the text editor's application name being the same as an iPod model name made searching difficult.

Anyway, when I created the SysInfo file in Text Editor and saved it, an empty file named SysInfo~ showed up in the Device directory. I left it there. Didn't seem to bother anything.

2) In Amarok 1.4.9.1, the device connecting options are accessed under the Settings menu, Configure Amarok menu choice. Click on the Media Devices "tab". If your Shuffle is mounted you should see it listed in the Media Devices list under the main label "Configure Portable Player Support". Select the Plugin: "Apple iPod Media Device" and hit Apply. Boom, the Shuffle shows up in the Devices UI. FYI - I was able to connect with gtkpod before doing anything in Amarok. Got an error about a photo directory missing or something like that. I set the model and color in gtkpod. This setting persisted and was displayed in Amarok.

3) In Amarok, I noticed that the list of songs displayed in the Devices panel are grouped by artist. This is a little annoying because this is not the play order. iTunes lets you manage the Shuffle's playlist order and visually inspect it. This helps if you are trying to organize songs that you can navigate to with the Next track button on the Shuffle. When I added some more songs via Amarok. They were added to the end of the "playlist" so that when I ejected and played all I had to do was advance to the end of the playlist to hear the songs I just added. It would be nice to see this playlist order in Amarok. I wonder if I can do this with Amarok's Create Playlist command when you right click on the Shuffle's "Playlist" icon on the Devices panel?

4) I wanted to see what would happen if I plugged the Shuffle back into the WinXP notebook and synced. None of the Amarok added songs showed up in the iTunes playlist display for the shuffle. In fact, when I ejected from WinXP, the Amarok added songs were gone from Shuffle. Back to Ubuntu to add the new songs again.

5) When I connected back to the Ubuntu box and Connected in Amarok, there is now a new SysInfoExtended file in the Devices directory of the Shuffle. Not sure when this showed up. It looks to be an XML file with the Firewire GUID and other properties.

6) After ejecting from Amarok the first time, the Shuffle's power switch was already in the Off position. Don't know if this made a difference, but I understand this to be the position to cause a reset if left Off for 5 seconds.

7) I noticed that the speed of syncing is a lot slower than my 80GB Ipod Classic. Must be the difference between the storage media.

Hope this helps some other 3rd Gen Shuffle users out there.

---

### Post by applehead on 2009-01-29
> **SneakPeak said:**
> I followed these instructions for my shuffle.  I can see all the files on the iPod in Amarok and in various other file browsers but my shuffle doesn't work.  When I press play I get alternate green and orange lights indicating no songs!!!

Ahhhhhhhhh  I have been working on this for about 8 hours now and nothing!!!!!

Does anybody know how to get the shuffle working???

I think you need to create a playlist and drag the files there.

Also, you need to tell amarok what type of ipod it is. (the ipod button)

---

### Post by Paul Vega on 2009-03-31
I am getting the following reply to my serial no. search. The first output is with the ITouch disconnected, the second is with it connected. 

paul@paul-desktop:~$ sudo lsusb -v | grep -i Serial
  iSerial                 1 0000:00:1d.7
  iSerial                 3 00027216B9CD
  iSerial                 1 0000:00:1d.3
  iSerial                 1 0000:00:1d.2
  iSerial                 3 0016e3fc3280
  iSerial                 3 BROD7F957378
  iSerial                 1 0000:00:1d.1
  iSerial                 1 0000:00:1d.0
paul@paul-desktop:~$ sudo lsusb -v | grep -i Serial
  iSerial                 3 459625aef8a5f6835708434384941ad42d07fa34
  iSerial                 1 0000:00:1d.7
  iSerial                 3 00027216B9CD
  iSerial                 1 0000:00:1d.3
  iSerial                 1 0000:00:1d.2
  iSerial                 3 0016e3fc3280
  iSerial                 3 BROD7F957378
  iSerial                 1 0000:00:1d.1
  iSerial                 1 0000:00:1d.0

Is it possible that this is the serial no.? It looks totally unlike anything you have suggested;
iSerial                 3 459625aef8a5f6835708434384941ad42d07fa34

Paul Vega

---

### Post by Paul Vega on 2009-04-07
Has this thread finished? Is there anyone who can recommend to me a plan of action?

---

### Post by iBurger on 2009-04-07
Try to reformat the nano using windows version of itunes (may be done virtualbox puel).

Software (as of Aril 2009):
Ubuntu 8.04
Itunes 8.1.1 (windows, made folders) 
Ipod Nano (third generation, video)

---

### Post by ubunter1 on 2010-08-11
hi, thanks for the little tutorial on how to get this working, i cannot get good results yet from mine. here are the specs, hopefully someone can help me.
ipod nano video 16gb silver, when i plug it in and open up gtkpod i get this- Could not open "(null)" for reading extended info.
Extended info will not be used.
iPod Database Import Failed: 'Illegal seek to offset 0 (length 4) in file '/media/STREET ROB/iPod_Control/iTunes/iTunesDB'.'

Newly mounted iPod at '/media/STREET ROB' could not be loaded into gtkpod.

next i tried to load ipod from the gtk menu and get this- Could not find iPod directory structure at '/media/IPOD'.
If you are sure that the iPod is properly mounted at '/media/IPOD', gtkpod can create the directory structure for you.

Do you want to create the directory structure now?, i put yes then- rror initialising iPod: Problem creating iPod directory or file: '/media/IPOD/iPod_Control'.
Could not open "(null)" for reading extended info.
Extended info will not be used.
iPod Database Import Failed: 'Illegal seek to offset 0 (length 4) in file '/media/STREET ROB/iPod_Control/iTunes/iTunesDB'.

what should i do? any help would be appreciated. thanks.

---

