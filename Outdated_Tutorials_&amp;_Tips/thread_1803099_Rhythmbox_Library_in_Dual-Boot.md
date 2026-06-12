---
title: "Rhythmbox Library in Dual-Boot"
date: 2011-07-12
forum: Outdated Tutorials &amp; Tips
---

### Post by Jalaska13 on 2011-07-12
If you've got a dual-boot environment, chances are your main music library is stored on your non-Ubuntu partition.  Of course, you could import your music to Rhythmbox, but this forces you to manually update every time you add music to your library, or re-import the whole thing.  Alternatively, if you set your main library folder as the library directory for Rhythmbox, it may maintain your files in an incompatible scheme with your other media manager.  The solution?  A single command line startup item.

In this example, sda1 is my non-Ubuntu partition.  The folder /mnt/sda1 has already been created, as has /home/username/Music/Mac.  
The non-Ubuntu system is Mac, and uses that file structure.

sudo mount /dev/sda1 /mnt/sda1/ ; 
sudo mount --bind /mnt/sda1/Users/username/Music /home/username/Music/Mac

First, this mounts the other partition in a constant location (so filepaths remain the same across boots and logins).
The second command makes it so that the contents of the Mac music folder appear in the folder /home/username/Music/Mac in the Ubuntu partition.

Lastly, set Rhythmbox (as is the default) to use /home/username/Music as its library directory.  This way, it will automatically import music from your non-Ubuntu partition and know when music has been added so it can update itself automatically.  Enjoy!

---

