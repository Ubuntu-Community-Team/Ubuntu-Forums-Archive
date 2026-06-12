---
title: "LUKS encrypted volume suddenly read-only"
date: 2023-10-19
forum: New to Ubuntu
---

### Post by evaristegalois on 2023-10-19
I have a LUKS encrypted USB volume that I've extensively used for a long time. There have never been any problems. I have most of the data backed up, but not all of it.

I usually just plug it in, Ubuntu asks for the passphrase, I enter it, and the volume is automatically mounted.

This morning, I received an error message: 

Unable to access "62 GB Volume"
Error mounting system-managed device /dev/dm-0: cannot mount /dev/
mapper/luks-a21b284c-4a69-4dd5-bccb-9e214c597423
read-only

I have quizzed the Bing chatbot extensively about this and tried unmounting and remounting it, but it always gets hung up on the fact that /dev/mapper/luks... is read-only. Bing suggested it may be a hardware issue or a filesystem error. 

On a non-encrypted filesystem, I can run fsck, but even that won't work here. If I run

sudo fsck /dev/mapper/luks-a21b284c-4a69-4dd5-bccb-9e214c597423

I get:

fsck from util-linux 2.37.2
e2fsck 1.46.5 (30-Dec-2021)
fsck.ext4: Operation not permitted while trying to open /dev/mapper/luks-a21b284c-4a69-4dd5-bccb-9e214c597423
You must have r/w access to the filesystem or be root

Even though I am obviously running this command as root. 

I am at my wits' end. I know the passphrase for the encrypted volume. How can I get access to the data?

---

### Post by TheFu on 2023-10-19
Bad news.  If you use encryption, normal file system tools won't help with data recovery.  

You need to run an **fsck** against the unlocked devices, file system. I don't know if that's  /dev/mapper/luks-a21b284c-4a69-4dd5-bccb-9e214c597423 or not. I've never used that type of device  name with my LUKS storage. Mine have always had LVM for volume management inside the LUKS container. The device would be the same as whatever gets mounted.
```
 sdf                               8:80   0 119.2G  0 disk  
 &#9500;&#9472;sdf1                            8:81   0   243M  0 part  
 &#9500;&#9472;sdf2                            8:82   0     1K  0 part  
 &#9492;&#9472;sdf5                            8:85   0   119G  0 part  
   &#9492;&#9472;c720 (dm-4)                 252:4    0   119G  0 crypt 
     &#9500;&#9472;c720--vg-root (dm-5)      252:5    0  51.9G  0 lvm   /mnt/root
     &#9500;&#9472;c720--vg-lv--swap (dm-6)  252:6    0   4.1G  0 lvm   
     &#9492;&#9472;c720--vg-lv--Stuff (dm-7) 252:7    0    50G  0 lvm   /mnt/Stuff
```
is what I had.  So the mounts would be 
```
sudo mount **/dev/mapper/c720--vg-lv--Stuff** /mnt/Stuff
sudo mount **/dev/mapper/c720--vg-root **/mnt/root
```

The bold parts are what need to be used for the fsck.

If you can't open the LUKS container, your data is gone. The backups are what you have left.  

**Using encryption means having excellent backups isn't just a suggestion. It is mandatory.**

---

### Post by pbear42 on 2023-10-19
Not an expert, but that sounds to me like a corrupted header.  Do you perhaps have a backup of *that*.

Alternatively, you could try opening manually, to see whether a more useful error message is reported.  Command in the form [COLOR=#ff0000]sudo cryptsetup -v luksOpen /dev/sdb1 LUKS-sdb1[/COLOR] (replacing sdb1 with the correct partition identifier, of course).  If this works, by the way, you will end up with the decrypted file system at /dev/mapper/LUKS-sdb1 (or whatever), which is much easier to work with the luks-[uuid].

---

### Post by evaristegalois on 2023-10-20
Yes, I can run:

> sudo cryptsetup luksOpen /dev/sdf1 luks-a21b284c-4a69-4dd5-bccb-9e214c597423

and then, when I run

> sudo cryptsetup status luks-a21b284c-4a69-4dd5-bccb-9e214c597423

I get 

> /dev/mapper/luks-a21b284c-4a69-4dd5-bccb-9e214c597423 is active.
  type:    LUKS1
  cipher:  aes-cbc-essiv:sha256
  keysize: 256 bits
  key location: dm-crypt
  device:  /dev/sdf1
  sector size:  512
  offset:  4096 sectors
  size:    120221632 sectors
  mode:    readonly


(Note how it says mode: readonly ??) However, when I try to mount using 

> sudo mount /dev/mapper/luks-a21b284c-4a69-4dd5-bccb-9e214c597423 /mnt/luks-a21b284c-4a69-4dd5-bccb-9e214c597423 -t ext4

I get the unfortunate

> mount: /mnt/luks-a21b284c-4a69-4dd5-bccb-9e214c597423: cannot mount /dev/mapper/luks-a21b284c-4a69-4dd5-bccb-9e214c597423 read-only.

and I think as long as I get that there is no way to access anything. No, I don't have the header backed up.

Is there really no way to get into an encrypted LUKS partition when I know the passphrase but it's just (I guess) slightly corrupted somewhere? Thank you for your help so far. 

By the way, when I used Disks to check this volume, it gave me the following error:

> Error while checking filesystem
Error checking filesystem on /dev/dm-0: Process reported exit code 12: e2fsck
1.46.5 (30-Dec-2021)
e2fsck: aborted
(udisks-error-quark, 0)

and when I run 

> sudo e2fsck -fv /dev/dm-0

in a terminal, I get (despite running it as a superuser),

> e2fsck 1.46.5 (30-Dec-2021)
e2fsck: Operation not permitted while trying to open /dev/dm-0
You must have r/w access to the filesystem or be root


---

### Post by TheFu on 2023-10-20
Try 
```
sudo fsck /dev/mapper/luks-a21b284c-4a69-4dd5-bccb-9e214c597423
```
first. This assumes the file system is one from Linux and there is an fsck program for the file system installed.

Access to encrypted anything can be completely destroyed due to corruption at any level.  **Backups are not optional.**

I avoid using other fsck variants, since the fsck front-end handles things that we should be doing.  Error 12 says the superblock isn't found or is corrupted.  That can be a cable issue, controller issue or hardware problem.

---

### Post by MAFoElffen on 2023-10-20
+1 -- That is what i would have recommended. But first...

This will ID any volume with a LUKS container:
```

lsblk -e7 -o name,label,size,fstype | grep 'crypto_LUKS'

```
Lets say that what came up in the output was /dev/sdb1

Then if you did
```

sudo cryptsetup luksDump /dev/sdb1 | wc -l

```
That will read the header and do a line count on the output. Ensure that command can read the header of that LUKS container, and that the line count is over 44. That count will increase by 15, for each key slot... Then do
```

sudo cryptsetup luksDump /dev/sda3

```
To ensure there are no extraneous characters in the header... Look at the Version and Key Slot where it says luksX to make out it it is LUKS1 or LUKS2... Which begs the question of how long ago you created this...

If not that long ago, then open it via
```

sudo cryptsetup -v open /dev/sdb1 luks-01

```
If that succeeds, then try to mount it as
```

# Syntax: sudo cryptsetup -v open <drive_name> <mapped_device>
sudo mount /dev/mapper/luks01 /mnt

```
There is a --repair option for 'cryptsetup which will make an attempt at repairig common problems when LUKS headers get corrupted, but make sure you get a bit-by-bit copy of the original media, or at the least a backup of the LUKS header.
```

sudo cryptsetup luksHeaderBackup /dev/DEVICE --header-backup-file /path/to/backupfile

```
Then cross your fingers and do
```

sudo cryptsetup repair /dev/DEVICE

```
If LUKS2, it has a secondary copy of the header in the container...

If you are real a masochist... Open a hex editor on the container and search for these two strings (individually):
```

#define MAGIC_1ST "LUKS\xba\xbe"
#define MAGIC_2ND "SKUL\xba\xbe"

```
That is the start of each header, and they are each 2M long. You can use dd & set the offset and backup the individual headers that way also.

I have quite a few scripts I wrote to help me parse through LUKS containers, their headers, and do different things with them. For example to match passphrases, key files, recovery keys, etc, with their respective key slot numbers, so I know what is where when I go to change them...

---

### Post by evaristegalois on 2023-10-20
your command 

```
sudo cryptsetup luksDump /dev/sdf1 | wc -l
```

only gives me 27. I am not sure about your 

```
sudo cryptsetup luksDump /dev/sda3
```

I don't understand what it does, and I already have an unrelated sda3 mounted.

The code

```
sudo cryptsetup -v open /dev/sdb1 luks-01
```

gives me

```
Cannot use device /dev/sdf1 which is in use (already mapped or mounted).
Command failed with code -5 (device already exists or device is busy).

```

Your 

```
sudo cryptsetup luksHeaderBackup /dev/mapper/luks-a21b284c-4a69-4dd5-bccb-9e214c597423 --header-backup-file ./backupfile
```

produces no output at all. No error message, no backupfile.

```
sudo cryptsetup --repair /dev/mapper/luks-a21b284c-4a69-4dd5-bccb-9e214c597423
```

says "--repair: unknown option"

I asked the Bing chatbot about opening a luks partition using a hex editor and it said that I'd first have to unlock the partition, which is precisely what I cannot do.

Thank you for your help,  MAFoElffen!

---

### Post by evaristegalois on 2023-10-20
In reply to TheFu: your command gives the above mentioned

```
fsck from util-linux 2.37.2
e2fsck 1.46.5 (30-Dec-2021)
fsck.ext4: Operation not permitted while trying to open /dev/mapper/luks-a21b284c-4a69-4dd5-bccb-9e214c597423
You must have r/w access to the filesystem or be root

```

even though I am running it sudo

---

### Post by MAFoElffen on 2023-10-20
Substitute your drive name for the LUKS container. My code, where i used /dev/sdb1, was an example, that followed "Lets say the output said /dev/sdba..." LOL

So 
```

sudo cryptsetup luksDump /dev/sda3
# Would be 
sudo cryptsetup luksDump /dev/sdf1

```
From what you are saying now...

It says it is busy? Is it mounted somewhere?
```

sudo mount

```

---

### Post by pbear42 on 2023-10-20
> **MAFoElffen said:**
> @pbear42 -- I have tried to warn you about the Forum policy of posting commands and raw output within CODE tags... I can't protect you anymore. I'll leave you to the Moderators to tell you... In an earlier thread you responded earlier today, I took the time to tell you how to edit your posts to keep you out of trouble. I see my time was wasted, on that. Content good, format violates Forum policies.
Pretty sure you're thinking of someone else.  I don't have many [recent posts]("https://ubuntuforums.org/search.php?searchid=29853522").  Anyhoo, if ya'll are this uptight, I'll save everyone the trouble and move along.  No wonder this Forum has so few helpers.

---

### Post by MAFoElffen on 2023-10-20
> **pbear42 said:**
> Pretty sure you're thinking of someone else.  I don't have many [recent posts]("https://ubuntuforums.org/search.php?searchid=29853522").  Anyhoo, if ya'll are this uptight, I'll save everyone the trouble and move along.  No wonder this Forum has so few helpers.
Sorry. I was mistaken. It was about 4 other people in the last day... My honest apologies. Just frustrated from reminding people to use codes tags, but only said to help people stay out of trouble, and to help protect the Forum's software. It sometimes hiccups on "code" outside of tags. 

BTW--> Good catch seeing something I missed someone saying in the separate home thread. That was a very important detail. We always need good helpers. I have seen some very good perspectives and ideas from your posts.

EDIT -- Can't send you a PM to apologize. So did it here. You were right. I was wrong. Edited previous post.

---

### Post by MAFoElffen on 2023-10-20
Attached is a screenshot the start of a secondary LUKS2 header in a disk Hex Editor. It's not something for someone that is not used to that sort of thing... I would try a lot of other things before that...

Such as trying to read the header (luksDump), backing up the 1st header. 
```

sudo dd bs=2M count=1 if=$HOME/backup_luks_header.bin of=/dev/DEVICE

```
The attached screenshot is the secondary header found by string "#define MAGIC_2ND"... Backup starting there for the next 2M... 

Which is this LUKS2 Container:
```

ubuntu@ubuntu:~/Downloads$ sudo cryptsetup luksDump /dev/sda3
LUKS header information
Version:           2
Epoch:             6
Metadata area:     2097152 [bytes]
Keyslots area:     2621440 [bytes]
UUID:              499a7b91-f4c0-4759-9a58-336516e504dc
Label:             ubuntu-save-enc
Subsystem:         (no subsystem)
Flags:           (no flags)

Data segments:
  0: crypt
    offset: 7340032 [bytes]
    length: (whole device)
    cipher: aes-xts-plain64
    sector: 512 [bytes]

Keyslots:
  0: luks2
    Key:        512 bits
    Priority:   preferred
    Cipher:     aes-xts-plain64
    Cipher key: 512 bits
    PBKDF:      argon2i
    Time cost:  4
    Memory:     32
    Threads:    2
    Salt:       cc f0 9a 04 32 2d 40 4d bc af 46 f9 ed c7 95 82 
                4a 59 36 14 56 11 8a 7d d7 31 ea 40 03 e3 bd a9 
    AF stripes: 4000
    AF hash:    sha256
    Area offset:4194304 [bytes]
    Area length:258048 [bytes]
    Digest ID:  0
  1: luks2
    Key:        512 bits
    Priority:   normal
    Cipher:     aes-xts-plain64
    Cipher key: 512 bits
    PBKDF:      argon2i
    Time cost:  4
    Memory:     1048576
    Threads:    2
    Salt:       c1 23 88 9c 21 a9 fb b2 1b aa fe dd 2b b8 38 53 
                7d 1d ac d9 40 04 c9 3e 79 f9 6b 76 53 ca 69 2c 
    AF stripes: 4000
    AF hash:    sha256
    Area offset:4452352 [bytes]
    Area length:258048 [bytes]
    Digest ID:  0
Tokens:
Digests:
  0: pbkdf2
    Hash:       sha256
    Iterations: 1000
    Salt:       70 5e 45 f4 4b 38 0e 6f 54 67 20 01 9b c8 93 e1 
                c3 85 48 10 e7 9f dc cd 6e b1 a1 b0 ab 77 03 52 
    Digest:     6e 5e 8e cd bf 61 5c a7 08 26 d2 fa 8f f9 a1 59 
                21 5c 66 a8 d0 1b 94 2e b7 25 5d 91 02 4d f8 b9 

```
Look back at my previous post... the command repair is without the --

---

### Post by evaristegalois on 2023-10-20
The command 

```
sudo cryptsetup luksDump /dev/sdb1
```

gives 

```
LUKS header information for /dev/sdb1

Version:       	1
Cipher name:   	aes
Cipher mode:   	cbc-essiv:sha256
Hash spec:     	sha256
Payload offset:	4096
MK bits:       	256
MK digest:     	a8 98 03 5d c0 fc 15 d4 4b 01 e2 55 ee 9c af 3b 9d 6a ef 00 
MK salt:       	15 91 6f d7 e8 55 c9 6c 63 3e 05 e9 bd b1 9e 46 
               	ba f8 14 9d de 93 be ca 46 8a d5 88 a6 82 ac 01 
MK iterations: 	118296
UUID:          	a21b284c-4a69-4dd5-bccb-9e214c597423

Key Slot 0: ENABLED
	Iterations:         	1892736
	Salt:               	df 1b c9 a8 a7 4a 4a b0 6f a3 67 a2 37 f9 5e 21 
	                      	25 66 b9 80 e9 52 c0 a5 4a 44 9a 71 ea e9 46 7e 
	Key material offset:	8
	AF stripes:            	4000
Key Slot 1: DISABLED
Key Slot 2: DISABLED
Key Slot 3: DISABLED
Key Slot 4: DISABLED
Key Slot 5: DISABLED
Key Slot 6: DISABLED
Key Slot 7: DISABLED

```

so it's version 1 in reply to MAFoElffen's 

> To ensure there are no extraneous characters in the header... Look at the Version and Key Slot where it says luksX to make out it it is LUKS1 or LUKS2... Which begs the question of how long ago you created this...

The command 

```
sudo cryptsetup -v open /dev/sdb1 my_device
```

gives

```
Cannot use device /dev/sdb1 which is in use (already mapped or mounted).
Command failed with code -5 (device already exists or device is busy).

```

before I unmount it in Nautilus, and

```
Device /dev/sdb1 does not exist or access denied.
Command failed with code -4 (wrong device or file specified).
```

after I unmount it in Nautilus.

The command

```
mount | grep sdb1
```

gives me nothing in either scenario.

---

### Post by evaristegalois on 2023-10-20
Here is some output from dmesg:

```
[79269.934970] usb 2-1: new high-speed USB device number 10 using xhci_hcd
[79270.085553] usb 2-1: New USB device found, idVendor=0781, idProduct=5530, bcdDevice= 1.00
[79270.085568] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[79270.085574] usb 2-1: Product: Cruzer
[79270.085579] usb 2-1: Manufacturer: SanDisk
[79270.085583] usb 2-1: SerialNumber: 4C530001121215104253
[79270.088466] usb-storage 2-1:1.0: USB Mass Storage device detected
[79270.090030] scsi host3: usb-storage 2-1:1.0
[79271.112479] scsi 3:0:0:0: Direct-Access     SanDisk  Cruzer           1.00 PQ: 0 ANSI: 6
[79271.112941] sd 3:0:0:0: Attached scsi generic sg2 type 0
[79271.114054] sd 3:0:0:0: [sdc] 120225792 512-byte logical blocks: (61.6 GB/57.3 GiB)
[79271.117359] sd 3:0:0:0: [sdc] Write Protect is on
[79271.117367] sd 3:0:0:0: [sdc] Mode Sense: 43 00 80 00
[79271.118230] sd 3:0:0:0: [sdc] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[79271.129899]  sdc: sdc1
[79271.132100] sd 3:0:0:0: [sdc] Attached SCSI removable disk
[79273.783100] sd 3:0:0:0: [sdc] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_OK cmd_age=0s
[79273.783111] sd 3:0:0:0: [sdc] tag#0 Sense Key : Medium Error [current] 
[79273.783115] sd 3:0:0:0: [sdc] tag#0 Add. Sense: Unrecovered read error
[79273.783120] sd 3:0:0:0: [sdc] tag#0 CDB: Read(10) 28 00 00 00 11 50 00 00 f0 00
[79273.783123] blk_update_request: critical medium error, dev sdc, sector 4432 op 0x0:(READ) flags 0x80700 phys_seg 30 prio class 0

```

---

### Post by kurt18947 on 2023-10-20
I don't have a clue what most of the preceding posts are saying but one of the common failure modes of flash media is to become read only. Unencrypted, that may not be a problem, just copy the data to a new device. Encrypted? I have no idea.

---

### Post by MAFoElffen on 2023-10-20
From you:
```

sudo fsck /dev/mapper/luks-a21b284c-4a69-4dd5-bccb-9e214c597423

```
And later it said it was busy... which it would be if it shows up in /dev/mapper... We are somehow on different pages...

Lets back up to the start... What shows up in /dev/mapper? Post this within code tags
```

ls /dev/mapper
lsblk -e7 -o name,label,size,fstype,type,mountpoint,model

```

---

### Post by MAFoElffen on 2023-10-21
Still waiting...

The reason is that the header file looks good. The commands you used to open said they "were busy"... Not that it wasn't a LUKS volume, nor that it errored during de-encryption... And it is showing as being within /dev/mapper/ hints that the container was opened and mapped to /de/mapper.

And with the commands you used here and there, you kept using different disk names to try to access the same device.

So yes, trying to get a clear picture of what is there, and what is going on.

---

### Post by evaristegalois on 2023-10-22
I am using different disk names because I am doing this on different computers. I always use the disk name given to me by lsblk.

```
sudo fsck /dev/mapper/luks-a21b284c-4a69-4dd5-bccb-9e214c597423
```

gives

```
fsck from util-linux 2.39.1
e2fsck 1.47.0 (5-Feb-2023)
fsck.ext4: Operation not permitted while trying to open /dev/mapper/luks-a21b284c-4a69-4dd5-bccb-9e214c597423
You must have r/w access to the filesystem or be root

```

even though I am doing it as root. I think it is at this point established that the drive is compromised. When I created an image file of the 60GB partition, the Gnome Disk utility told me that 1.3MB were corrupted and needed to be replaced by zeroes.

```
ls /dev/mapper
```

gives

```
control  luks-a21b284c-4a69-4dd5-bccb-9e214c597423
```

as expected. 

```
lsblk -e7 -o name,label,size,fstype,type,mountpoint,model
```

gives

```
NAME                                          LABEL       SIZE FSTYPE      TYPE  MOUNTPOIN MODEL
sda                                                     931.5G             disk            WDC WD10EZEX-08WN4A0
&#9500;&#9472;sda1                                        SYSTEM      260M vfat        part  /boot/efi 
&#9500;&#9472;sda2                                                    128M             part            
&#9500;&#9472;sda3                                        Windows    47.4G ntfs        part            
&#9500;&#9472;sda4                                        WinRE_DRV  1000M ntfs        part            
&#9492;&#9472;sda5                                                  882.8G ext4        part  /         
sdb                                                      57.3G             disk            Cruzer
&#9492;&#9472;sdb1                                                   57.3G crypto_LUKS part            
  &#9492;&#9472;luks-a21b284c-4a69-4dd5-bccb-9e214c597423            57.3G ext4        crypt           
sr0    
```

All of that is fine. In the file manager, the drive shows up and it asks for the passphrase to decrypt it. But then it makes the read-only complaint quoted in the original post. 

Somehow I need to fsck the decrypted partition. I now have an image file, that's perhaps easier to work with. Would ddrescue help?

---

### Post by MAFoElffen on 2023-10-23
For a filesystem to toggle to read-only on it's own, it does that usually for one-of-two reasons-- Ether the conatiner it is in is full, or the filesystem is corrupted. If full, then make room. If corrupted then try to repair the filesystem...

For there to be a /dev/mapper/luks-a21b284c-4a69-4dd5-bccb-9e214c597423 derived from /dev/sdb1, then the LUKS container had to be opened for device /dev/sdb1 and mapped to device /dev/mapper...

Hmmm... If you then did 
```

sudo crytptosetup luksClose /dev/mapper/luks-a21b284c-4a69-4dd5-bccb-9e214c597423

```
If this command errors out saying it is busy, then that usually mans that the container is mount somewhere. Look for that and unmount it...

After if it closed, then repopen it with a new mapped name
```

sudo cryptsetup luksopen /dev/sdb1 luks-01
ls /dev/mapper/

```
If it opened, then try to fix it with the underlying utility for fsck, e2fsck
```

sudo e2fsck -pf /dev/sdb1

```

---

### Post by MAFoElffen on 2023-10-23
I've been thinking about this... I've been around before USB flash drives existed. (I know... Dang)

When they first came out, some of them had a slide switch to turn on write protect, which made them read-only. This was a carry-over from that on floppy disks. But was marketed as being an extra feature to protect against viruses... This would be very, very rare these days, but this isn't one of those old drives is it?

Just thought I'd ask...
And to check if a drives firmware has it locked do
```

sudo hdparm /dev/sdb | grep 'readonly'

```
Adjusting the device to the drive name.

That would check to see if it the drive itself is software locked in the firmware. That can be toggled.

---

### Post by evaristegalois on 2023-10-23
I appear to have solved the problem. I used the Disks utility to create an image file of the LUKS encrypted partition. It complained about some corrupted sectors but created the image file. Then I opened the image using

```
sudo cryptsetup luksOpen luks_usb.img luks_usb
```

then I ran

```
sudo fsck /dev/mapper/luks_usb
```

this did not work on the decrypted and corrupted luks partition, but it did work on the decrypted (and presumably corrupted) opened image file! Then

```
sudo mount /dev/mapper/luks_usb /mnt
```

and the world was a happier place :) My lost files were all there.

Thank you all for your help, especially MAFoElffen!

---

