---
title: "[SOLVED] Why is copied folder always double it's size at destination?"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by Kellemora on 2008-11-19
Hi Gang

Something is bugging the heck out of me here!

I copy a folder that is 1.6 GB to a 4 gig partition.

Before copying the folder to the 4 gig partition it shows:
4.1 gig, 267kb used, 3.7 gig available.
Folder are EmptyFolderA (the one that will be copied to)
Folder Lost&Found (EMPTY)
Hidden Folder .trash (Empty)

After copying the FolderA from source to FolderA at destination.
FolderA at both locations show size 1.6 GB.
Lost&Found at Destination shows EMPTY
.trash at Destination shows EMPTY.
Partition shows 3.4 Gig used.

HOW can a 1.6 gig folder use up 3.4 gigs of Space.

I've reformatted the Hard Drive back to 4.1 gig, after it adds the Lost&Found Folder and the .trash folder and I make the FolderA I'm back to 3.7 gigs of empty space AS EXPECTED.

Somethings not Kosher here?  
Both drives are EXT3!

And there is NO TRASH at the Source (took an act of congress to empty it too!)

TTUL
Gary

---

### Post by CatKiller on 2008-11-19
Are there hidden files in the directory you're copying? The folder might actually be bigger than the 1.6 GB you're expecting.

---

### Post by Kellemora on 2008-11-20
Hi Cat

Yes there are hidden folders and they copy over too!
And they APPEAR in the COUNT ahead of the file size as well.

It's my user folder which of course contains hidden folders.
The count shows 422 files, of which, the folders are counted as files too, even if empty.

I too was thinking the hidden files were not counted, so I picked a couple of hidden files and counted them up myself.  Came up with like 432k, Rsynced them over to hdb and they ended up consuming 878k of space used up on the hard drive, but the files themselves still showed 432k.

Now I do know that if you change format styles, like use Fat32 instead of EXT3 they use more space because the filesystem is different.

It's just a major pain to make plans for things then find out you have to start over from scratch and DOUBLE everything you originally laid out!

And the not knowing WHY is bugging the heck out of me!

If the amount of space is reported wrong, it then makes copying files to fixed size media a near imposibility and would cause excessive waste of recordable media.  EG:  You plan on copying 400 or 500 megs to a 700 meg disk and find out there's NOT enough space on a blank 700 meg disk to hold 400 or 500 megs of data, because it's being reported wrong by the system.

Sound like a major BUG to me!!!!!

TTUL
Gary

---

### Post by CatKiller on 2008-11-20
Could be. I've not noticed this phenomenon.

---

### Post by mrboojive on 2008-11-20
Are there symlinks somewhere in the folder? It's possible that they could be affecting how the folder size is counted.

---

### Post by Kellemora on 2008-11-21
Hi Mr. B.

Nope, no symlinks, and I even made sure the trash was empty first too, as the .trash will copy over also.

Just playing around testing things, I reformatted the hard drive again to EXT3 and started copying folders that have NO hidden files in them.  Such as the Boot Folder that contains Grub.  It's 35.6 Mb at the source, 35.6 Mb at the destination, but is using 78.32 Mb of hard disk space on the other drive, more than double.  This seems to be consistant with every folder I've tried it on.  Both drives are IDE formatted to EXT3.  And it doesn't seem to matter if I use Copy/Paste or Rsync it over, end result is the same.

There is a good possibility it could be this older small hard drive I'm experimenting with and I don't have another one I can empty completely and reformat to conduct tests on right now.

I'm not going to mark this solved yet, to see if someone else has this problem.  But will pick up a new hard drive over the holidays here and if it don't do it on a new hard drive, then I'll mark this as solved and blame it on the hard drive itself.  Although I don't think that's it, because I was using it to store camera images and if I loaded 1 gig of photo's it only used up 1 gig of hard drive space.

Thanks for the thought though, I'll jot it down since I will be making several symlinks very soon.

TTUL
Gary

---

### Post by cariboo on 2008-11-21
When you formatted your destination drive did maybe set the block size to 2k instead of the normal 1k?

Jim

---

### Post by Kellemora on 2008-11-21
Hi Cariboo

If under the properties tab showing the hard drive as being EXT3 (1.0) in parenthesis means 1k blocks?  I don't know!

I guess I should mark this solved until I pick up another hard drive, this one is an oldie, hi hi.........

And the same problem does not occur on another not quite as old drive.

So I'm back to leaning that it's the drive again!

Me thinks I should quit messing with all these old smaller drives and buy a few Terrabyte drives.

I've been holding out because I don't know if I can trust those SATA drives yet!

TTUL
Gary

---

