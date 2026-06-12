---
title: "data files overwritten and swap partition hosed"
date: 2012-03-17
forum: New to Ubuntu
---

### Post by bwrth on 2012-03-17
Hi, just wanted some input on a problem I have just experienced before I try fixing it. I'm running Lubuntu 11.10 on a dual-boot laptop (with WinXP Pro). It's a HP/Compaq 6720s laptop with a single 80Gb drive which was partitioned up as follows:

/dev/sda1   NTFS   30 Gb with Windows XP Pro
/dev/sda2 extended 45 Gb with
      /dev/sda5 ext4   24 Gb  with Lubuntu 11.10
      /dev/sda6 swap    6 Gb  Linux swap space
      /dev/sda7 NTFS    partition for documents needed by either OS

I lost some documents the other day. I was downloading an old comedy film with JDownloader. By default, this is set to open up an archive (using the default Lubuntu install of Archive Manager) once it has downloaded all the parts. I was away from the computer when it did this. I came back and saw it had finished downloading but that the automatically-extracted film did not play. Then I noticed the hard drive was showing as full, so I figured there had been no room left to fully extract the file.

I made some space by backing up a largish file (gNewSense ISO) to a USB disk before deleting it from the HD. Re-extracted the film and this time it worked. At some point during this (I now forget), the bookmarks (ie. favourite locations I had stored) in the file manager disappeared. So it seemed some data had been overwritten. The next day, I tried opening up XPad where I had two weeks of notes I'd made since first installing Lubuntu. I found that all my notes were lost. Later, running gparted, I saw the swap partition was showing as having an 'Unknown' file system, suggesting damage.

Before I reformat this swap space, I thought I'd better ask here in case anyone had any thoughts on what occurred (beyond 'make sure you have enough HD space in future' and 'back-up anything important'! :-)) and what I might do to try and fix it. I'm guessing there's no likelihood of retrieving the lost XPad data and that the text isn't 'somewhere' in the swap file.

The whole thing is not a massive issue but I do feel slightly aggrieved that the software (either OS/kernel or JDownloader or Archive Manager or even XPad) have not 'respected' my user data. I have been in a similar HD-run-out-of-space situation before on XP and never lost any personal data. Feeling less trustful of the new system as a result.

---

### Post by Jon Monreal on 2012-03-17
Hello,

Have you used the Windows XP installation lately? Are you sure there are no problems with that which could indicate problems with the HD itself?

I have to wonder if running out of space wasn't the problem but a symptom of larger problems with the disk or OS (that is, you may not have actually run out of space).

---

### Post by winh8r on 2012-03-17
If you boot your machine from a live cd, and open a terminal and enter

```
sudo apt-get install testdisk
```

then run 

sudo testdisk

and allow it to detect the partition in question it should show up all the files that are there (in green) and all the deleted files (in red) and you can try to recover them from there.

If you have no luck with testdisk, it has a second part to the program called photorec which you can set to recover specific types of files from a deleted or damaged filesystem.

You will need to recover the files to a different drive/partition to where they are being recovered from.

More info on testdisk/photorec is available here:

[http://www.cgsecurity.org/]("http://www.cgsecurity.org/")

read the instructions through carefully before proceeding and you should manage to get your data back.

Hope this helps you.

---

### Post by bwrth on 2012-03-26
Thank you for the replies, guys. 

I checked the Windows partition and it works fine, though I almost never log into it these days and try to exit as quickly as possible when I do!

I was impressed by TestDisk and, especially, PhotoRec - they are very handy to know about. Was able to retrieve a lot of files though not the lost notes. Never mind.

My swap partition is another issue though, and I will set up a new thread for that, I think.

---

### Post by oldfred on 2012-03-26
Swap is totally unformated space so it should not show a format.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
HOWTO: Use swapfile instead of partition and hibernate 
[http://ubuntuforums.org/showthread.php?t=1042946](http://ubuntuforums.org/showthread.php?t=1042946)

---

### Post by jerome1232 on 2012-03-26
Gparted begs to differ, it should show as linux-swap

---

### Post by oldfred on 2012-03-26
@jerome1232
You are correct, it should show as type 83 or linux-swap.

---

### Post by bwrth on 2012-03-29
Thanks for the further replies.

So I reformatted the swap partition in GParted running from a 'live Lubuntu' stick and it formatted ok to linux-swap format. However, it showed up as Unknown when I next checked upon rebooting.

I now think my swap space shows up as Unknown format because I chose to encrypt my home directory when installing Lubuntu. I think I read that this would cause the Unknown format message? Can anyone confirm please? Thanks.

---

