---
title: "bash script to move files"
date: 2007-06-17
forum: Programming Talk
---

### Post by rustysail on 2007-06-17
Sorry if I'm posting this in the wrong forum.  I wasn't sure where my question would fit.

I have a cheap mp3 player that I want to work with.  It can't come close to holding my entire music collection, but I still like it.  I currently use it as a USB flash drive as well so the amount of space on it varies daily.  I know a small amount of bash scripting, but what I want to do with it is over my head.  I am interested in learning though.  I am using fiesty right now.  The player works on a drag and drop interface requiring no software.

I want to set up a bash script so that when I plug in my player songs are automatically taken at random from my music folder (/data/music) and put on the mp3 player (/media/disk).  I want it to continue copying the music until it runs out of room.  It needs to delete everything in its roots folder (the old music) before it puts int he new music, but it can't delete the folder inside labeled data because that is what I am using as a flash drive.

Any ideas would be a great help.  I want to learn, but I need a good shove in the right direction.  Thanks a lot.

---

### Post by nitro_n2o on 2007-06-17
If you want to learn, the best way is do it yourself, i'd suggest that you split in smaller tasks
First: write the script to delete files from your music player, which shouldn't be a big problem if you know some basic bash 
Second: write another script to only copy files 
After this point, you know how delete data, and copy new data
You just need a way to randomize things, which is the fun part :) 
I don't think you should worry about space.. The drive will not accept additional data if it's full, but you can keep a count of the size of each file you move in some counter and stop when you reach a certain limit. It'll be really a very bad idea to try to copy files to a music player for ever.... 
Have fun

---

### Post by rustysail on 2007-06-17
Thanks for the tip.  I will try that out.  Do you know how I would make the script run when I plug it into my computer?

---

### Post by thesm on 2007-06-18
> **rustysail said:**
> Thanks for the tip.  I will try that out.  Do you know how I would make the script run when I plug it into my computer?

System --> preferences --> removable drives and media --> click on the multimedia tab. Check "play music files when connected" then change the command to the script you want to run.  This is assuming your mp3 player comes up as a music player, if not, I have no idea :(. 

Hope this helps.

---

