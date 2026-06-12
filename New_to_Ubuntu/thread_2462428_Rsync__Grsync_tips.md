---
title: "Rsync / Grsync tips"
date: 2021-05-20
forum: New to Ubuntu
---

### Post by DitchingMS on 2021-05-20
Hi all! I've been gradually building up a new system from scratch and need some advice. The system is an always-on (Xubuntu) Dropbox backup machine based on a 2GB Intel Atom tablet, coupled with an old SMB NAS.

The concept is that when working away I can upload my photos to Dropbox when possible - then this machine will sync them into the local drive (got this working) in it's own time. 
In this way I'm using Dropbox as a buffer, because my connection is slow.

Once the files arrive on the local machine, I want them to be immediately copied to a NAS mount folder (already got the NAS mount working), verified that they're complete and functional, then deleted from the Dropbox sync folder and from the cloud. This means they're safely and quickly backed up and also Dropbox is kept empty.

Note I don't want them compressed or anything...just one for one copies. I'll buy more space if necessary.

I've downloaded grsync as I'm not command line experienced and prefer the gui - but I'm able to implement basic commands.

What I need to know is the best way to configure or script rsync / grsync to guarantee the integrity of the files, which is the top priority. These photos are my livelihood. Once I've moved them from my camera into Dropbox I'm at the mercy of the tablet and rsync and there are no backups.

Some concerns include:
- what if my remote upload is suddenly halted due to a dropped connection
- what if my local download connection (from my home ISP) drops
- what if my home LAN/NAS stops working while transferring a file
- what if the tablet stops working before or during a transfer. Power cut etc.
- I want to recursively copy all photos and folders which I've uploaded to Dropbox
- what if my camera has created duplicate folder names or duplicate file names on the SD card I'm uploading from, over the course of a few days?
- what if I mistakenly upload the same SD card twice? Is it worthwhile to compare the file properties, and if they are GUARANTEED the same file, just delete them? Or should I duplicate?
I don't want multiple copies of the same photos which I then have to manually filter through. There will be thousands.

Despite my long introduction I'm sure this is just a neat little rsync one liner! I'm sure you guys will know how best to do it!

Thanks in advance!

---

### Post by rbmorse on 2021-05-21
I won't get into the mechanics of your questions, but just so you know there is a thing called grsync which  is rsync with a GUI front end for when you want an alternative to the command line interface.

---

### Post by DitchingMS on 2021-05-21
Thanks, I'm already using grsync, it's just not clear how I am meant to use it to best effect for my specific requirements.

---

### Post by ActionParsnip on 2021-05-21
You could have a script that runs the rsync task and logs the result. If there is an issue the script can capture it and email you or similar. You could even break your rsync job down do that certain subfolders are dome separately so you can see which part failed. You could even have an MD5 test on the source and destination which will show partial files.
Another way would be to rsync to a temp storage on the remote system and, when the data is tested as "OK" then do a local rsync to prime time locally. You could send a text file of hashes for the destination to check with.
Depends how much **** covering you want to do really

---

