---
title: "How To Use partimage on SystemRescueCD"
date: 2006-07-31
forum: Outdated Tutorials &amp; Tips
---

### Post by Frank Golden on 2006-07-31
Hi All,
   This is my first attempt at a How To. Excuse my clumsiness.
This makes the assumption that you have a separate ext3 or Fat32
partition on your machine with enough room for the image you create. I believe the partition has to be at least as large as
the the one you are trying to copy from. Maybe someone can correct me if I am wrong or if anyone sees any errors im my
instructions. This works for me. Here goes. 
These instructions apply to what I have learned using partimage.
By all means Use At Your Own Risk.


                        A Guide to using partimage on the SystemRescueCD.
                                                      Ubuntu 6.06 LTS

This assumes a separate ext3 or Fat32 partition. If your Ubuntu install is 4GB or bigger use a ext3
partition.

First download the SystemRescueCD and burn to CD using instructions on site.

[http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)

All code that follows will be bracketed [   ] do not include brackets. Everything is case sensitive and
include spaces and punctuation marks.
Make sure your BIOS is set to boot from CD first.
After burning CD boot to it on the system you want to backup.
After booting SystemRescueCd, at the prompt

Type  [fdisk -l] where the l is a lower case L then hit enter

This will show you your partitions in a table.
You should see your HD listed as either hda or sda, with the individual partitions numbered.
For example hda1 or sda1, hda2 or sda2 etc.
The file system will be listed for each partition.
ext3 will be ext3 and Fat32 will be vfat.
 For now say that your spare ext3 or Fat32 partition is listed as hda3 or sda3.
remember that or write it down.
We will now make a directory in ram to mount the partition to.

Type  [mkdir /backup] then hit enter. You can name the directory anything you want I like /backup.

Now we will mount the storage partition. Assume it is hda3 and ext3 file system. 
On disk it is actually /dev/hda3.

Type  [mount -t ext3 /dev/hda3 /backup] then hit enter.  Mind your spacings etc.

This will mount your storage partition in ram at the directory you created earlier.
You will not see confirmation after each enter. Just the prompt. If there is a problem
a error message will appear.
Now we will start partimage, at the prompt 

Type  [partimage] then hit enter.

Partimage will open with a screen showing all you partitions. Using the arrow keys
highlight your Ubuntu partition (the one you want to image) and press tab.
This will move you to a space labeled * image file to create/use. You can call your image anything you want
but I prefer something descriptive like /backup/hda2partition (assuming hda2 is your Ubuntu partition).
Under action to be done highlight "save image into new image file" using arrow keys and hit
spacebar to select. Hit F5 key.
This will open next screen.
On next screen you can choose compression level. I use no compression. It's quicker.
Highlight your compression level using arrow keys and hit space bar to select. Under "options" leave the default 
X's in the "check partition before saving" and "enter description". Using the arrow keys move to "if finished ..."
highlight reboot and hit spacebar to select.
Move down to "image split mode" highlight the second item "Into files whose size is...." hit spacebar to select.
Arrow to right and set size to something bigger than your finished image will be. Hit spacebar to select.
Press F5 and a screen will appear where you can describe you image ( something like Ubuntu 6.06 or whatever)
it's your choice. Hit enter.
Partition image will take a few minutes to examine your partition then an information dialog box will appear.
If no errors hit enter and sit back and wait. There will be a progress bar and counter.  Depending on amount of ram available
size of partition image and machine speed this could take some time. After 10 minutes the screen will blank (powersaver)
hit any key to restore progress box. Powersave doess't affect the imaging process just hides the progress. Be patient. 
When progress reaches 100% screen will revert to a blue screen.
At bottom will be a dialog about copying used data blocks, the program is still running leave alone. It can take some time.
When done your machine will reboot. Again be patient.
You now will have a "byte by byte" image of you Ubuntu install stored on your ext3 or Fat32 storage partition. You can of
course store other data there just don't disturb you image file.

To restore image pop in your SystemRescueCd an allow it to boot. 
After booting

Type   [mkdir /backup] hit enter. Assuming the partition the image is stored on is the same as the example earlier (hda3 and 
is ext3 file system)

Type   [mount -t ext3 /dev/hda3 /backup] hit enter. 
If no errors

Type   [partimage] hit enter.

Again you will be at the first partimage screen. Scroll down to highlite the Ubuntu partition you want to restore (in this
example hda2) and hit tab.

In space” * Image to create/use” type in your image file name. I our example it was /backup/hda2partition.000 (don't omit
the .000 at the end) Those are zero's and I know they weren't included in the original name, but that is what partimage
named the file it stored. Tab or arrow to "action to be done" and highlite "restore partition from image file". Hit F5 key.
If you entered info above correctly dialog box will appear asking if the description of image is correct. Hit enter 
A secon screen will appear leave the top two choices blank and highlite reboot. Hit spacebar to select. Hit F5 to continue.
A confirmation screen will appear with partition info and asking for you to confirm. Hit enter.
Another dialog box will appear asking if you are really sure you want to overwrite. choose yes and hit enter.
Sit back and wait when progress bar reaches 100% computer will reboot. Remove the CD before the 
BIOS splash screen to keep from booting disk again.
If everything went well you will have restored to an earlier, not broken Ubuntu.

Hope these instructions are clear enough.

---

### Post by VirtuAlex on 2006-07-31
> **Frank Golden said:**
> This is my first attempt at a How To
Why didn't you post it in [HOWTOs forum]("http://ubuntuforums.org/forumdisplay.php?f=100")?

---

### Post by Frank Golden on 2006-07-31
> **VirtuAlex said:**
> Why didn't you post it in [HOWTOs forum]("http://ubuntuforums.org/forumdisplay.php?f=100")?Your right how do I get the moderators to move it?

---

### Post by aysiu on 2006-07-31
If you have a Ubuntu Desktop CD and an internet connection, you can also follow this tutorial:
[http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html)

---

### Post by Frank Golden on 2006-07-31
> **aysiu said:**
> If you have a Ubuntu Desktop CD and an internet connection, you can also follow this tutorial:
[http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html)Hi aysiu,
I used some of the info in your tutorial as well as the 
info at the SystemRescueCD and some trial and error to
figure out how to use the version on the SystemRescueCD.
I even installed SystemRescueCD on a 1GB Cruzer Titanium and boot to it instead of the CD. This neat program has saved
my hide on more than one occasion.

---

### Post by shanepardue on 2006-07-31
i have multiple files after i finished the image process. when i go to restore, i'll simply provide each image individually and by the end of that process, my partition will be as it was when i originally imaged it?

i know this may be worded weird, but it's the best i could do.

---

### Post by Frank Golden on 2006-07-31
> **shanepardue said:**
> i have multiple files after i finished the image process. when i go to restore, i'll simply provide each image individually and by the end of that process, my partition will be as it was when i originally imaged it?

i know this may be worded weird, but it's the best i could do.
I'm not sure shane I try to keep my image 1 file.

---

### Post by shanepardue on 2006-07-31
> **Frank Golden said:**
> I'm not sure shane I try to keep my image 1 file.

and you keep that file on a network? i was hoping to have a hard copy of my image.

---

### Post by Frank Golden on 2006-07-31
> **shanepardue said:**
> and you keep that file on a network? i was hoping to have a hard copy of my image.
No shanepardue I have one on an external USB HDD. However, I just got done playing around
with creating the image on the fat32 shared partition I maintain on my
dual boot HDD. I used the technique in my how to. You must make sure
the resulting image file is less than 4GB, Fat32 won't support files
bigger than 4GB. When I first tried it the file size reported by partimage
while it was copying was 4.01GB. Everything went fine until the counter
got to 4.0GB then error message-process killed. So I booted into 
Ubuntu and moved some of the data from my /home folder to my shared
Fat32 folder and tried it again. This time partimage reported 3.78GB
file size and image copy was a success. Copy time was about 7 min.
considerably faster than to an external drive. Restore was about 4 min.
and was flawless. The more I play with this great program the more I learn.

---

### Post by shanepardue on 2006-07-31
yeah, my images total to 28gb. i had to image a much bigger partition.

i think i may just store it on the network..a hard copy may be too much.

---

### Post by wieman01 on 2006-09-22
Buddy, terrific howto. Was pointing me in the right direction. Downloaded the Rescue CD and rocked. My wireless card was not recognized by the Ubuntu Live CD so I did have an problem. Your howto helped a lot.

---

### Post by wgaprotest on 2006-09-27
> **Frank Golden said:**
> No shanepardue I have one on an external USB HDD. However, I just got done playing around
with creating the image on the fat32 shared partition I maintain on my
dual boot HDD. I used the technique in my how to. You must make sure
the resulting image file is less than 4GB, Fat32 won't support files
bigger than 4GB. 

This is incorrect. A fat16 has a max size limit of 4G; fat32's size limit is 32G.

---

### Post by wieman01 on 2006-09-27
> **wgaprotest said:**
> This is incorrect. A fat16 has a max size limit of 4G; fat32's size limit is 32G.
No, FAT32 is indeed 4GB. I know because I got tripped up by it last week when I did my first backup following this howto. FAT32 could not handle the 5GB backup file, so I had to split it up.

---

### Post by eyyuplu on 2006-10-15
hda1                                 ntfs         19,53 GiB     &#9474;
                     &#9474;   hda2                                 -extended-               &#9618; &#9474;
                     &#9474;   hda5                                 fat32        17,73 GiB   &#9618; &#9474;
                     &#9474;   hdb1                                 ext3fs       8,10 GiB    &#9618; &#9474;
                     &#9474;   hdb2                                 -extended-               &#9618; &#9474;
                     &#9474;   hdb5                                 swap (v1)    392,18 MiB  &#9618; 

------
&#305; want backup to hda5(fat32) from hdb1(ubuntu hdd  8.1gb).&#305; do 
sudo mkdir /mnt/backups
sudo mount /dev/hda5 /mnt/backups

--error---

&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; save partition to image file &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Partition to save:.........../dev/hdb1                                       &#9474;
&#9474; Size of the Partition:.......8,10 GiB = 8702313984 bytes                     &#9474;
&#9474; Image file to create........./mnt/backups/linuxyedek.000                     &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474; Detected file sy&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Warning &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;                 &#9474;
&#9474; Compression leve&#9474;                                          &#9474;                 &#9474;
&#9474;                 &#9474; e2fsck found errors on the file system.  &#9474;                 &#9474;
&#9474;                 &#9474;                                          &#9474;                 &#9474;
&#9474;                 &#9474;    &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;          &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;      &#9474;                 &#9474;
&#9474;                 &#9474;    &#9474; Continue &#9474;          &#9474; Cancel &#9474;      &#9474;                 &#9474;
&#9474;                 &#9474;    &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;          &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;      &#9474;                 &#9474;
&#9474;                 &#9474;                                          &#9474;                 &#9474;
&#9474;                 &#9474;                                          &#9474;                 &#9474;
&#9474;                 &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;                 &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                                                              &#9474;
&#9474;                                    0%                                  sh: lin e 1: 10952 Parçalama ar&#305;zas&#305;    /sbin/e2fsck -nf -C 0 /dev/hdb1 >/dev/null 2>/de v/null&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;

checking the file system with fsck [* to cancel, CtrlS to pause, CtrlQ to resume

what can &#305; do?

---

### Post by wieman01 on 2006-10-16
[QUOTE=eyyuplu;1621036]I want backup to hda5(fat32) from hdb1(ubuntu hdd  8.1gb)./QUOTE]
HDA5 is a FAT32 file system. Honestly that could be an issue... I would not do that. Try another file system such as ext2 or ext3. FAT32 is no good idea.

---

### Post by Charles Hand on 2006-10-21
I backed up an internal drive to an external usb fat32 drive. I split the image into 2G sections, so I had 22 pieces.

I went to restore the image to the internal drive. After about fifteen minutes an error message appeared, something about "structure cannot be verified". Any attempt to run partimage again resulted in segfault.

I looked on the external drive, and five of the parts of the image had vanished. Seven new files had appeared, three with identical filenames 2G each, and four with identical filenames of zero bytes each.

That's bad. A backup system should not eat its backup media.

---

### Post by wieman01 on 2006-10-21
> **Charles Hand said:**
> I backed up an internal drive to an external usb fat32 drive. I split the image into 2G sections, so I had 22 pieces.

I went to restore the image to the internal drive. After about fifteen minutes an error message appeared, something about "structure cannot be verified". Any attempt to run partimage again resulted in segfault.

I looked on the external drive, and five of the parts of the image had vanished. Seven new files had appeared, three with identical filenames 2G each, and four with identical filenames of zero bytes each.

That's bad. A backup system should not eat its backup media.
Have you used the "compress" function? Used it once but it messed up my system. So I have learned my lesson & always use uncompressed archives. No problem

---

### Post by eyyuplu on 2006-10-21
> **wieman01 said:**
> [QUOTE=eyyuplu;1621036]I want backup to hda5(fat32) from hdb1(ubuntu hdd  8.1gb)./QUOTE]
HDA5 is a FAT32 file system. Honestly that could be an issue... I would not do that. Try another file system such as ext2 or ext3. FAT32 is no good idea.
&#305; want backup to fat32.because ext3 system full.can &#305; backup fat32?

---

### Post by wieman01 on 2006-10-21
> **eyyuplu said:**
> [QUOTE=wieman01;1622912]
&#305; want backup to fat32.because ext3 system full.can &#305; backup fat32?
I've just done it. Yes, you can.

---

### Post by wilberfan on 2006-10-28
A big tip of the penguin hat to you for this HOWTO!!  There's no way I would have figured out partimage without this!!

I even got Dapper backed up before installing Edgy this morning--although by the looks of things, I won't need those images!!  (Way to go, Edgy!)  :D

---

### Post by iammeagain on 2007-01-17
Just double checking, will fat32 not let you save over 4GB ? Cuz i just tried backing up a couple times, but it stopped at 4GB. I guess that means i need to partition my external hard drive to have ext3 right? Is there anything tricky about having it connected USB? or will it work pretty much the same as an internal drive? Thanx

---

### Post by wieman01 on 2007-01-17
> **iammeagain said:**
> Just double checking, will fat32 not let you save over 4GB ? Cuz i just tried backing up a couple times, but it stopped at 4GB. I guess that means i need to partition my external hard drive to have ext3 right? Is there anything tricky about having it connected USB? or will it work pretty much the same as an internal drive? Thanx
FAT32 won't let you save files larger than 4 GB. But Partimage let's you split backup files... So that should not be a problem.

---

### Post by iammeagain on 2007-01-18
> **wieman01 said:**
> FAT32 won't let you save files larger than 4 GB. But Partimage let's you split backup files... So that should not be a problem.

Whenever it hits 4 GB it just stops and returns to the command line, or freaks out and goes to the command line. I did attempt to set the files to over 4 GB so that might have caused it.:-k  Not sure, but Thanx

---

### Post by wieman01 on 2007-01-19
> **iammeagain said:**
> Whenever it hits 4 GB it just stops and returns to the command line, or freaks out and goes to the command line. I did attempt to set the files to over 4 GB so that might have caused it.:-k  Not sure, but Thanx
Set it below 3 GB and try again.

---

### Post by denverreynolds on 2007-02-22
I am trying to backup to a USB external hard drive. here are my steps:

mkdir /bkkup
mount -t usbfs /dev/sdb /bkup
partimage

then I select my linux HD
then my file name is /bkup/laptoppartition

when I try to hit ok at the very end it tell me "can not create tmp directory in /bkup. No write permissions."

Could someone help me please?

Ty!

---

### Post by iammeagain on 2007-03-10
> **wieman01 said:**
> Set it below 3 GB and try again.


i just used default settings the last time i tried and everything when smoothly, although, it said it was set at 2 GB and then seperated them at 4 GB. Don't know why? but i'm happy it worked.

---

### Post by phidia on 2007-04-30
I have my install on resierfs. Does this guide only work with ext2/3?

---

### Post by wieman01 on 2007-05-01
> **phidia said:**
> I have my install on resierfs. Does this guide only work with ext2/3?
I think it should. You could create a backup file first, then test it later on using Partimage. There is a "test option" which I frequently use for my backup files.

---

### Post by ledrek on 2007-08-20
Hi Frank, awasome post...being a real newbee to linux this was realy easy to follow.  Did a backup and restore of my Ubuntu with no problems.
THANKS.........:guitar:

---

### Post by kle on 2008-05-25
Well, I am responding to something you wrote in 2006 and now it is 2008. But THANK YOU!

---

### Post by karmila on 2010-10-26
I know it's 2 years from the last post but I booted systemrescuecd and this tutorial still relevant.

Btw, before I do the real action I have one question.

I want to backup image of my /dev/sda5 partition to /dev/sda3 partition (sda3 is my /home partition). Is it save? or partimage will completely delete my sda3 partition for the new image?

Any help is really much appreciated... :)

---

### Post by ensenadaubuntulover on 2011-02-24
this should be as an instruction...

IN THE RESCUE CD DESKTOP

---

### Post by pianomans on 2011-05-27
Frank, Thanks for this "how to". It help me a lot! A few tips for those who boot from USB stick like me.
If you rescue from USB (your backup file is on USB), there is no need to mount and to create new folder. You point to [/livemnt/boot] and name of file.

---

