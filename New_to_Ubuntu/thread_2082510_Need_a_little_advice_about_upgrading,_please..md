---
title: "Need a little advice about upgrading, please."
date: 2012-11-09
forum: New to Ubuntu
---

### Post by L Campbell on 2012-11-09
I have an HP desktop with one hard drive and it is dual boot with WinXP and 11.04.

My goal is to upgrade to 12.04, for which I have downloaded the .iso file, done the md5sum and burned a disk.

Now, when I try to install 12.04, I opted for the first choice, which is to install it along side WinXP.

Where I have become stuck is the place where I have to decide how much space to allocate to which program.

Currently 71.4 GB is on my left and 45.4 GB is on my right but I have absolutely no idea what to do next and would appreciate your suggestions.

TIA.

---

### Post by Mark Phelps on 2012-11-09
In the strict sense, upgrading would be REPLACING your older version of Ubuntu with a newer version.  Is that what you want to do?

You need to know that if you upgrade, in this sense, you can not later roll-back to the old version; instead, you would have to reinstall the old version from scratch.

It reads like what you really want to do is triple-boot -- with two versions of Ubuntu, and XP.

That is very different.

We need more details on what you want to do, first.

---

### Post by Bartender on 2012-11-09
I agree with Mr. Phelps.  It sounds like you're asking the install disc to install another version of Ubuntu.  If this is the case, you're gonna end up with a real mess - two versions of Ubuntu, two swap partitions, etc.

I think what you want is to replace your existing version?

Did you partition the drive so that you have a separate /home folder?  If not, I'd suggest backing up personal data, then over-writing your existing Linux installation.

If you did create a separate /home folder, make sure not to format it.  Plus, you will have to use the same username/password.  Don't make the same mistake I did - I changed my username/password once and ended up with a second /home folder!

---

### Post by L Campbell on 2012-11-09
> **L Campbell said:**
> I have an HP desktop with one hard drive and it is dual boot with WinXP and 11.04.

My goal is to upgrade to 12.04, for which I have downloaded the .iso file, done the md5sum and burned a disk.

Now, when I try to install 12.04, I opted for the first choice, which is to install it along side WinXP.

Where I have become stuck is the place where I have to decide how much space to allocate to which program.

Currently 71.4 GB is on my left and 45.4 GB is on my right but I have absolutely no idea what to do next and would appreciate your suggestions.

TIA.

Thanks for your interest.

What I want to do is to end up with Ubuntu 12.04 and WinXP

---

### Post by L Campbell on 2012-11-09
> **Bartender said:**
> I agree with Mr. Phelps.  It sounds like you're asking the install disc to install another version of Ubuntu.  If this is the case, you're gonna end up with a real mess - two versions of Ubuntu, two swap partitions, etc.

I think what you want is to replace your existing version?

Did you partition the drive so that you have a separate /home folder?  If not, I'd suggest backing up personal data, then over-writing your existing Linux installation.

If you did create a separate /home folder, make sure not to format it.  Plus, you will have to use the same username/password.  Don't make the same mistake I did - I changed my username/password once and ended up with a second /home folder!

Thanks, you are correct 

(I think what you want is to replace your existing version?)

I have not done anything about creating a separate /home folder.

Things like this make me nervous.

Kind Regards.

---

### Post by offgridguy on 2012-11-09
I hope you don't mind if i jump in here.  The reply by bartender brings up i question i have 
been  wanting to ask.  Is one swap partition all that is needed even if you have more than
one OS {all buntu's} ??

---

### Post by westie457 on 2012-11-09
> **offgridguy said:**
> I hope you don't mind if i jump in here.  The reply by bartender brings up i question i have 
been  wanting to ask.  Is one swap partition all that is needed even if you have more than
one OS {all buntu's} ??

Correct, only one Swap is needed for any number of *buntus on a system. More than one can get confusing (at least to me).
HoweverI do not know if the same would be true for something like Ubuntu and Red Hat for example.

---

### Post by jerome1232 on 2012-11-09
> **L Campbell said:**
> Thanks for your interest.

What I want to do is to end up with Ubuntu 12.04 and WinXP


Are you trying to do an in place upgrade to your 11.04 install or are you trying to install 12.04 over your old 11.04, thus wiping any data you had on your 11.04 install and starting with a clean slate.

---

### Post by monkeybrain2012 on 2012-11-09
Just save your /home from 11.04, choose "something else" and install Ubuntu 12.04 over where 11.04 used to be (there should be a swap partition from your previous configuration, don't touch it) Then after install, replace your /home with the back up (but make sure you have deleted outdate configurations, I usually delete most hidden config files except for a few things I need like Mozilla, skype and a few programs I want to save the configuration and get rid of all customizations that I suspect don't carry over to the new version to avoid conflicts) then you are good to go.


P.S. 11.04 has passed end of life, there is no sense keeping it around.

---

### Post by DuckHook on 2012-11-09
> **L Campbell said:**
> I have not done anything about creating a separate /home folder.

Things like this make me nervous.

At first the process feels overwhelming, but it also feels very rewarding once you achieve your goals. The people on this forum are very helpful so feel free to make use of us.

The idea behind putting the /home directory on a separate partition is simply one of future utility. By doing so, it is much easier to preserve your current data and much of your configuration on future installations. Many Linux users, for example, don't like to "upgrade" because we don't like to drag along old and  possibly obsolete system configuration files to a new version. By making a "clean" install, we don't have to worry about old system files that may be inappropriate for the new system. However, a clean installation wipes out all files in the partition in which it is installed and if your /home directory is in the same partition as the system files, then it becomes much harder to preserve personal data and things like e-mail settings. By segregating /home into it's own partition, it can be exempted from the deletion process of a new install and then simply attached to the new installation as its natural /home directory with all data intact. All very neat and tidy.

However, it is not necessary to do such things, and it's perfectly understandable if you just want to avoid the complexities of monkeying around with partitions. If so, then simply upgrading your installation will suffice. Thousands of people upgrade easily and with no issues. It goes without saying to **backup** your important data on both the Windows and old Ubuntu installs before upgrading, but this is just common sense. A belt and suspenders type thing. The full instructions for upgrading can be found here:

[https://help.ubuntu.com/community/PreciseUpgrades](https://help.ubuntu.com/community/PreciseUpgrades)

If you want to take this opportunity to further split off /home to a separate partition, then the procedure is a little more complicated, especially given an existing Windows partition. My recommendation for a newish user is to simply upgrade without bothering with the fuss of a separate /home partition for now. If you find that you have the curiosity and the inclination to explore repartitioning, then I would suggest that you do so on a spare computer that has no important data on it first. Once you feel comfortable with and knowledgeable about the process, then you can bring that knowledge to your mission-critical machine with confidence.

---

### Post by BertN45 on 2012-11-09
+1 DuckHood

---

### Post by offgridguy on 2012-11-10
Thank you ; DuckHook,  your reply answered another question i wanted to ask about
/home partition.

---

### Post by Bartender on 2012-11-10
Another option, if there is no separate /home partition.  The below assumes you have an Ubuntu install disc, ready to go.

Download latest GParted LiveCD.  Create the bootable disc.  Boot from the disc.  I don't know for sure what the previous Ubuntu installer did to your PC, but it's clear to see once you've booted into the GParted environment.

There are only so many options.  You'll have either:
A primary Ubuntu partition and a primary swap partition, or:
An extended partition with Ubuntu and swap inside as logical partitions, or:
A primary Ubuntu partition and an extended with swap inside.

The Linux partitions will be to the right of the Windows partition.  The Windows partition is almost always (always?) "first" on the HDD, or to the left.

Using the GParted LiveCD, you can delete the Linux partitions.  It's important to realize that doing this will mess up GRUB, and Windows will not boot until GRUB gets fixed.

Once you've wiped the Linux partitions, you can get out of GParted LiveCD, then restart with the Ubuntu install disc in the tray.  When you get to the right page, choose "Something Else" and aim Ubuntu at that blank space.  Once it installs, GRUB should be fixed.  The installer is smart enough to see the Windows partition, find the MBR, and adjust it.

If you're thinking, "why go thru the extra steps when I can just go straight to the Ubuntu install CD", well, it's much easier to set up Linux partitions from the GParted LiveCD if you want to try that than it is from the Ubuntu installer.  To me, choosing extended partitions from GPLCD is much clearer than it is from the Ubuntu installer.

---

### Post by L Campbell on 2012-11-10
> **DuckHook said:**
> At first the process feels overwhelming, but it also feels very rewarding once you achieve your goals. The people on this forum are very helpful so feel free to make use of us.

The idea behind putting the /home directory on a separate partition is simply one of future utility. By doing so, it is much easier to preserve your current data and much of your configuration on future installations. Many Linux users, for example, don't like to "upgrade" because we don't like to drag along old and  possibly obsolete system configuration files to a new version. By making a "clean" install, we don't have to worry about old system files that may be inappropriate for the new system. However, a clean installation wipes out all files in the partition in which it is installed and if your /home directory is in the same partition as the system files, then it becomes much harder to preserve personal data and things like e-mail settings. By segregating /home into it's own partition, it can be exempted from the deletion process of a new install and then simply attached to the new installation as its natural /home directory with all data intact. All very neat and tidy.

However, it is not necessary to do such things, and it's perfectly understandable if you just want to avoid the complexities of monkeying around with partitions. If so, then simply upgrading your installation will suffice. Thousands of people upgrade easily and with no issues. It goes without saying to **backup** your important data on both the Windows and old Ubuntu installs before upgrading, but this is just common sense. A belt and suspenders type thing. The full instructions for upgrading can be found here:

[https://help.ubuntu.com/community/PreciseUpgrades](https://help.ubuntu.com/community/PreciseUpgrades)

If you want to take this opportunity to further split off /home to a separate partition, then the procedure is a little more complicated, especially given an existing Windows partition. My recommendation for a newish user is to simply upgrade without bothering with the fuss of a separate /home partition for now. If you find that you have the curiosity and the inclination to explore repartitioning, then I would suggest that you do so on a spare computer that has no important data on it first. Once you feel comfortable with and knowledgeable about the process, then you can bring that knowledge to your mission-critical machine with confidence.

Thanks for all this information, I really appreciate it.

Truly, if I could have my 'druthers', I'd rather have 2 hard drives, one with 12.04 on it and the other with WinXP.

In the past I have made a couple of tries to do this but have not had success.

The reason that I have the two systems on the one hard drive is because I was unsuccessful with setting up two hard drives and I have a good friend who knew how to set up the dual boot.

Kind Regards.

---

