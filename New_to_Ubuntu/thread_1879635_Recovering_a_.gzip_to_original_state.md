---
title: "Recovering a .gzip to original state"
date: 2011-11-12
forum: New to Ubuntu
---

### Post by moallam on 2011-11-12
Hi there, 

I was trying to copy a file from the desktop into a folder. I accidently released the mouse while hovering on a .gzip file.

The ubuntu file system did not just add that file into the .gizp file. It deleted all the contents of the .gzip file and now the .gzip file only contains the file that was accidently moved into it.

Is this a normal behavior of the ubuntu file manager?

Furthermore, this .gzip file contained important financial data. Is there anyway I can recover it to its original state?

Thank you.
Mo

---

### Post by moallam on 2011-11-12
On second thoughts of what might have happened:

1. The Ubuntu file system deleted the original .gzip
2. The Ubuntu file system created a new gzip with the same name and the newly added file as its only content.

So, I may rephrase my question to be "how to recover a deleted file that's not in the trash?"

Also, I've verified the peculiar behavior of the system's archive manager. I created a new archive and put some dumb files in it. I dragged, using the mouse, another file on top of it. It clearly showed a "+" sign indicating that it was adding the file to the archive. Upon the release of the mouse, and then examining the archive, it only had the recently added file. All the dumb files were gone. Is that normal?

For what it's worth, I'm running Ubuntu 11.04 (don't know what Kernel) with the classic gnome interface (no unity)

Can anybody help?

Thanks in advance.
Mo

---

### Post by moallam on 2011-11-12
Update:

Another bit of info: The file type is actually .gz not .gzip as I originally thought, and it's a created by GNU Cash software.

After following this link

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

And this link

[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

Right now I'm using Photorec to scan my HD recovering only archive-type files. It's telling me estimated completion time approx. 4 hours. Fingers crossed. And I'll update this once scan is completed.

Thanks for any input, if anyone has some!!

Mo

---

### Post by MG&amp;TL on 2011-11-12
That is ...interesting. For now, just unzip the archive, add the file to the folder, then re-zip.

---

### Post by moallam on 2011-11-12
Update  Now Photorec recovered 2 .gz files but I'm out of disk space on the target drive!! I switched to root and deleted all unwanted recovered files, and still I have 0 free space. Looks like photorec has created a lot of temp files somewhere, or it messed up my entire file system. Luckily I have all my stuff on an external hard disk, and actually the file I was trying to recover is on that hard disk.  So, I'll reboot now and try fsck and see if this will fix the problem. Then I can have a look at these 2 .gz files that were recovered by photorec.  Later, Mo

---

### Post by moallam on 2011-11-12
Update:

Just to clear any ambiguity. The file that got corrupted (as described in the first post) was already on an EXTERNAL drive that did NOT boot my Ubuntu. I did NOT attempt any write operation to that external drive, since I knew it could only lessen my chances of recovering the corrupted file. 

When I ran Photorec, my source was the 500 GB external drive. My target, however, was my internal HD that also booted my Ubuntu, and /home partition had approx. 100 GB free. 

Photorec, apparently, recovered 2 .gz files into the target output directory on my /home. However, it ate up all disk space. Rebooting the system, it failed to start, naturally, because it's out of disk space. Rebooting with the clean option or fsck option didn't help either. So, now i'm stuck with an external drive that has all my work that I can't write to, and a computer that has 2 recovered .gz files that I can't access because it won't boot.

Next step. Get a live CD/USB ubuntu image and see if I can access that internal HD and see what is in the recovered files. If it works, all good. If not, I'll just give it up. I'll reinstall Ubuntu on the computer probably upgrading to the latest version, and will hook up my external HD and use it normally. I'll be set back for about 2 month of financial data worth as I slacked on my backup routine, and I deserve it.

One thing I know now for sure, the integrated archive manager that comes with Ubuntu stinks big time.

I'll keep you posted.

Mo

---

### Post by nhasian on 2011-11-13
I duplicated your experiment on Ubuntu 11.10.  I created four text files.  I put three of them into a .zip file and the same documents in a .tar.gz file as well using the built in File-Roller 3.2.1

then I drag and dropped the fourth file into both of the archives.  after  I examined both archives they both contained all four files.

I attempted to create a .gz archive but I was only given that option when selecting a single file.  When I tried to compress 3 files together I was not given the option to use .gz  I suspected this was a limitation of gzip and then I discovered this:

[http://www.gzip.org/#faq16](http://www.gzip.org/#faq16)

> 
Can gzip compress several files into a single archive?
Not directly. You can first create a tar file then compress it: 

> **moallam said:**
> 
I was trying to copy a file from the desktop into a folder. I accidently released the mouse while hovering on a .gzip file.

The ubuntu file system did not just add that file into the .gizp file. It deleted all the contents of the .gzip file and now the .gzip file only contains the file that was accidently moved into it.

Is this a normal behavior of the ubuntu file manager?

---

### Post by moallam on 2011-11-13
> **nhasian said:**
> ... and then I discovered this:

[http://www.gzip.org/#faq16](http://www.gzip.org/#faq16)

Thanks for the enlightenment, but that doesn't help my case, does it?

Ubuntu file/archive manager subsystem should warn users when they are moving files into a .gz file, not just let them inadvertently erase their original contents without warning. So, I'm still sticking to my conclusion that the current state of affairs stinks.

I just hope getting this info out here would help some poor soul to  understand what has happened to their .gz file and warn others to be  extra careful when using their mouse for file operations when a .gz is  involved. And may be, just may be, alert Ubuntu developers to include "a your xxx.gz is being replaced" warning as a feature in future releases, instead of fighting over unity vs classic gnome!!

At any rate, if you can tell me of a sure way to recover that lost file that was inside of the .gz, I'd really appreciate it. If you can tell me of a way to recover from the mess Photorec created while recovering my files, so that I'm able to boot this computer again, and save me the hassle of going in with a live CD and then an OS reinstall, I'd really appreciate that too.

Thanks,
Mo

---

### Post by carranty on 2011-11-13
I've not been able to replicate this issue in 10.04, when I drop a new file on an existing .gz file, it just adds the file to the archive, in addition to the previous contents - it doesn't replace them.

This is really weird behaviour and I don't think its the norm.  Sorry I can't be of more help.

---

### Post by nhasian on 2011-11-13
> **moallam said:**
> 
At any rate, if you can tell me of a sure way to recover that lost file that was inside of the .gz, I'd really appreciate it. If you can tell me of a way to recover from the mess Photorec created while recovering my files, so that I'm able to boot this computer again, and save me the hassle of going in with a live CD and then an OS reinstall, I'd really appreciate that too.

Thanks,
Mo

You can try to free up some disk space with:

Sudo apt-get clean

I know you said that the Photorec output went to your home directory but did it put its working files in /tmp?

---

### Post by moallam on 2011-11-14
> **nhasian said:**
> You can try to free up some disk space with:

Sudo apt-get clean

I know you said that the Photorec output went to your home directory but did it put its working files in /tmp?

I don't know. I got the Ubuntu 10.11 live CD and booted with it. I can access the internal HD now, and it seems that the 2 recovered .gz files are the ones that are taking up the disk space. I checked /tmp and it's empty. Still, I can't delete them (or any other files for that matter) to empty some disk space. Needless to say, I already transfered the files to another computer and their content was badly corrupted and worth nothing. So, I guess I'm done trying to recover the lost .gz

However, I don't know how to boot with live CD and invoke sudo apt-get clean. I guess I need to assign some working space, but I don't know how to do that.

In addition, when booting the computer now (I mean regularly, not with the live CD), there's a a new error message telling me that "Install Problem: The configuration defaults for GNOME Power Manager have not been installed correctly. Please contact you computer administrator"

Can you help me
1. delete files on the internal hard disk, while I'm booting with the live CD?
2. troubleshoot that new error message, provided that I know I have a bad battery on that notebook, and I keep it hooked up to AC power at all times.

Thanks for your support.
Mo

---

### Post by MG&amp;TL on 2011-11-14
```
apt-get autoremove
```

as well for disk space.

---

