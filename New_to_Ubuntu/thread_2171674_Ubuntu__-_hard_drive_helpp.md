---
title: "Ubuntu  - hard drive helpp"
date: 2013-09-01
forum: New to Ubuntu
---

### Post by julian2 on 2013-09-01
Hi There, 

First of all, i am a first time user and beginner to Ubuntu.
So far i am really enjoying the simplicity, and am beginning to explore.

However, i am now stuck. 

So I have everything pretty much set up i am running a 120gig SSD to run the OP System and few important applications.
I did this with Windows 7 and then stored all media on to an internal 1TB HD. So i want to set my Ubuntu up the same but i cant even figure out how to mount and access my internal 1TB HDD. 

Through "Disks" I am able to see the HDD but i am unable to mount. There is an option to format to use compatabile but i am not sure if this would erase all the data on the HDD and i definetly do not want this. 

That secondary HDD has W7 installed but i never use it. I just want the files to be safe and be able to set it up like i had before. 

Help?

Thanks in advance.

---

### Post by scbingham on 2013-09-01
gparted is the tool to use, it's on the live cd & available from the Software Center if not already installed on your system.
 
Obviously use with caution, make sure you have backups & make sure you're working on the correct disc!

Use this to resize your existing partitions & create a new one for your ubuntu data. Most people use the ext4 file system.

You'll need to create a mount point (directory) for your new file system & add that to /etc/fstab to auto mount.

Do some reading first & all should go smoothly.

Good luck.

---

### Post by oldfred on 2013-09-02
This thread has the specific commands to edit fstab that you need for both NTFS or ext4 data partitions.

 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6

      
 HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

---

