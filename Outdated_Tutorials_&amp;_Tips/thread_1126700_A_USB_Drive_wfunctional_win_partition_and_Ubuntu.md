---
title: "A USB Drive w/functional win partition and Ubuntu"
date: 2009-04-15
forum: Outdated Tutorials &amp; Tips
---

### Post by tamas305 on 2009-04-15
I decided I did not want people spamming me so here is how I did it. 

Note: I highly recommend you back up your data before you begin this tutorial because anything could happen. This is collage of what I put together from various other forums and it worked for me. I also advise (if possible) for you to unplug any hard drives attached to the system as a safety precaution. For this tutorial you will need:

  - Ubuntu Live CD
  - gParted Live CD
  - SuperGrub CD (download it but you may not need it)

*websites are constantly updating so any link I post now may be outdated in a week so just google them if you cannot find them. Now lets get our hands dirty...

***_Installation_***

Once you have used gParted to make all of the partitions that you needed. All you need is ext3 for Ubuntu and a fat32 for windows. 

Note: windows only recognises the first partition of a USB drive, make sure the fat32 is first. (When I say first I mean name wise not by how the gParted GUI displays it. i.e. /dev/sdb1). Remember to write down somewhere the partition number of the ext3 partition, this will become mighty useful later.

Insert the Live CD and click on full install. Go though all the menus until you get to the partitioner. Now here is the tricky part. Select manual install (guided overwrites all of your partitions including the fat32). Then from the next page select the partition from your USB drive you want to install Ubuntu to. (it will be an ext3 partition)

Note: make sure that install to correct directory or Ubuntu might overwrite something important. So, if possible, unplug your internal hard drive just in case.

Now set that ext3 partition as the "/" drive. (Ubuntu will install all of its files here, the "root"). Continue through the installer and install Ubuntu. Once done you will have correct the GRUB problem. 
[B][I][U]
GRUB problems: Error 22 especially.[/U][/I][/B]

Try to run your computer without the USB drive that has Ubuntu on it plugged in, what happens? Most likely you got an error.

The problem is that you installed GRUB's files onto the USB drives while you installed it into the Master Boot Record (MBR). So what happening is that GRUB tries to run and it cannot find its files because they are on your USB drive which is not plugged in.

Boot up the live CD and go into the demo mode. Open up a terminal (Applications --> Accessories --> Terminal). 

This is going to involve some MS-DOS like features, so pull your pants up and lets get going.

Into the terminal type:
```

sudo grub
```

This gets you the GRUB shell

```
find /boot/grub/stage1
```

This returns the location of GRUB's files. Note: whatever was returned for the find command you have to use it in the next line, you should still be in the grub>. 
```

root (hd?,?)
```

Use whatever find returned again, for example if find returned (hd0,1) then root (hd0,1) would be what you enter.

Now you have to make sure that GRUB is on the USB drive not on the MBR.

```
setup (hd?)
```

Replace ? with whatever drive you want to install GRUB on. Most likely your USB drive so use whatever number that find returned, for example if it returned (hd3, 15) then you would type setup (hd3).

To exit the GRUB shell type

```
quit
```

If it still does not work than I suggest using SuperGrub Live to delete GRUB completely from everything and then redo this entire tutorial. Cross your fingers that does not happen. Hopefully if everything works out correctly than you should be able to boot successful to Ubuntu when the USB is plugged in and to whatever OS you normally use.

*If there are any errors in this tutorial please let me know so I can fix them before anyone's computer breaks or worse. Thanks* 

Good luck,

-tamas

---

