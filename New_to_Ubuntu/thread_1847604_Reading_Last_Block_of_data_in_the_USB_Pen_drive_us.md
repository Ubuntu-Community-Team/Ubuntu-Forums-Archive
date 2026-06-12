---
title: "Reading Last Block of data in the USB Pen drive using dd or any other command"
date: 2011-09-21
forum: New to Ubuntu
---

### Post by psrdotcom on 2011-09-21
Hi experts/learners,

I am facing any issue while reading the last block of the USB Pen drive through script.

**Reading First Block of Data:**
*dd if=/dev/sdb1 of=/home/user/firstblock.txt bs=512 count=1*

**Reading Last Block of Data:**
*dd if=/dev/sdb1 of=/home/user/lastblock.txt bs=512 count=1 _**skip=??**_*

How i will come to know about the skip block of input file to read the last block in script.

Using dd command, i was able to read the data from the USB Pen drive but my issues are,
i) How the script will automatically know that, where the USB Pen drive is mouted?
ii) If it identifies the mount location of the pendrive, how it will know its size and read the last block of data alone.

Please try to help me and share your knowledge(Experts)/Improve your knowledge(Learners)

Thanks in advance.

---

### Post by anewguy on 2011-09-21
Does this mean the USB pen drive was formatted as an ext(x) file system?

Dave ;)

---

### Post by psrdotcom on 2011-09-21
Nope .. The USB Pen Driver will be formatted with FAT 32 File System ..

---

### Post by Lisiano on 2011-09-21
First of DD uses low-level access. As in it doesn't care wherever your USB is, it just wants the if=/dev/sdx to be correct. Now we don't know which /dev/sdx device it is, nor if it's even /dev/hdx
So how do we solve that? ```
sudo blkid
``` But this just prints out the devices, their labels and UUID... Wait. UUID, it never changes between mounts, AFAIC only when you remove and remake the partition. Cool. Let's say my UUID is 123456789-abcd-efgh-cool-deadbeefmate. We find the UUID and use cut to cut out the /dev/ name. ```
sudo blkid | grep "123456789-abcd-efgh-cool-deadbeefmate" | cut '-f1' '-d:'
```
Tada. Export it as a variable and you are all set!

For the skip part, take a look at ```
sudo fdisk -s /dev/sdb1
``` this prints out the partition size in blocks. I'm not exactly sure but if you skip up to that block you will probably have nothing else to read. So do some math using the shell ```
echo $[(`sudo fdisk -s /dev/sdb1`-1)*512]
``` I don't know how skipping works so that might not be what you want but you should be able to adapt it.

Now my take on how your script might look like
```
#!/bin/sh
USB_DEV_NAME=`blkid | grep "123456789-abcd-efgh-cool-deadbeefmate" | cut '-f1' '-d:'`

dd if=$USB_DEV_NAME of=$HOME/firstblock.txt bs=512 count=1
dd if=$USB_DEV_NAME of=$HOME/lastblock.txt bs=512 count=1 skip=$[(`fdisk -s $USB_DEV_NAME1`-1)*512]
```

EDIT: The way I put it in the script is that I assume you are running it as root or using sudo since dd didn't have sudo near it.

---

### Post by psrdotcom on 2011-09-21
Thanks for the detailed explanation .. i will try and if it works, i will mark this thread as solved.

---

### Post by psrdotcom on 2011-09-22
I will be using different USB pen drives in different times.

Can we have some generic solution to read the last block of every USB Pen drive?

As per your explanation, i can only do for particular USB pen drive .. but I want it to be generic ..

Can you help me ..

---

### Post by anewguy on 2011-09-22
EDITED:  original text removed here since vol_id hasn't been around for a long time.  I know that blkid also returns the UUID in it's output string for a device - for example:

dave@dave-MS-7576:~$ sudo blkid /dev/sdb1
[sudo] password for dave: 
/dev/sdb1: SEC_TYPE="msdos" UUID="2A29-EDE7" TYPE="vfat" 
dave@dave-MS-7576:~$ 

What I don't know right now is how to extract just the string inside the quotes for UUID, but once that is accomplished it's a matter of parameter substitution in your script and passing the device (/dev /sdxx) as a parameter to the script as well.

I'm not an expert on the script/command line by any means, so I'll see if I can find a way to extract the string and post it back here.  Someone who already knows will probably post back before me.

dave ;)

---

### Post by psrdotcom on 2011-09-22
Thanks for the reply .. I will also search and if I found some solution .. for sure, I will share with you ..

---

### Post by anewguy on 2011-09-22
> **psrdotcom said:**
> Thanks for the reply .. I will also search and if I found some solution .. for sure, I will share with you ..

I *KNOW* this can be done - I'm just getting frustrated with myself for not being able to figure it out right now :(.  Maybe it's because it's so late.  Going to get some sleep and look at it fresh tomorrow late afternoon.

Sorry

Dave ;)

---

### Post by Azdour on 2011-09-22
Hi,

I may be able to help out with the first part. Someone else can probably help with the cut part. For the argument and the return of what blkid creates:

```
xx=`blkid $1`
```

---

### Post by Lisiano on 2011-09-22
Question, are you going to run the script from the USB? If so, it could be possible to extract the location using the place where the script is ran.
Probably doing it somehow this way.
```
mount | grep `pwd | cut '-f1-3' '-d/'` | cut '-f1' '-d '
```
```
#!/bin/sh
USB_DEV_NAME=$(mount | grep `pwd | cut '-f1-3' '-d/'` | cut '-f1' '-d ')
``` Should work if it get's mounted somewhere to a 3rd level dir (Assuming root is 1st level), for example /media/usb. But I'd still suggest using UUID. Since it's more robust, you can create a file on the USB with it's UUID and grep it's content, then using that determine which USB the script is running on and reuse my code I posted before. Probably something in the lines of ```
#!/bin/sh
UUID=`cat .uuid`
USB_DEV_NAME=`blkid | grep $UUID | cut '-f1' '-d:'`
``` Both ways make the code more generic but you need to still run it from the USB, both ways let you keep the script wherever you want since cut will only give upto the 3rd dir ({/media/usb}/bin/script.sh) and cat .uuid can be changed to any place you want (/media/usb/bin/script.sh and it's config is in /media/usb/config/uuid so call this cat ../config/uuid)

Hope my noobie scripting skills help you.

It's safe to read a dev with dd even if you mounted it. All reading is safe. All writing is dangerous.

Btw something for UUID robustness. [http://en.wikipedia.org/wiki/Universally_unique_identifier#Random_UUID_probability_of_duplicates](http://en.wikipedia.org/wiki/Universally_unique_identifier#Random_UUID_probability_of_duplicates)

---

### Post by psrdotcom on 2011-09-22
Thanks for the great replies .. I will try it and get back to you with my results.

---

### Post by anewguy on 2011-09-22
You can get the UUID of a device with:

my_uuid=$(blkid -s UUID $1 | cut -d \" -f 2 )

So far, the original script as posted took a hard coded UUID.  The statement above assumes you are feeding the device name in on a parameter.  

If also tried to test just this piece of the original script with USB_DEV_NAME set to /dev/sdb1:

dd if=$USB_DEV_NAME of=$HOME/lastblock.txt bs=512 count=1 skip=$[(`fdisk -s $USB_DEV_NAME1`-1)*512]

It returns a null in the skip statement such that it errors out with divide by zero.

I'm still working out why that happened.

From there, to make it automatic, will need to add the code to get the device name as per Lisiano, however I don't see at all where the UUID would be needed then, as everything else revolves around the device name.  The UUID was only being used to get the device name.

I'll keep hacking at this and see if I can figure out something that works.

Dave ;)

---

### Post by psrdotcom on 2011-09-23
Guys,
I have come up with this solution. Verify and let me know, whether I am doing the correct way or not?

```

1. Finding my own device
$ sudo ls -l /dev/disk/by-id
#lists all the devices with its label and with partions

2. From this list I would like to take my own USB pen drive, since I have been given proper name to the device(s)
$ USB_NAME=sudo ls -l /dev/disk/by-id | grep PSR | 
# Gives my USB Pendrive, since I have named(label) the device with PSR

3. To get the last field from the list, use awk
$ sudo ls -l /dev/disk/by-id | grep PSR | awk '{print $NF}'
# List the ../../sdb1 format

4. From this list we have to get the block device name only
$ USB_DEV_NAME=`sudo ls -l /dev/disk/by-id | grep PSR | awk '{print $NF}' | cut -f3 -d/`
# Finally, we will the get the result as sdb1(the device which it was mouted)


```I got the correct result, But let me know, If I am going in wrong way to identify the device.

After getting the device name, I will be using dd command to read the data from the device.

dd if=$USB_DEV_NAME of=$HOME/lastblock.txt bs=512 count=1 skip=$[(`fdisk -s $USB_DEV_NAME1`-1)*512]

Reference: [Lisiano]("http://ubuntuforums.org/member.php?u=1108763") 4th Reply in this thread Thanks a lot guys,

Keep Rocking :guitar:

---

### Post by Lisiano on 2011-09-23
Just a parallel way to do this with blkid since it outputs labels too.
```
blkid | grep LABEL=\"PSR\" | cut '-f1' '-d:'
```

Also for some reason I get this, they don't contain any of my partition names
```
ls -l /dev/disk/by-id/
total 0
lrwxrwxrwx 1 root root  9 2011-09-23 10:14 ata-Hitachi_HTS545025B9A300_100827PBN204CSK0SENU -> ../../sda
lrwxrwxrwx 1 root root 10 2011-09-23 10:14 ata-Hitachi_HTS545025B9A300_100827PBN204CSK0SENU-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 2011-09-23 10:14 ata-Hitachi_HTS545025B9A300_100827PBN204CSK0SENU-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 2011-09-23 10:14 ata-Hitachi_HTS545025B9A300_100827PBN204CSK0SENU-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 2011-09-23 10:14 ata-Hitachi_HTS545025B9A300_100827PBN204CSK0SENU-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 2011-09-23 10:14 ata-Hitachi_HTS545025B9A300_100827PBN204CSK0SENU-part6 -> ../../sda6
lrwxrwxrwx 1 root root 10 2011-09-23 10:14 ata-Hitachi_HTS545025B9A300_100827PBN204CSK0SENU-part7 -> ../../sda7
lrwxrwxrwx 1 root root  9 2011-09-23 10:14 scsi-SATA_Hitachi_HTS5450100827PBN204CSK0SENU -> ../../sda
lrwxrwxrwx 1 root root 10 2011-09-23 10:14 scsi-SATA_Hitachi_HTS5450100827PBN204CSK0SENU-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 2011-09-23 10:14 scsi-SATA_Hitachi_HTS5450100827PBN204CSK0SENU-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 2011-09-23 10:14 scsi-SATA_Hitachi_HTS5450100827PBN204CSK0SENU-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 2011-09-23 10:14 scsi-SATA_Hitachi_HTS5450100827PBN204CSK0SENU-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 2011-09-23 10:14 scsi-SATA_Hitachi_HTS5450100827PBN204CSK0SENU-part6 -> ../../sda6
lrwxrwxrwx 1 root root 10 2011-09-23 10:14 scsi-SATA_Hitachi_HTS5450100827PBN204CSK0SENU-part7 -> ../../sda7
lrwxrwxrwx 1 root root  9 2011-09-23 10:18 usb-SEMC_CD-ROM_43423531314D33303347-0:1 -> ../../sr0
lrwxrwxrwx 1 root root  9 2011-09-23 10:18 usb-SEMC_Mass_Storage_43423531314D33303347-0:0 -> ../../sdb
lrwxrwxrwx 1 root root  9 2011-09-23 10:14 wwn-0x5000cca62aea9e81 -> ../../sda
lrwxrwxrwx 1 root root 10 2011-09-23 10:14 wwn-0x5000cca62aea9e81-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 2011-09-23 10:14 wwn-0x5000cca62aea9e81-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 2011-09-23 10:14 wwn-0x5000cca62aea9e81-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 2011-09-23 10:14 wwn-0x5000cca62aea9e81-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 2011-09-23 10:14 wwn-0x5000cca62aea9e81-part6 -> ../../sda6
lrwxrwxrwx 1 root root 10 2011-09-23 10:14 wwn-0x5000cca62aea9e81-part7 -> ../../sda7
```
```
sudo blkid
/dev/sda1: LABEL="Debian" UUID="94f3b19b-043f-461e-a801-d4617fca5f9b" TYPE="ext4" 
/dev/sda3: LABEL="Win7" UUID="2D3904F811C1A6E6" TYPE="ntfs" 
/dev/sda5: LABEL="Ubuntu" UUID="ada82c31-a482-466d-a82c-25727d629501" TYPE="ext4" 
/dev/sda6: LABEL="Home" UUID="96634547-a26a-4e88-8665-3e183189e47c" TYPE="ext4" 
/dev/sda7: UUID="c88d0151-71ab-4d8d-a16b-3c12140d6955" TYPE="swap"
```
Maybe you want /dev/disk/by-label instead of /dev/disk/by-id
```
ls -l /dev/disk/by-label
lrwxrwxrwx 1 root root 10 2011-09-23 10:14 Debian -> ../../sda1
lrwxrwxrwx 1 root root 10 2011-09-23 10:14 Home -> ../../sda6
lrwxrwxrwx 1 root root 10 2011-09-23 10:14 Ubuntu -> ../../sda5
lrwxrwxrwx 1 root root 10 2011-09-23 10:14 Win7 -> ../../sda3
```

---

### Post by psrdotcom on 2011-09-23
Yes. Thanks for the optimised commands.

---

