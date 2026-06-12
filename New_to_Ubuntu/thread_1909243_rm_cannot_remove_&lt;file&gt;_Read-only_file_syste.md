---
title: "rm: cannot remove &lt;file&gt;: Read-only file system -- But it's not!"
date: 2012-01-14
forum: New to Ubuntu
---

### Post by Birchle on 2012-01-14
I have no idea what just happened, or why, but I'm more than a little frustrated at it all, so please bear with me...

I have a dual-boot system, Win7 and Ubuntu 11.04, with two other FAT32 data partitions.  Those two partitions auto-mount when I start Ubuntu; someone from here helped me with that previously.  This is what they look like at this precise moment:
```
$ mount
/dev/sda6 on /media/MEDIA type vfat (rw,utf8,dmask=007,fmask=117,uid=1000,gid=46)
/dev/sda8 on /media/DATA type vfat (rw,utf8,dmask=007,fmask=117,uid=1000,gid=46
```There are a whole bunch of other lines that I don't recall seeing previously, as well, but that could be my faulty memory.  Let me know if you need them anyhow.

So, the actual problem:
I hibernated Ubuntu earlier today, and booted into Windows for a while.  On returning to Ubuntu, I went to check my email in Thunderbird, and was told that the folder was inaccessible due to an incorrect or too-long path (I don't remember the exact error anymore, sorry).  I tried to restart Thunderbird, and instead got the error that there was something wrong with the browser's security component.  Closed everything and restarted the computer, just in case something got messed up in the hibernate...  And got the same error again -- for both Thunderbird and Seamonkey.  Thunderbird and Seamonkey have their profile folders saved in one of the auto-mount FAT partitions.

I did find this ([http://kb.mozillazine.org/Could_not_initialize_the_browser_security_component](http://kb.mozillazine.org/Could_not_initialize_the_browser_security_component)), which is the error I'm getting, and looks plausible -- but it only has instructions for Windows.  And I'm not sure if any of those reasons are accurate, either.  If I check the permissions of the cert8.db file, both TB and SM tell me
```
Owner: read and write
Group: plugdev: read and write (what is plugdev?)
Other: none
```So the "not read-only" part doesn't seem to be the problem.  Perhaps it's corrupt?  So I tried deleting it -- it's greyed out in the file manager, so I tried sudo rm through the command line (though I own the whole partition anyhow, so there's no reason I should need sudo in the first place), and got
```
rm: cannot remove `cert8.db': Read-only file system
```Who knows if it's corrupt, I can't delete it anyhow!

I also tried to create a backup copy of the whole profile folder before messing with things, and when it tried to copy cert8.db, it failed with the error
```
Error splicing file: Input/Output error
```I found several threads suggesting that there might be a problem with the partition, that it's mounted read-only, even if the file itself isn't set to read-only, but the partition says it's mounted read-write (I believe), and it's worked fine for months, as well.  So what suddenly went wrong tonight?  And how can I fix it without losing all my browser history, bookmarks, saved tabs, e-mails, etc?

---

### Post by CharlesA on 2012-01-14
Run a chkdsk from Windows on those two FAT32 partitions to make sure there are no errors, then reboot and try accessing them again.

---

### Post by Birchle on 2012-01-14
> **CharlesA said:**
> Run a chkdsk from Windows on those two FAT32 partitions to make sure there are no errors, then reboot and try accessing them again.
Can do (though, I'm not sure how to do it...  Help?  And, why from Windows?  Does Ubuntu not have any good FAT32 checking stuff, since that's a mainly Microsoft format?), but I'm still perplexed as to why the DATA partition would report being mounted read-write, if it's actually read-only.  Any idea?

(It looks like the MEDIA partition is mounted properly.  Or at least, I was able to alter/save a random text file in there.  Too bad that's not the one that has all my more important stuff...)

---

### Post by CharlesA on 2012-01-14
> **Birchle said:**
> Can do (though, I'm not sure how to do it...  Help?  And, why from Windows?  Does Ubuntu not have any good FAT32 checking stuff, since that's a mainly Microsoft format?), but I'm still perplexed as to why the DATA partition would report being mounted read-write, if it's actually read-only.  Any idea?

(It looks like the MEDIA partition is mounted properly.  Or at least, I was able to alter/save a random text file in there.  Too bad that's not the one that has all my more important stuff...)

I'm not sure what utility you would use to check a FAT32 file system from Linux. You can run chkdsk from Windows by going to "Computer," right clicking on the drive, selecting properties and then click on "check for errors" on the tools tab.

---

### Post by Birchle on 2012-01-14
Well, it actually ran chkdsk before even booting into Windows for me to tell it to.  And it sure had a grand old time doing *something* for quite a while...  Supposedly there were no problems found when it finally booted and I told it to run again, though.

Back in Ubuntu, it looks like SM and TB both run again, now (though I wound up deleting the SM cert8.db file anyhow, since that one still gave a security error when I first tried).  Seamonkey lost all the appearance settings, though.  Not sure what else.  Thunderbird I might as well have installed from scratch, there's *nothing* in there anymore.  Is there any good way to recover things, at this point?  Or am I going to have to manually set it all up again?

---

### Post by CharlesA on 2012-01-14
Unless you had a backup of that file, you'd probably have to redo everything again.

---

