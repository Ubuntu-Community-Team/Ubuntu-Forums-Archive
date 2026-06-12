---
title: "Disabling &quot;Autorun&quot; on USB Disks"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by stevebond001 on 2008-11-07
Hi
I have 2 minor issues which aren't critical, but I would like to sort them out:

1.  I have a Kingston Data Traveller 2GB USB Disk.  When I insert the disk I get a message asking me whether I want to run software on the disk, with an option of "Run" or "Cancel" (screenshot attached).  I don't want this software to run (as this is the U3 software which runs under Windows), I just want the drive to be opened in Nautilus.

In Hardy this worked OK - however in Intrepid I can't work out how to change this behavior.

2.  The USB disk actually has 2 partitions (one to run the U3 Software and one with the programs / data on).  How do I configure my PC to not mount the first partition of the drive?

Any Ideas, anyone?

TVM

---

### Post by Tim Sharitt on 2008-11-07
To disable auto run prompt:
Hit Alt-F2 and enter **gconf-editor**. When the Configuration editor comes up, expand apps and scross down to nautilus. Expand nautilus and click on preferences. On the list to the right, check the box beside media_autorun_never. This will disable the autorun prompt for all inserted media.

---

### Post by stevebond001 on 2008-11-07
Thanks very much for the tip.  I've followed your instructions and it works perfectly.  However, it doesn't open the drive in Nautilus, like it used to do in Hardy.  Is there a setting to do this?

---

### Post by Tim Sharitt on 2008-11-07
I believe the media_automount_open option (should be right above the autorun option or close to it) is what needs to be checked, but I can't say for sure.

---

### Post by stevebond001 on 2008-11-07
Tried that but no joy.  I even un-ticked and re-ticked it but this still made no difference:(

---

### Post by mc4man on 2008-11-07
If that doesn't work - 

 What I see here is while it would seem logical that enabling 'media_automount', 'media_automount_open' and 'media_autorun_never' would do what your looking for it seems to also prevent flash drives from auto opening.
So I'd uncheck 'media_autorun_never' (ck. the other two

In the case of U3 partitions I've never seen them trigger the 'autorun' prompt. That partition is seen as a "SCSI CD-ROM" and isn't 'mounted' (run sudo lshw -C disk with the flash drive in to see.

What I'd look for is a file in your data (SCSI Disk) partition that's triggering the prompt. Obviously anything named autorun would qualify.

---

### Post by stevebond001 on 2008-11-10
Both partitions have "launch.exe" on them, so I guess that that's why the U3KINGSTON partition (the one I want to open) isn't opening?

I'm a bit perplexed as to why the default behavior has changed from Hardy to Intrepid - in Hardy the volume just opened.

---

### Post by stevebond001 on 2008-11-10
This gets stranger.....
When I unticked the 'media_autorun_never' button, the next time I plugged the USB Disk in I was prompted (for both drives) for what to do each time the drive was plugged in.
So I selected "Do Nothing" (don't ask me again) for the U3 System partition, and "Open Folder" (don't ask me again) for the U3KINGSTON partition.
I thought that would cure it, but when I plug the disk in now, both partitions still get loaded but neither of them open automatically in Nautilus.](*,)

---

### Post by eldragon on 2008-11-10
im about to rant, and rudely, so, if you are too sensitive, dont keep on reading.

.



.




..






.





**[SIZE="5"]WHO THE **** THOUGHT THAT IMITATING WINDOWS'S BEHAVIOUR TOWARDS AUTOSTARTING REMOVABLE MEDIA WAS A GOOD IDEA?![/SIZE]**

its one of the main source of virus transmission on windows. we dont want that here. no sir.

---

### Post by stevebond001 on 2008-11-10
All I want is for it to open automatically when I plug it in - That's not too much to ask for, is it?  :(

---

### Post by rbc on 2008-11-10
Unless you find it useful while running Windows, get rid of that U3 partition. It is the first thing I do when I get a thumb drive. [http://www.u3.com/uninstall/default.aspx](http://www.u3.com/uninstall/default.aspx)
The uninstall process should restore everything that is on the data partition, but make a backup just to be safe

---

### Post by stevebond001 on 2008-11-10
Thanks for the advice, but as I also use this on Windows based PCs I still need the U3 stuff.

It must be a combination of switches in the gnome config editor - I'll have a play around and see if I can bully it into submission.

---

### Post by Coreo on 2008-11-12
Here, this might be something close...

In Nautilus, go to Edit > Preferences. Go to the Media tab.

Under there you can choose what happens when media is inserted.
I have the box "Never prompt or start programs on media insertion" checked, and "Browse Media when inserted" checked as well.

Is this close to what you were looking for?

---

### Post by Coreo on 2008-11-12
I have a similar problem to what you were having.

Whenever I turn on my external harddrives and they are mounted, autorun pops up to tell me that there is software intended to run automatically.
Like you, I'd rather it just open the drive and forget about the autorun thing.
Ideally, there would be a way to set it individually for each drive. Because sometimes you want your flash drive to autorun, but never for external harddrives.
This is all an ideal situation, of course.

---

### Post by stevebond001 on 2008-11-13
Coreo
Many thanks for the advice

With your suggestion and a little tinkering, I now have the mounted drive opening when I insert it.  Here's what I eventually did:

1.  In Nautilus, go to Edit > Preferences. Go to the Media tab.
2.  Uncheck "Never prompt or start programs on media insertion".
3.  Check "Browse Media when inserted".
4.  Open the Gconf editor (Atl + F2 and type gconf-editor)
5.  Navigate to  Apps/Nautilus/Preferences.
6.  Edit the "media_autorun_x_content_ignore" key and remove all entries.
7.  Edit the "media_autorun_x_content_open_folder" key and add "x-content/software" to the key
8.  Close the Gconfig editor.

Now, when I insert the USB stick, Autorun does not appear and the volume opens for viewing............  Simple really, don't know why I didn't think of it sooner 	:roll:

My only (slight) niggle is that as my U3 USB memory stick has two partitions (one for the U3 program and one for the data) I can't suppress the partition with the U3 System from being displayed (as I only want to see the data partition).

Ah well, I guess I can't have it all.

Thanks for your help anyway.  Hopefully the above will help you with your external hard disk.  Let me know how you get on.

---

### Post by Coreo on 2008-11-14
Oh the wonderful solutions that we can come up with when we work together....haha!

Thanks stevebond001. I seem to have it all working now.
I did the same thing as you, to see if that worked.
The first time I reconnected my external HD, it popped up with the "Photo Manager" autorun. This was because under the Nautilus Preferences>Media tab, I had Photos set to ask me.

When it popped up, I just had to select "Do Nothing", and checked "Do Not Ask Again".

Should work great from now on!

Except there is one thing....the exact same problem as you with your U3. My harddrive is partitioned to have a reserved area called Exchange, which is where files can be dropped to "exchange" them between windows and Linux. Unfortunately, whenever I connect my HD, this partition opens up as well. It's not a huge problem, it's just another window to close.

Maybe we'll sometime figure out a way to suppress the opening of specific partitions....


Thank you for your help too!
I couldn't have got my fix without your help as well.  :D

---

