---
title: "HOWTO: Resize your HFS+ partition for free"
date: 2005-11-14
forum: Outdated Tutorials &amp; Tips
---

### Post by closet geek on 2005-11-14
Just thought I'd share my success.

You may have been pondering buying tools such as iPartition or VolumeWorks to shrink your OS X partition enabling you to install Ubuntu. There is no need to spend your hard earned $$$ as 'parted' can do this for you for free.

Getting started:

You must login to OS X and disable Journaling on your hard drive. To do this, launch Disk Utility, select your drive and click File -> Disable Journaling. It should be noted that I had some issues with this: Disk Utility claimed my file system was Journaled but at the same time wouldn't allow me to disable it. The work around is to launch a shell and type:

```

cd /Volumes/

```

then type:

```

ls

```

this will show you all the Volumes on your computer, make sure you note the name of the Volume you want disable Journaling on. In my case it was called  "Macintosh HD".

Run this command:

```

sudo diskutil enableJournal Macintosh\ HD/

```

of course replacing Macintosh HD with your Volume name. Bear in mind that the above is not a typo, it is supposed to read "enableJournal" even though we are trying to disable Journaling, this is due to a bug (in at least my Tiger install) that labelled the Volume as Journaled when it wasn't. After you have run the above run:

```

sudo diskutil disableJournal Macintosh\ HD/

```

verify that it says Journaling has been disabled.

Now reboot your Mac ensuring you have your Breezy install CD in the CD drive. Just after you computer starts to boot up (e.g. before you even see the grey screen with the Apple on it) make sure you hold down the "c" key. This will make your Mac boot from the Breezy CD.

Follow all of the Breezy install steps up until the partitioner. Instead of clicking "Continue" hit "Go Back" this should take you to a screen with a small list of options. From here you want to select "Go to a Shell".

Once the shell has started type: "parted", from here I can't give you exact instructions as these steps might vary slightly depending on your setup but for me I then typed:

```

print

```

this showed me my list of partitions, locate the partition you want to resize (it should be obvious) and note down the "Minor" number. Then in parted type:

```

resize MINOR_NUMBER_HERE START_BLOCK_SIZE_FROM_PRINT_OUTPUT NEW_END_BLOCK_SIZE

```

I do apologise if this step makes no sense, but it should be clear from the "print" command what I mean by my caps'ed underscored commands. My final resize command ended up looking like this:

```

resize 3 128.032 37237.821

```

at which point I hit enter and was rewarded by a warning message that went something along the lines of:

> 
I have detected an HFS+ system with some strange characteristics, in theory I can still shrink this but it's still experimental, please email me if it all goes wrong

I hit "I" to ignore this message and let parted try and shrink my HFS+ partition. Literally within 2 seconds I was back at a parted prompt. Having experienced how long it takes PartitionMagic to shrink an NTFS partition I was assuming the worse! However hitting the "print" command again showed me parted (at least) thought it had resized my partition successfully.

Hit "q" then type "exit" to return to the installer where you should then return to the partition tool hopefully now with some free space you can install your Breezy on. All worked like a charm for me, I'm now dual booting Tiger and Breezy.

Hope this helps.

cg

---

