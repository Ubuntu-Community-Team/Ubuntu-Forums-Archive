---
title: "HOWTO: iPod Classic (6G) with Amarok"
date: 2008-05-23
forum: Outdated Tutorials &amp; Tips
---

### Post by abhiroopb on 2008-05-23
This is a guide I have put together through various other guides and my personal experience with the new black 80gb iPod Classic. This works for me so hopefully it will work for you!

[B]
NB: Going to start RIGHT at the begining, so I am assuming that you have ALL your music somewhere on your computer.[/B]

[SIZE="5"][COLOR="Red"]
**1. Cleaning out you're iPod**[/COLOR][/SIZE]

1. Connect the iPod.
2. It should appear in nautilus (if it does not, see below)
3. Browse to the iPod folder.
4. You should see the following folders: Calendars, Contacts, iPod_Control, Notes, Recordings.
6. Delete everything [COLOR="Red"]**(NB: This erases you're iPod to factory settings erasing everything, including Music, Pictures, Videos, and Contacts)**[/COLOR]
7. Eject you're iPod.
8. Wait a bit and the apple logo should appear on the iPod
9. Select you're desired language.

If you're iPod did not automount do the following:

Create a folder in the media directory:

```

sudo mkdir /media/iPod2

```

Check where the iPod is mounted:
```

sudo fdisk -l

```

When you find the iPod (it should be FAT) make a note of what it says (e.g. /dev/sdf)

then type in the following:
```

sudo mount /dev/sdf /media/iPod2

```

This should have it mounted.


[COLOR="Red"][SIZE="5"]**2. Amarok and Libgpod3:**[/SIZE][/COLOR]

From: [http://ubuntu-utah.ubuntuforums.org/showthread.php?t=658523](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=658523)
(I have condensed it with the useful bits for Amarok)

Apple have recently released a new look for their ipods, but with the new interface comes more firmware encryption to stop 3rd party media players (including Amarok, Rhythmbox and gtkpod) syncing music to the ipods.

Since there is no itunes for linux it was up to the guys at [http://ipodminusitunes.blogspot.com](http://ipodminusitunes.blogspot.com) to crack it.

This should work for any new nanos and iPod classics. Please be aware that this is rather experimental. The programs installed by this tutorial are from the hardy repository so don't be suprised if they break stuff.


Here's how to get it working (type this into terminal one line at a time, use the same terminal session for all):

First to install the latest libgpod
```

sudo -i
cp /etc/apt/sources.list /etc/apt/sources.list.tmp
echo deb http://gb.archive.ubuntu.com/ubuntu/ hardy main restricted universe multiverse >> /etc/apt/sources.list
apt-get update
aptitude install libgpod3 libgpod-common

```

Then installing amarok (NB: if you already had amarok this will overwrite everything!)
```

aptitude install amarok

```

Removing the old libgpod
```

aptitude remove libgpod2

```
(this may prompt you to remove the ubuntu-desktop package, don't worry - it's only a meta-package)

then check if it works. if it does run

```

rm /etc/apt/sources.list
mv /etc/apt/sources.list.tmp /etc/apt/sources.list
apt-get update

```


[COLOR="Red"][SIZE="5"][B]
3. Setting up Amarok[/B][/SIZE][/COLOR]

1. Here I assume you know how to use amarok (i.e. adding music, doing your own customisations, etc).
2. After you have done all that connect up your iPod.
3. Go to devices and your iPod SHOULD appear here (you may have to click connect) - you will be asked to "Initialize your iPod", say OK"
4. Set your iPod model by going to iPod (just below main toolbar on top)>Set iPod Model>Classic>80gb OR 160GB (black or silver).
5. Next go to collection and right click on whatever songs you want to transfer and select transfer to media device.
6. Next go back to device tab and select transfer (from the top).
7. Hopefully everything should transfer.


[COLOR="Red"][SIZE="5"]**4. Properly Disconnecting**[/SIZE][/COLOR]

From: [http://ubuntuforums.org/showthread.php?t=497201](http://ubuntuforums.org/showthread.php?t=497201)
(slightly tweaked so that it worked for me)

1. Click on the gears next to where it says iPod, this should open up a dialog for mounting and post-disconnect commands.
2. Leave the mount command blank and put the following in the disconnect box:

```

rm /media/iPod/iPod_Control/iTunes/iTunesLock;rm "/media/iPod/iPod_Control/iTunes/Play Counts";eject -t -d %d

```

where it says "rm /media/iPod/iPod Control" change "/media/iPod" to wherever your iPod is mounted (this can be found by going to nautilus browsing the iPod and looking at the address bar).

3. Click OK
4. WAIT for everything to complete (including on the bottom statusbar of Amarok which should say Flushing iPod Cache).
5. When everything seems to have stopped click on iPod>Update Artwork (this may take a while depending on the number of songs, but after it is done you will see Artwork updated on the bottom).
6. Click disconnect, it should say device successfully disconnected.
7. Now right-click on the iPod icon (either in nautilus or on the desktop, and select eject).

THATS IT!

Let me know if you have any problems or if there is an error in the guide.

NB: All of this worked for me and my iPod is running fine with music AND videos.

---

### Post by gsiliceo on 2008-05-25
Hello this is a cry for help, the Banshee project needs your help, the 1.0 version will come out soon, but the ipod support is not complete and since you appear to have the knowledge and gear(ipod 6g) we could use your help testing the latest svn trunk version to report bugs.
Currently the people reporting bugs about the ipod are MIA.
There is one bug you might particulary help triage.
[http://bugzilla.gnome.org/show_bug.cgi?id=389550](http://bugzilla.gnome.org/show_bug.cgi?id=389550)

The reason for this is that we want to be banshee the best media player for the gnome desktop with excellent ipod support.

Thanks in advanced. A Banshee project advocate.

P.S Im sorry for being out of topic. I felt that a PM would be an invasion of your privacy.

---

### Post by abhiroopb on 2008-05-26
Hey no problem. I'd be glad to help.

Unfortunately I have a lot of work at the moment, and also I have NEVER done anything like that before. If you could provide some assistance. For one what is an svn trunk?? I searched a lot and I do have subversion installed but I'm still not sure what it does exactly. Going off topic so perhaps you could PM the answer.

---

### Post by gsiliceo on 2008-05-26
PM send out.

---

### Post by markyb on 2008-05-26
I have not set this option up yet, but was wandering if you do does it mean you cannot upgrade the firmware anymore?  Can this only be done through itunes?
Thanks.

---

### Post by abhiroopb on 2008-05-26
I'm not really sure about a firmware upgrade. I don't know exactly how to do it, in fact amarok may be doing it when it initializes. Sorry but I don't know.

---

### Post by MeanStreak on 2008-06-03
Hi,

Thanks for your post. I have one question re: Amarok and Libgpod3, I already have Amarok installed so can I simply skip the Amarok installation step? 

Cheers

MeanStreak

---

### Post by abhiroopb on 2008-06-03
> **MeanStreak said:**
> Hi,

Thanks for your post. I have one question re: Amarok and Libgpod3, I already have Amarok installed so can I simply skip the Amarok installation step? 

Cheers

MeanStreak

See thats what is the main thing about this setup. I don't know exact technical details, but the amarok you probably have installed is using libgpod2, and you HAVE to force amarok to use libgpod3. In fact if you simply try and remove libgpod2 apt-get will also remove amarok, gtkpod, and rhythmbox (if you have them installed). Using the hardy repositories and aptitude means you force your computer to use libgpod3, although this does mean updates for amarok become an issue later (since you have to delete the hardy repository). However, until the new amarok comes out, this works very well.

So in answer to your question please don't skip the amarok installation!

---

### Post by Stagger Lee on 2008-06-12
hi, thanks for the helpful guide. 

I did what you said, but when I start Amarok my ipod is not there. Hitting connect does not help, or maybe I should give a different command than mount %d? Please note that the iPod is mounted on the desktop. 

I have an iPod 6G 80GB, black, just like yours. :) I am running Xubuntu gutsy on an eeepc asus. 

This is starting to get very frustrating, I hope you can help somehow. Thanks

---

### Post by abhiroopb on 2008-06-12
When you say not there what do you mean? First of all connect the iPod, and see if you can see the iPod in nautilus. If so then go to the Media tab in Amarok and see if anything happens when you press connect.

---

### Post by Stagger Lee on 2008-06-12
Hi, thank you for your quick and kind reply. 

By not there I meant I could see it in Nautilus but not in Amarok, and if i hit connect nothing would happen. 
In the meantime I have managed to load it in gtkpod though,and I have copied  a folder of mp3s I had on my harddisk. 

But, 
when I try to add the folder containing the whole backup of my iPod, gtkpod adds 6 or 7 GB then crashes. That has happened 3 times. What I do is Add Folder and select the iPod Backup folder (containing basically everything I previously had on my iPod), which is on an external USB hard drive. 
I am running it on a fresh install, I have added no packages except the ones that are mentioned in this guide. 
I would appreciate it if you could help me. If not, thanks anyway for the how-to that actually got me to put at least one folder back on.

---

### Post by Stagger Lee on 2008-06-12
Also, I tried to install Rhythmbox instead of Amarok via Aptitude, but it would say it couldnt. Do you think it is safe to repeat the process and see if i can install rhythmbox an have it use libgpod3? I remember Rhythmbox could import the mp3 from my iPod back up and copy it to the new iPod, just I would not see them on the iPod itself but only within Rhythbox. 

Thanks a lot!!

---

### Post by Stagger Lee on 2008-06-13
Just for the records, I did this process and installed Rhythmbox instead of Amarok, worked like a charm. Thanks for the useful howto!

---

### Post by phr0ze on 2008-06-13
Is this part still needed?

sudo -i
cp /etc/apt/sources.list /etc/apt/sources.list.tmp
echo deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy main restricted universe multiverse >> /etc/apt/sources.list
apt-get update


Shouldn't that already be the source if we are using hardy?

Sorry for such a silly question, but I'd hate to mess with sources.list if i dont have to.

---

### Post by abhiroopb on 2008-06-13
Hey sorry I didn't get back to you earlier, exam time for me! Anyway glad it worked! AS for your other point basically it doesn't make much of a difference whether you follow that step or not. I wrote this with a view of someone using gutsy. Now if you follow these steps it won't actually change anything, on the other hand you don't really have to do them anyway!

---

### Post by GepettoBR on 2008-07-05
@Stagger Lee:

I also had this problem, where Amarok would not detect my iPod. This is what I did to fix it:

1)First, make sure your iPod is mounted and available in Nautilus.
2)Then, in Amarok, go to tools>configure amarok.. and click on the Media Devices tab.
3)Click the Autodetect Devices button. Amarok should find your iPod. If it doesn't (mine didn't), click the Add Device button.
4)Select Apple iPod Media Device from the pulldown menu, and fill in your iPod's name on the first field and the mount point on your second field. If you don't know the mount point, right-click your iPod icon on the desktop, click properties and go to the Volume tab. The mount point is shown there.
5)Click Ok and your iPod should now be on the list. Go back to Amarok's main windows, to the Media Devices menu, and click Connect, then click the iPod button that's next to the Connect, Disconnect and Transfer buttons and select your iPod model.

This method worked for me with abhiroopb's instructions, and it also works for 5G iPods.

---

### Post by luckyuser on 2008-08-29
PROBLEM: Ububtu freezes while Amarok is transferring files!

I have been doing the steps in this tutorial over and over, and I've made some progress, however one thing continues to happen.
When attempting to transfer my entire library (40GBs), Ubuntu freezes in mid transfer, and I have to restart my computer. This has also happened when trying to make smaller transfers (i.e. 8GBs). 

I have also has trouble getting the iPod to see the music, so I transfered just one file - and it worked. The iPod could see the 1 song I transfered.

ATTEMPTED SOLUTION:
I am continuing to make small transfers of about 100 files at once. Ubuntu still freezes in mid transfer, but when the transfer does complete (freeze-free) i can see the newly added files. 

This way is not perfect, so I am wondering if there are any wiz's out there that know what's up, or have suggestions?

---

### Post by SuperGiraffe on 2008-10-17
Thanks for the instructions. I'm now able to transfer songs to my iPod!
Before looking at this thread i connected my ipod to amarok and transferring songs appeared to work. I disconnected my ipod but no songs were visible and reconnecction showed an error ```
Media Device: could not find iTunesDB on device mounted at /media/SUPERGIRAFF_'. Should I try to initialize your iPod? 
```
So I was stuck with a full ipod that didn't show any songs. My only option was to delete everything and try again from scratch.
I followed steps 2,3, and 4 so I ended up with an ipod filled with songs from amarok! Sweet! 
I had been looking at other threads before this one for instructions but the procedure they outlined was a bit different. Specifically Step 4: Disconnection seemed to be important. so be sure to delete the ituneslock and playcounts before using the eject command (not gnomeeject or kdeeject) on the appropriate media mount point.
```
rm /media/SUPERGIRAFF_/iPod_Control/iTunes/iTunesLock;rm "/media/SUPERGIRAFF_/iPod_Control/iTunes/Play Counts";eject -t -d %d
```
Anyways, thanks guys. My ipod works with amarok.

I was wondering though,both my ipod's truncated name and the ipod's truncated name appended with an underscore appear. Apparently it is a bug but it hasn't done anything else i can see and i'm not sure how to fix. This happen to anybody else?

---

### Post by jurij20 on 2008-12-11
I just want to thank you for your tutorial. It was great and it worked like a charm. Well, at least after 4 attempts. 
I got one question tho; does the iPod's battery recharge when I connect it in Amarok ?

---

### Post by GepettoBR on 2008-12-11
> **jurij20 said:**
> I just want to thank you for your tutorial. It was great and it worked like a charm. Well, at least after 4 attempts. 
I got one question tho; does the iPod's battery recharge when I connect it in Amarok ?

The iPod's battery charges whenever it's connected to a power source. If you plug it into your computer it charges, even if you don't open Amarok/iTunes/whatever.

---

### Post by abhiroopb on 2008-12-11
Does anyone think it is worth upgrading this for Intrepid? I'm using Rhythmbox now because (in my opinion) it is much simpler and works quite easily (out of the box, including album art). So, what does everyone think?

Thanks,

---

### Post by GepettoBR on 2008-12-11
These same instructions worked for my amarok in Intrepid. Rhythmbox works too, but I only tested it after setting up Amarok, so some required steps might be here too. I have a 5G, though, not a 6G.

---

### Post by abhiroopb on 2009-05-13
In Jaunty, it works flawlessly, just need to add the iPod to the "media devices" in amarok configurations.

After that everything can be imported (including album covers)

---

