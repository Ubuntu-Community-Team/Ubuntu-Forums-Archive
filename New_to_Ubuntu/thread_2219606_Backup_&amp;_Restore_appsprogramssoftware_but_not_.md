---
title: "Backup &amp; Restore apps/programs/software but not /home"
date: 2014-04-24
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2014-04-24
I'm having to consider a clean install. I use 12.04 now but would probably use 14.04 for the clean install OS. I have Deja-Dup's  backup on an external drive. It has my /home on it.

I want to find a simple solution to backing up the apps in /usr and other "File System" location other than /home. I want to create the 14.04 in the current partitions I have, viz.: / is about 20 gig and /home is about 970 gig and 'swap' is about 8 gig. That being: /dev/sda1 (`/`) and /dev/sda3 (home) and dev/sda4 (swap).

After 14.04 is installed and updated, I want to run the application/configs/other software and have it restored and have the Update Manager or Synpatic know to look at these and update them as well.

Is there a solution here?

---

### Post by whitesmith on 2014-04-24
Your partitioning looks good, except /swap is maybe a little overweight, but you're safe in playing it conservative. I've never used Deja-Dup, but I can tell you that Simple Backup will handle stuff in directories other than /home. You might look into that unless you're married to Deja-Dup. Perhaps someone having experience with that backup tool can add to my response. Regards.

---

### Post by monkeybrain20122 on 2014-04-24
For the sake of upgrade there is no point and no need to backup the whole root partition.

You need to save the directory sources.list.d for your ppas, and then move it over to the new install and run "sudo apt-get update",  but you have to edit the entries in the files inside to change all occurrences of 'precise' to 'trusty'. Bear in mind that you may get errors because some ppas for precise may not have updated to work for trusty.

To reinstall your software [http://askubuntu.com/questions/17823/how-to-list-all-installed-packages](http://askubuntu.com/questions/17823/how-to-list-all-installed-packages)
Again some packages for Precise may not be available in Trusty or may have different names.

Edited: if you want to backup the root partition just in case that you may need to reinstall 12.04 you can use fsarchiver, but to restore it you need to have the /home or a clone of it. I don't know how Deja-Dub backups the /home, if it just backups the files without the correct uuid and file structure then it won't work.

[http://www.fsarchiver.org/QuickStart](http://www.fsarchiver.org/QuickStart)

---

### Post by 3rdalbum on 2014-04-24
Use the "Something Else" option in the Ubuntu installer. Specify your current / partition as having the mount point /, and do not format it. Specify your current /home as having the mount point /home, and your choice whether to format it or not.

When you click the Next button, the installer will tell you a confusing message about your current system files being overwritten (/var, /use etc). Click Continue.

The installer will look at your currently installed software and will remember what packages are installed. After the base installation of 14.04 it will download the 14.04 versions of those programs and install them for you. Just keep the installer running - this step takes a while. When it finally says you can restart, or if you decide it's not worth waiting and you skip the package downloads, then you can safely reboot and your old software will be waiting for you.

---

