---
title: "[SOLVED] 8.10 - Hardware Drivers/Nvidia not activating"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by Dragonseer on 2008-10-31
Hello all, have just installed Intrepid and very pleased so far.  I just have an issue enabling the recommended Nvidia driver from the Hardware Drivers panel.  At first it appeared in a pop up and I clicked through believing I had enabled the driver.  However I didn't see the 'restart required' icon pop up, as I am used to from Gutsy/Hardy etc, so I tried running the process again.  The driver didn't initialise on reboot and now the process hangs when it searches for the driver. :(  How would I go about clearing this history and doing it from the terminal?  The driver in question shows Nvidia no 173.  Any help would be appreciated!!  :KS

---

### Post by confused57 on 2008-10-31
From a terminal:
```
sudo apt-get update
```

then try reinstalling nvidia driver, it worked for me.

---

### Post by Dragonseer on 2008-10-31
I have tried this and unfortunately it does not stop the package manager from hanging.  Upon pressing "activate" the "Downloading and installing driver..." dialogue appears and freezes at 0% progress.  It cannot then be cancelled.  I would like to try fetching the update file from the terminal but I don't know the location or proper file name.

---

### Post by starcannon on 2008-10-31
the repositories are probably over capacity right now. It may be worth running the default but limited vesa driver for a week, and try again. I won't do anything other than download the 8.10 iso using torrent until the "frenzy" that follows every release has settled down. Note that the "frenzy" makes now the optimal time to download the torrent :) so its win:win for me ;)

For me release is 1 to 2 week later, but I get bliss in return.

GL and have fun.

---

### Post by The Doell on 2008-10-31
The same thing happend to me, when trying to download the driver it hung at 0%.  Clicked cancel nothing happened...then after a while I was prompted to install the Nvidia driver, some how it had downloaded.  I did not see the % increase at the download prompt. Best bet so far is to let it sit for a while...

---

### Post by Dragonseer on 2008-10-31
Aha! - 'New Restricted Drivers in Use' - Success!!

I left the package manager spinning away in the background, surfed around for a bit, and tried another reboot - and it's working.  I guess we can put that down to stressed repos.  Thanks everyone!!  :lolflag:

---

### Post by s.ingallo on 2008-10-31
Hi guys, I also had a problem with the activation of NVIDIA drivers (version 177), in fact whenever I tried to activate the driver nothing happened, it just gave me no response. I solved the problem by changing the source repository from the Italian to the main source, now everything work.

I hope these informations will be useful for someone out there!!!

Bye Bye

---

### Post by grotsop on 2008-10-31
I had the exact same issue. Here is how I fixed it, I selected the nvidia-glx-177 package in the Synaptic Package Manager for installation upon which it prompted me to insert the 8.10 CD,(seems like part of the problem was that I upgraded from the ISO file I mounted on my computer, so I quickly burned the CD.) Then Synaptic reported:

[INDENT]
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable) E: Unable to lock the download directory[/INDENT]

So I cleared that up with this:

[INDENT]
sudo rm /var/cache/apt/archives/lock[/INDENT]

After that the activation when fine.

---

