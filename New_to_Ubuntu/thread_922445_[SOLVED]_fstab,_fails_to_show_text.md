---
title: "[SOLVED] fstab, fails to show text"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by ctoaun on 2008-09-17
Greetings

Alrighty then

**Goal:** Edit fstab to facilitate the automounting of /dev/sda14, fat32.

**Problem:** Fstab is invisible or blank.

**Steps used:**

1)  fdisk -l result normal

2)  sudo gedit /etc/fstab   **Result:** Blank text box appears

There is a "text editor" installed.

Could someone please point me in the right direction?

Merci

---

### Post by jken146 on 2008-09-17
Type ```
cat /etc/fstab
``` and see what comes out.

---

### Post by ctoaun on 2008-09-17
> **jken146 said:**
> Type ```
cat /etc/fstab
``` and see what comes out.

I took your advice. The result was WEIRD?!

With sudo fdisk -l, /dev/sda14 appears in an alphanumeric list as previously stated.

Using your "sudo cat /etc/fstab," /dev/sda14 does not appear. Interesting.

Perhaps you know why this is so since you suggested it, yes?

---

### Post by jken146 on 2008-09-17
Please post the outputs of ```
sudo fdisk -l
``` and ```
cat /etc/fstab
```

---

### Post by ctoaun on 2008-09-17
> **jken146 said:**
> Please post the outputs of ```
sudo fdisk -l
``` and ```
cat /etc/fstab
```

Sure, here it is in original format

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=e0d0555e-3ab2-4ee5-9540-070a9bdc94d2 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=839f4649-1947-4b4e-b892-93c314d04b58 /boot           ext3    relatime        0       2
# /dev/sda7
UUID=0af4c385-8963-41eb-9617-835daf444a26 /home           ext3    relatime        0       2
# /dev/sda12
UUID=7a83a3d8-af3a-487d-a332-8df67e132114 /opt            ext3    relatime        0       2
# /dev/sda11
UUID=84b2cb96-7085-4bd7-a531-516e4303287a /srv            ext3    relatime        0       2
# /dev/sda8
UUID=3afca555-6dff-48e0-804e-c6c3204edf2b /tmp            ext3    relatime        0       2
# /dev/sda9
UUID=3579e360-0d3a-4635-abbd-47a146cd358e /usr            ext3    relatime        0       2
# /dev/sda13
UUID=4979ca50-fb67-4263-9e72-7cdf960c9ce4 /usr/local      ext3    relatime        0       2
# /dev/sda10
UUID=99bce638-ba8e-4b12-b4d8-e53aa85d9db2 /var            ext3    relatime        0       2
# /dev/sda5
UUID=a84cfb84-f6c3-442e-b6cd-9f63c2d76250 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

See? Weird, sda14 is gone

---

### Post by alienexplorers on 2008-09-17
Try usinf pysdm (located in the repositories) to edit the fstab file.

---

### Post by rsambuca on 2008-09-17
Is this a usb drive or something?  And we are still waiting for you to post the output of ```
cat /etc/fstab
```

---

### Post by jken146 on 2008-09-17
What does ```
sudo fdisk -l
``` say?

---

### Post by rsambuca on 2008-09-17
> **jken146 said:**
> What does ```
sudo fdisk -l
``` say?

That's what I meant!

---

### Post by ctoaun on 2008-09-17
> **jken146 said:**
> What does ```
sudo fdisk -l
``` say?

Oops! I did not see that before. It looks normal to me

 Device Boot      Start         End      Blocks   Id  System
/dev/sda1               4        6713    53898075    7  HPFS/NTFS
/dev/sda2   *        6714        6739      208845   83  Linux
/dev/sda3            6740       14593    63087255    5  Extended
/dev/sda5            6740        7079     2731018+  82  Linux swap / Solaris
/dev/sda6            7080        7456     3028221   83  Linux
/dev/sda7            7457        9280    14651248+  83  Linux
/dev/sda8            9281        9791     4104576   83  Linux
/dev/sda9            9792       11189    11229403+  83  Linux
/dev/sda10          11190       11578     3124611   83  Linux
/dev/sda11          11579       11724     1172713+  83  Linux
/dev/sda12          11725       11991     2144646   83  Linux
/dev/sda13          11992       12526     4297356   83  Linux
/dev/sda14          13038       14593    12498538+   b  W95 FAT32

See? or did I miss something?
thanks

---

### Post by ctoaun on 2008-09-17
> **rsambuca said:**
> Is this a usb drive or something?  And we are still waiting for you to post the output of ```
cat /etc/fstab
```

Hola,

Nope. It's an internal partition disk one. External disk have never been a problem for me. Now attempting to create a customized boot disk with usb floppy reader, that is tortuous. What am I saying? Writing to a USB (Kubuntu) is an accomplishment not yet achieved by moi.

---

### Post by drs305 on 2008-09-17
Add this to your fstab for /dev/sda14 fat32. Make sure the **mountpoint** exists:

```

/dev/sda14 /media/**mountpoint** vfat users,uid=1000,umask=027,utf8 0 0

```

You can add a group if you want, after the "uid=1000". Depending on what you want: gid=1000 is your group.

If you need to make a mountpoint:
```

sudo mkdir /media/**mountpoint**

```

Then mount it and check:
```

sudo mount -a
mount

```

Added: An earlier post mentioned pysdm, a gui-based fstab editor. If you want to look at it, there is a link to a tutorial in my signature line.

---

### Post by ctoaun on 2008-09-17
> **drs305 said:**
> Add this to your fstab for /dev/sda14 fat32. Make sure the **mountpoint** exists:

```

/dev/sda14 /media/**mountpoint** vfat users,uid=1000,umask=027,utf8 0 0

```

You can add a group if you want, after the "uid=1000". Depending on what you want: gid=1000 is your group.

If you need to make a mountpoint:
```

sudo mkdir /media/**mountpoint**

```

Then mount it and check:
```

sudo mount -a
mount

```

Added: An earlier post mentioned pysdm, a gui-based fstab editor. If you want to look at it, there is a link to a tutorial in my signature line.

> **alienexplorers said:**
> Try usinf pysdm (located in the repositories) to edit the fstab file.

Alrighty then, so I have my work cut out for me. At sometime, over the next few days, I look forward to giving this a whirl and keeping all apprised of the results.
Until then, thank all for pointing me in the right direction.

---

### Post by drs305 on 2008-09-17
> **ctoaun said:**
> Alrighty then, so I have my work cut out for me. At sometime, over the next few days, I look forward to giving this a whirl and keeping all apprised of the results.
Until then, thank all for pointing me in the right direction.

Hey, this shouldn't take more than 5 minutes (if it works) ;-)

If it does, please mark the thread solved, if it doesn't - come on back!

---

### Post by ctoaun on 2008-09-18
Greetings, as promised here are the results. Unfortunately, the problem remains.



> **alienexplorers said:**
> Try usinf pysdm (located in the repositories) to edit the fstab file.

The program when executed shows grayed out unusable screens. Perhaps it was meant for an older version of Ubuntu? The instructions for backing up fstab worked. Unless you or someone else has something further to add, this is a "dead end." This what I [used]("http://ubuntuforums.org/showthread.php?t=872197")
Thanks anyway, though

> **drs305 said:**
> Hey, this shouldn't take more than 5 minutes (if it works) ;-)

If it does, please mark the thread solved, if it doesn't - come on back!

Not true. I am at the 1.6 hour mark with no progress made, so I am taking you up on your offer. :) :(

> **drs305 said:**
> Add this to your fstab for /dev/sda14 fat32. Make sure the **mountpoint** exists:

```

/dev/sda14 /media/**mountpoint** vfat users,uid=1000,umask=027,utf8 0 0

```

You can add a group if you want, after the "uid=1000". Depending on what you want: gid=1000 is your group.

If you need to make a mountpoint:
```

sudo mkdir /media/**mountpoint**

```

Then mount it and check:
```

sudo mount -a
mount

```

Added: An earlier post mentioned pysdm, a gui-based fstab editor. If you want to look at it, there is a link to a tutorial in my signature line.

This is similar to something I've used in the past. While I appreciate help, please understand that the advice posted above is like having steps 1, 4 & 11 of a 15-step process. Therefore, *I cannot use the information posted above in its current format.*

    I simply do not have a computer science degree, years of formal/informal training with linux systems. 

[COLOR="Red"]**Questions that I about the help posted above are as follows**:[/COLOR]

1) /dev/sda14 factors into this somewhere, true, so where doe it fit in 
    this equation?

2)  If memory serves me correctly, "mount point" is what I choose to name something, no, yes?

3) If memory serves me correctly, mount points should be made before the fstab modifications, true?

4) I tried random things to mount this drive. Here is a result:

sudo mkdir /dev/sda14/media/share
mkdir: cannot create directory `/dev/sda14/media/share': Not a directory

I tried the foregoing because nothing else worked.

Since my fstab has been posted on page one, I am hoping that you or someone could _***in sequential order***_ tell me what I should do to make use of the preceding info.
>
To thee who might be dubious, I've completed similar task, so I know that succeeding at this is well within my capability.
>
Merci

---

### Post by drs305 on 2008-09-19
> **ctoaun said:**
> 
Not true. I am at the 1.6 hour mark with no progress made, so I am taking you up on your offer. :) :(

I am sorry we are not communicating in a manner that is helpful. I will try again.
> 
This is similar to something I've used in the past. While I appreciate help, please understand that the advice posted above is like having steps 1, 4 & 11 of a 15-step process. 

I will try to go step by step.

> 
1) /dev/sda14 factors into this somewhere, true, so where doe it fit in 
    this equation?

/dev/sda14 is the **device** or **partition** you are trying to mount.
> 
If memory serves me correctly, "mount point" is what I choose to name something, no, yes?

Yes, mostly. The mount point is the name of the folder on which a device is placed. Linux thinks in terms of folders/files, not equipment. So for the rest of this, I will refer to a mount point named MOUNTPOINT. You decide what you really want to call it. In each command, subtitute the name you desire for MOUNTPOINT.

> 
3) If memory serves me correctly, mount points should be made before the fstab modifications, true?

Not necessarily. Although it may make sense to make the mountpoint first, it really doesn't matter until you *execute* the new fstab by remouting the devices. As long as the MOUNTPOINT exists when you try to mount the device, it doesn't matter what order you do things.

> 
4) I tried random things to mount this drive. Here is a result:
**sudo mkdir /dev/sda14/media/share**

This did not work because you combined two commands. I suggest you cut and paste the commands so there are no errors. In this case, it should have been: **sudo mkdir /media/share** You are making a directory (mkdir) placed in the folder media (/media/) named: share

Let's try again.

1. Make the mount point (change MOUNTPOINT to whatever you want, for instance, if you want to name it '*share*', it would be "sudo mkdir /media/share"). 
```
sudo mkdir /media/**MOUNTPOINT**
```
1a. If the mount point already exists, you will get an error message:
"mkdir: cannot create directory '/media/MOUNTPOINT': File exists.
If that happens, then you already have a folder by that name. Choose a new name for now and continue. We can sort this out later.
2. Change the ownership of the mountpoint to yourself. Change ***yourusername*** to your log on name. Do not forget the ":" after your name:
```

sudo chown -R ***yourusername:*** /media/MOUNTPOINT

```
3. Make a backup copy of fstab:
```

sudo cp /etc/fstab /etc/fstab.0919backup

```
4. Open fstab for editing. The example uses gedit. You can use nano or some other text editor if you prefer:
```

gksu gedit /etc/fstab

```
5. Go the bottom of the fstab file and add these two lines:
```

#Entry for /dev/sda14
/dev/sda14 /media/**MOUNTPOINT** vfat users,uid=1000,umask=027,utf8 0 0

```
6. Save and close the file.
7. Make sure /dev/sda14 is not mounted already:
```
sudo umount /dev/sda14
```
8. Mount /dev/sda14 using fstab:
```
sudo mount -a
```

That should be it.

---

### Post by ctoaun on 2008-09-19
> **drs305 said:**
> 
8. Mount /dev/sda14 using fstab:
```
sudo mount -a
```

That should be it.

Other than step 8, your response was yielded stellar results in optimal time. As someone who knows how a textbook should be written, with all due humility, I am impressed with your response. It is multiple cuts above, and I say that with respect and humility. Thanks! After 300 views, my post with one distro has yet to be questioned, much less challenged, by anyone, even though I requested that I be informed of any errors that I may have made. Your steps 1-7 are excellent, something that anyone can follow, a response after my own heart!! People like you will be the reason that windows users persevere with Linux.



The failure of step 8 may or may not have been my fault. However, should it be written as 8a, 8b, 8c or just 8a then 8b? I do not know, I only know that after awhile, I just give up and try random things.

Here is sample output:
Everything was fine until step 8.

~$ sudo mount /media/share

mount: can't find /media/share in /etc/fstab or /etc/mtab

bubba001@bubbascomputer:~$ gksu gedit /etc/fstab

bubba001@bubbascomputer:~$ 


I regret being a pain in the ****, however, I can only be human.

Awaiting your response or any response
>
Merci

---

### Post by rsambuca on 2008-09-19
His step 8 should be followed precisely as it is written.   Open a terminal window and at the prompt copy and paste that exact command and press your enter key.  'sudo' gives you administrative privileges, 'mount -a' is the command to mount all of the partitions that are detailed in the /etc/fstab file.

Edit:  After running the sudo mount -a command, it won't say anything (unless there is an error).

---

### Post by ctoaun on 2008-09-20
> **rsambuca said:**
> His step 8 should be followed precisely as it is written.   Open a terminal window and at the prompt copy and paste that exact command and press your enter key.  'sudo' gives you administrative privileges, 'mount -a' is the command to mount all of the partitions that are detailed in the /etc/fstab file.

Edit:  After running the sudo mount -a command, it won't say anything (unless there is an error).

Thanks for the spark of inspiration.
The problem was that YOU & drs305 both typed "MOUNTPOINT" on my fstab in step 5 as opposed to typing /media/share, which was what had been working all alone.

How dare the two of you conspire to use padawan powers to adversely affect my control of my computer!!!
>
>
>
Seriously though,
Thanks a million, everything mounts in all accounts.:) :))
>
Plus sérieusement,
Je tiens à dire à vous tous, 
a big 
[SIZE="4"]merci[/SIZE]

---

