---
title: "Nautilus extremely slow/lags"
date: 2011-09-20
forum: New to Ubuntu
---

### Post by TCAllen07 on 2011-09-20
I recently started having issues when using nautilus. When opened, it's very slow to load, often randomly freezes for a few minutes, and when I go to close it it will hang, a metacity window will pop up asking if I want to Force Quit or Wait, and if I just choose wait it will eventually close (~10-15 seconds later). 

Using a different file browser/manager (actually called File Manager), I don't have this problem, or for that matter with any other programs. When I'm using Nautilus extensively, it will occasionally freeze the panels on my desktop. 

I attached two screenshots. The first (Screenshot-2.png) shows just trying to open a folder in nautilus (on the right you'll see both System Monitor & top running, both show Nautilus being a CPU hog for a solid 1-2+ minutes). The second (Screenshot-3.png) shows what happens when I attempt to close a Nautilus window. 


Any ideas or diagnostics I could check out?

Many thanks!

-Trevor

---

### Post by TCAllen07 on 2011-10-26
Update & related question: 

Due to the issue with Nautilus & other reasons, I went ahead and did a fresh install of 11.04 (Natty). I had /home on a separate partition and simply pointed this partition as the /home mount point for the new install, so as not to lose my personal data. However the same problem exists, with Nautilus functioning extremely slowly, which significantly slows the boot/log-in process & many standard tasks requiring file management. 

My thought is that there are some Nautilus config files somewhere on my /home partition that remained despite the fresh install? Is there a way to completely re-install Nautilus w/o wiping /home? 

I also installed Lubuntu on a separate partition and used the same /home mount point, but it doesn't have this problem (I'm guessing because it doesn't use Nautilus?) 


Any thoughts or ideas? 


-- Trevor

---

### Post by audiomick on 2011-10-26
To see the config files in your /home/user folder, go there (in Nautilus) and enable "view hidden files" in the view menu. You will then see a heap of files with a dot before the name, like .something . There is one there called .nautilus, but on this machine it is empty. You could probably safely erase it, I think. Seems like most programs just create a new .config file if the old one gets lost.

---

### Post by jwcalla on 2011-11-02
Did you ever find a solution to this?  I don't know when it started but it takes Nautilus a long time (several seconds) to open now.  Every time.  And top shows no CPU usage and the disk isn't doing anything.  It seems to flake out when I connect / disconnect a USB device also.

I don't remember it being like this.

Navigating through folders seems fine.  It just takes forever to load for some reason.  Could it be hanging on a disconnected network share?

---

### Post by TCAllen07 on 2011-11-03
> **jwcalla said:**
> Did you ever find a solution to this? 

I haven't yet, but I plan on doing a fresh install in a few days, having removed (and backed up in case it was pointless and causes other harm) all of the hidden folder in my /home directory, which are typically (to my understanding) used to hold config data. I'm hoping the cause will be removed, and I can try and isolate it. I'll make sure to post the results here. 

It's still bad for me, nautilus hogs CPU badly when opening & closing. I'm not *positive* it's Nautilus, it could be the window manager (Metacity?) but I'm sticking w/ Nautilus as the issue for now...


P.S. I've been using a Lubuntu dist I installed along side in the meantime, which works well enough (minus the inconveniences of a lighter distro).

---

### Post by TCAllen07 on 2011-11-03
Oh, also just FYI: I tried installing Nautilus Elementary in case it might overwrite the problem, but had no such luck. In fact, I think enabling Breadcrumbs and/or effects included in Nautilus Elementary slowed it down even more... 

So I removed that and went back to Nautilus standard, but the problem remains. Will keep the thread updated as I work on it (when I get the time :neutral:)!

---

### Post by jwcalla on 2011-11-05
In my case it turns out that I had an NFS share shortcut on my "Places" content pane that was slowing down the loading when the networked system was offline.  It wasn't visible until the other system was up and Nautilus would load instantaneously in that case.  I removed the shortcut and now all is back to normal.

---

### Post by celiapgt on 2011-11-29
I have the same problem: nautilus is very slow, almost unresponsive. I pulled my hairs trying every solution there is on every forum, until I forcefully reinstalled nautilus and rebooted. Then it was OK. BUT after I mounted several partitions where I store different kind of data (ext3, ext4 and ntfs file systems, only), then it became very slow again!!!

For safety reasons, I want my data in different partitions, but then when I use nautilus, it doesn't respond fast, as it should do.

Ubuntu gurus, Gnome gurus, please help. I just don't know how to trace the problem... I'm not that expert...

I'm using Ubuntu 11.10 with Gnome3 (in Unity I have the same problem; I checked it), with five different partitions in two big disks, and a AMD64-bit machine.

---

### Post by TCAllen07 on 2012-01-11
Sorry about the long-overdue update. 

In the end, I gave up and did a complete fresh install. I backed up my home partition and wiped out that as well as the root partition. I'm still not entirely sure what caused the huge nautilus issue. 

I did, however, save all of the config files that are saved in the home partition (i.e. all of the hidden folders in /home/username) including nautilus's. So if anyone wants to see anything from those files/folders that may help figure out what the problem was, let me know and I'll get them to you or post them here. 

-TA

---

### Post by TCAllen07 on 2012-01-11
> **jwcalla said:**
> In my case it turns out that I had an NFS share shortcut on my "Places" content pane that was slowing down the loading when the networked system was offline.  It wasn't visible until the other system was up and Nautilus would load instantaneously in that case.  I removed the shortcut and now all is back to normal.

Thanks for this. I thought I might have the same issue (with an NTFS networked drive using NTLMv2 authentication), but removing it didn't help my case. Good thought, though, and I'm glad it worked for you!

---

