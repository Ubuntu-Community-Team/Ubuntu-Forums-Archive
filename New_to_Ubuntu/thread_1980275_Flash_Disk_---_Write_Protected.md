---
title: "Flash Disk --- Write Protected"
date: 2012-05-14
forum: New to Ubuntu
---

### Post by czgirb on 2012-05-14
Today I try to delete some files, which stored in Flash disk. But it cannot be deleted.
* I try to choose that file > right-click PROPERTIES >
* within the PERMISSION tab, both GROUP and OTHER section's access are READ-ONLY,
* when I tried to change it. It said THE PERMISSION COULD NOT BE CHANGED.
* Either the EXECUTE section, which CHECKED the ALLOW EXECUTING FILE AS PROGRAM.
Would you mind to tell me how can I delete the file and re-format the Flash disk?
Please guide me ...
Thanx

---

### Post by NikTh on 2012-05-15
Hi , 
this "write protected" thing i think its from windows something. Maybe you didn't use the safe removal option. 
If you want to format the flash disk (You will LOSE EVERYTHING !!) then 

1) try with disk utility . Umount the disk and click "delete" then click "create" to specify a new filesystem

2)try almost the same with gparted. If you want to install it , open a terminal and ```
sudo apt-get install gparted
```

3)another option is dd command but you must  BE CAREFUL with this command.

---

### Post by czgirb on 2012-05-15
When I tried to format the flash disk, by using:

Places > Computer > select the Flash disk, right-click > Format ... it said:
[B]
[SIZE=3]Error formatting volume[/SIZE]
Error creating file system: helper exited with exit code 1: cannot open /dev/sdg1: Read-only file system[/B]

---

### Post by czgirb on 2012-05-15
> **NikTh said:**
> Hi , 
this "write protected" thing i think its from windows something. Maybe you didn't use the safe removal option. 
If you want to format the flash disk (You will LOSE EVERYTHING !!) then 

1) try with disk utility . Umount the disk and click "delete" then click "create" to specify a new filesystem

2)try almost the same with gparted. If you want to install it , open a terminal and ```
sudo apt-get install gparted
```3)another option is dd command but you must  BE CAREFUL with this command.

How to Umount the flash disk?

SORRY!
[B][I]Open the terminal and type sudo umount /dev/fd0
type password
umount: /dev/fd0: not found[/I][/B]
Any clue?

---

### Post by Baldrick_NZ on 2012-05-15
I wonder if this could be solved by```
gksu nautilus
```with the USB Flash drive connected, then right click over the usb drive and change the permissions that way?

---

### Post by czgirb on 2012-05-15
> **NikTh said:**
> 
... try almost the same with gparted. If you want to install it , open a terminal and ```
sudo apt-get install gparted
```

After install **gparted**, how can I run **gparted** program?

Gparted was found System > Administration > Gparted > Paertition > Format to > Fat32
Edit > Apply All Operation > Apply > the following information is appeared:
[B]An error occured while applying the operation
See the details for more information.
IMPORTANT
If you want support, you need to provide the saved details!
See [http://gparted.sourceforge.net/larry/tips/save_details.htm](http://gparted.sourceforge.net/larry/tips/save_details.htm) for more information.
[/B] 

> **NikTh said:**
> 
another option is dd command but you must  BE CAREFUL with this command.


DD command? How to use it? Please guide me

---

### Post by NikTh on 2012-05-15
> **czgirb said:**
> DD command? How to use it? Please guide me
I prefer to wait a more experience user to do this.( guide you)
You(we) can screw up your system if something goes wrong . 
sorry.

But you must give the output of command ```
sudo fdisk -l 
``` with your flash disk connected.

---

### Post by NikTh on 2012-05-15
> **NikTh said:**
> Hi , 


1) try with disk utility . Umount the disk and click "delete" then click "create" to specify a new filesystem

.
Did you try **disk utility** ? i guess that you use 10.04 or 11.04 , i think its on administration section.. find that program and try. 
DON'T forget to umount first (you can umount from disk utility , just click "**umount volume**") and then **DELETE** . At the end **Create** a new filesystem .

---

### Post by czgirb on 2012-05-15
> **NikTh said:**
> 
try with disk utility . Umount the disk and click "delete" then click "create" to specify a new filesystem


**System** > **Disk Utility** > select the **Flashdisk** >
right-panel: **Unmount Volume** > **Delete Partition** >
The following information immediately show-up:
> 
[SIZE=3]**Error deleting partition**[/SIZE]
An error occured while performing operation on .... (Partition 1 of Flash Drive UT_USB20): Operation Failed
Details:
[QUOTE]
Error erasing: helper exited with exit code 1: In part_del_partition: device_file=/dev/sdg, offset=32256
Entering MS-DOS parser (offset=0, size=1065353216)
MSDOS_MAGIC found
[/QUOTE]

---

### Post by Face-Ache on 2012-05-15
> **Baldrick_NZ said:**
> I wonder if this could be solved by```
gksu nautilus
```with the USB Flash drive connected, then right click over the usb drive and change the permissions that way?

This is what i thought might also have worked.

I used it to change the permissions of the Backgrounds directory so that i could easily save any wallpaper files that i liked in this folder, and it worked fine.

---

### Post by czgirb on 2012-05-16
> **Face-Ache said:**
> This is what i thought might also have worked.

I used it to change the permissions of the Backgrounds directory so that i could easily save any wallpaper files that i liked in this folder, and it worked fine.

How to do this?
Please guide me ...

---

### Post by Face-Ache on 2012-05-16
With the USB drive plugged in, open up a terminal with Ctrl-Alt-T, and type in "gksu nautilus" without the " quotes.

You should get a screen pop up that asks for your login password, type in your password.

Navigate to your USB drive, and then set the Permissions for each file like you tried to do in your initial post.

Once the Permissions have been set to read/write, you should then be able to delete each file.

I understand that the "gksu nautilus" command gives you the required file and folder privileges to change the permissions  :)

Let us know how you get on! Good luck.

---

### Post by oldfred on 2012-05-16
If it is FAT or NTFS formated you cannot change permissions or ownership as they do not support LInux file features as they are Windows file formats. Normally Nautilus just mounts in read/write so I am not sure what issue may be. sudo nautilus should then work but be careful not to modify any other files or folders in your system.

If a flash camera type (flat) card plugged into a USB adapter, it may have a tiny read only slider on the side. Sometimes that gets moved accidentally.

---

### Post by Ghost_Mazal on 2012-05-16
I have the same issue suddenly with my usb stick. It always worked fine , now suddenly it says "read only filesystem" and I can't do anything on it :mad:

FAT32 on mine

---

### Post by Face-Ache on 2012-05-16
> **oldfred said:**
> If it is FAT or NTFS formated you cannot change permissions or ownership as they do not support LInux file features as they are Windows file formats. Normally Nautilus just mounts in read/write so I am not sure what issue may be. sudo nautilus should then work but be careful not to modify any other files or folders in your system.

If a flash camera type (flat) card plugged into a USB adapter, it may have a tiny read only slider on the side. Sometimes that gets moved accidentally.

So would the OP need to plug the USB drive into a Windows OS to modify the 'read only' permission?

17,000 posts - congrats too, by the way  :)

---

### Post by quirino77 on 2012-05-16
I would suggest to plug and try on Windows.

Since nothing works, could it be a hardware protection? Some flash have a little switch that write protects the unit.

---

### Post by NikTh on 2012-05-22
> **quirino77 said:**
> I would suggest to plug and try on Windows.


+1 

more probably is that windows created this problem , eg : plug out the flash disk without first do "safe removal" . 
So one solution is that quirino suggests . 
In a windows environment plug the flash and _immediately_ right click and **"quick format"** .

---

### Post by czgirb on 2012-05-23
> **NikTh said:**
> +1 

more probably is that windows created this problem , eg : plug out the flash disk without first do "safe removal" . 
So one solution is that quirino suggests . 
In a windows environment plug the flash and _immediately_ right click and **"quick format"** .

In windows XP's environment, the flash is detected to be:
* Virus infected and Write-Protected.

You said **immediately right click** and **quick format**.
How to do that? Cos my AV is always quickest than my hand.
Please described ...
Thank you

---

### Post by carl4926 on 2012-05-23
I'm assuming the device is sdb, but change this accordingly and
Back in Ubuntu do

```
sudo dd if=/dev/zero of=/dev/sdb bs=1M
```

Then use gparted to partition and format to FAT

---

### Post by jtarin on 2012-05-23
> **czgirb said:**
> In windows XP's environment, the flash is detected to be:
* Virus infected and Write-Protected.

You said **immediately right click** and **quick format**.
How to do that? Cos my AV is always quickest than my hand.
Please described ...
Thank youStart XP in safe-mode

---

### Post by czgirb on 2012-05-23
> **carl4926 said:**
> I'm assuming the device is sdb, but change this accordingly and
Back in Ubuntu do

```
sudo dd if=/dev/zero of=/dev/sdb bs=1M
```Then use gparted to partition and format to FAT

**This is my result:**
> [I]czgirb@ubuntu:~$ sudo dd if=/dev/zero of=/dev/sdb bs=1M
[sudo] password for czgirb: 
dd: opening `/dev/sdb': No medium found
czgirb@ubuntu:~$ [/I]**The following is Gparted_details.htm**

> [SIZE=2]GParted 0.5.1[/SIZE]
 [SIZE=2]Libparted 2.2[/SIZE]
[SIZE=2]**Delete /dev/sdg1 (fat32, 979.97 MiB) from /dev/sdg**  00:00:00    ( ERROR )
[/SIZE][SIZE=2]calibrate /dev/sdg1  00:00:00    ( SUCCESS ) [/SIZE]        [SIZE=2]path: /dev/sdg1
start: 63
end: 2007039
size: 2006977 (979.97 MiB)
[/SIZE][SIZE=2]delete partition  00:00:00    ( ERROR )
[/SIZE][SIZE=2]libparted messages    ( INFO )
[/SIZE][SIZE=2]Unable to open /dev/sdg read-write (Read-only file system).  /dev/sdg has been opened read-only.
[/SIZE][SIZE=2]Unable to open /dev/sdg read-write (Read-only file system).  /dev/sdg has been opened read-only.
[/SIZE][SIZE=2]Unable to open /dev/sdg read-write (Read-only file system).  /dev/sdg has been opened read-only.[/SIZE]
[SIZE=2]Unable to open /dev/sdg read-write (Read-only file system).  /dev/sdg has been opened read-only.[/SIZE]
[SIZE=2]Unable to open /dev/sdg read-write (Read-only file system).  /dev/sdg has been opened read-only.[/SIZE]
[SIZE=2]Can't write to /dev/sdg, because it is opened read-only.[/SIZE]
[SIZE=2]Unable to open /dev/sdg read-write (Read-only file system).  /dev/sdg has been opened read-only.[/SIZE]
[SIZE=2]========================================[/SIZE]
[SIZE=2]**Create Primary Partition #1 (fat32, 1011.91 MiB) on /dev/sdg**[/SIZE]    [SIZE=2]========================================[/SIZE]


---

### Post by carl4926 on 2012-05-24
I did tell you to identify your device properly

It looks like you are dealing with sdg not sdb. It's VERY important you get this detail correct!

```
sudo dd if=/dev/zero of=/dev/sdg bs=1M
```
Assuming your device is still sdg !

---

### Post by czgirb on 2012-05-24
> **carl4926 said:**
> I did tell you to identify your device properly

It looks like you are dealing with sdg not sdb. It's VERY important you get this detail correct!

```
sudo dd if=/dev/zero of=/dev/sdg bs=1M
```Assuming your device is still sdg !

I'm sorry Carl, I just copied the code and I'm never do a modify
> 
czgirb@ubuntu:~$ sudo dd if=/dev/zero of=/dev/sdg bs=1M
[sudo] password for czgirb: 
dd: opening `/dev/sdg': Read-only file system
czgirb@ubuntu:~$ 

---

### Post by carl4926 on 2012-05-24
Did we establish if this device has a device lock on it?

---

### Post by czgirb on 2012-05-24
> **carl4926 said:**
> Did we establish if this device has a device lock on it?
SORRY ... what it's mean? Please use easy english. My english is not good.
SORRY

---

### Post by carl4926 on 2012-05-24
Some USB pen drives have a small sliding switch on the side to lock the device to Write Protected mode

See this image
[http://www.motherboards.org/images/reviews/hardware/1132_p1_5.jpg](http://www.motherboards.org/images/reviews/hardware/1132_p1_5.jpg)

---

### Post by czgirb on 2012-05-24
No! No! My USB is not.
Let me tell the story. About half a year ago, I plugged the FDD into my friends Windows XP's computer in order to copied some file ... but since the FDD was caused the computer's system freeze in 10-minutes, so it was un-plugged. And that's the problem's occured.

---

### Post by carl4926 on 2012-05-24
Sounds like it needs flushing:)

---

### Post by Ghost_Mazal on 2012-05-24
I have the sam issue again on a different stick. Previously wiping the partition fixed it. Now , nothing works , not even dd can wipe it.

What to do if even dd are not allowed to wipe ?

s```
udo dd if=/dev/zero of=/dev/sdb bs=1M
dd: opening `/dev/sdb': Read-only file system

```

---

### Post by lile001 on 2012-05-24
> **Ghost_Mazal said:**
> I have the sam issue again on a different stick. Previously wiping the partition fixed it. Now , nothing works , not even dd can wipe it.

What to do if even dd are not allowed to wipe ?

s```
udo dd if=/dev/zero of=/dev/sdb bs=1M
dd: opening `/dev/sdb': Read-only file system

```

I have run into the same issue, and concluded that my flash drive was just broken. (Or I did not possess the skill to fix it!) I went through a long thread on this forum trying to fix it and had no luck.  Flash drives are cheap - get another one!

---

### Post by irv on 2012-05-24
I've had a few USB sticks go bad on me, but I have also salvaged some also. Try this by following these steps.
1. start gparted.
2. Select the USB drive for the Gparted > Device menu at the top.
[ATTACH]218641[/ATTACH]
3. Make sure you have the partition on the USB drive selected and from the partition menu select delete. If the drive is mounted you may have to unmount it from the same menu first.
[ATTACH]218642[/ATTACH]   [ATTACH]218643[/ATTACH]
4. Click on the green arrow at the top to apply changes.
5. At this point you might have to exit gparted and then restarted. As I remember I had to do this for some reason.
6. Next select the device menu and create a new partition. You can set the format at this point. If you want to read it with windows make it Fat32. I also set the boot flag if I want to boot from the USB drive.
[ATTACH]218644[/ATTACH]
If the drive is salvageable you should have a good drive again.
Hope this works for you.

---

### Post by czgirb on 2012-05-25
**An error occured while applying the operation**
See the details for more information.
**IMPORTANT**
[I]If you want support, you need to provide the saved details!
See [http://gparted.sourceforge.net/larry/tips/save_details.htm](http://gparted.sourceforge.net/larry/tips/save_details.htm) for more information.[/I]

Any opinion?

---

### Post by carl4926 on 2012-05-25
Try dd again

---

### Post by czgirb on 2012-05-25
czgirb@ubuntu:~$ sudo dd if=/dev/zero of=/dev/sdg bs=1M
[sudo] password for czgirb: 
dd: opening `/dev/sdg': Read-only file system
czgirb@ubuntu:~$

---

### Post by irv on 2012-05-25
How big a memory stick are we talking about here? I bought an 8gig stick yesterday for $8. If it is an 8gig or less go out and buy another one. aggravation is got to be worth something.

---

### Post by carl4926 on 2012-05-25
> **irv said:**
> How big a memory stick are we talking about here? I bought an 8gig stick yesterday for $8. If it is an 8gig or less go out and buy another one. aggravation is got to be worth something.

+1

Like I said. Visit the bathroom, carefully flush the old one.
Go shopping

---

### Post by Ghost_Mazal on 2012-05-25
> **carl4926 said:**
> +1

Like I said. Visit the bathroom, carefully flush the old one.
Go shopping

Hehehehe , I think the one I'm battling with is gonna go the same route

---

### Post by NikTh on 2012-05-25
> **czgirb said:**
> czgirb@ubuntu:~$ sudo dd if=/dev/zero of=/dev/sdg bs=1M
[sudo] password for czgirb: 
dd: opening `/dev/sdg': Read-only file system
czgirb@ubuntu:~$

Try fsck command to see .. 
```
sudo fsck.vfat -a /dev/sdg
```

If error occurs try with /dev/sdg1 instead.

---

### Post by irv on 2012-05-25
I just order two 16 gig USB's off Amazon for under $20 with free shipping. I use them for testing different distors.

---

### Post by eleftg on 2012-05-25
Unfortunately, the "Write protected" message (unless there is a hardware write lock switch) is the way your USB stick tells you "I'm dead. Goodbye my old friend". Any USB flash disk has a certain number of write/erase cycles as life expectancy. When this limit is passed you must change it. Remember that most USB sticks have lifetime warranties ;-) so you can possibly trade it for a new one at the place you purchased it.

---

### Post by czgirb on 2012-05-26
OK! Thanx

---

