---
title: "Error mounting HDD"
date: 2019-01-12
forum: New to Ubuntu
---

### Post by furioususer on 2019-01-12
Today I bought and mounted my new hard drive. I started with       formatting the disk to NTFS filesystem and then proceeded with transferring a couple of GB       from an older disk to this new one. Up to this point it all worked without       any glitches. But when I disconnected the disk and then connected       it again I got this error msg: 
  **Error mounting /dev/sdb2 at /media/fz/Red 1TB: Command-line `mount  -t "ntfs" -o  "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177"  "/dev/sdb2" "/media/fz/Red 1TB"' exited with non-zero exit status 12:  NTFS signature is missing.****Failed to mount '/dev/sdb2': Invalid argument****The device '/dev/sdb2' doesn't seem to have a valid NTFS.****Maybe the wrong device is used? Or the whole disk instead of a**[B]partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
  [/B]
My questions:
       
[LIST=1]
[*]Why did this happen first of all? 
I safely removed the disk like I have done a million times, so this  can't be the reason. But I did start with a slow formatting and aborted it  right       away when I realized it would take so long and did a quick       formatting instead. Could this be the reason? I also changed the name of the disk and then quickly changed it back. 
[*][https://askubuntu.com/questions/335909/error-mounting-dev-sda2-at-media?answertab=active#tab-top](https://askubuntu.com/questions/335909/error-mounting-dev-sda2-at-media?answertab=active#tab-top)
According to the above page I should be able to resolve this by typing in **mount -o ro /dev/sdb2 /media/fz/Red 1TB **in the Terminal (ctrl+alt+T). Is this correct? And what should I expect when I enter that command? Do I have to do enter this command every time I disconnect and mount the disk (I use an external HDD reader so I do disconnect/connect disks all the time)? 
[*]If I use this command as recommended, what does it mean for my       data? Do I have to format the disk and start all over again again or does it just fix it       and I can go on as normal? 
[*]If I fix this and get access to my data again, what says that I won't run in to the same       problem again? Right now I only transferred a couple of GB to the       new disk, but if I transferred the intended 1 TB and run in to the same issue later down the line...       the hassle with saving so much data will be too hard. So this goes back to the first question posed I guess. Not knowing what caused this issue in the first place is what worries me, I'm not asking for a seer. 
[/LIST]

I saw some threads/posts from others with the same issue but       it seemed to be connected to Windows installations - I have Ubuntu       14.04 LTS. And they don't go in to detail to answer my questions above.

---

### Post by yancek on 2019-01-13
You are posting at an Ubuntu 'Linux' forum indicating that you formatted a partition on your drive to ntfs, a windows filesystem so my questions would be:

How did you format ntfs, what tool/software did you use?
Why use ntfs?  Do you need to share between windows and Linux computers/operating systems?  If that's the case, you would be better off using windows to create an ntfs partition.  Generally, GParted or other Linux tools will work but if you have windows available, it is always better to use its software as it is always better to use Linux tools on a Linux system.

When you dis-connected and then re-connected the drive, how did you try to mount/access it?
Do you have another OS installed on this machine?

> **mount -o ro /dev/sdb2 /media/fz/Red 1TB **i

What I would expect when you enter that command is that it would fail every time.  Did you use this command in a terminal to mount?  Did you preceded the command with 'sudo'?  Not that you have a space between Red and 1TB, why?  You need to either use an escape character or put the command in quotes:

```
**sudo mount -o ro /dev/sdb2 "/media/fz/Red 1TB "**
```

Did you verify the disk/partition is still sdb/sdb2 as dis-connecting/connecting disks will not always give the same device name.  A situation where using a UUID would be useful.

---

### Post by furioususer on 2019-01-13
I used an application called Disks. It comes pre-installed.

> Why use ntfs?
It's supposed to work with "most systems", so I didn't see an issue with using NTFS on Ubuntu. What should I use? Ext4? And I may use it between Windows computers as well (sometimes I can bring my HDD to a friend or something that has Windows). No, I don't have access to a Windows installation. 

I have no other OS installed. I've never used dual boot.

> "When you dis-connected and then re-connected the drive, how did you try to mount/access it?
Like I always have: I go through **Files** and press the eject button under **Devices**. And it mounts automatically when the drive is connected and turned on. So I don't do anything to mount it. Right now I have duplicate (2 of them) Red 1TB under **Devices**. When I click them/mount them I got that long error msg I wrote about in my original post.


> Did you verify the disk/partition is still sdb/sdb2 as dis-connecting/connecting disks will not always give the same device name.
I'm not very good with the Terminal, so I'll try to answer this to the best of my abilities. I typed **lsblk** and got this: 
[I]NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
loop1    7:1    0  89,5M  1 loop /snap/core/6130
sdb      8:16   0 931,5G  0 disk 
&#9500;&#9472;sdb2   8:18   0 346,1G  0 part 
&#9492;&#9472;sdb1   8:17   0 811,6G  0 part 
loop4    7:4    0 173,6M  1 loop /snap/spotify/28
loop2    7:2    0  89,5M  1 loop /snap/core/6034
loop0    7:0    0  88,2M  1 loop /snap/core/5897
sda      8:0    0 111,8G  0 disk 
&#9500;&#9472;sda2   8:2    0 103,4G  0 part /
&#9500;&#9472;sda3   8:3    0   7,9G  0 part [SWAP]
&#9492;&#9472;sda1   8:1    0   512M  0 part /boot/efi
loop5    7:5    0 173,3M  1 loop /snap/spotify/26
loop3    7:3    0 174,4M  1 loop /snap/spotify/30[/I]

Since there is no name under mountpoint I don't know how I can cd to that search path. When I type cd sdb in Terminal I get: 
cd sdb
bash: cd: sdb: No such file or directory
cd sdb1
bash: cd: sdb1: No such file or directory
cd sdb2
bash: cd: sdb2: No such file or directory

Note I have two disks: one is a SSD of 120 GB where Ubuntu is on and the other is a 1 TB disk (the disk I have issue with).

> A situation where using a UUID would be useful
What does this mean? Why? How? 

> sudo mount -o ro /dev/sdb2 "/media/fz/Red 1TB** "**
I tried this and after I entered my password I got **mount: mount point /media/fz/Red 1TB  does not exist**

---

### Post by furioususer on 2019-01-13
Let me clarify: the disk I'm having issue with is only used for storing data. My OS installation (Ubuntu) is on a SSD disk with the Ext4 filesystem. Should I have used Ext4  for the storage disk too?

---

### Post by ajgreeny on 2019-01-13
Do you still have a Windows machine that you can attach the problem drive to, and if so, does Windows see the disk as you would expect it to?

I know nothing about Disks as I do not use Windows any more except as a very occasional VM of XP (yes still XP!) and W7, but they're both used only for one single application to update a GPS navigation device, nothing else, but I am aware that Windows can sometimes create what are known as dynamic partitions, definitely not usable in Linux in any way.

---

### Post by furioususer on 2019-01-13
> Do you still have a Windows machine that you can attach the problem drive to, and if so, does Windows see the disk as you would expect it to?
I previously wrote: No, I don't have access to a Windows installation. 


> I know nothing about Disks as I do not use Windows 
**Disks** comes pre-installed with Ubuntu 14.04 LTS!

---

### Post by yancek on 2019-01-13
The only reason to have a drive partition with an ntfs filesystem on it when you are using any Linux as an operating system is because you intend to regularly or at least sometimes use the disk on a windows operating system.  The reason for that is that a Linux OS like Ubuntu can read/write to a windows ntfs partition while a default windows installation cannot read/write to a Linux filesystem.  So the choice is yours based on your usage so if it has a primary purpose of being used for storage, use a Linux filesystem such as ext4.  If you think you might use it to share between windows, you could simply create 2 partitions, one ext4 and one ntfs.  One problem with using an ntfs filesystem when your only OS is Linux is that if the ntfs filesystem gets corrupted in some way, it is highly unlikely that you will be able to fix it unless it is an extremely minor problem.

When you have the external drive plugged in, run the command:  df -h and if it is mounted it should show the mount point.   

If you do not  see a directory/mount point Red 1TB when the external drive is attached, you can create it?
Create the mount point but do not use spaces in file names:  ```
sudo mkdir /media/fz/Red_1TB
```
then run the mount command again.  If that fails you might need to start over.

I would suggest that you move any data you currently have on the drive to another location and start over.  If the drive is going to be primarily used on Ubuntu, create and ext4 filesystem and if you want create another partition with an ntfs filesystem.  I would also recommend GParted which should be on the Ubuntu installation media.  If you no longer have that you can download it to your Ubuntu install or download an iso and burn it to a CD.

---

### Post by oldrocker99 on 2019-01-13
There are Windows programs which will allow a Windows OS read ext4-formatted drives, instead of "Windows cannot read this disk. Do you want to format it?" Here's a link: [https://www.howtogeek.com/112888/3-ways-to-access-your-linux-partitions-from-windows/](https://www.howtogeek.com/112888/3-ways-to-access-your-linux-partitions-from-windows/).

I had a NTFS partition when I was dual-booting, before I deep-sixed that malware magnet, and I could read and write to it, FWIW.

And do **NOT** use NTFS as your system disk, or, for that matter, /home.

---

### Post by furioususer on 2019-01-13
My main concern and objective is to rescue/save the data from       this drive/disk I can't access anymore. I would even be happy if I       could manage to just get a log (like an inventory) over what I exactly stored on the device       (that way I could download some of it from internet       again). 
    
       These different suggestions you gave me, will they risk this objective? Would it help if I had access to a Windows computer instead?

> I would suggest that you move any data you currently have on the drive to another location and start over. 


How? That is what I'm trying to do.

---

### Post by oldrocker99 on 2019-01-13
The drive will only be read, and copied to your backup, not written to. It won't risk your objective.

---

### Post by furioususer on 2019-01-13
I tried your instructions but it didn't seem to work. 

I wrote **sudo mkdir /media/fz/Red_1TB **and proceeded with entering my password. Afterwards I entered the command df -h again but there was still no Red_1TB folder in the list. So I tried to repeat this process but this time I was met with the msg[B] mkdir: cannot create directory &#8216;/media/fz/Red_1TB&#8217;: File exists 

[/B]So it has been created after all? But it doesn't show up in the list. 

May I also add, I started Gparted and the disk shows up there with info about size and how much of the disk I have used. It also appears that I can change label and add new UUID via this program. This is the most visible information about the disk I've manage to access so far. Is this something that can help me/us with recovering my data (I will follow your instructions of formatting to Ext4 but first I need to save my data)?

Edit: Oh, it seems like I can also "check and repair file system" through Gparted. Should I do try this first of all? If you answer yes, should I go ahead despite the warning (standard protocol) of it MAY cause loss of data?

---

### Post by yancek on 2019-01-14
> I wrote **sudo mkdir /media/fz/Red_1TB **and proceeded with entering my password

Apparently, you missed the line I posted immediately after the above, shown below.  You need to then use the mount command to mount that partition.

[QUOTEthen run the mount command again.  If that fails you might need to start over.
][/QUOTE]

```
sudo mount /dev/sdb2 /media/fz/Red_1TB
```

You should then be able to access the data on that partition and copy it elsewhere.  You won't need to be able to write to the disk as you are only copying FROM it.  And do not do any formatting until you have recovered your data.  Repairing the ntfs filesystem with GParted 'might' work but as I indicated above, the ntfsfix software can do very minor repairs to ntfs but obviously, there is no guarantee.  I would try copying the data without trying any repair first.

---

### Post by ajgreeny on 2019-01-14
But if you can get to a friend with Windows as you allude to in post #9, and run chkdsk a couple of times on that disk, you may then be able to read from, and even write to the disk easily from your ubuntu machine.

It is essential that you have a Windows system available if you have an NTFS partition as Linux is very limited in what it can do to a damaged NTFS filesystem.

---

