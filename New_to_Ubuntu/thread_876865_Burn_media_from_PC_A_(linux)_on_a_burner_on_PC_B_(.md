---
title: "Burn media from PC A (linux) on a burner on PC B (windows)"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by RavUn on 2008-08-01
Hello, I have my ubuntu box but it's an old PC I threw together and it does not have a burner.  I'd like to be able to burn CDs and DVDs on my brother's Windows box.  What would be the easiest way to do this if we're both sharing a router?

I have the ssh server setup on my linux box and I have samba installed on it also.  I am able to see my brother's computer on my Ubuntu machine... is there anything I need to setup to see my Ubuntu computer on my brother's PC?  

Also, would I have to download the files to his computer before burning or could it burn the files remotely (is that the right word?)?

I think it may be fairly simple to do, I just want to try to paint a picture in my head before attempting to have a go at it when I get home.  Also, what would be the best AVI to DVD tool for linux?  I'd like to be able to put multiple files on one DVD.  I don't have much experience with DVD burning.

Thanks.

---

### Post by northern lights on 2008-08-01
> **RavUn said:**
> I am able to see my brother's computer on my Ubuntu machineEasiest then would be to have your brother share a folder with write permissions and shove the data in there

> **RavUn said:**
> is there anything I need to setup to see my Ubuntu computer on my brother's PC?
If you have 'samba' installed, it should work vice versa. On your brother's desktop, right-click on 'My Network Places' and select 'Search for Computers', enter your hostname, initiate search. Does it find your box? Alternatively, enter your IP, instead of the hostname.

> **RavUn said:**
> IAlso, would I have to download the files to his computer before burning or could it burn the files remotely?
With his comp finding your box, transfer is not necessary.

> **RavUn said:**
> what would be the best AVI to DVD tool for linux?check out 'devede', it's in the repos.

---

### Post by halitech on 2008-08-01
if you are going to have the files on your computer and using his to do the burning, make sure you select the lowest possible speed and if his burner supports it, make sure burn right or burn protection is turned on, otherwise if there is any hiccups during the transfer it could create a coaster.

Depending on what you want to do, you could use K3B to create an image only, then transer that to his system to burn.

for movies, Devedee is good, also ManDVD (not in the repos) is good if you need multiple movies on a single dvd and you want a menu so you can select what what movie (or show) you want to watch.

---

### Post by flytripper on 2008-08-01
dunno if poss. i did use 1 pc to install a game on another once.... perhaps you can simply share the drive on your network and tell your burning program to burn to that one.

---

### Post by halitech on 2008-08-01
I think I've tried that before but all you can do is read the drive as it doesn't "talk" to the hardware the same way so it won't see the burning capabilities (I could be wrong though, been awhile since I tried it)

---

### Post by RavUn on 2008-08-03
I'm able to see my computer from his and am working with manDVD right now.  I plan to create an .iso image then want to burn that.  Does anyone know of some software to use on a Windows PC to easily burn an .iso image?  Nero and alcohol 120 aren't free I don't think.

Also, I left it as PAL format since I didn't really know the difference.  Think that will matter much?  Perhaps I should reconvert in NTSC format.

---

### Post by halitech on 2008-08-03
CD Burner XP is free and works fine for cds (haven't used it with dvd iso's yet as parents system doesn't have a dvd burner)

[http://cdburnerxp.se/](http://cdburnerxp.se/)

---

### Post by bwainscott on 2008-08-03
ISO Recorder is light, quick and free

[http://isorecorder.alexfeinman.com/isorecorder.htm](http://isorecorder.alexfeinman.com/isorecorder.htm)

---

### Post by halitech on 2008-08-04
> **RavUn said:**
> 
Also, I left it as PAL format since I didn't really know the difference.  Think that will matter much?  Perhaps I should reconvert in NTSC format.

if you are in North America then yes it should be NTSC

check here if you aren't so you know which is the standard for your country

[http://www.ihffilm.com/videostandard.html](http://www.ihffilm.com/videostandard.html)

---

### Post by RavUn on 2008-08-04
Thanks for the help.  

What I did was use ManDVD to put a few vids into one DVD then generated the "DVD Structure" (which I assume creates the .vob file) then made an iso image and am burning that on the windows computer.  Hopefully this works.  I have one already done in PAL format and working on a different one in NTSC to see if that works.

I'm pretty sure the type of DVD and the manufacturer can determine whether or not the DVD plays, so I'll keep my fingers crossed.

---

### Post by halitech on 2008-08-04
as long as you added the videos to the menu (step 4 I think) and it is in a format that will work in your area and with your dvd player you should be good to go. I've literally made hundreds of these using this program and except for the one time I forgot to change from PAL to NTSC I've never had a bad one

---

