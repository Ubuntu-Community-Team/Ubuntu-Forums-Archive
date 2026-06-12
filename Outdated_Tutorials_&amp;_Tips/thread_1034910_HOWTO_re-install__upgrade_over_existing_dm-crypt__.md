---
title: "HOWTO: re-install / upgrade over existing dm-crypt / LUKS system"
date: 2009-01-09
forum: Outdated Tutorials &amp; Tips
---

### Post by MaddMatt on 2009-01-09
**EDIT: 2011-05-08** brendankidwell informs us that this HOW-TO is still relevant to the latest Ubuntu versions: > [These instructions work] for upgrading from Kubuntu 10.10 to Ubuntu 11.04. In this case, ignore the bit about using a (now ancient) Ubuntu 8.04.1 install disc. Use "Ubuntu 11.04 alternate install" for your correct architecture.


**Introduction**

So lets say you are running a 32-bit dm-crypt system, and want to 'upgrade' to a 64-bit version. Perhaps you are in the habit of 'upgrading' by doing a fresh-install of the new distro. Maybe you screwed up your system and want to do a fresh-install. 

If one of these scenarios is you, then this HOWTO is for you!

The reason I am writing this is because I too wanted to join the 21st century by upgrading to a 64-bit version of Intrepid, and I ran into some serious problems! After 3 weeks and some helpful tips, I got my system running again, and hopefully this HOWTO will help you to avoid the same hurtles that I experienced! So, without further ado...

**Prerequisites**
[U]
You:[/U]
[LIST]
[*]You are running a system with dm-crypt/LUKS, and probably LVM. 
[*]You keep a separate /home partition in which all of your files and settings exist. 
[*]You want to do a fresh install
[/LIST]
[U]
Things you need:[/U]

[LIST]
[*]A note-pad with these commands written on it, or a separate computer, or a dualboot system
[*]Ubuntu 8.04.1 Hardy Heron Alternate-install CD (64-bit Recommended!)
	**[SIZE="2"]NOTE: Even if your end-goal is to install Intrepid Ibex (8.10) you must do a fresh-install of Hardy first and then upgrade. The reason for this is the Intrepid alternate disc (at the time of writing) does NOT handle encryption well, and your install will [probably] fail.[/SIZE]**
[/LIST]

_Recommended pre-steps:_

[LIST]
[*]As always, back-up any critical data, including any files in /root that you may want to save
[*]Make backups of your /boot directory, /etc/fstab, /etc/crypttab, /etc/apt/sources.lst and any other special configuration files you may want to keep.
[*]Helpful: print out a 'vim' cheat-sheet for text editing from the command line.
[/LIST]


**Procedure:**

[LIST=1]
[*](Optional) Make a list of all installed programs so you can easily re-install your favorites later: 
```
$ dpkg --get-selections > ~/installed-packages
```

[*]Insert the 8.04.1 Hardy Heron alternate-install CD, and reboot your computer
[INDENT] [/INDENT]
[*]Upon booting the CD,** select the 'recovery' option** from the menu. This is necessary for the installer to read your current configuration and load the dm-crypt modules. 
[INDENT] [/INDENT]
[*]Follow the prompts. You will be asked for your hostname and the password to your current dm-crypt volume
[INDENT] [/INDENT]
[*]When you reach the recovery menu, press the escape key one or more times in order to get to the 'table of contents'. 
[INDENT] [/INDENT]
[*]One down from the recovery menu is the set-up-partitions menu. Select it and hit 'enter'.
[INDENT] [/INDENT]
[*]Select **'Manual' partitioning**
[INDENT] [/INDENT]
[*]The should have detected your LVM setup and should display the local volumes. 
	
select your /boot partition:
        (in this example it will be /dev/sda0  ) 
	set it to use it as your /boot partition, and to format it. 

select your / (root) partition:
	(in our case, we will call this /dev/mapper/Encrypted-root  )
	set it to use it as your / partition, and to format it. 

select your /home partition:
	(Again, our example this will be /dev/mapper/Encrypted-home  )
        set it to use it as your /home partition, but DO NOT FORMAT it. 
	
your swap partition should already be selected for use and formatting. 
	
You can add any additional partitions you wish to.
[INDENT] [/INDENT]
[*]Continue with the install - everything should work well from here on out. _Be sure to create your username the same as your last one if you want it to take advantage of all of the files and settings in your /home directory_.  
[INDENT] [/INDENT]
[*]After the install finishes, reboot the computer. This is where the tricky part begins. 
[INDENT] [/INDENT]
[*]When your computer says 'grub stage 2 loading', press 'esc' to get to the grub menu, and select 'recovery'. 
[INDENT] [/INDENT]
[*]After loading the first part of the kernel (your initrd file from the /boot directory) your computer will stop. **It will appear to be frozen, but _JUST WAIT_.** What has happened is that the ubuntu installer failed to configure /etc/crypttab, and so your initrd cannot load the rest of the kernel from your computer because it has no clue what /dev/Encrypted/root is. LUCKILY - initrd has a built in busybox/ash shell, so you need to wait for the initrd to time out and drop you to this shell (as root). 
[INDENT] [/INDENT]
[*]After waiting patiently for it to drop you to the shell, manually create your /etc/crypttab file either with vim or by using the command line like this:
```
echo "Encrypted /dev/sda1 none luks" > /etc/crypttab
```
Where Encrypted is the map name of the LVM partiton, and /dev/sda1 is the location of your LVM partition. 
[INDENT] [/INDENT]
[*]After that step, manually unlock your partitions with the following command:
```
cryptsetup luksOpen /dev/sda1 Encrypted
```
This command will ask you for your password to the encrypted volume. 
[INDENT] [/INDENT]
[*]Now that the system can find your root partition, exit the busybox terminal to continue booting your system. 
```
exit
```
[INDENT] [/INDENT]
[*]If everything worked well your new system should boot just fine. Hooray! Now, the /etc/crypttab file that you created in the busybox initrd terminal will not be permanent, so you will need to create that again. Either use the terminal or your favorite editor; your choice - just be sure to do it as 'sudo' this time.
```
$ sudo echo "Encrypted /dev/sda1 none luks" >> /etc/crypttab
```
(Note that this time I used '>>' instead of '>'. This appends the line to the bottom instead of overwriting the file.)
[INDENT] [/INDENT]
[*]Now that your /etc/crypttab file is all squared away, be sure to update your initrd image so that you can boot normally again:
```
 sudo update-initramfs -k all -c -v 
```
[INDENT] [/INDENT]
[*]If the last one ran without errors, reboot and be done! If you want to upgrade to Intrepid, follow the instructions here: [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)
[INDENT] [/INDENT]
[*]To install all of your old and favorite software, use the list you created from step #1:
(You may want to first edit the list using a text editor to include only the extras, and none of the core programs if you just preformed an upgrade.)
```
$ sudo dpkg --set-selections <installed-packages
$ sudo apt-get dselect-upgrade
```
[/LIST]
 

Hooray! You have now done a fresh-install without losing your data or settings. Pat yourself on the back! I sincerely hope that these instructions work for you. I haven't confirmed the /etc/crypttab problem with the 32 bit version yet, but others have agreed that Intrepid + dm-crypt causes serious problems. It will be very nice when the nice folks on the installation teams add the encryption libraries to the LiveCD. Let me know if you have problems or comments to add to this! 
 
[B]
Special thanks to cyberdork33, hyper_ch, RansomStark, and the [email]dm-crypt@saout.de[/email] mailing list[/B]

---

### Post by John Wiersba on 2009-04-25
Thanks for posting this.  Any update for installing Jaunty into an already-LUKS-encrypted partition?  (You mention that Intrepid has problems)

---

### Post by MaddMatt on 2009-04-29
> **John Wiersba said:**
> Thanks for posting this.  Any update for installing Jaunty into an already-LUKS-encrypted partition?  (You mention that Intrepid has problems)

I am currently backing up my system to give Jaunty the once over with this- I understand the problem was with the intrepid alternate CD, so hopefully the problem was fixed, but I will be able to tell you for sure by the end of the week. 
Cheers!
m

---

### Post by MaddMatt on 2009-05-12
Hi John, 

Sorry to take so long to get back to you. I tested the re-installation over Intrepid, and I did indeed need to re-do some of these steps. One thing I noted, however, was instead of dealing with the whole busybox terminal at boot (steps 11-16) you can just keep the recovery CD in, run the recovery menu again, and then start a terminal in your / directory. Then continue with step 17... Let me know if you have questions! 

Cheers, 
m

---

### Post by John Wiersba on 2009-07-05
MaddMatt,

I have just gotten some test hardware to use to try your procedure.  I installed 8.10 and then upgraded to 9.04.  Everything went as you described.  However, I was unable to use your modification (from May 12) of skipping steps 11-16 (busybox).  After I rebooted the CD into the recovery/rescue menu again, I was able to update /etc/crypttab and successfully run update-initramfs.  But when I rebooted, it still dropped into busybox, My encrypted partition was already unlocked, so I re-ran update-initramfs.

I don't know exactly why I had to run update-initramfs twice -- apparently the first time didn't really work?  I did check that /boot was mounted before I ran it the first time.  So, I'm not sure what happened.  However, after running it a second time, I was able to continue booting successfully as you described.

Any further thoughts?
-- John

**Update**
I figured out what's going on.  For some reason, mount shows that /boot and /home are mounted, but they're not.  If you ls the files in them, you can see that they're just the empty mount points.  So, first mount /boot before running update-initramfs.

Also, to save some typing, you can save a copy of /etc/crypttab in your home directory to be copied back to /etc after the reinstall.  Also, that way you'll have the UUID form of the device name, which is superior to the physical partition (/dev/sda5) form.

---

### Post by John Wiersba on 2009-07-07
MaddMatt,

I have created a new thread at _[HOWTO: install and reinstall on an encrypted LUKS/LVM system]("http://ubuntuforums.org/showthread.php?t=1205372")_ with terse but very detailed instructions based on the information you provided in this thread.  Thanks again!

-- John

---

### Post by MaddMatt on 2009-07-07
Hi John, 

glad you got it figured out! Mounting /home isn't necessary, but unmounting the liveCD /boot and mounting your own /boot partition is crucial. I like your howto as well- very detailed. My original post in tern was heavily aided by the people on the dm-crypt mailing list, so I guess what goes around comes around. Thanks cheers!

-M

---

### Post by John Wiersba on 2009-07-07
Hi, MaddMatt!

In my scenario, I had to mount /home in order to retrieve the copy of /etc/crypttab (which contains the encrypted partition's UUID) that I had stored in /home.  I didn't want to have to explain how to figure out the UUID which was anyway already in the old (8.10) version of crypttab.  I prefer UUIDs over physical device names for robustness.

For some very strange reason, the mount command showed that all the LVM partitions were already mounted, but they weren't really (as could be seen by visiting the mount point to see what was available there).  So, I didn't even have to umount them, I just mounted them.

-- John

---

### Post by dsg18096 on 2009-09-08
Thanks for this post.  It was very helpful in my upgrade from 32bit
Hardy to 64 bit Jaunty last night.  But of course I just had to be a
bit different.  Perhaps things have changed but in my past experience
with it, the alternate CD always wanted to take over the entire disk
when doing encryption and my system is dual boot.  As such, I adapted
this to work with the live CD installer.  In case it helps anyone
else, here's what I did:

boot the live CD, open a terminal and sudo su -.

apt-get install cryptsetup lvm2 # this will also install a dependency
                                # that I'm not remembering right now

cryptsetup luksOpen <device> <map name>
vgscan

# at this point /dev/mapper should contain the device files for the
# earlier LVM installation

Run the installer.  Do a manual partitioning and set up the partitions
using the LVM devices and whatever was /boot before.  It should only
be necessary to reformat the / and /boot partitions and the installer
picks up any swap partitions without extra work.  If it matters to
you, check the advanced button on the last installer page to ensure
you install grub in the partition you want it, if not the MBR.

After the installer finishes, do not reboot.  Go back to that root
shell (or open a new one if you closed it) and prep the new system to
properly deal with the encrypted root.

# mount <lvm root device> /target
# mount </boot device> /target/boot
# mount -t proc proc /target/proc

This next one is probably not the best approach, but I could not
recall how to properly mount the virtual /dev filesystem so...

# cp -a /dev/sd* /target/dev

works well enough.

# chroot /target

Remember that the Live CD installer does not include cryptsetup and
lvm2 so

# apt-get install cryptsetup lvm2 
# edit /etc/crypttab as described above
# update-initramfs -k all -c -v
# exit

At this point, assuming I haven't forgotten to document a step,
reboot, and the system should properly prompt for the luks password at
the splash screen and boot.

---

### Post by John Wiersba on 2009-09-08
DSG, FYI, the Alternate installer allows you to manually partition as you see fit.  I think you should be OK with a dual-boot scenario.

-- John

---

### Post by cbonar on 2010-01-01
Thanks for this how-to, it works like a charm with the alternate iso of karmic (no need to upgrade from a previous version) !

---

### Post by brendankidwell on 2011-05-06
**MadMatt**, you rock. Thanks for the howto.

I just wanted to chime in and say the recipe at the top of the thread works for upgrading from Kubuntu 10.10 to Ubuntu 11.04. In this case, ignore the bit about using a (now ancient) Ubuntu 8.04.1 install disc. Use "Ubuntu 11.04 alternate install" (or later probably will work in the future).

> **MaddMatt said:**
> [LIST]
[*][S]Ubuntu 8.04.1 Hardy Heron Alternate-install CD (64-bit Recommended!)
	**[SIZE="2"]NOTE: Even if your end-goal is to install Intrepid Ibex (8.10) you must do a fresh-install of Hardy first and then upgrade. The reason for this is the Intrepid alternate disc (at the time of writing) does NOT handle encryption well, and your install will [probably] fail.[/SIZE]**[/S]
[/LIST]


---

### Post by MaddMatt on 2011-05-09
> **brendankidwell said:**
> 
I just wanted to chime in and say the recipe at the top of the thread works for upgrading from Kubuntu 10.10 to Ubuntu 11.04. In this case, ignore the bit about using a (now ancient) Ubuntu 8.04.1 install disc. Use "Ubuntu 11.04 alternate install" (or later probably will work in the future).

Sweet, glad that it worked for you. I'll update the post at the top with the new information. 

Also there's a brainstorm idea about [including full-disk encryption on the main installation CD]("http://brainstorm.ubuntu.com/idea/24712/") instead of needing to use the alternate CD - you may want to consider voting for it, as it could negate this process in the future. 

Cheers,

Matt

---

### Post by aktiv on 2011-05-09
This isn't working for me. Trying to upgrade from 10.10 to 11.04 with this method. I am never prompted for keys to the encrypted drives. I have a LV split in 4, each individually encrypted.

Since I don't have a CDROM, I'm booting the iso from a USB-stick. I have several iso's on it. My grub entry for it looks like this:

menuentry "Ubuntu Live Alternate 11.04 64bit Rescue Option" {
   set gfxpayload=keep
   loopback loop /boot/iso/ubuntu-11.04-alternate-amd64.iso                          
   linux (loop)/install/vmlinuz boot=install rescue/enable=true iso-scan/filename=/boot/iso/ubuntu-11.04-alternate-amd64.iso noeject noprompt --
   initrd (loop)/install/initrd.gz
}

It boots fine into the rescue mode. I then mount the iso to /cdrom with the shell option. But I am never prompted for keys to unlock my drives.

---

### Post by aktiv on 2011-05-11
Ok, I figured out how to fix it. If anyone has the same problem, you gotta ctrl-alt-f2 into the ash shell, and open the drives with cryptsetup luksOpen <encrypted> <decrypted>. The <decrypted> drives will then be available to the partitioner when you go back to the installer.

---

