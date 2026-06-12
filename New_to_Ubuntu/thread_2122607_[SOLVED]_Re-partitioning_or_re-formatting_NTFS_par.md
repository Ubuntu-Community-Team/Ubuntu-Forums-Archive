---
title: "[SOLVED] Re-partitioning or re-formatting NTFS partition fails"
date: 2013-03-05
forum: New to Ubuntu
---

### Post by Wadcutter on 2013-03-05
I have two 250BG hard drives in my computer. Sda holds my system (Precise 12.04 and files) while sdb formerly was broken into three partitions. First partition was formatted to ext3 and held my Ubuntu systems (first 9.10 and later 10.04). The second partition was NTFS and functioned as a Windows backup to XP which was on Drive A. The third partition was a small swap partition for Ubuntu.

Now that I've replaced Windows on Drive A entirely with Ubuntu 12.04, I want to turn Drive B into two ext4 partitions for Linux backup and storage (no more Windows on this computer).

I opened sdb in Gparted (installed version) and tried to eliminate the swap partition and then evenly divide the HD into two more or less equal sized ext4 partitions. But approximately half of the HD is apparently still under the influence of NTFS and I get an error message on any actions involving it, such as re-sizing, re-formatting to ext4 or even deleting it. Sometimes an error message will say Gparted cannot identify the file system and other times I get a message that the partition is in use and no actions can be performed. I also cannot make the Ubuntu (now ext4) partition any larger since it apparently would encroach on the old NTFS partition.

I burned a Live GParted CD but that puppy is far above my pay grade. I could not understand some of the choices it was asking me to make and was uncertain whether it understood  that I want to make changes on drive B, but do nothing to Drive A, which is working fine . There is no data to be saved on (B), but everything to be careful of on (A).

My worst mistake was eliminating Windows from this computer before dealing with the Windows partition.  If I can't come up with a better solution, I suppose I can pull the HD from this computer and hook it up to a Windows computer to rid myself of the NTFS partition. But any other suggestions will be welcomed and appreciated.

---

### Post by oldfred on 2013-03-05
Is the NTFS partition inside an extended partition with swap? You system is probably mounting swap which also mounts the extended partition so you cannot work on it while mounted.

You can use Ubuntu liveCD or your gparted liveCD. Either way you have the same gparted with perhaps minor version differences.

If you see little key symbols then the partition is mounted. And even a liveCD may mount swap to speed things up, so you have to right click and swap off.

If you also have a swap on sda, both swaps may be mounted in fstab. Take a look at fstab to see what it is using.
       cat /etc/fstab

---

### Post by Wadcutter on 2013-03-05
I've been trying different things on this drive because I'm not worried about losing data. I have managed to (it appears) eliminate the sdb swap partition. Now I only see 2 partitions. sdb1 is 115.98 GB and formatted ext4 and not mounted. sdb 2 is also 115.97 Gb but the file system is shown as unknown and it is unmounted. There is also a warning message  for sdb2 that GParted is "unable to detect the file system becuase it is either damaged, unknown to GP, missing (unformatted) or the device entry /dev/sdb2 is missing"

Any attempts to format this partition to anything results in an error message and failure. The exact details of the failure are not spelled out for me to read but can be saved to my root directory for some future use by GParted support. (I can't read the report and it seemed extremely complicated.)

 fstab gave info mostly about my current installation which pertains to sda. However, it did show both sda7 and sdb2 as having swap partitions during installation and that is probably the problem you mentioned. sdb does not show one now, but it may still be lurking somewhere and I don't know how to find or eliminate.

A

I had to finish the above post hurriedly and didn't get the chance to add that if there is a way I could completely wipe this drive of all formatting and partitions and start over again as if it just came out of the box, I would gladly do that. There's nothing on it that I need to save so starting from square one would be fine.

---

### Post by carl4926 on 2013-03-06
When you run the installer there is an option to erase everything and re-install Ubuntu
Looks like this
[https://docs.google.com/file/d/0B3e0lLG3OdqETlE1dndoVTZWbWM/edit?usp=sharing](https://docs.google.com/file/d/0B3e0lLG3OdqETlE1dndoVTZWbWM/edit?usp=sharing)

---

### Post by Wadcutter on 2013-03-06
I decided to try something I had used before that I knew to be pretty safe, i.e. a Knoppix distro that ran from the CD. I figured there was less chance of screwing up the (A) drive containing my OS if I was operating from a CD (GParted Live is probably the same idea, but it was looking a little over my head when I tried it earlier).

On Knoppix (ver 5.1) I found GParted and I ran it. I tried to format the recalcitrant partition to ext3 ( it didn't offer ext4 as a choice) and it apparently worked. So I pulled the Knoppix CD and re-booted into 12.04 and voila-the bad partition was formatted as ext 3. I re-formatted to ext 4 and re-sized it and now I am good to go with two usable Linux partitions on my secondary drive.

 A bonus to all this trouble is that it apparently uncovered a glitch whereby there were two swap partitions on two different HDs in play at the same time. The result was that I could never make this computer hibernate properly. It would act like it was hibernating but the box would never shut down. You could still hear the power supply running the fans even though everything else seemed to hibernate. I gave up the idea of hibernating 12.04 and had been using "suspend" to at least slow things down when I was going to be away for a bit. But now after ridding the sdb drive of the swap partition, I find that "suspend" works just like hibernation in that it shuts down everything including the HDs, monitor, AND the fans in the box.  You can hear a pin drop now with it in "suspend" , just like a proper hibernation. While it may not be true hibernation, it is certainly a lot closer to it than I have even been before with this computer running Ubuntu.

Thanks to oldfred and carl4926 for your suggestions.

---

### Post by mikechant on 2013-03-06
I realize that you've sorted this out now, but for future reference if you want to clear down a whole disk and start again, Gparted does have a 'new partition table' option, which will effectively get rid of everything - including corrupt or unknown partitions - and let you start afresh.

---

