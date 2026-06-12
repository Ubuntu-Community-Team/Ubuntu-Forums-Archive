---
title: "Questions about installing/dual booting Ubuntu 12.10 on a second hard drive"
date: 2013-03-30
forum: New to Ubuntu
---

### Post by Nanotech220 on 2013-03-30
_Summary:_
 -How do I set up partitions a second hard drive so both Windows and Ubuntu can use it?
 -Is it OK to have multiple filesystems on the same drive by using different partitions?
[U]
Some Background Info:[/U]
  I'm new to Linux, haven't installed anything yet, and already I have questions. Recently I saw that I was running low on space on my desktop PC's (500 gigabyte) internal hard drive so I purchased an extra (1 terabyte) internal hard drive. I've been curious about Linux so I thought about installing Ubuntu on my new drive while having Windows 7 remain installed on my first hard drive, allowing me to dual-boot. But I still want to be able to access the files on the second drive in windows (especially since I originally bought it to provide extra storage space for windows), which would not be possible if the entire 1 terabyte drive is formatted in the Ext4 filesystem that Ubuntu needs, which windows 7 can't use.

  So I began wondering if it would be possible to have a both an NTFS partition on the new drive (for extra windows programs and files I want to be able to access in both OS like Music and Videos (since Ubuntu and Windows can both read NTFS)) and then the Ext4 partitions for Ubuntu on the same new drive.

_The questions:_
 -Is there any disadvantage to having multiple partitions with different filesystems on the same drive? Do I need to worry about file corruption somehow? Or is this actually a good idea?
-Would it be better to re-install/move windows to the 1 TB drive and install Ubuntu on the old 500 GB drive? That way they each have their own hard drives. (And no, before anyone asks, using the entire 1 Terabyte drive just for Ubuntu is not currently an option.)

_The plan:_
-Windows would remain installed on the old hard drive (the one with only the old NTFS partition) completely separate from Linux.
-The plan is Create an NTFS partition and Ext4 partitions for Ubuntu on the new hard drive.
-The Ext4 partition(s) are for Ubuntu.
-The new NTFS partition would not be for a windows installation, but for extra storage space for windows and provide a location for files I want access to regardless of if I am in Ubuntu or Windows.

Note:
 -Nothing has happened yet, the new hdd is still sitting unformatted in its unopened box. Ubuntu is still just on a live CD. I'm still in Windows 7 64 bit using my old hard drive as I type this.

Thank you for any help or clarification you can provide. I am looking forward to learning about Ubuntu and getting to use it.

---

### Post by DuckHook on 2013-03-30
Welcome to the forums and to Linux/Ubuntu!

You are very wise coming to this forum and researching before you make the plunge. Since this exact question (or one close enough) has just been asked, I would direct you to [this]("http://ubuntuforums.org/showthread.php?t=2130394") thread first. If you have further questions after reading it, please post back and the people here are always happy to help.

---

### Post by Nanotech220 on 2013-03-30
Thank you for the reply DuckHook.

After reading through the thread you linked to I'm still _*very*_ confused :confused: .  I'm sorry (and I mean you no disrespect) but it does not appear to have helped me with my questions, as our two situations, at first, seem to me to be very different (Dual-booting from one hdd compared to from two separate ones). I hope you can clarify this.

 The only thing I got out of that discussion is that it appears to say that it is indeed safe to have multiple partitions with differing filesystems on the same drive (*which you could have simply told me...*) but I would like some confirmation from you that this is indeed the case, as you go on to say in your own words that "Partition changes are the leading cause of borked HDDs, lost data and frantic pleas for help on these forums.". Does this mean I may run a risk by having multiple partitions?

You also said in that thread ([http://ubuntuforums.org/showthread.php?t=2130394&p=12579311#post12579311](http://ubuntuforums.org/showthread.php?t=2130394&p=12579311#post12579311)) "Is there a reason you need a NTFS partition in... NTFS is a horrible file structure that needs to be defragged constantly", do you have a better suggestion as to what I can do in my situation? It's all so very confusing for me to understand what I'm supposed to get out of _that_ thread.

While it is unrelated to my original question, you do make a good case that we should use consider using 12.04 rather than 12.10. What is the disadvantage(s) (if any) of 12.04 compared to the newest version (12.10, etc.)?

 In that thread you say to back up everything (which is always good advice) but since this is a new (blank) drive in question, I'm unsure what you mean. The old drive with all my windows stuff is going to be untouched and a big reason for getting the new one is to back up the old one. (Which can not be done until AFTER the new one is partitioned...)

I appreciate the advice in the thread for how to set up the partitions but I feel we are not at that step yet, and it left me more confused than anything.

Thanks for any assistance you can provide. I think I'll need it.

---

### Post by DuckHook on 2013-03-30
Sometimes, I forget that what seems obvious to me isn't at all obvious, and certainly not to new users. Sorry for confusion.

The similarities between your needs and those of the linked thread  are:

1. Any sort of partitioning is possible, and especially so if you actually want to put the new OS onto a disk of its own.
2. NTFS and ext4 can co-reside on one disk with no problems, the only drawback being complexity and potential confusion.
3. It follows that it is not necessary to move W7 to the new disk as you can easily add data partitions to the larger disk to look after any needed W7 expansion.

From the above, it further follows that:

Your plan is a good one. It bears many similarities to the linked thread because both seek to keep Windows where it is, create new ext4 partitions for Ubuntu, and already has/or plans to have a NTFS partition to be shared between the two OSes. In the case of the linked thread, it's all happening on one disk whereas you wish to spread it over two, but conceptually, it's the same desire with pretty much the same procedures in both cases.

So as not confuse you further, let me lay it out step by step (I'm lazy so will copy and paste many of my steps from the linked thread, with appropriate revisions):

1. Backup, then backup your backup. I am referring to your Win data here. It looks like you have W7 installed, so if you have W7 install/recovery disks, have them at hand. Backup *always* refers to some external media that can be ported to another box entirely if necessary, else it is useless and a waste of time. Either DVDs or an external USB device.

2. You don't need to resize partitions on your old HDD so the remarks concerning repartitioning don't apply.

3. Ubuntu has recently announced that future versions will only have 9 month support, so if you are intent on using 12.10, just be aware that you are committing to a journey on the unending upgrade treadmill. By contrast, 12.04 is LTS that will be supported until 2017. Choose your version wisely.

4. Your current partition architecture (on old first HDD) along with your proposed scheme (on new second HDD) is fine. Create NTFS partition, create ext partitions, and Ubuntu will go into the ext4 partitions.

5. You need a NTFS partition so ignore the corresponding comment #5. NTFS is still a horrible file structure, but you need this for Win, so you are stuck with it.

6. Create your Ubuntu partitions on your second HDD first using gparted, then map your various directories to these partitions during the install.

7. Create one partition of 30 GB at beginning of disk for /

8. Create one partition of whatever you want, but at end of disk for swap.

9. Create a third partition of, say, 400 GB for /home.

10 Create a final partition for data to be shared between W7 and Ubuntu. You will have to create this partition with Win tools because W7 refuses to play nice with other OSes. Format it as NTFS and this will be what you share between OSes. You will have to be careful to fill it only with data that you know both OSes can safely access: photos, music, common data files. You won't be able to use it for apps unless you dedicate it to only one OS or the other since any manipulation of app files by a foreign OS may render the app unlaunchable.

This above scheme will put you at the maximum number of partitions for your second HDD if you use the old MBR partitioning scheme. If you use GPT, you can have up to 128 partitions.

When installing Ubuntu, make sure that you choose "something else" when the install process asks you early on where you want to put your install. First, make sure that you change to drive sdb (this is critical. You do not want to overwrite your W7 drive "sda". This is also the reason for backups, in case you screw up at this point), then map / to the partition you defined in step 7, swap to the partition you defined in step 8, /home to the partition you defined in step 9, and leave the partition defined in step 10 alone for now.

Finally, make sure that GRUB is installed in sda (your W7 drive). GRUB will overwrite your windows bootloader, but this is what you want. Henceforth, GRUB will handle the loading of your operating systems and will offer you the choice between W7 and Ubuntu.

Write down the whole process to make sure you are comfortable with it. Before proceeding, ask questions if any occur to you. Remember, you are actually in a better place than someone trying to make two OSes cohabit on one HDD.

Re: Ubuntu 12.10 or 12.04

It goes without saying that the newer version will offer more bells and whistles whereas the LTS will offer better stability. You must use your own initiative to discover what new bells and whistles the new version offers and whether these are important enough for you to get on the upgrade treadmill. I consider myself a seasoned Ubuntu user and I prefer the stability of LTS to the wow-appeal of new stuff. Only you can determine what your needs are, so there is little that anyone can do to advise you here.

---

### Post by oldfred on 2013-03-31
You have to use Something Else or manual install. And on the partitioning screen at the bottom is a combo box. It will default to installing grub2's boot loader to the drive that is sda. You have to change that to the drive that you are installing Ubuntu into, usually sdb.

If you use gparted to create partitions in advance, you can create the NTFS partition with it. It will work just fine. But in actuality there are two versions of NTFS, one XP and the other Vista/7. If using as a data partition it does not matter and the first time you run chkdsk from your Windows 7 it will convert it. The difference is in the partition boot sector, but if not booting it does not matter.

---

### Post by DuckHook on 2013-03-31
Hi oldfred,

If grub is installed to sdb, won't OP have to change boot order to sdb first, or am I missing something?

---

### Post by oldfred on 2013-03-31
Yes that is correct, I should have mentioned it. 

I normally want grub in the same drive as Ubuntu and Windows boot loader on the Windows drives. Very old systems with IDE and drives with master/slave settings can only boot sda.
If each drive can boot without the other then when (when, not if) one drive fails, you can go into BIOS and boot other drive. Still need those backups. :)

---

### Post by DuckHook on 2013-03-31
> **oldfred said:**
> ...I normally want grub in the same drive as Ubuntu and Windows boot loader on the Windows drives. Very old systems with IDE and drives with master/slave settings can only boot sda.
If each drive can boot without the other then when (when, not if) one drive fails, you can go into BIOS and boot other drive.

Ahh. I get it. sda is left completely untouched with bootloader intact. But GRUB on sdb will recognize the Win installation anyway and offer it as a boot choice. Much neater than my suggestion.

@OP

What oldfred has done is change my procedure just a bit, but a very important bit. He has isolated your old disk entirely so that no change is made to it whatsoever. This is obviously a very good thing because if it doesn't change at all, you can be sure that it will work as it always has. By placing the bootloader in sdb, you now have two ways to boot:

1. If you set your system bios to boot from your old disk (sda), it will only boot Windows using the Windows bootloader (as it is doing now).
2. If you set your system bios to boot from your new disk (sdb), it will boot using GRUB and offer you a choice of either Ubuntu or Windows.

My solution replaced the windows bootloader with GRUB. His leaves windows bootloader intact and installs GRUB on your new disk, thus offering you the old disk as an intact fallback position. Very neat, very tidy, and very safe.

Repeat: after installing, you will have to change your bios boot order to boot from sdb first. If sdb ever fails, you can change bios to boot from sda and Windows will still come up.

As I already said in the linked thread, when advice conflicts, always listen to oldfred.

> Still need those backups. :smile:

Will I ever live this down?:redface:

---

### Post by Nanotech220 on 2013-03-31
DuckHook,
Thank you for the more detailed reply!
Yeah, sometimes us new users need all the details they can get, even if they seem obvious. What you wrote is exactly what I needed and was looking for.:) 
Thank you! :cool:

A few more questions:
 1-If I go with 12.04, (Stability is good. A recent pack of updates from Microsoft seems to have had the unfortunate effect of rendering my current system somewhat unstable. I saw my first blue screen in 8 years a few weeks ago. This was a big part of the reason for my sudden interest in Ubuntu. I have no idea what happened and am kinda scared of their updates now), is it still possible to upgrade to a newer Ubuntu version at a later date with minimal problems?

2-Will programs I download (Ex: from the Ubuntu's software centre or elsewhere) still be supported or even developed for 12.04 or will they only work in the latest release (12.10)?

3-As I was researching on <[http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/](http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/)> I read that "When dual-booting Windows 7 and a Linux distribution _on a computer with *one* hard drive_, the best option is to have Windows 7&#8242;s boot manager be the primary boot manager." Since I'm going with a two drive setup does this still apply or can I use GRUB as my boot manager as you indicated? (Just noticed oldfred's post, guess that answers this question. Thanks oldfred! :))

4-From the same site <[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/2/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/2/)> (using 2 hard drives this time!;)), they mention creating a "/boot" partition of 35 MB to 500 MB as the first partition. I notice this seems to be missing from your directions. Is the boot partition necessary for what I want to do?

5-You said in step "7. Create one partition of 30 GB at beginning of disk for /" and step "8. Create one partition of whatever you want, but at end of disk for swap.", Does it matter where the third partition "of, say, 400 GB for /home" is located (beginning or end)?

I'm tired and it is late. I can't think of any more questions to ask you right now.

Thank you for your help! I'll print your directions out later and hopefully we will be able to have this set this up after your reply.

 oh, just noticed this. (wow it's late)
Happy Easter everyone!

---

### Post by oldfred on 2013-03-31
Software with 12.04 will continue to get security updates. But generally the version does not change, Firefox now seems to be an exception as to provide the secuity updates it must just be easier to fully update to new version.

I have 12.04 as my main working system, but in other 25GB partitions install newer versions just to see if changes in software or system might be worthwhile for full conversion. And to know more about what changes will happen in the future. 

I do not even normally agree with leaving the Windows boot loader in charge. Windows is not designed to multi-boot and has to have work arounds. There were some issues with conflicts with Windows DRM licensed software (using Flexnet) writing into the same space as grub but grub fixed that.

Most Desktop systems do not need a /boot. If running a server you may need it. A few older BIOS and very large drives have issues and may need it, but if you have  (root) in the first 100GB of hard drive, it definitely should not be needed.

Actually all partitions can be anywhere on drive. Duckhook suggestions are good. I prefer to use a couple of primary partitions at beginning of drive, then make entire rest of drive as the extended partition with many logical partitions inside it. And swap at end of extended and at end of drive. Then you have a bit more flexibility of adding partitions it later you want to in the extended.  Or you could shrink /home or your NTFS data if in the extended and make another 25GB partition if you later wanted to experiment with another version. If you use all 4 primary partitions that becomes just about impossible. 

@DuckHook - the number of users who do not backup, mean we cannot recommend it enough.:)

---

### Post by DuckHook on 2013-04-01
> **Nanotech220 said:**
> 1-If I go with 12.04...is it still possible to upgrade to a newer Ubuntu version at a later date with minimal problems?

The short answer is: As you fall further and further behind the latest and greatest, it is only to be expected that you will find upgrading more and more complicated and difficult. This is true of any OS, and Ubuntu is no exception.

The long answer is: This is not really a problem. Old Linux hounds prefer to upgrade by wiping out the old system entirely anyway. We like to make sure that our new versions don't inherit incompatible configuration files or apps, so a fresh virgin install is actually our preferred method. Therefore, it is immaterial how many versions behind we are because the new install is not dependant on the old one.

> 2-Will programs I download (Ex: from the Ubuntu's software centre or elsewhere) still be supported or even developed for 12.04 or will they only work in the latest release (12.10)?

The way the repositories work is that they are actually customized for each version. So, 12.04 has its own repositories and 12.10 has its own. When you download 12.04 apps you are downloading apps that have been tested to work with 12.04. You may not get the latest version that has been built to work with 12.10 or 13.04, but at least it will continue to work with 12.04. Therefore, when Ubuntu commits to supporting a version over the long term (an LTS version), this support is also extended to the apps in the corresponding repository.

If you download an app from outside of the repositories, then, of course, this support will be lacking. However, one of the biggest errors that new users migrating from Windows make is downloading apps willy-nilly from outside of the repositories. This is another bad habit that Windows has conditioned people to practice over the decades and is a major reason that worms, trojans and viruses find Windows such an inviting playground.

For 99% of users, there is no reason to ever download anything outside of the repositories. I haven't checked for a long time, but I believe that the various repositories are currently carrying well over 40,000 packages. I mean, really? An average user can't find something that works well enough for them from among 40,000 packages?

> ...I read that...the best option is to have Windows 7&#8242;s boot manager be the primary boot manager." Since I'm going with a two drive setup does this still apply or can I use GRUB as my boot manager as you indicated? (Just noticed oldfred's post, guess that answers this question. Thanks oldfred! )

oldfred has given an excellent answer. However, I can't help adding a further note. I generally find Windows tools to be inferior to Linux tools (I know this sounds like a controversial statement, but let me explain). Windows tools will generally work adequately with Windows, but will range from awful to totally worthless for anything else. Often, this is by design--to discourage you from trying anything else. This is especially true of the Windows bootloader. It is not designed to play nice with other OSes, and I most strongly disagree with the author of the blog that you read. It is just bad advice. GRUB will recognize Windows, but the Windows bootloader does not recognize Ubuntu (at least, not without installing extra components and making you jump through hoops). In your case, you bypass the problem by installing separate OSes on separate HDDs, but if a multitude of OSes must cohabit on the same HDD, then there isn't really even a basis of comparison between GRUB and the Windows bootloader.

> ...Is the boot partition necessary for what I want to do?

oldfred answers this very well.

> ...Does it matter where the third partition "of, say, 400 GB for /home" is located (beginning or end)?

The neat freak in me says that it does matter, but not by very much. It is easier to grow a partition towards the end than it is to grow it towards the beginning. Therefore, if you place /home at the beginning, it will be easier to grow it later. But since this is just a personal preference on my part, you are free to place it anywhere you like. By extension, if it is actually more likely that you will grow the data partition, then perhaps it should be placed at the beginning instead of /home, 'home is moved to the end, and /home could even be reduced so that unallocated space is left between the two partitions.

It must be noted that oldfred makes another excellent suggestion: replacing both the /home and data partitions with an extended partition that contains many logical partitions is the most flexible mathod of all. Actually, I was aware of this, but steered away from it because most new users have a hard enough time trying to understand primary partitions, never mind extended/logical ones, so I tried to keep it simple. However, if you do your research and feel that you understand logical partitions well enough to implement it, then by all means do so. That method will give you all the flexibility that you need.

> ...oh, just noticed this. (wow it's late)
Happy Easter everyone!

My tardiness in getting back to you has been due to having to entertain our gaggle of family for Easter. Happy Easter to you too.

---

