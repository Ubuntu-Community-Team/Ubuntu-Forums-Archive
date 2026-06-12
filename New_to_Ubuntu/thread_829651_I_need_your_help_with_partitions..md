---
title: "I need your help with partitions."
date: 2008-06-15
forum: New to Ubuntu
---

### Post by Camuso21 on 2008-06-15
To start out I'll tell you my problem, then I'll explain the steps I've already taken.

I installed Ubuntu using Wubi, which I assumed partitioned my 60Gb HD. I initially alloted 10Gb for Ubuntu as I was unsure whether or not I would keep it. Now I love it, and want to shrink my windows NTFS partition down to basically nothing, and resize my Ubuntu partition to take up the rest. 

Now heres where I'm at. I have a Knoppix Live CD which I ran and opened up QTParted, this showed that my sda drive had three partitions on it, the Windows NTFS partition (50Gb) a second FAT32 partition (5Gb) and a third I believe it was a FAT16 (this could be wrong, I believe it was something <1Gb). 

So I'm really new to Linux, and really lost. What do I do? Again all I want is three partitions, about a 20Gb Windows NTFS partition, then use the rest for a Linux, I'm looking for suggestions for the best way to both partition the Linux portion (swap size, format etc...) and how to do it. 

Thanks in advance.

---

### Post by Fingel on 2008-06-15
I'm sure Qparted can resize NTFS partitions. So you want to shrink the NTFS partition down 30 gb. That should be straight forward. What I don't understand is you didn't list the ubuntu partition in the list that qparted shows. If it was there, it would be as simple as extending the ubuntu partition to fill the new empty space.
Partitioning for linux is easy. The only 2 partitions are / (root) and swap. Swap is by convention twice the size as your RAM. The rest of linux will fit under /
However, a lot of people like to make a seperate /home partion. This is because if you want to reinstall or dual boot another partition you can save your home directory where all your personal data is stored. It can save a lot of headaches. 
There are a few filesystem available for linux, but most people go with Ext3. 
Hope that helps.

---

### Post by Lord Xeb on 2008-06-15
Before you do anything to the Windows partition, make sure you defrag it as like 10 times to move overthing as tightly as possible. Then shirk it down using GParted on the Ubuntu LiveCD to 20GB and make the rest unalloacted. Then go into Windows and use Wubi. You will have to wipe you current install of linux and then do a reinstall but that will fix everything I think. Someone should double check to see if I am right or not. Also, in the defragging of windows, the green lines of Unmoveable files. Those are Widows itself. If everything is all over the drive (meaning the Green lines) then you need to figure out something to get everything moved. 

For the linux portion, if you are using Wubi, the Ubuntu install will automatically setup swap space equal to your RAM size or the amount of ram you allocate to it. I suggest making 3 partitions (not counting the swap):

For one of them make it about 5GB and have it formated to FAT32. This will be your "Share space" it will allow you to share files amoung linux and windows more easily.

Next one should be /Home. Make it about 25-30 GB (your /Home folder is actually the largest of them all. Also doing this will allow easy reinstalls sice you will be keeping important information and just re-writting the main partion which is /)


Lastly, make the rest of the space as / or at least give it 5GB because / (root) will grow depending on the amount of apps and stuff you install and it holds the rest of the Directories like /usr, /var, etc...


All of the sizes I mentioned are sugject to change do the Swap. DO NOT GET RID OF SWAP! Make it the same size as the amount of ram you have (in MB)

---

### Post by tysonh on 2008-06-15
heres what i did.  I had windows installed on my laptop before I start the ubuntu install.  Once I go to the partitions set up in the ubuntu install I resized windows to 27g.  I made a 2g swap.  I made 31g partition for ubuntu.  I didn't make a extra partition for home or anything like that I only use 3 partitions when I dual boot.  It works fine and I've never had a problem with it.

I left the boot flag on for the windows partition and I use grub for the boot loader.  At start up it allows to me to pick which one to boot.

---

