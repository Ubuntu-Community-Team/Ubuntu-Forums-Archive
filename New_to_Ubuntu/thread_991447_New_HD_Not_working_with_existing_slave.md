---
title: "New HD Not working with existing slave"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by carusoswi on 2008-11-23
Don't know if I should post this problem here or not, so, if it's the wrong place, please forgive me.

Anyhow, I run a dual boot with XP and ubuntu.

Decided to put in a new drive.  My slave drive is a 320 gb Western Digital, so I purchased a 500 GB WD for my new Master HD.

Just to be certain I absolutely could not overwrite important data on that drive, I pulled it out of the system (by disconnecting the data and power supply cables before preparing my new drive and installing XP and Ubuntu.

Spent most of the afternoon getting my Ubuntu partitions just the way I wanted them (that's another story), and, when everything was working just the way I wanted it to work, I replaced the cables on my 320 gb slave drive, closed everything up, booted her up, and was sitting back admiring how much new storage space I now have when I noticed that the slave drive was not showing up.

Re-booted and went into my machines setup, sure enough, slave on 0 is showing none.

Pulled everything apart, checked my connections, nothing would make this drive work in the system.

I have both drives set for cable select.

Tried placing that slave into an external ADS box, it would not enumerate when I plugged in the firewire cable.

Tried setting the new drive as master, the slave as slave.  This caused the new drive to show up with nonsense characters, and the machine would not boot.

Now, I'm thinking two drives are messed up.

Pulled the slave out of the system, booted to the new drive, worked fine.

As a last resort, I plugged the old master (a 120 gb seagate) back into the system with the slave online - put everything back the way it was before I had my bright idea to install a new drive, everything worked fine.

So, what's really going on here?

Could I have bumped up against some sort of max HD capacity for my machine?  That doesn't really make sense to me.

The new drive is partitioned with 137gb going to Windows, 43 gb going to Ubuntu in three partitions, with one 397 gb NTFS which I had planned to share between the two OS's.

This seems to work fine when the new drive is the only drive in the system.

Things go really south when I hook up the 320 gb WD as slave.

I figured to similar drives should work fine together.

Something else that surprised me was that I got those nonsense characters when I plugged the old drive back in a master one time.

What would cause these problems?
Am I doing something wrong, or is some other component on my machine failing.

The computer is a Shuttle XPC S56G.  It's been working just fine for four years or so.

Advice highly appreciated.

Thanks.

Caruso

---

### Post by CatKiller on 2008-11-23
Set the drive that you want to be Master as Master with the jumper, and set the Slave to Slave with the jumper on that one. *(There may be different jumper settings for Master and Master-with-another-drive - some drives have this and some drives don't)* Cable Select usually works, except when it doesn't. Also, there is a Master end and a motherboard end of IDE cables. I don't know if your one is labeled or coloured.

I have seen gibberish descriptors for drives with the jumpers incorrectly set; when it was set up, the drive was fine, so you don't need to fear for your data just yet.

Edit in *italics*.

Edit 2: I've just seen that you said you'd set the jumpers. Do you have the Master-with-another-drive-attached option? Have you tried a different cable, or a different channel? Or one drive on each channel?

---

### Post by nhasian on 2008-11-23
first of all, you should set the jumpers on the drives.  dont leave them on cable select.

Set one for Master and the other as Slave.  Some drives have a Master/Single jumper, and sometimes it is different if its just a single drive on the cable so check the diagram on your drives.  

Once you have set the jumpers for all your drives, plugged in the data and power cords, make sure your bios sees all the drives properly.

Once the bios sees as your drives properly, let us know if there are any hiccups.  For example, if you removed a drive while installing ubuntu you wont have a line for it in your /etc/fstab file and will have to mount the HD manually or add the line to your /etc/fstab file so it is automounted on bootup.

---

### Post by carusoswi on 2008-11-23
Thanks for the quick replies.
I found the problem (how do I mark a thread soved?).
I swapped out the data cable for another from an old box that I've been using for parts - problem solved.

When the slave drive kicked in and mounted itself on an earlier attempt, I new that the problem could not be jumpers, and perhaps not the drive, although, if it were failing, I don't know how it would behave.

This self mounting took place after I opened this thread.  Figuring that, somehow, the problem magically disappeared, I dutifully reinstalled the sound card (which I had been leaving out as I swapped drives in and out trying to trouble shoot the problem), put back all the screws, put the cover back on, only to discover that the problem was back.

I had noticed that my drive activity light had stopped functioning properly about a month or so ago.  It would light up briefly when the machine was turned on, but then, would not light when there was drive activity.  I notice that, having replaced the data cable, the light is functioning normally again.

I guess being all scrunched up inside that little box may have caused a break in one or more of the wires.

Anyhow, everything is working now.  This is the first time I've ever experienced this problem.  I have to tell you, I didn't want to spend five frustrating hours of my day chasing it down, but, I will know this symptom the next time I see it.

Thanks again for your help.

Caruso

> **nhasian said:**
> first of all, you should set the jumpers on the drives.  dont leave them on cable select.

Set one for Master and the other as Slave.  Some drives have a Master/Single jumper, and sometimes it is different if its just a single drive on the cable so check the diagram on your drives.  

Once you have set the jumpers for all your drives, plugged in the data and power cords, make sure your bios sees all the drives properly.

Once the bios sees as your drives properly, let us know if there are any hiccups.  For example, if you removed a drive while installing ubuntu you wont have a line for it in your /etc/fstab file and will have to mount the HD manually or add the line to your /etc/fstab file so it is automounted on bootup.

---

