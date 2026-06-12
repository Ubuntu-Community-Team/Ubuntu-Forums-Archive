---
title: "SSD and home folder data with a second hard drive. Whats my best option?"
date: 2014-02-21
forum: New to Ubuntu
---

### Post by i0ls on 2014-02-21
I recently got my newest rig built to replace our Imac that's getting tired and I am more than happy to have Ubuntu back as my main desktop OS. 
I just got my SSD set up and installed a 2tb secondary hard drive, I am looking at options to move our large files onto the second hard drive. I know that i can probably move the entire home folder over, but will that give me slower performance with opening applications? My SSD is a 120 gb, I think that's probably enough room for the OS and the apps that we will be using.
So moving folders like music, documents, photos etc from the home folders of each user to a "home folder" on the second hard drive seems like my best option for both performance and storage capacity. 
Am I way off on this? Is there a slicker way to accomplish this than just moving the folders and making a link in nautilus?
Any advice is greatly appreciated, thanks.

---

### Post by i0ls on 2014-02-21
I think that I found what I was looking for. Its called a "symbolic link", I didn't quite know what to call it.
Essentially what i had done already was add the drive to fstab, set a group to access  the drive, make a fake home folder for each user on the second hard drive, and make a symbolic link for each of the folders in the home folder to the second hard drive following the instructions in this post here.
[http://askubuntu.com/questions/214643/help-with-creating-symbolic-link](http://askubuntu.com/questions/214643/help-with-creating-symbolic-link)
This seem like a logical way to approach this issue?

---

### Post by oldfred on 2014-02-21
That is exactly what I have done. I leave /home inside my / (root) on my SSD. My SSD is 64GB and I have two /, current and future of about 28GB each. And my working install uses about 11GB and /home is 2GB. Most of my /home is actually .wine for Windows version of Picasa. But I am aggressive about moving any data folder or even some of the normally hidden folders in /home like the Firefox  & Thunderbird profiles into my data partitions.

I use linking, but some suggest using bind.
 Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
User Morbius1 prefers bind over linking in post #4
[http://ubuntuforums.org/showthread.php?t=2192848](http://ubuntuforums.org/showthread.php?t=2192848)

With a large data drive, I also install also install Ubuntu. I want every drive to be bootable in an emergency.
      
 Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs, mostly now test installs on hard drive as SSD is main working installs.

If not having Windows, I also suggest gpt partitioning, and if drive may in the future be transfered to a UEFI system include the small efi partition at beginning of drive. Difficult to add later when drive is full of data and efi partition should be first or at least near beginning of drive. If gpt partitioned and booting in BIOS mode you also neeed a bios_grub partition unformatted 1 or2MB with bios_grub flag.

      
 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

---

### Post by i0ls on 2014-02-21
Thank you for the reply.

While it looked like everything was set up and sweet. I started to copy some data and found out quickly that it copies to BOTH the SSD and the HDD. How do i go about looking like its in my home folder and actually being in the hdd?
If I copy to the HDD will it also end up on the SSD?
EDIT:
yes it also ends up on the ssd. now i really need help.
I want to have the files only on the hdd and look like there on the ssd in the home folder. plz help, thx

---

### Post by oldfred on 2014-02-22
I do not see how you are copying data to both SSD & hard drive.

But if you have link set up, then the link in the SSD really refers to the data that only is on hard drive but makes it seem like it is in /home on SSD?

---

### Post by i0ls on 2014-02-22
I can see the files in the home folder and the link folder with the files in the hard drive. I had 115gb free and copied half of my stuff and had 8gb free. Should I be copying to the home folder or directly to the hard drive?
ls -l shows the links I set up. 
Where did I go wrong??

---

### Post by oldfred on 2014-02-22
Post the
 ls -l
and 
df -h

Some of the tools that show usage include the links, others do not, so that can also be confusing.

---

### Post by i0ls on 2014-02-22
Hi thanks for the help. This my first SSD on Linux with multiple accounts and lots for data that needs to get stored. I actually erased the data from the ssd after copying some of it over. I didn't want to keep the ssd that full. After erasing it I get the same approx 115gb free and copied something else and the free space on the ssd went down again. does a symbolic link put the data in both places? I was looking for something that would automatically drop all the data on the hdd.

ls -l:
total 60
 4 Apps        4 Downloads          4 Music      0 Shared      4 Wallpaper
 4 Desktop    12 examples.desktop   4 Pictures   4 Templates   4 Xbmc
 4 Documents   4 Fonts              4 Public     4 Videos

df -h:
/dev/sdb1       110G   37G   68G  36% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            3.9G  4.0K  3.9G   1% /dev
tmpfs           795M  1.2M  794M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            3.9G  324K  3.9G   1% /run/shm
none            100M   36K  100M   1% /run/user
/dev/sda1       1.8T   18G  1.7T   2% /mnt/Vault
/dev/sdc2       298G  298G  758M 100% /media/MAC BACKUP

---

### Post by i0ls on 2014-02-22
I just tried copying some flac files directly to the hard drive with the links on it in the "music" folder. The ssd had 75 GB free before copying anything. After I moved a couple folders on to the hdd in the symbolic link folder "music" my ssd had 63 GB free. 
here is what i used to make the sym link for the music folder
ln -s /home/ian/Music /mnt/Vault/Ian
have i done this incorrectly?

---

### Post by i0ls on 2014-02-22
i did a lot of looking around and it wasn't until i actually found another forum that someone else made there sym links backwards to realize what I had done. 
I also didn't know that running ls -l in the directory where your sym links are will actually tell you who is going to where. The list that I posted earlier was all that I thought it did which seemed vague...
Thank you oldfred for dealing with my lack of knowledge and actually trying to figure out what is happening. It takes making this mistake once to learn I suppose.

---

