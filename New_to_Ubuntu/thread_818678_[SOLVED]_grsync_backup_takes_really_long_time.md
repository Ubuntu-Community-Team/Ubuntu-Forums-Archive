---
title: "[SOLVED] grsync backup takes really long time"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by dansan on 2008-06-04
I've been trying out grsync as a backup solution. Although it seems to work (haven't tried restore yet), it takes so longk that I generally let it run overnight. To me this is whacko. Has anyone using grsync got speedier performance? By the way, the backup includes a VirtualBox machine. At 35+ minutes grsync starts backing that up. At that point the Global Progress bar states that about 3800 minutes remain!         

I let grsync back up my home directory to a USB HD. The Rsync Output area shows the command being executed (rsync -r -t -p -v). Psychocats "Backing up Ubuntu" says to use rsync -av in terminal.  

A lot of time is spent on the "building the files list" stage. That's where it's at as I write this. It says "13000 files..." When it reaches 14680, it starts copying to the HD, but then pauses a long time, reporting that it's skipped a "non-regular file". The light on the HD flickers, so something is probably happening.

Is using terminal faster than this? How long is it taking others (for about 15000 files)?

Thanks,
Daniel

---

### Post by Baelus on 2008-06-04
Using the terminal or a gui shouldn't make a difference. They're both used to give commands to the rsync engine, which does all the work.

Speed depends on a lot of things. The size of the files would be important. If you're copying 15000 media files then it will take a lot longer than 15000 text files. It's really the amount of data you're moving, not the number of documents.

Also, how the drives are connected will change the time it takes. USB 2 is pretty speedy, about 60 megabytes a second. Thats peak performance though. Average will be a bit lower. Ethernet is slower at around 10 - 12 megs a second for a 100Mb connection.

I would think how fast the drives themselves are would make an impact too. A 5400rpm laptop drive will be slower than a 7200rpm or 10000rpm harddrive.

Generally, if you're moving 2 -3 hundred gigabytes of data it'll take a couple of hours or so. I admit that 60 hours doesn't sound quite right. Then again, it depends on how much you're trying to backup.

Looking at the rsync arguments I think using -a would be better. It stands for 'archive' and basically preserves all the permissions, times, owner information, etc. It also incorporates the -r ('recursive') switch, so it'll drill down through all the directories as well.

I always like to use -v ('verbose') to know whats going on.

Update is useful too. Use -u to skip newer files on the destination drive.

If you're watching the transfers then use --progress and --human-readable to give you something to watch. It's also good for troubleshooting to see what's going on.

When you want to run a simulation then use the -n switch. It will go through the motions and give you feedback on what it will do.

There are a ton of other options you can find in 'man rsync', but I find these tend to do the job.

That's about the extent of my understanding.

By the way, when you're dealing with your data, you want to be as sure as possible of what you're doing. It just takes one slip to cause some damage. So check everything out, my advice too, and test, test and test the operation you run before commiting to it.

Hope that helps out.

- B

---

### Post by mdpalow on 2008-06-05
+1 for Baelus' reply.

QuickStart will do a sync for you, but I'm not sure how much faster it will be for you since I don't know what the 15,000 files are.

However, I use QuickStart to setup my sync and it works fine. Also there are TAR and image backup options which you can choose from as well. If you choose TAR, you can even exclude certain folders if you find them too big to include into your regular back-up.

Check out my signature for more information if you're interested.

---

### Post by dansan on 2008-06-05
Thanks Baelus and mdpalow.

I'll definitely read man files more carefully in future. I also learned something by installing QuickStart, which makes everything visible. As I suspected, but couldn't see before using QS, including VirtualBox in a daily backup really slows things down. I have to reorganize that part.

I'm gradually learning my way into Ubuntu, and I greatly appreciate the help on backup, which is an essential for my business operations.

Daniel

---

### Post by mdpalow on 2008-06-06
> **dansan said:**
> Thanks Baelus and mdpalow.

I'll definitely read man files more carefully in future. I also learned something by installing QuickStart, which makes everything visible. As I suspected, but couldn't see before using QS, including VirtualBox in a daily backup really slows things down. I have to reorganize that part.

I'm gradually learning my way into Ubuntu, and I greatly appreciate the help on backup, which is an essential for my business operations.

Daniel

Interesting you should mention VirtualBox. A while back, I was using VMware. Same as VB, but just different company/name. When I backed up my system using QuickStart, it certainly slowed down a lot on the VMware files, but nothing really crazy. I remember creating a 10 gig virtual drive for VMware. However, it did slow things down enough that it got me thinking. Why not just sync my VMware folder using QS to another drive and then EXCLUDE the VMware folder during my back-ups. Since VMware folder hardly every changed, my sync never took more than a second to back-up and my real back-up was much faster.

---

