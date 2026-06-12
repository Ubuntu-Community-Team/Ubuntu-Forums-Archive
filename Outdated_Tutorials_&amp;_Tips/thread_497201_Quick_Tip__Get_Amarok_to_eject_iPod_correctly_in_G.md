---
title: "Quick Tip:  Get Amarok to eject iPod correctly in Gnome"
date: 2007-07-10
forum: Outdated Tutorials &amp; Tips
---

### Post by martinw89 on 2007-07-10
This is just a quick tip to get Amarok to correctly eject the iPod in Gnome, specifically Amarok 1.4.5 in Ubuntu Feisty with a 5th gen iPod.  Files in earlier/later iPods might be in a different location.  However the eject command will still work.  Because Amarok was designed in KDE, it has a few quirks that don't agree with Gnome users.  But this should clear anything up.  Go to the device settings for your iPod by going to "Settings -> Configure Amarok -> Media Devices".  Then click on the wrench and hammer to go into the settings.  There will be a "post-disconnect command" box.  Erase anything there and copy-paste the following command in that box:```
rm %m/iPod_Control/iTunes/iTunesLock;rm "%m/iPod_Control/iTunes/Play Counts";gnome-eject -t -d %d
```
The first two "rm" commands are there just in case Amarok does something incorrectly; I believe it automatically removes the iTunesLock file but hey it can't hurt to remove it twice :)  The second file is a database of all the songs you've played, if you don't remove this file these songs will be added to statistics multiple times.  Again, Amarok might remove this file but it can't hurt.  

The final command, "gnome-eject -t -d %d" is the juicy part.  The "-t" means text only, it allows it to just be a background command.  The "-d %d" means that gnome-eject will use the device "%d", which in Amarok's case means where the iPod is located.  When you right click on a device in Gnome and click "eject" this is essentially what happens.  This command allows you to remove a device without having root permissions, aka we don't need to type "sudo".  If we had to use "sudo" in this string of commands it would not work because we would have no where to type our password.

On a side note, click "Synchronize with Amarok statistics" to have Amarok submit all of the songs you've played on your iPod to last.fm, if you use the service.  Otherwise they will only be added to the Amarok statistics, which can still be useful.  Amarok also does a good job of syncing audio, including syncing album art.  I've heard that Amarok does a really good job on Podcasts as well, so really Amarok can be a full "headquarters" for your iPod!

Thanks for looking, I hope this helps :)

---

### Post by reclusivemonkey on 2007-07-11
I will try this when I get home, thanks for the tip! =]

---

### Post by midjunkie on 2007-07-21
Works like a charm, thanks!!

---

### Post by martinw89 on 2007-07-22
No problem, thanks for trying it out :)

---

### Post by benx009 on 2007-07-22
good tip:)

---

### Post by Darko Beta on 2007-07-26
Great tip!  I have been wrestling with this for a while...

---

### Post by soxs on 2007-08-14
*THUMBS UP*
It just works!

Thx very much!

---

### Post by barkej on 2007-10-17
Worked great for me.

---

### Post by Zorael on 2007-10-17
Does anyone know the KDE equavilent of the last command? (gnome-eject -t -d %d)

---

### Post by soxs on 2007-10-17
if you have a fresh install of amarok simply have alook at the *after eject command*. This should be the standard kde eject term.

---

### Post by rohan! on 2007-10-17
hmm :( still doesn't work for me.

---

### Post by get$ on 2007-10-17
Thanks so much! This has been bugging me for months.

---

### Post by jupetsu on 2007-10-21
Worked for me. Thanks man.:)

---

### Post by itmanvn on 2007-11-23
tried and then my Ipod Nano 8G Gen3 say: No Music :(

---

### Post by soxs on 2007-11-23
Maybe you have to compile from source as nano 3g is quite new..
Err.. I read about in the FAQ at the amarok homepage but I don't remember that much.. so its best to have ook yourself

---

### Post by DreamerHxC on 2008-02-25
Thanks for the tip, very useful, though Amarok takes like 5 minutes to disconnect the iPod, why could it be?

EDIT: Great, now it works very good; it was slow because Amarok didn't select my iPod model properly.

---

### Post by asnd16 on 2008-03-25
sweet thanx!

---

### Post by Kiri on 2008-03-26
Didn't work for me :(
Same error on disconnect

---

### Post by soxs on 2008-03-27
Gutsy works fine, but hardy some how gots messed up in this respect... really odd.

---

### Post by abhiroopb on 2008-03-29
Didn't work for me get the same error, any ideas guys?

---

### Post by soxs on 2008-03-29
I found several iPod regressions on launchpad:
Plx test and confirm/add info
[https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/139226](https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/139226)
[https://bugs.launchpad.net/ubuntu/+bug/206537](https://bugs.launchpad.net/ubuntu/+bug/206537)
[https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/164682](https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/164682)

---

### Post by dunkyp on 2008-04-30
The way to get amarok to do this properly is to delete your amarokrc file and let it rebuild your database when you connect the ipod again amarok will spot it as /dev/<whatever> and from there you just set the plugin to apple ipod and hey presto that works. to eject the ipod just change the disconnect command to gnome-eject -d %d. and if you want your ipod to automont simply add mount %d to the mount command :D

---

### Post by soxs on 2008-05-01
> **dunkyp said:**
> The way to get amarok to do this properly is to delete your amarokrc file and let it rebuild your database when you connect the ipod again amarok will spot it as /dev/<whatever> and from there you just set the plugin to apple ipod and hey presto that works.
Good to know, thx.
> **dunkyp said:**
> to eject the ipod just change the disconnect command to gnome-eject -d %d. and if you want your ipod to automont simply add mount %d to the mount command :D
Wrong, the command you see in post #1 is best, as it will protect your iPod and yourself from getting bothered everytime you connect again, because of a remaining lock-file from last disconnect, which will happen when you disconnect your iPod too soon.

---

### Post by abhiroopb on 2008-05-13
I have a 80gb black classic. and am using amarok 1.4.9.1

I edited the code to do the following:

rm "media/ABHIROOP'S/iPod_Control/iTunes/iTunesLock";eject -t -d %d

Few things to note:

I tried various methods of ejecting, connecting/disconnecting and this is what would happen (from another thread of mine):

> 
So I finally managed to get amarok configured properly to use the iPod.

1. used this guide here to set it up so that my 80gb black classic iPod can be used ([http://ohioloco.ubuntuforums.org/sho...d.php?t=658523](http://ohioloco.ubuntuforums.org/sho...d.php?t=658523)).

2. I can connect it on amarok, I transfer music and then I update the artwork.

3. When I click disconnect (my post disconnect command is umount %d && eject %d - found it on amarok website I think) it disconnects and I can see the iPod ejecting.

4. I can browse my music without any issue including seeing the artwork.

PROBLEM:

5. When I plug the iPod back into the computer, nothing happens, absoloutely nothing.

6. Checking fdisk -l, I can see where the iPod is, and I mount it manually, I then have to delete the iPod_Control folder (actually I only have to delete the iTunes folder, but the database gets screwed up so it makes sense to delete everything), unmount the iPod and then do a hard eject (as I can't see any other way to eject the iPod properly).

7. Connect it to amarok and it connects fine, asks if I want initialize the database (as I have obviously deleted it).


This problem ONLY seems to occur if I actually add songs to the iPod. If I were to connect the iPod and then disconnect it (without adding any songs), upon reconnection it would appear fine.

This is obviously VERY annoying, as it means I can add songs once, and then have to delete everything in order to add it again!!!

Help please!


I tried your disconnect command but I found the following errors for my version of amarok and iPod:

1. doing rm %m/iPod_Control/iTunes/iTunesLock did not work for me, and I had to specify the complete path (as you see from above).

2. I removed the play counts as statistics weren't that important for me.

3. IN this version of amarok/iPod, "eject" works rather than gnome-eject.

Still the iPod does not fully eject as I have to manually eject it from the mounted devices. However, at least now I can reconnect it again (which as you can see was a problem before).

Thanks a lot! The main problem was the iTunesLock file I guess which amarok wasn't removing properly!

---

### Post by abhiroopb on 2008-05-13
It worked and now it doesn't work again! AAAAAH! Help!

---

### Post by soxs on 2008-05-14
> **abhiroopb said:**
> 
1. doing rm %m/iPod_Control/iTunes/iTunesLock did not work for me, and I had to specify the complete path (as you see from above).

This implies that your iPod was not detcted properly. Remove all detected devices and autodetect them manually.

Note: Mounting by label helped me a lot, so your iPod gets mounted at one and the same mountpoint all the time (this *may* be part of your problem). See: [http://ubuntu.wordpress.com/2006/03/01/editing-fat32-partition-labels-using-mtools/](http://ubuntu.wordpress.com/2006/03/01/editing-fat32-partition-labels-using-mtools/) 

> **abhiroopb said:**
> 
3. IN this version of amarok/iPod, "eject" works rather than gnome-eject.

gnome-eject had a bug


> **abhiroopb said:**
> 
Thanks a lot! The main problem was the iTunesLock file I guess which amarok wasn't removing properly!
Thats the reason, you should use the eject command from post #1. It will remove any garbage Lock files after ejecting the iPod.

Note: _NEVER_ use anything uggly like " ' " in a device name!!

Btw. what ubuntu version do you use?

EDIT: link updated

---

### Post by abhiroopb on 2008-05-14
Firstly I think it worked last night, not too sure what happened but yes I believe it worked. Will do a more thorough test later today.

1. You're link was broken, also could you explain more clearly what you mean? In any case it works the way I did it so at this point I'm inclined not to change it, unless there is a good reason for doing so.

2. gnome-eject: yes I guess it did, because all I had to do was change this! Is there a difference?

3. Of course the command works great, a few things in the intial post it says that amarok automatically removes the lock file? I assume it did this for older iPods. Also my iPod is HIGHLY tempremental, I have only JUST started to use this eject command but my iPod has worked reasonably well for a long time now! So I don't know where the bug is exactly.

4. About the "'" are you saying I shouldn't use this around the removal of lock file? I assumed it would be OK since you used it to remove the play counts, also I had an apostrophe (ABHIROOP'S) in my name.

---

### Post by abhiroopb on 2008-05-15
UPDATE: Again connected it and nothing showed up. So I manually deleted the play counts file (just to do something!), the lock file was not in the folder (so presumably it has been deleted). 

Reconnected and still nothing. Doesn't show up at all!!

This is very frustrating, and I can't figure out whats going on! Any thoughts/help would be great

---

### Post by abhiroopb on 2008-05-15
UPDATE 2: Went into iPod_Control/Device/SysInfo

And I added a "0x" in front of the 16 characters of FirewireGuid.

Connected fine, lets see if it lasts!

---

### Post by abhiroopb on 2008-05-15
UPDATE 3: LAST FIX DID NOT WORK

Unplugged, plugged into a different port and it worked fine. However, this does not always work....so it just seems random when it works and when it doesn't.

---

### Post by soxs on 2008-05-15
Plx edit your posts and show that you updated it. (aka *update*)

So the correct link: [http://ubuntu.wordpress.com/2006/03/01/editing-fat32-partition-labels-using-mtools/](http://ubuntu.wordpress.com/2006/03/01/editing-fat32-partition-labels-using-mtools/)

This will make sure your ipod gets mounted at ```
/media/IPODNAME
``` where IPODNAME will be defined as label for the second partition via mtools (see link). This ensures a constant mountpoint for your ipod which helped me personally _A_ _LOT_ (in fact I had the same random fuss as you)

Edit#0:Never use " ' " in device names! (nor any other garbage charcters)

Edit#1: do own a firewire ipod?

Edit#2: Similar thread: [http://ubuntuforums.org/showthread.php?t=695027&page=2](http://ubuntuforums.org/showthread.php?t=695027&page=2)

---

### Post by abhiroopb on 2008-05-15
1. Thanks changed my iPod name to simply: iPod

I actually had this guide at hand: [https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

Quite good as it has various filesystems.

Anyway it changed successfully.

However, the problem still exists. Sometimes the iPod is detected and sometimes it is not. NO idea why. I've tried so many different solutions now! :p

Its a USB iPod 6g 80gb black classic

---

### Post by abhiroopb on 2008-05-15
dmesg command:

This is where NOTHING happens:

```

[10609.836000] usb 5-6: new high speed USB device using ehci_hcd and address 16
[10609.972000] usb 5-6: configuration #1 chosen from 2 choices
[10609.980000] scsi18 : SCSI emulation for USB Mass Storage devices
[10609.980000] usb-storage: device found at 16
[10609.980000] usb-storage: waiting for device to settle before scanning
[10614.980000] usb-storage: device scan complete
[10614.984000] scsi 18:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[10615.000000] sd 18:0:0:0: [sde] Spinning up disk....ready
[10618.176000] sd 18:0:0:0: [sde] 19488471 4096-byte hardware sectors (79825 MB)
[10618.176000] sd 18:0:0:0: [sde] Write Protect is off
[10618.176000] sd 18:0:0:0: [sde] Mode Sense: 68 00 00 08
[10618.176000] sd 18:0:0:0: [sde] Assuming drive cache: write through
[10618.176000] sd 18:0:0:0: [sde] 19488471 4096-byte hardware sectors (79825 MB)
[10618.180000] sd 18:0:0:0: [sde] Write Protect is off
[10618.180000] sd 18:0:0:0: [sde] Mode Sense: 68 00 00 08
[10618.180000] sd 18:0:0:0: [sde] Assuming drive cache: write through
[10618.180000]  sde: sde1
[10618.216000] sd 18:0:0:0: [sde] Attached SCSI removable disk
[10618.216000] sd 18:0:0:0: Attached scsi generic sg5 type 0
[10627.432000] usb 5-6: USB disconnect, address 16

```

I plug it in, nothing happens, so after a bit I just pull the plug out.

This is where it was correctly recognised and mounted to (/media/iPod)
```

[11085.280000] usb 5-6: new high speed USB device using ehci_hcd and address 20
[11085.412000] usb 5-6: configuration #1 chosen from 2 choices
[11085.420000] scsi22 : SCSI emulation for USB Mass Storage devices
[11085.420000] usb-storage: device found at 20
[11085.420000] usb-storage: waiting for device to settle before scanning
[11090.420000] usb-storage: device scan complete
[11090.424000] scsi 22:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[11090.444000] sd 22:0:0:0: [sde] Spinning up disk....ready
[11092.896000] sd 22:0:0:0: [sde] 19488471 4096-byte hardware sectors (79825 MB)
[11092.896000] sd 22:0:0:0: [sde] Write Protect is off
[11092.896000] sd 22:0:0:0: [sde] Mode Sense: 68 00 00 08
[11092.896000] sd 22:0:0:0: [sde] Assuming drive cache: write through
[11092.896000] sd 22:0:0:0: [sde] 19488471 4096-byte hardware sectors (79825 MB)
[11092.896000] sd 22:0:0:0: [sde] Write Protect is off
[11092.896000] sd 22:0:0:0: [sde] Mode Sense: 68 00 00 08
[11092.896000] sd 22:0:0:0: [sde] Assuming drive cache: write through
[11092.900000]  sde: sde1
[11092.928000] sd 22:0:0:0: [sde] Attached SCSI removable disk
[11092.928000] sd 22:0:0:0: Attached scsi generic sg5 type 0

```

Whats strange is that it seemed to work AFTER I'd played a couple of songs on the iPod.

So, when I made changes (in this case I guess to the play counts on the iPod) something got detected on my computer.


**UPDATE: **

This solution works (but I would ideally not want to have to use this):

1. Create a directory to mount to: sudo mkdir /media/iPod
2. Let GEdit open the file fstab: sudo gedit /etc/fstab
3. Add at the bottom: /dev/sde1 /media/iPod vfat nosuid,noauto,nodev,rw,umask=077,gid=1000,uid=1000,user,defaults,noatime,iocharset=utf8 0 0

(found this in a very old guide of how to set up you're iPod).

4. In Amarok add a device: set the mount point to /media/iPod

Now it connects/transfers everything fine.

However, the "unmounted" iPod is always present in the file tree (even when nothing is actually plugged in). Otherwise this seems to work fine.

---

### Post by soxs on 2008-05-15
Does your ipod mount always when you plug it to your PC?
If not, then it is an usb-driver/kernel related issue.

One last option would be to completely purge amarok via
```
sudo apt-get remove --purge amarok
``` and afterwards open a termnial and paste ```
rm -Rvf /home/YOUR_USER_NAME/.kde/share/apps/amarok
``` **[COLOR="DarkRed"]Caution![/COLOR]** **[COLOR="DarkGreen"]You will lose all your playcounts aswell covers and the whole amarok database must be rebuild[/COLOR]**, but it might fix your issue.

---

### Post by abhiroopb on 2008-05-15
When you say "mount" do you mean that after I plug it in can I immideately see it in nautilus and can I access it in amarok, or do you mean that can I (after plugging in) mount it manually. 

I can ALWAYS mount it manually (and after putting it in fstab it simply means clicking on mount). And if I do fdisk -l it always appears there.

What it isn't doing is mounting automatically after plugging in.

I frequently clean out my amarok folder in any case so I don't think that that is a problem.

---

### Post by soxs on 2008-05-15
I mean if you plug it that you can accesss it via nautilus and ```
mount
``` shows you where it is mounted. No matter what amarok does.

Do not mount it by hand. this will not help at all (in order to fix the problem)! It must be mounted automatically.

Go to your media folder and delete any iPod* folders. they are garbage (unplug you iPod first, added an eject comand for security to make sure ipod content does not get purged). ```
sudo eject /media/IPOD_LABEL; sleep 5; sudo rm -vf /media/IPOD_LABEL*
```

Do _NOT_ put a line into /etc/fstab, this will defnitly NOT help! If you have one, remove it. Reboot.

The unplug/plug your iPod again

---

### Post by abhiroopb on 2008-05-15
Like I said I cannot access it at all (however, it appears in lsusb, and I can use mount to mount it manually). I've resigned myself to doing it by hand until I can figure out how to do it automatically.

---

### Post by soxs on 2008-05-15
Start another thread and ask there why usb device does not mount.
I am clueless atm.

Standardly it is supposed to automount your ipod. Does automount for any other device? If not, you will have to install hal.

---

### Post by abhiroopb on 2008-05-15
Apologies but I think this was a hal issue as I tried my usb stick and that did not work. (feeling a little foolish right now!). Hopefully thats the end of that.

---

### Post by cpetercarter on 2008-05-16
I have a 2GB nano, and am running Hardy on my computer. I have found that the command at #1 successfully disconnects the iPod from Amarok, if I replace "gnome-eject" with "eject". To be on the safe side, I also right-click on the iPod icon on the desktop and then on "eject" before removing the iPod.

---

### Post by soxs on 2008-05-16
Why replace gnom-eject with eject? Gnome-eject does a clean job, the bug is fixed, which causes an error on eject. Why do you prefer eject? Does gnome-eject not work in your case?

---

### Post by cpetercarter on 2008-05-16
Because "gnome-eject" doesn't work on my system. I get the error message that Amarok has not been able to run the disconnect commands. With "eject" I get the message that Amarok has successfully disconnected the iPod.

---

### Post by soxs on 2008-05-17
That's really strange.

---

### Post by abhiroopb on 2008-05-17
I get the error with gnome-eject, so I used eject. Whats the difference anyway? In fact amarok recommends eject.

---

### Post by smellydog on 2008-05-17
I had to use eject instead of the gnome-eject too.

---

### Post by ioeth on 2008-06-16
I can confirm that I'm seeing the same behavior.  I'm running Hardy Heron with Amarok 1.4.9.1 (Using KDE 3.5.9) under Gnome, and using the "gnome-eject" command from post #1 always presents the "Post-disconnect comand failed..." error.  Changing it from "gnome-eject" to "eject" seems to fix the problem, though.  Now if I could only figure out how to get it to unmount at the same time...

---

### Post by abhiroopb on 2008-06-17
Don't worry about unmounting. I find its overall safer to use the built-in gnome unmount command.

---

### Post by itsbradman on 2008-07-27
funny thing here with hardy.  finally got amarok launching automatically when I connect my ipod, which is great.  when I use the eject command, it successfully disconnects from the ipod without unmounting it, which is fine.  the funny part is that it also ejects my dvd drive :lolflag:

---

### Post by Ralph L on 2008-10-02
On my gnome hardy system with the post disconnect command of "eject %d" the dvd drive is ejected upon disconnect.  

I also have a partition on which I loaded gnome and then, using synaptic, loaded the KDE desktop.  Under that system "echo "<your password>" | sudo -S eject -m %d" originally ejected the ipod correctly.  However, I reloaded amarok and now eject on this system also ejects the dvd drive, not the ipod.  I can't figure it out.  Just a note:  Originally under gnome/kde I had to use the sudo command with eject.  Now eject works without sudo but ejects the wrong thing.

If anybody solves this be sure to post it.

Ralph

---

### Post by YTIBFLIG on 2008-11-12
Sorry, do you know why with my ipod (shuffle 2nd generation) this command doesn't work (with amarok 1.4)???:confused::confused:

Thanks a lot....:KS

---

### Post by anomnomnomaly on 2008-11-30
I'm having trouble getting Amarok to eject my 160gb black iPod Classic. Everything worked perfectly in Ubuntu 8.04, but I just did a fresh install of Ubuntu Studio 8.10 and things are a little tricky. 

Luckily, without having to do anything except Add Device (in Settings --> Configure Amarok --> Media Devices) and specify the mount point, etc. of the iPod and click Connect, I was able to successfully mount and transfer songs to my iPod. I just can't get it to eject properly. 

I can eject it just fine by opening a terminal and typing "gnome-eject -t -d /dev/sdc1" but using the post-disconnect command "gnome-eject -t -d %d" gives me a "post-disconnect command failed" popup. Curiously, I even got the same result by using "gnome-eject -t -d /dev/sdc1" as my post-disconnect command, which works in terminal!

I've tried some other post-disconnect commands with no success. I don't think I even have the kdeeject command, but I'd like to try it since I think it ejects from the mount point instead of /dev/whatever. Anyone know how I would go about installing kdeeject? I can't find the package in Synaptic, but maybe it's called something else or it's in a repository I don't have listed.

Any help would be much appreciated.

(also, this is my first post here -- hi! :D)

---

### Post by mattack on 2008-12-04
Here's what works for me:
```
umount %m && eject /dev/sdc2
```
For some reason using %d or %m for the eject command didn't work. To determine the dev, I used ```
gnome-eject --display-settings -p /media/IPOD
``` Substitute /media/IPOD with your iPod's mount point.

---

### Post by clconway on 2009-01-30
```
gnome-eject -n -p /media/IPOD
``` works for me. Thanks.

---

### Post by brianfinley on 2009-02-05
Thanks!  Worked for me, but I had to modify it slightly.  I had to use the full path to gnome-eject "/usr/bin/gnome-eject" on Intrepid.

-Brian

---

### Post by PsyWolf on 2009-05-02
i'm running amarok 1.4 on jaunty (had to add a repository to do it)  the only command that completely ejected the ipod for me was 

```
gnome-mount -t --eject --device /dev/sdc2
```

you may have to edit the /dev/sdc2 to point to the correct place

---

