---
title: "DVD drives wont burn anything over 4.2gigs"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by onesojourner on 2008-08-01
I have several old back up files that are in the 4.3-4.5 gig range and for some reason my DVD drive wont let me burn anything over 4.2. I thought maybe my drive was bad, so I grabbed another ide burner and hooked it up to a usb adapter and I get the same issue. anything over 4.2gigs will not burn. I am trying to use dvd-r 4.7 gig disks. Both drives are ide.

---

### Post by dhughes on 2008-08-01
What burning application are you using?

---

### Post by dca on 2008-08-01
...and what write speed are you setting it to...

---

### Post by dca on 2008-08-01
Are you using Kubuntu/K3b??? I found this from older vers, you may have to install different app???
 
[http://ubuntuforums.org/showthread.php?t=74430](http://ubuntuforums.org/showthread.php?t=74430)

---

### Post by onesojourner on 2008-08-01
I am work so I am going to try to remember off the top of my head. I tried setting the burn speed from max to lowest. I have tried the default ubuntu writing software. I have tried Bresero and I have tried k3b. All 3 fail.

---

### Post by dhughes on 2008-08-02
> **dca said:**
> Are you using Kubuntu/K3b??? I found this from older vers, you may have to install different app???
 
[http://ubuntuforums.org/showthread.php?t=74430](http://ubuntuforums.org/showthread.php?t=74430)


 Also this [http://ubuntuforums.org/archive/index.php/t-387994.html](http://ubuntuforums.org/archive/index.php/t-387994.html)

 But the gist of it is this:
[i]ViperKnight
March 19th, 2007, 05:18 AM
You have to specify the DVD format as "UDF" for it to burn files larger than 4GB. It's the same in Windows.

I think K3B has this option somewhere....but I haven't tried it. There's a "Add UDF Structures" option available under "FileSystem" from the Burning window in K3b. But as I said....I haven't personally tried it so I can't confirm that it works. But I'm pretty sure it has to do with burning the DVD as a UDF instead of standard ISO due to the filesize limit.

Hope that helps.[/i]

 I don't know it that works or not, the next two people to comment ignored it so maybe it does and maybe it doesn't.

**edit**: and this [http://ubuntuforums.org/showthread.php?t=352386&highlight=k3b](http://ubuntuforums.org/showthread.php?t=352386&highlight=k3b)

---

### Post by onesojourner on 2008-08-05
I just confirmed that I can burn the same file when I boot to xp.

---

### Post by dca on 2008-08-05
Is this file listed as 4.2 gig in Windows as well?  In other words I think we're playing a numbers game.  The DVD makers label the blank DVD as 4.7GB worth of use but it's the same numbers game that HDD makers use.  IOW, 1024kb = 1MB (not 1000kb)...  Something like that.  If the file size is close (because POSIX OS' work in absolutes we'll say).
 
Knowing that, do the two file sizes display differently across both OS'? 
 
If so, you may be able to burn the file in k3b as .iso file...  See if it lets you select the file to add to project, select burn, I think a dialog box pops up, when it does, tick "only create image".  An image tab should appear allowing you to add path/filename...
 
Same should work in Braseo, create new DataDVD project, add the file, click burn, and when the dialog window pops up, select 'file image'...  change properties to create on desktop.  Re-open whichever app (Brasero or k3b) and select 'Burn from ISO' or something similar and see if it lets you create that ways.  
 
Some of the things I've found in searching is there's issues when burning single files larger than 2gig in Linux as well.

---

### Post by LowSky on 2008-08-05
dca is right a 4.7GB disc is really 4.589GB, then you have to account for the fact that the size stated is an average. then you have to account for your hard drives file system and how is compresses files. On one system it can read 4.2GB but be 4.5GB on another.

---

### Post by onesojourner on 2008-08-21
I burned the file from an ext3 files system in xp.

---

