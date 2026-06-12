---
title: "Unable to Partition"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by Matt86 on 2008-10-09
Hello everyone,

After considering creating a linux partition for years I've finally decided to install Kubuntu and give it a try; the idea of running a non-corporate OS has always appealed, and I'm very eager to learn about something outside my WIN XP OS.

As I use my computer for work, and I've got a very well established WIN XP installation, I definitely want to start my linux experience with a small partition (10GB) until I come to grips with everything and potentially shift entierly.

I'm currently using an HP compaq nx7010 laptop - I've done some reading and other users seem to have no issues running Linux on this machine.

The problem I am currently having is creating a partition on my Hard Drive - an 80GB FUJITSU MHV2080AT which currently has 23.7 GB of free space.

I firstly tried the Kubuntu installer, which resulted in an error resizing my partition. I then tried using Partition Magic in Windows, again to no avail - I was quoted 'error 1529 while executing batch' and 'error 1529 information mismatch in directory entry'. This took place when partition manager tried to create the partition during a reboot.

I did some more reading to see if anyone else has had simmilar problems, and took all the advice I could find: I defragged the drive, performed a registry cleanup, and tried to partition again, this time using Gparted via a live-CD. Again, some problem, an error ocurred in resizing.

If I enter disk management in windows, the drive is healthy, but there seems to be no option of creating a partition from there either.

I'm now at a loss of what to do, and feeling quite disheartened as I really want to get Kubuntu running.

If anyone has any suggestions or help, it would be very appreciated!

Thanks in advance,
Matt

---

### Post by phidia on 2008-10-09
I've never liked gparted that much but I realize plenty of people here use and like it.
I use command line tools frequently because they are often faster and have more options. In that vein try cfdisk > sudo cfdisk /dev/sda**in place of sda you would put your actual drive. And be sure to look at the [man page]("http://unixhelp.ed.ac.uk/CGI/man-cgi?cfdisk+8") for cfdisk.

BTW I doubt that your laptop will have "no issues". 
Running Ubuntu/linux does require more operator involvement, but as you said you learn from that.

Most laptops have some problems with suspend/resume. Although it may work partially there can IMO be some fussy bits.

---

### Post by Matt86 on 2008-10-13
> **phidia said:**
> I've never liked gparted that much but I realize plenty of people here use and like it.
I use command line tools frequently because they are often faster and have more options. In that vein try cfdisk **in place of sda you would put your actual drive. And be sure to look at the [man page]("http://unixhelp.ed.ac.uk/CGI/man-cgi?cfdisk+8") for cfdisk.

BTW I doubt that your laptop will have "no issues". 
Running Ubuntu/linux does require more operator involvement, but as you said you learn from that.

Most laptops have some problems with suspend/resume. Although it may work partially there can IMO be some fussy bits.

OK, the tip is appreciated, but is cfdisk not linux-based software? As I'm still running WinXP how am I going to use it? Is it in-built so that I could run it from a linux live-CD?

And also, is it non-destructive? I'm pretty sure I could set up a new partition by a destructive method, i.e. fdisk or even just reformatting and using the XP installer, but my point is that I would like to create the partition without bringing down my current setup...

If worst comes to worst I could reformat and start over, but I'd really prefer not to - I did a reformat not so long ago and don't want to go through it all again for the sake of linux experimentation.

Any ideas anyone?

Thanks,
Matt

---

### Post by handydan918 on 2008-10-13
> **Matt86 said:**
> OK, the tip is appreciated, but is cfdisk not linux-based software? As I'm still running WinXP how am I going to use it? Is it in-built so that I could run it from a linux live-CD?
Precisely. both cfdisk and its predecessor, fdisk, are present on most Linux distros. > 
And also, is it non-destructive? I'm pretty sure I could set up a new partition by a destructive method, i.e. fdisk or even just reformatting and using the XP installer, but my point is that I would like to create the partition without bringing down my current setup...
NO. NO. IT IS NOT non-destructive. ALL formatting operations are potentially destructive, and backups should always be made. Ya been told!> 
If worst comes to worst I could reformat and start over, but I'd really prefer not to - I did a reformat not so long ago and don't want to go through it all again for the sake of linux experimentation.

Any ideas anyone?
Do your experimentation on a (old/salvaged?) desktop?> 
Thanks,
Matt

---

### Post by i_have_a_sempron on 2008-10-13
One thing I have noticed with gparted, is that it has issues when you make a new partition AND try to format it at the same time. Howeverthat might be my machine malfunctioning. If you must,try gparted but have it make a nonformatted partition, then when doing a kubuntu install, it will format the partition it self.

---

### Post by Matt86 on 2008-10-14
Yeah, I've thought of this too - still no joy. It looks like I might have to do another reformat to make my partition.. Oh well, I'm pretty eager to get started as a linux user so maybe I'll just bite the bullet and do it.

---

### Post by hyper_ch on 2008-10-14
> **handydan918 said:**
> and backups should always be made.

I agree... you should always have backups no matter what you're doing. If your harddisk fails, as it is only a piece of mechanical technology, you'll lose all data. Regular backups are a must...

---

### Post by bumanie on 2008-10-14
I find the dedicated gparted live cd is better than the one that is included in the ubuntu live cd. If you decide to dual boot 1) back up important information 2) defrag windows at least twice 3) you can pre-partition with the gparted live cd, it works well with xp 4) I would give a bit more space than 10gb if possible for ubuntu.
There are lots of installation tutorials around, read a few and decide which method you feel more comfortable with. 
Post back if you have any more questions, there are plenty of people who are prepared to help.

---

### Post by indytim on 2008-10-14
Send us your current partition lineup.  You may be running into the partition wall where you need to create an extended partition first.

IndyTim

---

### Post by Matt86 on 2008-10-14
Well, I've made a breakthrough.

I did some more defragging, but with Perfect Disk rather than the inbuilt XP defragger. This condensed my files much better. Hoping this would solve the problem I booted up Gparted again, but to no luck. Tried Partition Magic, no luck.

Then I booted up Gparted again, but choose the 'HP Laptop' configuration and ran the GUI from the inbuilt forcevideo script. Got that running, and to my surprise it actually made the partition. I've allocated 45 GB to WinXP and 30 GB to Kubuntu and now I'm just formatting the new partition prior to install.

Thanks for everyone's help, I'm very glad to finally be able to get Kubuntu up and running - hopefully if things work out I'll downsize my WinXP partition even further to give more space to Kubuntu.

I'm sure I'll be back to bug you with more questions/problems when I actually have to start coming to grips with a new OS

Cheers,
Matt

---

