---
title: "booting error: crystswap"
date: 2012-08-30
forum: New to Ubuntu
---

### Post by Satchel88 on 2012-08-30
I installed from a USB.  When I boot, I get an error that says "The disk drive for devmapper/crystswap1 is not read yet or not present."  If I skip mounting (which take me to a normal UBUNTU minus a few features/my wallpaper.   The funny thing is when I boot with the USB in, I don't get this error.  What should I do?

EDIT: never mind, having the USB in doesn't help, after all.

---

### Post by Satchel88 on 2012-08-30
Also, just for reference I did find this thread: [http://ubuntuforums.org/showthread.php?t=646340](http://ubuntuforums.org/showthread.php?t=646340) but it didn't make any sense to me, sorry.  :x

---

### Post by Bashing-om on 2012-08-30
Satchel88;
  Hi ! Welcome to the post.

See if this link is the solution:
[http://askubuntu.com/questions/56843/could-not-mount-dev-mapper-cryptswap1](http://askubuntu.com/questions/56843/could-not-mount-dev-mapper-cryptswap1)

Then advise us of status.

[INDENT]kind regards <==BDQ
[/INDENT]

---

### Post by Satchel88 on 2012-08-30
I looked and I have a folder called fstab.d.  In file viewer it's empty and in terminal all I can get it to say is "/etc/fstab.d/ is a directory" so I'm not sure where to go from here. 

Thanks for your help!

---

### Post by Satchel88 on 2012-08-30
hmm

So.  I found dev/mapper folder and in it I found a shortcut to "cryptswap1"  It won't let me open it, though,  and I can't find anywhere the actual file.   When I tried to copy it to fstab.d (clearly I have no idea what I'm doing but I thought it was worth a try) it won't let me put anything in that folder.  Probably for the best... 0_o

Anyway, that's where I am.

---

### Post by Bashing-om on 2012-08-30
/fstab.d does not register with me// lemme look/integrate and I will get back to to you.

[INDENT]BDQ
[/INDENT]
[INDENT][RIGHT]
[/RIGHT]
[/INDENT]

---

### Post by Satchel88 on 2012-08-30
thanks.  I don't know if it matters but when I do a listing of the /etc/ folder contents in terminal it lists /fstab and /fstab.d as folders...but it only lets me open ./fstab.d (which is listed as blue) and /fstab is in white.

---

### Post by Satchel88 on 2012-08-30
thanks.  I don't know if it matters but when I do a listing of the /etc/ folder contents in terminal it lists /fstab and /fstab.d as folders...but it only lets me open ./fstab.d (which is listed as blue) and /fstab is in white.

---

### Post by NikTh on 2012-08-30
Hi , 
you can give here the results of 

```
cat /etc/fstab
sudo blkid
``` 

Put the results between ```
 brackets . [noparse][code]The Results Here
```[/noparse]
Thanks

---

### Post by Bashing-om on 2012-08-30
Ok, I am somewhat prepared.

the "The disk drive for devmapper/crystswap1 is not read yet or not present."  refers to encrypted partitions. At this point in booting we are looking at the swap partition.
1. Did you encrypt any partitions when you installed:/commands are below to check for encrypted partitions/
2. We look at /etc/fstab to see what is booted. 
First highly recommended study material.
fstab tutorial:[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

now check to see if swap is encrypted:
```
sudo blkid | grep swap

```reminder: the use of sudo requires your password; and no echo will be returned to the screen.

on my unencrypted system out put is this:
sysop@main:~$ sudo blkid | grep swap 
[sudo] password for sysop: 
/dev/sda7: UUID="192a4783-56fa-4fd0-a62f-c45a14c08482" TYPE="swap"


check for encrypted partions: 
```
sudo dmsetup status 

```Next: look in /etc/fstab for an entry "similar" to this:
# swap was on /dev/sda5 during installation
#UUID=fe10641d-a928-479e-ab3a-b0706b97b601 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0

Now we verify partition/uuid:
```
ls -l /dev/disk/by-uuid/<the uuid of the swap partition>

```The <sda5> part at the end is the important part. Once you are sure the UUID matches the partition number, run
```
 sudo fdisk -l /dev/<sda>

```and make sure that /dev/<sda5> is a swap partition.
To verify UUID and filesystem type  run:
```
 sudo blkid /dev/<swap partition> -c /dev/null

```To try your new configuration immediately you have to reload /etc/fstab:
```
 sudo mount -a

```as per the above fstab.d is not involved. Look this advise over. Advise us if anything is unclear or you need additional assistance (as in reading your fstab) // I keep an open mind that all is in order in the above and the problem may indeed be some thing else//..[INDENT]regards <==BDQ
[/INDENT]

---

### Post by Satchel88 on 2012-08-30
For NikTh,

```
me@mypc:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=33589fb7-c168-42fa-81bf-0ee9fc49761a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
#UUID=93933714-e902-478e-9833-7805c9a43e0a none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
me@mypc:~$ sudo blkid
[sudo] password for me: 
/dev/sda1: UUID="33589fb7-c168-42fa-81bf-0ee9fc49761a" TYPE="ext4" 
/dev/mapper/cryptswap1: UUID="52f9f283-f7f8-425a-a95f-c35cda9db1a5" TYPE="swap" 
/dev/sdb1: LABEL="PENDRIVE" UUID="9E9E-0E40" TYPE="vfat" 
me@mypc:~$ 
```Is that what you're looking for/does that answer anything?

Bashing-om, I'm going to read through your instructions a couple times and get back to you with results and/or questions.

Thank you both very much for your help, I appreciate it!  :)

---

### Post by Satchel88 on 2012-08-30
```
sudo blkid | grep swap

```results in
```
/dev/mapper/cryptswap1: UUID="52f9f283-f7f8-425a-a95f-c35cda9db1a5" TYPE="swap"
```

So...that means my system is unencrypted like yours, right?   I don't think I have any partitions/encryptions .




```
sudo dmsetup status 

```results in
```
cryptswap1: 0 2074624 crypt
```


As for looking in /etc/fstab...I'm unable to see that folder in the GUI and in terminal I can't access it/am told it doesn't exist.  /etc/fstab.d is empty and seems to be read-only.
 



In regards to partitions when I installed Ubuntu (on my ASUS netbook) I did a complete install (as in, I didn't "try Ubuntu" or install it alongside my old OS) and deleted Windows and all my old files and everything so I don't *think* I partitioned anything off...

---

### Post by Satchel88 on 2012-08-30
Finally, that /fstab/ tutorial mentions that flashdrives can be included in the /fstab/, but as I mentioned the problem seems to occur with or without my flashdrive inserted.  Might be irrelevant.

---

### Post by Bashing-om on 2012-08-30
ok ... got a handle on it ... your fstab is  booting swap as encrypted (why I can not know).... what we are going to do is edit the /etc/default/grub file; we will fix the line that is trying to boot encrypted; when we know what partition we are dealing with.
1. verify that the grub file exist as in /etc/default/grub //Not etc/fstab. (or is this system file moved to another location in 12.04 ?) looks to me like it is moved
to /etc/fstab ?
2. Verify the uuid of the swap partition;
   ```
 sudo blkid

```3. Prepare yourself to make the adjustment in the grub file.
4. Remember we must update the grub file upon completion of the edit:
```
sudo update-grub
```5. reload fstab:
  ```
sudo mount -a
```
when you are ready and if you need the direction, we will edit the grub file.
[INDENT]BDQ
[/INDENT]

---

### Post by NikTh on 2012-08-30
> **Satchel88 said:**
> Is that what you're looking for/does that answer anything?


Hi , I asked for another result also . 

```
sudo blkid
``` . 

We will try to commented out the line 
```
/dev/mapper/cryptswap1: UUID="52f9f283-f7f8-425a-a95f-c35cda9db1a5" TYPE="swap" 
```and add a new line for swap in fstab. 

Thanks

---

### Post by Bashing-om on 2012-08-30
@NikTh ; I concur// I ask again for my edification if fstab has been moved from the default directory (as is in 10,04 and earlier) ? By the way I have a spare (suspect bad) drive I will install 12.04 onto as soon as I get a favorable oportunity.

@Satchel88; We'll verify the uuid and make the edit.

[INDENT][INDENT]regards <==BDQ
[/INDENT][/INDENT]

---

### Post by NikTh on 2012-08-30
@Bashing-om , no . Fstab is in the known place /etc/fstab . If you suspect but not sure for the disk, you can examine it with SMART tools. (if the disk supports smart data).

---

### Post by Bashing-om on 2012-08-30
@NikTh (off topic)..roger/too many windows open here and mind on too many things, thanks for keeping me straight. The drive checked good with smart tools (why I am going to ga and use it, huh)

BDQ

---

### Post by Satchel88 on 2012-09-04
Ok, sorry...been a busy week.

Anyway,

```
sudo blkid
```
results in
```
/dev/sda1: UUID="33589fb7-c168-42fa-81bf-0ee9fc49761a" TYPE="ext4" 
/dev/mapper/cryptswap1: UUID="7fdeb834-6356-443a-82fd-c233eb4ec1ec" TYPE="swap"
```


So the next step is...editing the grub file?  How do I do that?

---

### Post by Bashing-om on 2012-09-04
we are going to edit your /etc/fstab
here is the corrected line (the correct uuid has been inserted for you-double check me that I have not made a type-o).

UUID=5600e3b4-ca64-4836-a1cc-86d5b763346d none            swap    sw              0       0

first make a back-up copy of the existing file:
```
cp /etc/fstab /etc/fstab-orig
```now open a text editor (my choice is gedit)
```
gksudo gedit /etc/fstab
```type your pass word into the pop up window
gedit has the file loaded:
arrow down to the line to-be-ignored; place a pound sign at the beginning of the line.
Now with your cursor at the end of the line-to-be-ignored; do a return key (gets us a new blank line)
now to copy the above corrected line: with the mouse right click at the beginning of the line and right click, while holding the button down drag across the entire line, release mouse button (this in the ubuntu forums window while the text editor remains open);     In the text editor; place cursor at beginning of new blank line and right click again, menu pops up choose paste, the selected line is inserted.

at this time save the document from the task bar menu.
exit the text editor->back to command line.
  exit all and ..... 

reboot, and all should be good.[INDENT]regards <==BDQ
[/INDENT]

---

### Post by Satchel88 on 2012-09-04
Thanks.

So, it's letting me edit the fstab file!  Yayy...

Here's what is in the file:


```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=33589fb7-c168-42fa-81bf-0ee9fc49761a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
#UUID=93933714-e902-478e-9833-7805c9a43e0a none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
```

Edit:  So, I'm unsure of where to put the revised line you gave me as I don't see the phrase "to-be-ignored" in here.

---

### Post by Bashing-om on 2012-09-04
apologize in that i am unclear in my directions.

ok...not having seen your complete fstab did not notice but another line needs to be commented out( the # symbol at the beginning of the line).
comment out this line:
/dev/mapper/cryptswap1
such that it starts like this:
#/dev/mapper.....................................

make the new blank line after this line that was commented out (with #)
insert the corrected text line into this blank line.
save the file with the changes.
reboot and see  how it works!


alternate subject:"to-be-ignored"  That was but just my phraseology to denote that the use of the '#' symbol indicates to bash that this line beginning with '#' is to be ignored by the bash interpreter. Any line in a bash script file (which fstab is) beginning with # is to be ignored.
[INDENT]regards , <==BDQ

[/INDENT]

---

### Post by Satchel88 on 2012-09-04
I think that did it!!

Thanks very much...I appreciate your help/patience/willingness to re-explain when needed.

:)

cheers

---

### Post by Bashing-om on 2012-09-04
You are welcome.
Can you imagine how little now I would know if I had no assistance in my past ?
And, I firmly believe in Free Open Source systems ..I support it as I can.

[INDENT]Enjoy ubuntu !  <==BDQ
[/INDENT]

---

