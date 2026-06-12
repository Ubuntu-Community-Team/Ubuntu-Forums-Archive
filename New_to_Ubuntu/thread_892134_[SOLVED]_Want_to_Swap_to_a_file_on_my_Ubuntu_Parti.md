---
title: "[SOLVED] Want to Swap to a file on my Ubuntu Partition"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by Ralph L on 2008-08-16
I want to set up my system to swap to a file on the main Ubuntu partition rather than to a separate swap partition.  I have multiple Ubuntu partitions, and I don't do much swapping so I don't see the need to create a separate partition for each of my 3 Ubuntu partitions.  And I want to be able to hibernate from each partitions and switch to another one.

Here are some instructions I pulled off a two web sites and put toghether:

BEGINNING OF INSTRUCTIONS

user@computer:~$ sudo dd if=/dev/zero of=/mnt/512Mb.swap bs=1M count=512
Password:
512+0 records in
512+0 records out
536870912 bytes (537 MB) copied, 35.3802 seconds, 15.2 MB/s
user@computer:~$ sudo mkswap /mnt/512Mb.swap
Setting up swapspace version 1, size = 536866 kB
no label, UUID=dd6a01c8-93f0-41e0-9b7a-306956d8821b
user@computer:~$ sudo swapon /mnt/512Mb.swap

sudo gedit /etc/fstab

and add this line at the end of the file: 

/mnt/512Mb.swap  none  swap  sw  0 0save and reboot 


Note: You can use suspend on disk with a swapfile. To do that we have to add an option passed to the kernel. Add the resume=/dev/<partition> resume_offset=<offset to the swapfile in blocks> : 

sudo filefrag -v /swapfile
#output : First block: 102300Copy the first block number of the swapfile (ex:102300) and edit the defoptions line of /boot/grub/menu.lst : 

# defoptions=quiet splash resume=/dev/sda3 resume_offset=102300The update your grub configuration : 

sudo update-grubOn this example, the swapfile is on partition /dev/sda3. You are now able to use suspend on disk (hibernate). 

END OF INSTRUCTIONS.

Some questions on these instructions:

1.  Are these instructions still correct or have things changed?  The instructions say to create the swapfile in /mnt.  My /mnt is empty and I would guess its for a reason.  Is there another place where the swap file should be defined?
2.  Do I need to do the second part of the instructions to get hibernate to work on the newly defined swap file?
3.  How do I disable use of the current swapping to a separate swap partition, so I can remove that partition.
4.  And just for my education, what is in /dev/zero that needs to be copied to the swap file?

Thank you for any information.
Ralph

---

### Post by nicedude on 2008-08-16
This isn't how Linux works as unlike WIndows it wants its swap space on a different partition. I would recommend just doing it the way it was meant to do it. You only need say a 2GB SWAP & 15-30GB EXT3 with a mountpoint of / to install Ubuntu just fine.

---

### Post by Rolcol on 2008-08-16
> **nicedude said:**
> This isn't how Linux works as unlike WIndows it wants its swap space on a different partition. I would recommend just doing it the way it was meant to do it. You only need say a 2GB SWAP & 15-30GB EXT3 with a mountpoint of / to install Ubuntu just fine.

From what I've read, a swap file is just as good as a swap partition as long as the containing partition is not full (so there's no fragmentation).

I don't know if you need to do the second set of instructions to be able to hibernate but the first set is good enough if you want to use a swap file rather than a partition.  Just be sure to remove the entry that uses the partition as swap as well.   The mnt folder is where things are mounted by the command line by a user.  It's fine to use mnt as the folder containing the swap file.  If you want to mount a patition, however, you'll have to use another folder (you can create one inside /mnt just for that).

Edit:  I'll go ahead and try hibernating to a swap file.  I'll get back with the results.

Edit2:  I just set up the swapfile but I couldn't hibernate.  Clicking on hibernate would just lock my screen.  I don't want to mess up my computer so I'm not going to try the second set of the instructions.

---

### Post by Ralph L on 2008-08-17
Thanks guys for the speedy response.

Rolcol, your remarks were very helpful.

I think I asked a stupid question below.  Since I specified /mnt/file, the file had to go on the / (root) partition.  I would have had to specify /home/... to get it on the /home partition.

Thanks anyway.

Ralph

One more question.  The procedure that I listed above (and followed) for making a swap File does not show assigning the File to a specific disk or partition.  Other discussions I have seen talk about assigning the swap file to a particular disk (or even splitting the swap space among multiple disks).  So there must be a way of assigning the file to the particular disk.  I just used the command 
sudo dd if=/dev/zero of=/mnt/512Mb.swap bs=1M count=512 

This, of course, does not specify a particular disk or partition so I don't know where the file went.  Since I have several partitions, it most likely went to the /home partition, the / (root partition), or one of the other partitions on the disk.  Moreover, if I do "sudo fdisk -l, none of the UUIDs on the partitions match the UUID put out by mkswap when I turned the dd created file into a swap file.

1.  Anybody know how to find what partition the I made the swap file on?

2.  Anybody know how to create the swap file on a particular partition?

3.  If I need to create a different swap file, because it is not on the / partition (where I want it), how do I delete the one I created so I can create a new one?

Any help is appreciated.

Thanks
Ralph

---

### Post by egalvan on 2008-08-17
[http://blog.mypapit.net/2007/07/how-to-add-linux-swap-file-if-you-dont-have-swap-partition.html](http://blog.mypapit.net/2007/07/how-to-add-linux-swap-file-if-you-dont-have-swap-partition.html)


:popcorn:

---

### Post by egalvan on 2008-08-17
[http://linux.about.com/od/linux101/l/blnewbie4_2_13.htm](http://linux.about.com/od/linux101/l/blnewbie4_2_13.htm)


:popcorn:

---

### Post by kansasnoob on 2008-08-17
Well, I'm sharing a SWAP partition with two Linux OS's (I've done it with as many as three):

[ATTACH]81887[/ATTACH]

But to do so you'll have to change the uuid of the swap partitions in the various operating systems. I just recently learned that:

[http://ubuntuforums.org/showthread.php?t=879192](http://ubuntuforums.org/showthread.php?t=879192)

---

### Post by Ralph L on 2008-08-23
Final note:

Using the instructions given in the first post of this thread I was able to swap memory to a file, but I was unable to get the hibernate to work. I gave up and established a swap partition for each of the 3 Ubuntu operating systems (OS's) However, at that time I was unaware of all the sections of the /boot/grub/menu.lst file.  It may be that if the "resume=/dev/sdax" line was correctly added to the lines labeled "kernel", hibernate would work with swap files as well as with swap partitions.

To allow hibernation from each of multiple Ubuntu partitions and not have one partitions's hibernate file overwrite another partition's hibernate file, separate swap partitions are needed for each Ubuntu partition.  This requires editing of both the /etc/fstab file and the /boot/grub/menu.lst file.  The important thing is for the fstab file is to have the correct corresponding swap partition assigned to the OS, since the install my not select the swap partition you wanted.  This is done using the UUID of the swap file you want assigned listed in the fstab line with the swap parameter as in 

UUID=54d07c02-9e25-4873-946d-5e7c088b0c0e none swap sw 0 0

To get the UUID use the sudo blkid command.  Each Ubuntu partition's swap file will likely need editing.

Next editing of the /boot/grub/menu.lst is required. The instructions given in the last part of the first post on this thread dicuss editing of "defoptions".  Doing this did not work for me.  I edited the section of menu.lst after the ## ## End Default Options ## line.  This section is used to setup the OS selection menu for booting.  It has a section for each choice on the OS selection menu. Only the last Ubuntu partition loaded has a menu.lst file with all the choices in it, so that is the important one.  For each of the partitions I ascertained that the "resume=/dev/sdax" was present and correct on the "kernel" line, as in:

kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=bbbfa018-a516-41f0-a83f-1b4db337a95f ro quiet splash resume=/dev/sda9

I did not put the resume= parameter into the "recovery mode" sections.  

Once I had updated the section for each of the 3 Ubuntu partitions, I ran the sudo update-grub command.  I presume this transfers information from the menu.lst file to grub.  I only ran update-grub for the last partition I loaded, although I updated the menu.lst file for each partition that was installed earlier.  I don't think this had an effect, since I didn't run update-grub on those partitions.

Rebooting and running showed that I could hibernate one partition, start another one, hibernate it, and go back to the first.  In short each hibernate was independent.

The only glitch has been that now and then the resume will get to the point where it should request the password, but not dispaly anything.  In this case I have to do a forced power down and lose the hibernate information.  If anyone knows how to fix this problem, it would be appreciated.

Ralph

---

### Post by unutbu on 2008-08-23
Thanks Ralph L for taking the time to write up your solution!

> 
Rebooting and running showed that I could hibernate one partition, start another one, hibernate it, and go back to the first. In short each hibernate was independent.
[list=1]
[*]After you hibernate, how do you start another OS? Do you power off and power on, and boot a different OS? 

[*]If so, how do you  switch between hibernated states?
[/list]

---

### Post by Ralph L on 2008-08-24
unutbu

1.  After I hibernate the computer powers off.  So I press power on and when it comes to the OS selection menu at the start of the boot process, I select the OS I want, and if that OS was previously hibernated, it will resume.  Otherwise it will do a full boot.  I have a total 4 OS's on the disk and I can shut each down using a hibernate, then select any of the 4 and it will resume--even the Windows partition. 

2.  Because each OS has its own hibernate disk space, I almost always shut down using hibernate.  Upon power up I just pick the OS I want to resume.  It is also possible to shut down an OS by picking restart (rather than hibernate).  Of course this will not create a hibernate file for the next start up of this OS so next time this OS is started, it will do a full boot.  But the restart also stops at the OS selection menu and one can pick any OS.

---

### Post by Ralph L on 2008-10-24
Whoa!! After using the solution I described above for a while I discovered that I was bashing my various disk partitions (operating system and shared partitions), when I added files to one partition and then resumed in a different partition.  I am guessing that the disk directory is not completely updated when a hibernate is done so that after resuming in a different partition, that partition doesn't know about the new files.

So far I have been able to recover each damaged partition by running "sudo fsck -f" on each partition. (I had to use the /dev parameter, but that is illegal to post here)  A note of praise: The fact that I could do this recovery at all left me very impressed with the ext3 file system.

At any rate I have stopped using hibernate on my multi-partition system.  If I can figure out how, I will submit a bug report on this.

Ralph

---

