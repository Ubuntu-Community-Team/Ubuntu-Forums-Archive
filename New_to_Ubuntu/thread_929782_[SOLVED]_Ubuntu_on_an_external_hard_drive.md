---
title: "[SOLVED] Ubuntu on an external hard drive?"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by h4nn4h on 2008-09-25
Hello everyone,

I'm very new to ubuntu, and linux in general (if that even is a correct sentence, I really don't know anything about it), and obviously to this forum to. So hi, and please tell me if my question has been asked a thousand times before!

I've always used windows (XP), but I really like the idea of linux. So I want to give Ubuntu a try (it seems to be the most popular/easy to use for beginners), but I'm not ready to let go of windows entirely before I'm sure it's right for me. Windows is installed on my internal hard drive (C:), and there's only 5 GB free on that one. That's why I would like to install Ubuntu on my external hard drive (E:). It's 250 GB, 150 GB of which are currently free. Is this possible, without losing the already existing data? I googled a bit about this, but I can't find any information that is really "beginner" enough for me. I'm not an idiot computer-wise, but hardly a genius either...just an avarage user who has no experience with linux at all.  Please tell me how to get started :-)

---

### Post by h4nn4h on 2008-09-25
ps: I should probably say, I already downloaded the installation cd, gave the demo a try (I liked it!), and clicked "install", but when I came to the warning that data would be destroyed I aborted the process.

---

### Post by eddVRS on 2008-09-25
Hi h4nn4h, welcome. Glad you like Ubuntu when you ran it from the disk.

Have a read of this: [http://ubuntuforums.org/showthread.php?t=80811](http://ubuntuforums.org/showthread.php?t=80811)  it might help you answer your question.

It might be wise to make a backup of any important files, and do a defrag in Windows. You will at some point be given the option to partition the drive so that you can install Ubuntu

Good luck, let me know if you run into dificulties :)

---

### Post by keplerspeed on 2008-09-25
Firstly, yes you can boot from an external hard drive. see here [http://ubuntuforums.org/showthread.php?t=80811](http://ubuntuforums.org/showthread.php?t=80811) but as you dont want to loose data off your external hd you will have to partition the external hd, format the partition to ext3 for example and install ubuntu there. However, you will need to ensure your computers BIOS settings are set to boot from USB otherwise you will have to press f10 or whatever it maybe on boot to change your boot order. This 'should' all be possible from the installation cd.

---

### Post by h4nn4h on 2008-09-25
Thanks for the quick reply!

The main problems are that
a) I've never partitioned a hard drive before and
b) I think my BIOS doesn't have that option, to boot from a USB device. My computer is about 5 years old, but after I added some extra RAM earlier this year (I now have 1 GB of RAM instad of 256 MB) it works as good as new and I'm not going to replace it any time soon. 

Should I put away my Ubuntu-dreams (:D) or is there a way around these problems (especially b, a I could probably figure out myself)

---

### Post by snowpine on 2008-09-25
Hi there, since your computer can't boot from the USB, my recommendation is to install Ubuntu in the free 5gb on your hard drive. You can set up a "dual boot" so that you can choose between Ubuntu and Windows each time you boot. With 5gb, you would not have much room left over for documents, but you can access all of your documents on the Windows partition. Perhaps you could move some old files to the external hard drive to make space. :)

Or, if you just want to try Ubuntu for a while to see if you like it, you can just use the Live CD without making any changes to your computer. That is the most fool-proof way to test it out.

---

### Post by eddVRS on 2008-09-25
Check your BIOS, you might get lucky, 
I've got an old rig lying around that I think can boot from USB.

Edit: Or go with what Snowpine has suggested, and you can use the USB drive to store any user/personal information/files etc...

---

### Post by h4nn4h on 2008-09-25
Alright, I'm cleaning up the C-drive right now, I think I can get a few extra gb free. Then I'll try again. I'm still confused about this partitioning though...Do I need to do that before I install ubuntu, or is it part of the process, or...?

---

### Post by snowpine on 2008-09-25
> **h4nn4h said:**
> Alright, I'm cleaning up the C-drive right now, I think I can get a few extra gb free. Then I'll try again. I'm still confused about this partitioning though...Do I need to do that before I install ubuntu, or is it part of the process, or...?

Ubuntu will set up the partitions it needs as part of the installation process. When you get to the Partitioning step, it should give you the option to "Resize existing partition and use freed space". 

The option you do NOT want to choose is "Guided: Use Entire Drive" because that will wipe out your Windows and all your data!

It goes without saying that you should back up all of your data before re-partitioning your hard drive. :)

ps I recommend defragmenting your drive from within Windows as a good first step. This will make it easier for Ubuntu to resize the partition.

---

### Post by h4nn4h on 2008-09-25
Okay, so I cleaned up the hard drive, 11 GB are now free, and I defragmented it in windows. When I get to the partitioning part in the installation (I'm currently on the live cd) I get three options...I tried the one "use biggest uninterrupted free space" (this is a rough translation from my dutch language installation), but it says it can't do that because the needed space isn't there. Is this normal? The other options are "use entire disk", which is to be avoided since I want to keep my windows installation, and "manually", which gives me 82 MB of unused space on the C-drive. I'm confused now!

---

### Post by snowpine on 2008-09-25
> **h4nn4h said:**
> Okay, so I cleaned up the hard drive, 11 GB are now free, and I defragmented it in windows. When I get to the partitioning part in the installation (I'm currently on the live cd) I get three options...I tried the one "use biggest uninterrupted free space" (this is a rough translation from my dutch language installation), but it says it can't do that because the needed space isn't there. Is this normal? The other options are "use entire disk", which is to be avoided since I want to keep my windows installation, and "manually", which gives me 82 MB of unused space on the C-drive. I'm confused now!

So it doesn't want to resize the partition for some reason. After you deleted files in Windows, did you empty the trash? If the files are still sitting in your recycle bin, that would explain it.

Assuming you have emptied the recycle bin, it sounds like you might need to shrink the Windows partition manually. It's nothing to be scared of, but it's probably a good idea to back up any important documents first. What you're going to do is boot with the Ubuntu Live CD, then go to the System menu and choose the GParted Disk Partition Editor. It will graphically show the partitions on your disk as colored bars. Click on the right edge of your big Windows partition and drag it to resize the partition. You want to create enough empty space for Ubuntu; 10gb should be enough. (You don't want to leave your Windows partition with absolutely 0 space free; best to leave some "wiggle room"). Then, click Apply to actually perform the action. That is the only action you need to do; don't delete or create or reformat any partitions at this time. Now, there is an empty space on your drive and you should be able to install with the "use biggest uninterrupted free space" option.

ps the 82mb free space is probably just a little "gap" that Windows left during the install; I wouldn't worry about it right now.

---

### Post by h4nn4h on 2008-09-25
Thanks for all the help, but I must be doing something wrong. I keep getting an error that the operation could not be completed when I try to resize the partition.

---

### Post by h4nn4h on 2008-09-25
On the other hand, something must have changed because now I can use the second option in the partitioning-part of the installation. Here goes...the worst thing that can happen is that I'll have to install windows over again, which is no big deal because there isn't anything important on the C-drive anymore...Hope all goes well though!

---

### Post by C.S.Cameron on 2008-09-25
A lot of older computers will boot from USB HDD and not from USB Flash.
I install to USB HDD the same as to internal HDD.

Unplug your HDD power cables or disable your HDD's in bios. (optional).
Boot the Live CD..
Plug in the USB device.
Run Install.
When you get to partitioning you can use:
Guided, resize ...and use remaining space.
Then drag the bar right to show how much FAT you want to keep
Complete the setup, when it is done you will have Ubuntu on USB.

---

### Post by h4nn4h on 2008-09-25
I'm now talking from my brand new ubuntu installation. I'm not sure what happened with my partitions, but the main thing is it's working now. Thanks everyone!

---

### Post by snowpine on 2008-09-25
> **h4nn4h said:**
> I'm now talking from my brand new ubuntu installation. I'm not sure what happened with my partitions, but the main thing is it's working now. Thanks everyone!

Congratulations! Welcome to Ubuntu!

---

### Post by Marshal0505 on 2008-09-25
Aah welkom, blij dat het gelukt is :)
Stick around , it's a nice place !

---

