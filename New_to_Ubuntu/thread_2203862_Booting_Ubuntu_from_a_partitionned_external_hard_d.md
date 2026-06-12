---
title: "Booting Ubuntu from a partitionned external hard drive on USB 3.0"
date: 2014-02-05
forum: New to Ubuntu
---

### Post by alexandre4 on 2014-02-05
Hi,

I am new to Ubuntu (haven't had the chance to even try it, in fact), and to pretty much every PC doodads that aren't the Adobe Creative Suite :P .

A couple of days ago, I bought an internal hard drive, the same type I already have as a kind-of main hard drive (for most of my programs and games, basically anything that needs to work fast but not über-fast, which is what my SSD is for) on my desktop PC (a Western Digital Black 2To (which is the same as the Caviar Black btw, but with a simplified name)), and yesterday I went to Best-Buy to get the hard drive encloser I bought from their online store (the encloser being a Vantec NexStar3 SuperSpeed USB 3.0 & eSATA 3.5'', which I'm not very fond of since one of the screws they included with it lost its head while I was trying to screw the hard drive in place, but anyway...). Now that I've physically installed the hard drive into the encloser, I need to decide a couple of things about how it will be formated, but since I'm not very good and knowledgable with these kind of things, I am here asking for your help.

So, what I want to do with my hard drive is, mainly, use it for video editing, but also for audio/photo editing and everything that concerns the said Adobe Creative Suite (Premiere Pro, Photoshop, Illustrator, After Effects, Audition, Flash, etc), and a bit for storage too (mostly projects made with these programs, plus all sorts of audio, photo and video materiel ready to be used for future projects). But, I'd also like to install Ubuntu, on a separate partition, and configure things so that my desktop PC boots with Ubuntu on my external hard drive whenever it (the external hard drive) is connected (on USB 3.0 or eSATA, for which (eSATA) I do not have any port on my desktop PC, but eh, just in case I get one some day...) and powered-up, while still being able to boot with my current OS, which is installed on my internal SSD, when the external hard drive isn't connected on starting up the PC.

Right now, my new hard drive is all screwed up (in the literal sense) and wired to the encloser and that's pretty much it. I still need to figure out whether I'd be better off configuring my external hard drive into MBR or GPT mode (Master Boot Record or GUID Partition Table), and then how to create partitions (one for Ubuntu and eventual updates or addons, no matter how much space needs to be assigned for Ubuntu for it to have what it needs to be kept up-to-date and be upgradable). The only thing I know really (or at least, that I think I know) is that it needs to be formated in NTSC.

Oh and, I also need (or would very much like) to be able to use my hard drive (the projects and storage part, not the Ubuntu one, since I plan on using Ubuntu only on my desktop PC and possibly on an eventual laptop, hence the fact that I want Ubuntu to be on an external hard drive) on PCs with an older OS, mostly Windows XP and maybe even older ones, but only to transfer some files onto my hard drive in case I need to.


Thanks already for your answers! :)


Alexandre P.

---

### Post by vitz_3 on 2014-02-05
Hey Alexandre, :)

The Ubuntu built in installer is pretty good at doing things like what you're describing. When you first start the installer disk you get presented options on how you'd like to partition the target disk. It's actually pretty good about it and straight forward. 

When the installer fires up (12.04 in my example case) click "Something Else". Create the Ubuntu partition at the front of the drive as format ext4 with whatever size you'd like, a swap partition (there are differing opinions on a good size to use but I'd go with a size equivalent to your RAM size) then the rest as freespace or FAT32. The only issue with this is FAT32 doesn't allow for single files larger than 4GB in size which can be difficult when holding project files like that. I don't remember off the top of my head whether or not gparted allows you to create NTFS partitions but if you had a Windows installation you can use the disk manager there to reformat the FAT32 partition as NTFS then you're golden.

If you want to be safe when doing the install I'd suggest just disconnecting your internal hard drives from your SATA controller so you don't accidentally format the wrong drive in the process or muck up the windows bootloader. Drive naming conventions can get confusing to new users sometimes.

Here's a quick video I found showing how the disk partition editor is used. [http://www.youtube.com/watch?v=qBCHsgry2RQ](http://www.youtube.com/watch?v=qBCHsgry2RQ)

Best of luck! Let us know how it works out.

---

### Post by alexandre4 on 2014-02-05
Thank you for your answer! But, before trying to install Ubuntu, I'll need to initialize and format my external hard drive, which I haven't done yet since I don't really know what would be the best in that matter for the uses I've specified. Could you tell me what is best in my case? Namely, should I initialize my external hard drive into Master Boot Record or in GUID Partition Table (considering the use I'll make of it and the fact that I'd like to be able to use the hard drive on older computers too (with Windows XP and older) in case I need to transfer some files)? And after that, do I need to create a single partition before running the Ubunutu installer, or will I be able to create partitions directly from the installer even on a hard drive that has no partition (for the moment) and is not formated (in NTSC for example)?

Thanks already :)

---

### Post by oldfred on 2014-02-07
XP will not read gpt partitions, otherwise I would suggest using the newer gpt for all new drives as it is an improved partitioning scheme.

With flash drives, Windows only sees the first partition. I might make first partition NTFS and then install Ubuntu to the rest of the drive.

Installer will not create NTFS partitions as mentioned above, but you can either partition in advance with gparted as that is just a bit easier and lets you create NTFS. You still have to use Something Else or manual partitioning (+ to add, or change) as you still have to specify format like ext4, mount like / (root) or /home. Be sure to change combo box - device for boot loader at bottom of partitioning screen  to external drive, it defaults to sda which usually is internal drive. Showing in attached. I click on change to get pop-up screen as I was overinstalling a new version to old version partition.

---

