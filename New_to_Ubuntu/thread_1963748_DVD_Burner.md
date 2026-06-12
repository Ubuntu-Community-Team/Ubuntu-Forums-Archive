---
title: "DVD Burner?"
date: 2012-04-22
forum: New to Ubuntu
---

### Post by crestmount on 2012-04-22
Totally new to Ubuntu and looking for a simple DVD burner that works--Brasero proved a dud.  Any suggestions would be great (instructions in how to install would be great also)

---

### Post by Gremlinzzz on 2012-04-22
k3b
sudo apt-get install k3b
:popcorn:

---

### Post by forrestcupp on 2012-04-22
k3b is top notch. It's in the repos, so you can install it with the Software Center.

Edit: I got ninja'd. :)

---

### Post by mike555 on 2012-04-22
Xfburn works for me ...... others may recommend K3B , but be aware that installing K3B also installs a bunch of KDE stuff you might not want.

---

### Post by anewguy on 2012-04-22
+1 on k3b.  I've also had problems off and on with Brasero and k3b just plain works.  Don't worry about the kde stuff it installs - it won't hurt at all.

BTW - just so we might know - what kind of problems are you encountering with Brasero?

Dave ;)

---

### Post by crestmount on 2012-04-22
Just tried the xfburner--thought I had burnt a movie on, but when I tried to open it to watch, the disc didn't even come up as in my computer

---

### Post by crestmount on 2012-04-22
Am now trying K3B--go to burn a disc and get the following error messages:
The project does not contain all necessary DVD files.
The resulting DVD will most likely not be playable on a HiFi DVD player.
Could not determine the size of resulting image file.

---

### Post by crestmount on 2012-04-22
Have deleted the Brasero--it said I was missing a couple of files needed

---

### Post by Gremlinzzz on 2012-04-22
So it wasn't the burners:popcorn:

---

### Post by 3rdalbum on 2012-04-22
Would have been helpful if you had said earlier that you wanted to convert ordinary video files to DVD format.

In theory Brasero should do it, but I've had that mysterious "missing packages" message too. In the end I used Devede to make a DVD image and then used Brasero to burn the disc image, which it does fine. In Devede you should specify that you want an ISO disc image.

---

### Post by anewguy on 2012-04-23
While I don't believe we're allowed to discuss the hows and therefores in this forum, if it's a commercial DVD you've ripped you need to be sure you've installed the things that let you work with encrypted media.

Dave

---

### Post by forrestcupp on 2012-04-23
Also, if you happen to be copying a video DVD, there is a great chance that the video data on the commercial DVD is too large to fit on a blank DVD. If that is what is going on, check out k9copy. It will shrink the DVD data to fit on a regular blank DVD for you. It won't crack copy protection, though. You have to find other sources to do that.

K9copy is in the repos, too.

---

### Post by morhin on 2012-04-23
The easiest one I've found is Thoggen DVD Ripper. It's almost too easy. I've even copied instruction dvd's that have sections in them. But it will store these as individual units and at setup you have to okay each section individually. A small price for an easy ripper.
For movies and such it's a snap. 

I found out about it in Ubuntu for Non-Geeks by Rickford Grant with Phil Bull. I'm running Lucid Lynx 10.04. I'm not moving to 12.04 until the new book by these guys comes out. I'm already noticing folks running around trying to find where they moved everything. This book is a great guide and converted me to ubuntu with the way they deal with non-geeks like me.
They talk about several rippers but Thoggen works for me.

Just go to Applications/Ubuntu Software Center/ (type in) Thoggen...... then install it. It'll show up in Applications/Sound and Video

Morhin

):P

---

### Post by morhin on 2012-04-23
I covered the ripping now for the burning. Put a blank recordable dvd in your burner, making sure to select a media format supported by your drive, and a Blank Disc window will appear asking what you want to do. Jut click "OK" to open the Nautilus's CD/DVD Creator window. Copying the files is pretty much a drag and drop maneuver. Just open a new Nautilus window, and drag the files you want to burn to disc for that window to the CD/DVD Creator window.
You need to know that the files you copied to the Creator window are only links to the original files. If they are moved then the copy link is no longer there. Just something to be aware of.

Morhin

;)

---

### Post by wolfen69 on 2012-04-23
> **mike555 said:**
> Xfburn works for me ...... others may recommend K3B , but be aware that installing K3B also installs a bunch of KDE stuff you might not want.
But it also doesn't hurt anything. I also recommend k3b if you want a Nero-like experience.

---

### Post by NoNameWill on 2012-04-23
Do you have have ubuntu-restricted-extras package installed? And if you do did you run the script to install libdvdcss2?

Restricted extras are available from the software center GUI or the repos read the info on the package it will lead you to a link that will explain what command to run to install libdvd4css. 

It is quite simple.

---

### Post by anewguy on 2012-04-23
I may be wrong here, but I was thinking that was one of those things we didn't actually mention right here on the forum, because of legalities especially in the U.S..  I *think* we normally direct them somewhere off-site for that info.

Dave ;)

---

### Post by crestmount on 2012-04-24
Thanks guys--I suppose the confusion for me was that when I was using Windows I was able to copy avi files straight to a DVD--never realised that this couldn't happen in Ubuntu

---

### Post by NoNameWill on 2012-04-24
> **crestmount said:**
> Thanks guys--I suppose the confusion for me was that when I was using Windows I was able to copy avi files straight to a DVD--never realised that this couldn't happen in Ubuntu

You never said .avi 

[http://www.mguhlin.org/2011/07/burn-avi-to-dvd-on-ubuntulinux.html](http://www.mguhlin.org/2011/07/burn-avi-to-dvd-on-ubuntulinux.html)

---

### Post by forrestcupp on 2012-04-24
> **crestmount said:**
> Thanks guys--I suppose the confusion for me was that when I was using Windows I was able to copy avi files straight to a DVD--never realised that this couldn't happen in Ubuntu

If you want to do a specific thing, you have to tell us what that is, or we will just give you general answers.

---

### Post by ph4nt0m117 on 2012-04-24
> **crestmount said:**
> Totally new to Ubuntu and looking for a simple DVD burner that works--Brasero proved a dud.  Any suggestions would be great (instructions in how to install would be great also)

AHAHAHA BRASERO.  That's funny.  Someone tried Brasero.  I'm sirry its just no one I know has ever used it.

Here's a good recommendation for you.

Start/Ubuntu icon - settings - ubuntu software center

Search DVD burner.

Being new to ubuntu doesn't mean it is ungodly hard.  The Software Center is best resource for anything needed.  Otherwise google! :D

---

### Post by SeijiSensei on 2012-04-24
Different methods apply depending on what you want to do with those AVI files and what codec was used to encode the video.  Files encoded with DivX or XviD can often be played directly on DVD players with DivX support.  For those types of players, you just need to copy the files directly to the DVD; K3b calls this a Data Project.  However for this to work, the videos often have to meet certain size limitations.  Typically the maximum supported size for an XviD video that can play on a standard DVD player is 720x480.  High-definition formats like anamorphic DVD (848x420) or true HD formats like 720p or 1080p won't fly with most players supporting DivX.

If your intent is to create a video DVD that can be played on any DVD player then, as mentioned earlier, your best bet is to use DeVeDe to create an ISO image and burn the image to the DVD with K3b.

---

### Post by forrestcupp on 2012-04-25
Besides copying video DVDs, k9copy can also author DVDs by taking avi files or any video files and burning a video DVD. You can even split the video into chapters. It can either output to an ISO or directly to the DVD drive.

I'm liking k9copy a lot. But if you need more control over what the menu looks like, instead of just ease of use, DeVeDe is your best bet.

---

