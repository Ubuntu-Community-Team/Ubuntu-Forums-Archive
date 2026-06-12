---
title: "Dual boot Win7/Ubuntu on Toshiba A200"
date: 2012-05-27
forum: New to Ubuntu
---

### Post by newcomer111 on 2012-05-27
Hello everyone,

I'm about to install Ubunto on dual boot with Windows7, so I need to verify my configuration.

I have a Toshiba Satellite A200-1XO laptop (certified for Vista), I deleted all partitions, created three new ones and installed Windows7.

So I've arranged my hard disk this way:

(None): reserved for recovery 
C: for Windows7
D: empty, for Ubuntu (so it will divided in three: System, Data and Swap).
E: another partition for data (movies and song...)


Could you confirm my configuration, please? Will be there any problem with the dual boot?

Can't wait to join you guys :popcorn:

---

### Post by virajsawa on 2012-05-27
Well as long as you have labelled the partition in which you gonna keep ubuntu 'PRIMARY' you will not encounter any problem.
(Unless any specific with motherboard.. some boards don't support ubuntu)

---

### Post by Bucky Ball on 2012-05-27
All looks good. 'D' will end up being three separate partitions:

sda*: / = root partition, where Ubuntu lives, 20Gb plenty;
sda*: /home = what you have as a data partition, make it the /home partition. This is where your settings and personal data lives (large as you like);
/swap = /swap, 2Gb fine.

... where sda* = sda5 for example.

Another thing; you want to create an extended partition with the space that is D (delete the partition and create an extended partition in the free space). Then, when you are installing, choose 'Something Else' and install Ubuntu and the other data partition inside the extended partition as logical drives/partitions. Reason? You can't have more than four primary partitions on one physical drive.

You will see the extended partition there and it is pretty straightforward. Create the Ubuntu partitions using the default mount points /, /home, /swap tweaking the suggested sizes I gave above. You'll also see the Win7 partitions; they will be NTFS. All good, just leave 'em alone. ;)

Hope that helps.

---

### Post by codingman on 2012-05-27
no problems with this setup, just pop in the cd and restart into it, then allocate the system to the desired partition

---

### Post by Bucky Ball on 2012-05-27
> **virajsawa said:**
> Well as long as you have labelled the partition in which you gonna keep ubuntu 'PRIMARY' you will not encounter any problem.
(Unless any specific with motherboard.. some boards don't support ubuntu)

Not sure where you heard/read this but it is wrong. Ubuntu does NOT need to be on a primary partition. It will happily run on a logical drive (inside an extended partition). Windows, on the other hand, needs to be (without some serious stuffing about) on a primary. It likes drive one, partition one (primary).

I also have no idea where you heard/read some motherboards don't support Linux. Never heard of a Windows motherboard. Some MBs are friendlier than others, but no support whatsoever? ;)

---

### Post by codingman on 2012-05-27
> **Bucky Ball said:**
> Not sure where you heard/read this but it is wrong. Ubuntu does NOT need to be on a primary partition. It will happily run on a logical drive (inside an extended partition). Windows, on the other hand, needs to be (without some serious stuffing about) on a primary. It likes drive one, partition one (primary).

Windows 8 is going to let you choose, but currently it can only stand drive one, the main reason why you cannot make a dual-boot machine if you have ubuntu first (well, at least not easily)

---

### Post by newcomer111 on 2012-05-27
Thank you guys for you replies.

> 
Another thing; you want to create an extended partition with the space  that is D (delete the partition and create an extended partition in the  free space). Then, when you are installing, choose 'Something Else' and  install Ubuntu and the other data partition inside the extended  partition as logical drives/partitions. Reason? You can't have more than  four primary partitions on one physical drive.OK let me get this straight:
Delete partition D (from windows, right?)
Create an extended partition (always from Windows)
Don't format it yet (since it won't be possible with ext4 file system)
Put the CD and reboot
Choose the "Other thing" option
**Don't choose **"primary" for the three Ubuntu's partitions


> **Bucky Ball said:**
> 

I also have no idea where you heard/read some motherboards don't support Linux. Never heard of a Windows motherboard. Some MBs are friendlier than others, but no support whatsoever? ;)
Well.. on the other hand, I've heard that some laptops, like mine I guess, are certified for Vista only, which makes boot problems when installing a non-Windows OS.
Is it? (even, it was OK when I tested Ubunto from the live CD)

So there is no reason to be worried, right?:-\"


Edit: Another thing, the size of D is 20G: so 14G for root, 5 for data and 1G for swap.
Is it OK?

---

### Post by Bucky Ball on 2012-05-27
> **newcomer111 said:**
> Thank you guys for you replies.

OK let me get this straight:
Delete partition D (from windows, right?)***(you can do this from the Ubuntu Live CD also using Gparted (partition manager); doing it this way ensures all partitions are unmounted, or can be, as you're running from the CD, not the hard drive or any partition)***
Create an extended partition (always from Windows) ***(and this; Gparted)***
Don't format it yet (since it won't be possible with ext4 file system) ***(you can't format an extended partition; it is a big 'holder'/empty partition, if you follow)***
Put the CD and reboot
Choose the "Other thing" option ***(Something Else ;) )***
**Don't choose **"primary" for the three Ubuntu's partitions ***(You can't select 'Primary' for a logical drive/partition inside an extended partition)***

Well.. on the other hand, I've heard that some laptops, like mine I guess, are certified for Vista only, which makes boot problems when installing a non-Windows OS.
Is it? (even, it was OK when I tested Ubunto from the live CD)

So there is no reason to be worried, right?:-\"


Edit: Another thing, the size of D is 20G: so 14G for root, 5 for data and 1G for swap.
Is it OK?

I've put my replies in bold italics in brackets above.

No reason to worry. I have a Win7 sticker on mine with a Powered by Ubuntu sticker right next to it. Certified that Win7 will work on it by Microsoft and the computer manufacturer I guess. I certify that Ubuntu runs on it, too (along with Arch and OpenSuse). ;) 

20Gb will do it but you are going to run out of the 5Gb /home pretty quick unless you are intending to keep the bulk of your personal stuff on the other data partition to share with Win (in which case the second data partition should be formatted to NTFS; they can both read/write to that). All good apart from that. ;)

---

### Post by newcomer111 on 2012-05-27
All right! Thank you a lot Bucky Ball :)

I'll keep you posted after the install.

Linux here I come \\:D/

---

### Post by Canansp on 2012-05-27
Hi Newcomer! Welcome to the forum. I have a Toshiba Satellite A200-12X, which is almost 5 years old, and my Ubuntu installation went flawless. 

I have to say, I am not dual booting my system, since I decided to get rid of Windows. I did not have any problems with my hardware, or anything.

How old is your laptop? The newer, the more prone it is to have problems with hardware recognition. This said, I am sure you won't have any problems. 

Have a nice day,

---

### Post by wilee-nilee on 2012-05-27
> **newcomer111 said:**
>  Create an extended partition (always from Windows)

I would not make any partitions for Linux in windows ever, period.

---

### Post by Mark Phelps on 2012-05-29
> **wilee-nilee said:**
> I would not make any partitions for Linux in windows ever, period.

An Extended partition is just an empty container, so it shouldn't matter which tool you use to create it.

But, since GParted does support that, I would agree that using GParted would be best in this situation.

---

### Post by newcomer111 on 2012-05-30
Ubuntu is well installed, by dual boot with Win7. 
All the drivers are OK (except I didn't get the maximum resolution with my graphic card, but well...)

I really appreciate your help :)

---

### Post by Bucky Ball on 2012-05-31
No problems, excellent news and enjoy the new system and learning curve. ;)

---

