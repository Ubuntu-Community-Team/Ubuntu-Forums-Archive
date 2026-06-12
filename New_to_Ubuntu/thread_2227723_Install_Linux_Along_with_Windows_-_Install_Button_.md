---
title: "Install Linux Along with Windows - Install Button Stays Grayed Out"
date: 2014-06-03
forum: New to Ubuntu
---

### Post by KAWill70 on 2014-06-03
What does it mean if the Install Button stays grayed out when choosing the install along with Windows option?

I have a WinXP installation on a 20 GB disk and attempted to install Lubuntu 14.04 and also Mint 13 on the same disk.  The slider comes up and suggests a certain partition size for Windows and Linux.  The slider works but the install button stays grayed out in both cases.  Could the 20 GB disk be too small?

I finally gave up and used the last install option and resized the Windows partition myself leaving some extra space.  Everything worked fine.  However, on the first boot of WinXP from the grub boot menu Windows sensed some change and wanted to run ChkDsk.  Once complete the next boot was fine.

In general, are there bugs with the Install Along With Windows option?

---

### Post by grahammechanical on 2014-06-03
Not necessarily with the installer but often with Microsoft not liking us installing Linux. On older motherboards with a BIOS boot system we are only allowed a maximum of 4 primary partitions. Microsoft often makes sure that the maximum of 4 primary partitions is used up. And that is why the installer will not let us install alongside.

We have to delete one of the 4 primary partitions and resize the other partitions to create unallocated space. The installer will then use the unallocated space to create a fourth primary partition but it will be a special primary partition called an Extended partition into which it will create at least two Logical partitions, one for Ubuntu and one as a swap partition. We can have as many Logical partitions as well like but first we need that special Extended partition.

We should always use Windows tools to resize Windows partitions. It is best to defrag first and to do it more than once and then test that windows loads, which will usually require the running of ChkDsk.

Regard.

---

### Post by KAWill70 on 2014-06-03
Thanks for the help.  The surprise here is that there was only one partition initially on the 20 GB WinXP disk.  One would not think that the Install button would stay grayed out when using the Install Along With Windows option in this case.

When I finally used the "Something Else" Linux Install option and resized partitions myself, I first reduced the Windows partition size to free some space.  An EXT4 /root partition was created and then a small Swap partition was created at the far end of the disk.  Those were both logical partitions.  Windows had no issue other than wanting to run chkdsk.

I should mention that Mint 13 had the same problem with the grayed out install button using the Install Along With Windows option.  Somehow I got that to change at one point and proceeded with the installation.  Everything looked fine booting to the Grub menu.  However, WinXP would not boot.  All I got was a blinking dash or underscore.  Something was running as Cntrl Alt Delete rebooted the computer.  Grub.cfg entries looked reasonable and I also tried an update-grub.  I never recovered WinXP even after booting the installation CD and Recovery Console followed by fixmbr and fixboot.  You would think that would let the disk boot to WinXP.

---

### Post by Vladlenin5000 on 2014-06-03
Rule of thumb to avoid breaking Windows: Use Windows tools to resize Windows partitions, reboot and do *chkdsk *at least once (twice is better, more than that a waste of time).
Then - and only then - proceed with the dual-boot installation.

The usual reason for the button being grayed out has already been pointed out by [ 						 							]("http://ubuntuforums.org/member.php?u=1087323")[[COLOR=#000000]grahammechanical[/COLOR]]("http://ubuntuforums.org/member.php?u=1087323") in the reply. The usual, but there are many possible causes: Hibernate Windows, encryption, etc.

---

### Post by KAWill70 on 2014-06-03
Thanks all for the help.  It sounds like one should not use the Install Alongside Windows option at all.

Instead, one should modify and create partitions in the safest manner and then use the Something Else path in the Install menu.

---

### Post by Impavidus on 2014-06-03
If you already have the unallocated disk space, the install alongside option works quite well. Resizing WinXP partitions is relatively reliable too (I did it once from a Dapper Drake live disk after defragging, can't be much worse now), the big trouble comes with resizing Win7 partitions. But I think that with WinXP, Lubuntu and Mint a 20GB drive may be a little small.

---

### Post by Vladlenin5000 on 2014-06-03
> **Impavidus said:**
> But I think that with WinXP, Lubuntu and Mint a 20GB drive may be a little small.

You think? :lol:
20GB is small for Windows 7 alone.

---

### Post by LastDino on 2014-06-03
Judging by your disk size, this might be pretty old system as even my first system bought in 2003 had 40 gigs. I hope you installed Lubuntu. And probably should consider using only one OS and get rid of XP as it has been dumped. It's quite unsafe to use non-patchable windows system (or any for that mater) if it was ever safe to use windows patched or not anyway.

---

### Post by KAWill70 on 2014-06-03
Thanks to everyone for the help.  I picked up the 20 GB disk drive recently for $5 just to experiment and learn my way around Linux and Windows installations.  Believe it or not, WinXP is only about 1 GB after installation with no updates and not including the swap file.  It really runs fast with nothing installed.  The motherboard is nine years old.

I was actually just installing WinXP and either Lubuntu 14.04 or Mint 13.

After getting WinXP and Lubuntu working, I decided to try the WinXP Recovery Console again to see if WinXP boot could be restored to the disk using fixboot and fixmbr.

It worked perfectly.  I then reinstalled Lubuntu to get the grub boot menu back.

---

### Post by KAWill70 on 2014-06-04
Does anyone know how smart the Installer is in the case of Install Alongside Windows?

I'd guess that the Installer can determine where the last file is in the volume but don't know that for certain.  I'll assume that it cannot move files.

When I manually resized the partition I first ran the defragmenter to see where the last files were located relative to the size of the total volume, although you wonder if the defragmenter display really shows everything.

It's also not clear if the Installer tries to make an intelligent decision when it first presents the Divider settings.

---

### Post by squakie on 2014-06-04
As an adjunct to those reading this looking for help:  as vlladlenin5000, do all resizing using the Windows tools.  There was one step missing there I'd like to add:  ALWAYS defrag the volume twice BEFORE resizing if you want to avoid data loss.  So the procedure would be:

In Windows:

- back up ANYTHING you might need or want

- right-click on the disk, choose tools, then choose defrag.  No matter what it says about fragmentation, run it.  When it completes, do it again.

- using the Windows tools (see disk management), shrink the size of the partition as you desire

- reboot Windows - it may want to run chkdsk - let it

- reboot Windows again - you want to do this until it boots cleanly without running chkdsk

NOW proceed on......

---

### Post by KAWill70 on 2014-06-05
> **squakie said:**
> As an adjunct to those reading this looking for help:  as vlladlenin5000, do all resizing using the Windows tools.  There was one step missing there I'd like to add:  ALWAYS defrag the volume twice BEFORE resizing if you want to avoid data loss.
That may explain why one or more Linux Installs Alongside Windows failed on my system.  No defrag was done and Linux did the resizing as opposed to Windows tools.  Windows may be very sensitive to changes in the partition and especially files marked as unmovable such as the swap file.  I wonder if Linux would know enough to leave those Windows files alone and not move them.

Last night I installed Lubuntu 14.04 Alongside Windows in a little different manner and it worked perfectly.  This was for testing only.  WinXP was a fresh install.  I had the Windows format tool during install create three partitions and Windows was installed in the last partition [E:].  Partition C: was created as a primary partition, and interestingly D: and E: came out as logical partitions.  Windows formatted only C: and E: during the installation.  The C: partition wound up with a number of Windows boot related files.

To install Lubuntu, I deleted the D: partition while in Windows to create free space.  After running Lubuntu live from Flash, I entered the install dialog and selected Install Alongside Windows.  The installer created two logical partitions using the empty space between C: and E: to handle the root and swap partitions.  Everything works and Windows runs in partition E: after booting via the grub boot menu.

---

### Post by squakie on 2014-06-05
We're all just glad you got it going!!  Remember to post ANY questions you might have - no such thing as a dumb question (heck, just see all of MY questions ;) ).

---

