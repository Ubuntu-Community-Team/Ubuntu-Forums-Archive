---
title: "Dual Boot with Win7"
date: 2013-01-17
forum: New to Ubuntu
---

### Post by mrpr3sid3nt on 2013-01-17
Hi, I am running Ubuntu 12.04 and would like to dual boot with Win7.

I have installed Ubuntu at the start of my drive, now when I try to install Win7 to the other partition I get an error. Is it possible to move my Ubuntu installation to a later part of my hdd so that I can install Win7 at the start? Alternatively is there a way to create a restore point of my Ubuntu installation to install later from livecd?

I would prefer not to format my hdd and clean install Win7 as I have had this installation of Ubuntu for a while and it is set up how I like it. I have a separate hdd that I can use to move things around if necessary.

Thanks, Andy

---

### Post by cogier on 2013-01-17
You are doing this the wrong way round. While there may be a way to sort out the situation you now find yourself in I suggest that you install Windows first and then Ubuntu.

The reason for this is that Windows does not look for any other operating system whereas Ubuntu does so will see Windows when installing.

---

### Post by d4m1r on 2013-01-17
OK, so wait...Do you already have Win7 installed or do you have a totally clean HDD? Here is my advice;

1) Install Windows 7 on a single partition (split the HDD during the Windows install process)

2) Install Ubuntu AFTER, on its own partition (format the split partition during the Ubuntu install process)

You will then have each OS on it's own partition, and Ubuntu is able to detect a Windows install so you will always get a prompt when booting up the computer as to which OS you want to go into...

---

### Post by DracoMaille on 2013-01-17
According to the information you have given, you should be able to install Win7 on the NTFS partition of your drive.  It would be helpful in diagnosing the issue further if you could give the exact wording of the error message you get when you try to install Windows.  That helps to determine if it is an Ubuntu or a Windows problem.

I don't think that the location of the operating systems on the drive should affect your ability to install or use them, so I don't recommend trying to move all of the drive information around -- you might inadvertently corrupt file locations and confuse your OS causing lagging and other hassles .. also I am not entirely sure that there are not aspects of Ubuntu that would be unable to be moved with simple copy functions, which could also cause you a lot of hassle if you lose a key component of the OS.

Alternatively, you could use your secondary hard drive to clean install Windows, and then edit your boot process to let you choose which drive/OS to start from.  It would be dramatically slower on a USB external drive, however.

Also, if you can get Windows onto the NTFS partition, you can use the tool found in this thread to update your boot process to give you the option as to which OS to boot.    [http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)

---

### Post by oldfred on 2013-01-17
You have managed to format the drive all as an extended partition. Windows has to install to a primary partition fromatted NTFS with the boot flag or unallocated space where it can create the primary NTFS partition.

I do not like moving partitions but you can use gparted to move your Linux install, I would be sure to have a good backup of /home and a list of all installed apps from dpkg or synaptic.

When dual booting I suggest another NTFS shared partition for data. Then you do not have to write into the Windows system partition. That has been known to cause issues. 

       GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by mrpr3sid3nt on 2013-01-17
Ok, I have made a note of the error I get when I choose where to install Win7:

'Setup was unable to create a new system partition or locate an existing system partition. See the Setup log files for more information.'

For clarity. I have Ubuntu installed on the 98.59GiB part of the disc in my screenshot, the 357.85GiB part is where I would like to install Win7. 

I have another hdd which is empty, I get the same Win7 error when I try to install Win7 on there.

---

### Post by oldfred on 2013-01-17
Your 357.85GiB is inside the extended partition, so you can only create logical partitions. 
Windows will only install to primary (or actually it will install to a logical if it is a second install and you are booting Windows first install from a primary partition).

You have to do major partition reorganization with gparted.

---

### Post by mrpr3sid3nt on 2013-01-18
Ok, thanks for your help. I will reformat and start again after going through the gparted tutorials provided by oldfred.

Thanks

---

