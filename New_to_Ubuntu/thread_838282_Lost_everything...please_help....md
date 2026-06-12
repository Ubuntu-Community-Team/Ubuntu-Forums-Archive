---
title: "Lost everything...please help..."
date: 2008-06-23
forum: New to Ubuntu
---

### Post by kam.samji on 2008-06-23
Hi. Just when i was getting teh hang of things...i mess up!! Here's my problem..

I have a small windows partition and a larger Ubuntu partition working perfectly..until...

_**Pre Weekend:**_
I was trying to clean up the windows partition so i could doa  resize of both partitions...In using Windows' own "Clean Up" option, I managed to get rid of lots of temp files, Yippee I thought...except on reboot Windows would not start. Came up with a black "can not find boot" or somethign like that. Basically telling me it could not load up Windows. Told me to load my Windows installation CD and choose 'Repair'.

I did this and standard warning came up about data loss etc, but it specifically referred to the Windows Partiion...(should have gone with my gut feeling and backed up Ubunut, but hey..). Anyway, after teh end of the painful process, I had a brand ne installation of Windows Vista on teh FULL HD!!! No Ubuntu to be seen anywhere!

**_Post Weekend_**
I have since run Ubuntu Live CD and installed the latest Ubuntu and rejigged teh HD to make it dual boot. I have also updated Ubunut using Update Manager. Not done anything else.

the reason I write is that it just occurred to me, that I may be able to recover some data (if it's not too late). Not worried about music or photos (that would be a bonus), but more about emails and documents (Thunderbird and Open Office (Spreadsheet).

If anyone can help, then I would be grateful. I am fairly competent honest (it was windows that deleeted the files, not me, honest!!), although, I'm not so hot on this Command Line stuff yet, so that may need explaining.

Many Thanks

Kam.

---

### Post by hyper_ch on 2008-06-23
you will need an recovery tool like photorec ([http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)). I just know photorec right now because it was recommended a few days ago to "circumvent" the dangers of the gpcode virus (this virus will encrypt .txt, .pdf, .doc, .jpg, .* files on windows and then delete the original files. As they can't break the encryption [yet] they suggest to recover the deleted files).

I have also used a long time ago r-studio ([http://www.r-studio.com/](http://www.r-studio.com/)) when I accidentally deleted the wrong partition ;) I konw, it happens to me also and one should always have backups ....

Important thing right now, if recovery is important: UNPLUG THE HARDDISK, get a new harddisk and install an OS on there. The more you use the harddisk that you want to recover data from, the harder it gets.

---

### Post by sydbat on 2008-06-23
It seems the option you chose from the Windows CD was to reformat your hard drive. If you had more than 1 partition before and now only have 1 partition total, anything you had on that computer is gone. Unless someone here knows anything about time travel...

---

### Post by kam.samji on 2008-06-23
That's the thing, the stupid disc didn't give me an option. It just went ahead, and I could not cancel once I'd started. Yes, after the process, there was only one partition.
I'm hoping there is still a way...unfortunately, I don't have another pc. I do have a spare drive, so will try the above suggestions...plus any more that people can suggest.

Thanks

Kam

(ps - should I recover in Windows or Ubunut?)

---

### Post by muteXe on 2008-06-23
So when you reinstalled windows on one partition it actualled installed itself on the whole disk?  That is odd.  I would have expected you having problems with grub after the reinstallation of windows, but unless you chose an option for windows to use the whole drive i would have thought your ubuntu would have been there. Somewhere.

---

### Post by Duck2006 on 2008-06-23
Test disk may help to recover the data.

[http://en.wikipedia.org/wiki/TestDisk](http://en.wikipedia.org/wiki/TestDisk)

---

### Post by kam.samji on 2008-06-24
The windows disk is not an installation disk as such, it's a Recovery Disk. I had to burn it myelf when i first bought the laptop as new ones don't come with installation disks anymore! So there were no options at all...just a case of putting disc in and re-booting. I couldn't even cancel. I could have just opened the tray midway, but i thought that would have caused mor damage.

Anyway, will try the suggestions...but do i try them in Windows of Ubunut please?

---

### Post by Duck2006 on 2008-06-24
Run test disk from linux.

---

### Post by kam.samji on 2008-07-08
> **Duck2006 said:**
> Run test disk from linux.

Rigth...spent hours last night running photorec as i was more concerned about my .jpgs and Open Office docs.

The result was many, many gigs of documents which I will have to sift through.

My questions are:
1. Can I safely delete all the text files and .dll files that have come up? Also, can i safely delete all other docs that I do not obviously need? It may seem like a silly question, but I don't want to ruin my chance of getting back a .jpg because i deleted a .dll in my haste.

2. the first few .jpgs I have seen are thumbnail size and not the full ones. Am I correct in assuming that the full sized files will be there and the thumbnails are just one of many variants that were on my pc (for teh various 'views' I suspect)

I hope this make sense!

Thanks

Kam

---

### Post by xebian on 2008-07-08
> **kam.samji said:**
> Rigth...spent hours last night running photorec as i was more concerned about my .jpgs and Open Office docs.

The result was many, many gigs of documents which I will have to sift through.

My questions are:
1. Can I safely delete all the text files and .dll files that have come up? Also, can i safely delete all other docs that I do not obviously need? It may seem like a silly question, but I don't want to ruin my chance of getting back a .jpg because i deleted a .dll in my haste.

2. the first few .jpgs I have seen are thumbnail size and not the full ones. Am I correct in assuming that the full sized files will be there and the thumbnails are just one of many variants that were on my pc (for teh various 'views' I suspect)

I hope this make sense!

Thanks

Kam

Not sure how this tool works but don't delete any files.  Just copy them to a safe backup.  
If you installed your new Windows using the quick format, it probably just wiped the FAT file, and the real files are still there.  Hence you are able to see them.  But right now you are looking at the real files.  If you delete any they will be gone forever, and the next time you run Windows, they will not be there because the FAT is just a pointer to the real physical address.

---

### Post by kam.samji on 2008-07-08
> **xebian said:**
> Not sure how this tool works but don't delete any files.  Just copy them to a safe backup.  
If you installed your new Windows using the quick format, it probably just wiped the FAT file, and the real files are still there.  Hence you are able to see them.  But right now you are looking at the real files.  If you delete any they will be gone forever, and the next time you run Windows, they will not be there because the FAT is just a pointer to the real physical address.

So, are you suggesting I sift through and save what i want and then safely delete everything else? Looks like it's going to be a long night!!!

---

### Post by Duck2006 on 2008-07-08
> **kam.samji said:**
> Rigth...spent hours last night running photorec as i was more concerned about my .jpgs and Open Office docs.

The result was many, many gigs of documents which I will have to sift through.

My questions are:
1. Can I safely delete all the text files and .dll files that have come up? Also, can i safely delete all other docs that I do not obviously need? It may seem like a silly question, but I don't want to ruin my chance of getting back a .jpg because i deleted a .dll in my haste.

2. the first few .jpgs I have seen are thumbnail size and not the full ones. Am I correct in assuming that the full sized files will be there and the thumbnails are just one of many variants that were on my pc (for teh various 'views' I suspect)

I hope this make sense!

Thanks

Kam



Yes delete every thing that you don't need, and save every thing that you want to keep.

---

