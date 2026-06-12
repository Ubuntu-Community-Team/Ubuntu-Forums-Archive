---
title: "Really need help mounting Windows."
date: 2008-11-11
forum: New to Ubuntu
---

### Post by Dot Cong on 2008-11-11
So I've given up on Windows and I want to use Ubuntu now. I already have it installed and am in fact using it right now. The thing is, I have a LOT of stuff on my XP partition that I would rather not lose, but I can't seem to get Linux to mount the NTFS partition. I've Googled it and used some of the walkthroughs and tips but still can't get it. So far I've tried using Terminal, in which case I get a huge long thing telling me all about mounting. I spose this is because I'm doing something wrong. I've also edited the /etc/fstab with this [/dev/hda1 /media/windows ntfs nls=utf8,umask=0222 0 0] which has not helped me in the least. The latter actually got me a little further, but now when I try to mount the partition it says Cannot Mount Volume. You are not privileged to mount this volume. So, could someone PLEASE help, I would greatly appreciate it. Thanks!

---

### Post by taurus on 2008-11-11
Install ntfs-config and use it to mount your ntfs partition.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

---

### Post by dark_harmonics on 2008-11-11
> **Dot Cong said:**
> So I've given up on Windows and I want to use Ubuntu now. I already have it installed and am in fact using it right now. The thing is, I have a LOT of stuff on my XP partition that I would rather not lose, but I can't seem to get Linux to mount the NTFS partition. I've Googled it and used some of the walkthroughs and tips but still can't get it. So far I've tried using Terminal, in which case I get a huge long thing telling me all about mounting. I spose this is because I'm doing something wrong. I've also edited the /etc/fstab with this [/dev/hda1 /media/windows ntfs nls=utf8,umask=0222 0 0] which has not helped me in the least. The latter actually got me a little further, but now when I try to mount the partition it says Cannot Mount Volume. You are not privileged to mount this volume. So, could someone PLEASE help, I would greatly appreciate it. Thanks!

try this in your fstab:

/dev/hda1 /media/windows ntfs noperms 0 0

Then mount with:
sudo mount -a

---

### Post by Dot Cong on 2008-11-11
OK now I get this message:

Mounting /media/windows failed.

$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 /media/windows -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 /media/windows ntfs-3g force 0 0

What do I do now? If i type one of the options in I get the same long message. I can't access Windows in order to shut it down either. And I honestly don't know squat about Ubuntu and open source, I'm learning as I go.

---

### Post by dark_harmonics on 2008-11-11
FORCING THE MOUNT CAN CORRUPT YOUR WINDOWS PARTITION.

The best solution is to load the disk on a windows computer and shut the system down cleanly.

That being said, i have forced it out of lazyness many many many times without failure, BUT IT HAS HAPPENED TO ME ONCE.

If you want to force it try

```
sudo mount /dev/sda1 /media/windows -o force
```

I did the same thing as you, I just started experimenting with it and fell in love :) Now all my computers are linux!

---

### Post by Poyntz on 2008-11-11
Create a directory in mnt for windows
eg, 
```
sudo mkdir /mnt/windrive
```
- makes a directory called "windrive"

Now search to verify what the name of the partition is
```
ls /dev/*da1
```

It will return a result /dev/<partition>

Now mount the partition to the directory:
eg,
```
mount /dev/sda1 /mnt/windrive
```
- where your partition should replace **sda1** and your directory should replace **windrive**

---

### Post by Dot Cong on 2008-11-11
Hahah well I have yet to fall in love with it, but I will say it's quite a bit smoother and faster than Windows.

Ok when I try to force I get this:

fuse: mount failed: Device or resource busy

Now what? I can't get into the Windows to use it. The main reason I'm quiting Windows is because, yet again, I am force to activate XP and since I moved recently I have no idea where my CD Key is. And though I know there are less than legal alternative ways, let's just say they couldn't help me.

I will admit that using the Terminal is actually kind of fun though.

---

### Post by dark_harmonics on 2008-11-11
> **Poyntz said:**
> Create a directory in mnt for windows
eg, 
```
sudo mkdir /mnt/windrive
```
- makes a directory called "windrive"

Now search to verify what the name of the partition is
```
ls /dev/*da1
```

It will return a result /dev/<partition>

Now mount the partition to the directory:
eg,
```
mount /dev/sda1 /mnt/windrive
```
- where your partition should replace **sda1** and your directory should replace **windrive**

Very good points. If the mountpoint /media/windows didnt exist then you couldn't mount a partition to it. From his error message he must have an NTFS volume on /dev/sda1.

Just to make sure; could you give us the results of this:

```
 sudo fdisk -l 
```

---

### Post by Dot Cong on 2008-11-11
Where do you live? Because I'm getting on a plane and coming to kiss you. I now have access to my Windows Partition. Thank you so much everyone for all of the help. I will DEFFINATELY return here for future Ubuntu help.

Thanks again!

---

### Post by Dot Cong on 2008-11-11
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x104f104e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38245   307202931    7  HPFS/NTFS
/dev/sda2           38246       60129   175783230   83  Linux
/dev/sda3           60130       60801     5397840   82  Linux swap / Solaris

It appears to have worked, I'm accessing the drive now, I am currently looking at the files on my Windows Partition Desktop.

Oh one more quick question, will I be able to write to the Windows partition? Or should I move everything from my Windows partition to my Ubuntu partition and then reformat the Windows partition?

---

### Post by dark_harmonics on 2008-11-11
> **Dot Cong said:**
> Where do you live? Because I'm getting on a plane and coming to kiss you. I now have access to my Windows Partition. Thank you so much everyone for all of the help. I will DEFFINATELY return here for future Ubuntu help.

Thanks again!

Awesome to hear :) I remember trying to figure things outmyself. Do some looking around in here and you never know what you might learn!

---

### Post by dark_harmonics on 2008-11-11
You dont have to move it to an EXT3 partition but i would certainly do that on my computer. Yes you should be able to write that partition in Ubuntu. If you dont feel the need or dont feel comfortable, then you dont have to extract the data and format it. 

Be very careful using it but the package you will need for partition editing in the gui is gparted. you can install with:

```
sudo apt-get install gparted
```
it will then appear under system -> administrator ->partition editor

---

### Post by Dot Cong on 2008-11-11
Ok well if I can write to the partition then I won't bother trying all of that complicated stuff right now. I'll just use the Windows partition for storage. It's a 500g HDD, 300g for Windows and 200g for Ubuntu so I should be fine on storage space heh.

---

### Post by Poyntz on 2008-11-12
it's recommended you do the latter. if you've ever installed a program like wine you'll see how it creates its own mock up windows folder because working across OS partitions isn't recommended.

---

### Post by Dot Cong on 2008-11-12
Oh ok well I'll do it soon then. Thanks for the heads up.

---

### Post by Idefix82 on 2008-11-12
What I would do if I were you is copy all your data from the Windows partition onto the Ubuntu partition, reformat the Windows partition as Ext3 and copy the data back. This has several advantages: the data will be more secure since Ubuntu should never have problems accessing and modifying an Ext3 partition and also the partition will never get fragmented since Ext3 is a journaling file system.
At the same time you won't need to resize your Ubuntu partition so negligeable risk of data loss.

---

### Post by Dot Cong on 2008-11-12
I did that with the above specified program and it reformatted but now I have a lost+found folder on the partition that's around 100g but I can't access it. When I try to access it I get this message: The Folder Contents Could Not Be Displayed. You do not have the permissions necessary to view the contents of "lost+found". Could someone tell me how to change the permissions for this so I can delete it? Thanks.

---

### Post by dark_harmonics on 2008-11-13
> **Dot Cong said:**
> I did that with the above specified program and it reformatted but now I have a lost+found folder on the partition that's around 100g but I can't access it. When I try to access it I get this message: The Folder Contents Could Not Be Displayed. You do not have the permissions necessary to view the contents of "lost+found". Could someone tell me how to change the permissions for this so I can delete it? Thanks.

Check out the last two posts on this thread: [http://ubuntuforums.org/showthread.php?t=229143](http://ubuntuforums.org/showthread.php?t=229143)

It is not recommended that you delete that folder. It would be better to switch to the lost and found directory and just remove the contents if you dont need them. 

Files are moved there (according to the thread) when your file system is checked and bad files are recovered.

---

