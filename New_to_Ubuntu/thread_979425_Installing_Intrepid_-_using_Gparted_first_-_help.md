---
title: "Installing Intrepid - using Gparted first - help"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by Orographic on 2008-11-11
Hi all,

My problem:

I currently have Hardy installed and am very happy with it but want to have a look at Intrepid. The easiest way for me at the moment to image my Ubuntu installation is to use Acronis TI but the Intrepid install utility uses a different formatting approach and makes Acronis backup sector by sector. This equals very slow backups.

See initial thread here from someone else:

[http://ubuntuforums.org/showthread.php?p=6103957](http://ubuntuforums.org/showthread.php?p=6103957)


My solution: (for now, will try other options as time permits)

I have Parted Magic and want to use Gparted to prepare this disk for an Intrepid install rather than letting the Intrepid utility format my disk.

The help I need:

What do I need to tell Gparted to do so as to manually prepare my disk for Intrepid? And once I have prepared the disk properly, do I just insert the Intrepid CD and opt for manual partitioning?

This is an internel test harddrive that I play around with so it doesn't matter if errors are made but obviously I do want to have Intrepid running ASAP.

Thanks all in advance. I'm more than happy to help others with this issue as it arises if I can get some help on this issue. :)

---

### Post by Tatty on 2008-11-11
Im not quite sure what you mean by getting the hard drive "prepared" by gparted.

To install intrepid, all you need is a free partition on your drive. If you do not want to remove hardy then simply create a new partition with gparted and install intrepid to that.

Did that help, or have I misunderstood what you are asking?

---

### Post by Orographic on 2008-11-12
Hi there,

Thanks for your reply. I'm very new to Linux but am a quick learner. 

I want to remove Hardy from the current drive I am on and then install Intrepid but I want to partition this drive via Gparted instead of letting the Intrepid installer do it. This is the only way to allow Acronis TI image Intrepid the normal way without having to do it sector by sector which takes hours.

So, when Gparted starts up what do I do?

Do I just set up one partition as ext3?

What will happen when I then insert the Intrepid live CD?

---

### Post by Tatty on 2008-11-12
You will have to boot to a live CD before you can edit the partitions.  You cannot change the partitions on a mounted partition.

So boot into your live CD then go to System->Administration->Partition Editor, which will load up gparted.

Then delete hardy and create a new ext3 partition for Intrepid.

Start the installer then select manual partitioning in the editor and then select the partition you just created.

Is Hardy currently the only partition on your drive?  It will make it easier if it is.  If not then dont worry, just be careful that you select the right partition :)

---

### Post by Orographic on 2008-11-12
That was clearly explained, thanks. Yes, Hardy is the only partition. Will give it a go now. I can always quickly restore Hardy in five minutes via Acronis TI if the new install falters.

Will report back as time allows.

---

### Post by Orographic on 2008-11-12
Hmm, no luck. I did exactly as you said but when I selected the new Ext3 I created for Intrepid it said, 'No root file Detected' and something like 'Please correct this in the Partition Editor'.

Any thoughts?

Luckily I was able to restore Hardy via Acronis in five minutes, so no harm done.

Was I supposed to only delete the ext3 partition where Hardy was or the swap file, extended partition too?

---

### Post by Orographic on 2008-11-12
Anymore thoughts in this problem from anyone?

---

