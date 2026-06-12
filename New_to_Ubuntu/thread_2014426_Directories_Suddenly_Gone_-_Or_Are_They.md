---
title: "Directories Suddenly Gone - Or Are They?"
date: 2012-07-01
forum: New to Ubuntu
---

### Post by In2Blues on 2012-07-01
I'm running Ubuntu 12.04 LTS on a dual boot system with Win7.  I don't know a lot about Linux so am very careful with "sudo" and follow all help directions to the letter so as not to damage anything.

Yesterday I was attempting to copy several files from a USB stick to an external HD (NTFS) using Nautilus.  It froze and I couldn't do anything but reboot with the little button on the front of my computer. ;)

I tried again and the same thing happened, so I booted into Win7 and tried it there.  Also froze.  Used the little button again and rebooted to Ubuntu.

I suddenly realized that my two biggest directories -- Documents02 and Downloads02 -- on my external HD were completely gone.  Hundreds of files no longer there.  The strange thing is that these two directories were not connected in any way to the directory that I was copying to.  Yet, the one I was copying to is fine.

I Googled for help and tried several solutions, including Foremost.  Foremost did seem to "recover" several files, most of which I couldn't even open, but there are many, many more missing.

All the undelete utilities I've tried don't show anything that Foremost found, so I'm thinking that they're not really deleted, just hidden somehow.  I have "view hidden files" on in Nautilus, but still can't see any of them.

I've been careful not to do anything with that HD so as not to overwrite what may still be there (hopefully!!!).

Any and all suggestions will be greatly appreciated, as most of these files are non-replaceable.

Thanks in advance.

Terry

---

### Post by NikTh on 2012-07-01
Yeap . This is NTFS (Not Trusted File System) from $MS. I was in the same situation some months before , with an ext HDD (ntfs) and windows OS. I lost all of my data (lot of movies) and unfortunately didn't recover. 
I will suggest you to try testdisk (if you didn't already) .  [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
Good Luck with you files.. i know the feeling

---

### Post by In2Blues on 2012-07-01
I did try TestDisk., but to no avail.

Thanks anyway.

If it was only movies, I wouldn't be so upset.  But it was all of my documents and downloads.  :cry:

Terry

---

### Post by cryptotheslow on 2012-07-01
As above - try the recovery programs in the testdisk suite. Testdisk itself is for recovering entire deleted partitions. However it brings with it a program called Photorec which despite its name can recover a lot of different file formats.

When in Ubuntu open a Terminal and install the testdisk suite with:
```

sudo apt-get install testdisk

```

Then take some time to read through the walkthrough for Photorec here:

[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

Just make sure you pick the right device to recover from and write the recovered files somewhere that isn't on the device you are trying to recover from!

Good Luck

---

### Post by In2Blues on 2012-07-03
Thanks for the info.

I tried Photorec and it recovered a lot of stuff, but nothing in proper folders and nothing with the original names.  It also marked a lot of files as text files that aren't text files.

What a mess.  I may have to resign myself to a loss of thousands of files.  Irreplaceable stuff.  

Terry

---

