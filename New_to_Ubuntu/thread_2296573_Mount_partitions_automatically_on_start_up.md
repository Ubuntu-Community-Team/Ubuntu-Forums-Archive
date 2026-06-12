---
title: "Mount partitions automatically on start up"
date: 2015-09-26
forum: New to Ubuntu
---

### Post by c10h15n2 on 2015-09-26
Hi. I have dual boot with Ubuntu 15.04 and Windows 10 and after I followed a tutorial called "Mount partitions automatically on start up" ([http://ubuntuhandbook.org/index.php/2014/07/mount-partitions-automatically-ubuntu-14-04/](http://ubuntuhandbook.org/index.php/2014/07/mount-partitions-automatically-ubuntu-14-04/)) I get this error when Ubuntu starts:

```
ACPI PCC probe failed
```

I can only see and use the terminal. A fullscreen terminal with black background. I had two media partitions, one where Windows 10 is installed and one with movies and other stuff and I disabled/enabled (I really don't know what it was) the partition where Windows 10 is installed. Is there any way I can undo the things I edited in "Disks" from the terminal ? check out the link above to see what I mean. thank you.

---

### Post by sandyd on 2015-09-26
Hi, can you post the output of the following.

```

sudo fdisk -l
sudo parted -l
cat /etc/fstab
```

If you know the mountpoint, you can remove the automatic mount from /etc/fstab by commenting out the line that contains the mount by using the following command to edit the file. Control +X saves the file.

```

sudo nano /etc/fstab
```

---

### Post by c10h15n2 on 2015-09-26
Thanks a lot for the fast reply!

Here is the output: [picture](http://i.imgur.com/9l2El2L.jpg)

---

### Post by sandyd on 2015-09-26
> **c10h15n2 said:**
> Thanks a lot for the fast reply!

Here is the output: [picture](http://i.imgur.com/9l2El2L.jpg)

missing ```
cat /etc/fstab
```
output

---

### Post by c10h15n2 on 2015-09-26
oops, sorry about that, here they are: [parted -l]("http://i.imgur.com/JPk8fWx.jpg"), [cat /etc/fstab]("http://i.imgur.com/2SaqrVw.jpg")

---

### Post by sandyd on 2015-09-27
Sorry about this - there is something odd going on in your fstab file. The mount for your root partition is missing, which is likely why your having trouble starting up Ubuntu.

Can you add the output of
```

blkid
``` as well?

---

### Post by c10h15n2 on 2015-09-27
[blkid](http://i.imgur.com/eRZgI5l.jpg)

I also took a picture of the things that show up before I enter anything in the terminal; maybe it's important somehow: [img](http://i.imgur.com/ZJ0vRgO.jpg)

---

### Post by The Cog on 2015-09-27
I would guess that adding this line to /etc/fstab will fix things:
```
/dev/sda6    /    ext4     errors=remount-ro    0     1
```
The number of spaces between items doesn't matter (at least one), but I left big gaps so it's easy to see.

It would normally use a UUID="blah..." clause instead of /dev/sda6 but you can edit that after you have a working GUI and you can copy/paste it from the blkid output.

The easiest editor to use for now would be nano:
```
sudo nano /dev/fstab
```

---

### Post by c10h15n2 on 2015-09-27
If you meant to say "**/etc/fstab**" I tried to add that line but it says that the file is on read-only mode and I can't save the changes.

---

### Post by yancek on 2015-09-27
You could try doing a filesystem check.  How to is explained at a number of sites including the one below.  Boot the Ubuntu Live CD/flash drive or any Linux and run it.

[https://www.maketecheasier.com/check-repair-filesystem-fsck-linux/](https://www.maketecheasier.com/check-repair-filesystem-fsck-linux/)

---

### Post by c10h15n2 on 2015-09-27
> **yancek said:**
> You could try doing a filesystem check.  How to is explained at a number of sites including the one below.  Boot the Ubuntu Live CD/flash drive or any Linux and run it.

[https://www.maketecheasier.com/check-repair-filesystem-fsck-linux/](https://www.maketecheasier.com/check-repair-filesystem-fsck-linux/)

I read that there are some 'dangers' doing that given my situation and I  don't want to take the risk... I've started using Ubuntu a month ago  and I don't feel very confident about doing anything that isn't safe  enough for a rookie to do. 

Just by following that "Mount partitions automatically" tutorial I've seen how 'fragile' the OS is and how easy is to screw up everything. I guess that if I would have access to the GUI again and go to 'Disks' and change back that setting it will work again. Isn't there any way to acces it ? Something like 'Start in safe mode' as in Windows.. #-o

---

### Post by sandyd on 2015-09-27
> **c10h15n2 said:**
> I read that there are some 'dangers' doing that given my situation and I  don't want to take the risk... I've started using Ubuntu a month ago  and I don't feel very confident about doing anything that isn't safe  enough for a rookie to do. 

Just by following that "Mount partitions automatically" tutorial I've seen how 'fragile' the OS is and how easy is to screw up everything. I guess that if I would have access to the GUI again and go to 'Disks' and change back that setting it will work again. Isn't there any way to acces it ? Something like 'Start in safe mode' as in Windows.. #-o

The root partition is sort of like your C: drive in windows, if you don't have it mounted, nothing will work.

That being said, how are you running the current commands?

Are you booted up in the system, in recovery mode, or running the commands via livecd?

---

### Post by c10h15n2 on 2015-09-27
no, I just start Ubuntu as always and after some errors show up (which never appeared before) I get this full screen terminal. As far as I know, I haven't unmounted the root partition, I only edited the settings for the partition where Windows is installed (so one of the media partitions). As I said in the beginning, I did exactly what this tutorial shows: [link]("http://ubuntuhandbook.org/index.php/2014/07/mount-partitions-automatically-ubuntu-14-04/"). Then, after reboot, my windows C partition disappeared completely and I went back to change that option in "Disks" hoping it will come back again. After another reboot I got that error and no GUI, just a terminal. Maybe I accidentally modified the settings for another partition -_-...

---

### Post by sandyd on 2015-09-27
> **c10h15n2 said:**
> no, I just start Ubuntu as always and after some errors show up (which never appeared before) I get this full screen terminal. As far as I know, I haven't unmounted the root partition, I only edited the settings for the partition where Windows is installed (so one of the media partitions). As I said in the beginning, I did exactly what this tutorial shows: [link]("http://ubuntuhandbook.org/index.php/2014/07/mount-partitions-automatically-ubuntu-14-04/"). Then, after reboot, my windows C partition disappeared completely and I went back to change that option in "Disks" hoping it will come back again. After another reboot I got that error and no GUI, just a terminal. Maybe I accidentally modified the settings for another partition -_-...

Ok, do you have the original installation media?
If you don't, you can just create another usb/dvd, but you will need one to fix the current issues.

---

### Post by c10h15n2 on 2015-09-28
ok, I created another one. Now what ? :-k

---

### Post by sandyd on 2015-09-28
Do the following when booted up via livedvd/usb

Look up your UUID via blkid
```

sudo blkid | grep sda6

```

It should output something like (the type doesn't matter)
```

/dev/sda6: UUID="[COLOR="#FF0000"]ecaefd3d-a0ce-44c0-9485-89b423940d48[/COLOR]" TYPE="xfs"

```
What you need is the red portion

```

sudo mkdir /mnt/ubuntu
sudo mount /dev/sda6 /mnt/ubuntu
sudo nano /mnt/ubuntu/etc/fstab

```

Add the following line, and press control+x to save. Replace red_portion_here with the red part you got when you ran blkid
```

UUID=*[COLOR="#FF0000"]red_portion_here[/COLOR]*    /    ext4     errors=remount-ro    0     1
```

```

sudo umount /mnt/ubuntu
sudo reboot

```

if mount spits out errors, or mounts read-only, post back.

---

### Post by c10h15n2 on 2015-09-28
So when it shows this [image](http://assets.ubuntu.com/sites/ubuntu/1527/u/img/download/desktop/try-ubuntu-before-you-install/image-tryubuntubeforeyouinstall-1.jpg) I select 'Try Ubuntu' and then do all of those things ? Or I just get that UUID, remove the USB,  and then run the other  commands ?

---

### Post by yancek on 2015-09-28
You originally indicated you could boot Ubuntu but had no GUI.  If that's the case, just do that and run the sudo blkid to get the UUID for sda6, then open a text editor (nano or gedit or whatever you have) with:  sudo nano /etc/fstab and copy the line suggested above by sandyd, replacing the shown uuid with yours.  If you are doing this from the flash drive or DVD then you need to run all the other commands to mount, as shown:

> sudo mkdir /mnt/ubuntu 
sudo mount /dev/sda6 /mnt/ubuntu 
sudo nano /mnt/ubuntu/fstab

Three separate commands, hit Enter key after each.  When you have edited the fstab then unmount.

> sudo umount /mnt/ubuntu
sudo reboot

Curious as to what happened to that line as the fstab entry you posted earlier clearly shows there was an entry for sda6?  If that doesn't work, you'll need to run a filesystem check.

---

### Post by c10h15n2 on 2015-09-28
When I try to add something in /etc/fstab it says that it's on read-only mode and I can't save the changes.:(

---

### Post by c10h15n2 on 2015-09-28
edit:  I started Ubuntu from the USB by selecting 'Try ubuntu'  ([img]("https://assets.ubuntu.com/sites/ubuntu/latest/u/img/download/desktop/try-ubuntu-before-you-install/image-tryubuntubeforeyouinstall-1.jpg"))  and then run those commands to mount and also edited /mnt/ubuntu/fstab,  then unmount and reboot. Nothing happened. I still get those errors and  no GUI when I start ubuntu. 


> **yancek said:**
> You originally indicated you could boot Ubuntu but had no GUI

yes, I can use only the terminal, but I can't play a song for example, open a folder with nautilus, open the browser or other things.


About '**fsck**', somewhere it was said "*An important thing to note is that fsck cannot be used on a mounted  partition. If you do so, there is a high chance that it will damage the  filesystem.*" so I don't dare to mess around with this command by my own. Can you please give me the exact commands that I should run for the filesystem check ?

---

### Post by yancek on 2015-09-28
> mount and also edited /mnt/ubuntu/fstab

There was a typo there.  Boot the usb, run the command again to mount and then open with a text editor as root (using sudo) /mnt/ubuntu/etc/fstab.  The file you want to edit is in the /etc directory under the mount point /mnt/ubuntu.  If you repeat the commands above it should make the change and the partition should not be mounted.  

When that is done, boot the usb again to the Ubuntu Desktop and run:  sudo umount /dev/sda6.  If you get the output below, you're good to run fsck.

> umount: /dev/sda6: not mounted


The link below has some explanations and examples.  In your case, use the following from the usb after you have verified the partition is not mounted:  sudo fsck /dev/sda6

[http://www.thegeekstuff.com/2012/08/fsck-command-examples/](http://www.thegeekstuff.com/2012/08/fsck-command-examples/)

---

### Post by sandyd on 2015-09-28
> **yancek said:**
> There was a typo there.  Boot the usb, run the command again to mount and then open with a text editor as root (using sudo) /mnt/ubuntu/etc/fstab.  The file you want to edit is in the /etc directory under the mount point /mnt/ubuntu.  If you repeat the commands above it should make the change and the partition should not be mounted.  

When that is done, boot the usb again to the Ubuntu Desktop and run:  sudo umount /dev/sda6.  If you get the output below, you're good to run fsck.




The link below has some explanations and examples.  In your case, use the following from the usb after you have verified the partition is not mounted:  sudo fsck /dev/sda6

[http://www.thegeekstuff.com/2012/08/fsck-command-examples/](http://www.thegeekstuff.com/2012/08/fsck-command-examples/)
Fixed it - whoops

---

### Post by c10h15n2 on 2015-09-29
> **yancek said:**
> There was a typo there.  Boot the usb, run the command again to mount and then open with a text editor as root (using sudo) /mnt/ubuntu/etc/fstab.  The file you want to edit is in the /etc directory under the mount point /mnt/ubuntu.  If you repeat the commands above it should make the change and the partition should not be mounted.  

When that is done, boot the usb again to the Ubuntu Desktop and run:  sudo umount /dev/sda6.  If you get the output below, you're good to run fsck.




The link below has some explanations and examples.  In your case, use the following from the usb after you have verified the partition is not mounted:  sudo fsck /dev/sda6

[http://www.thegeekstuff.com/2012/08/fsck-command-examples/](http://www.thegeekstuff.com/2012/08/fsck-command-examples/)


Good news, the filesystem check repaired the problem and now everything is back to normal. Thank you very much! :D

One more thing though, I don't have the Windows partition listed anymore. I took a screenshot in 'Disks' (where I made the first changes before getting the errors): [image](http://i.imgur.com/buasNxg.png) . Should I modify something here ?

---

### Post by yancek on 2015-09-29
What do you mean by not having the windows partition listed?  Your Disks output shows four windows partitions.  What do you want to 'list' and where?

---

### Post by c10h15n2 on 2015-09-29
Here: [http://i.imgur.com/BlcB71u.png](http://i.imgur.com/BlcB71u.png)

---

### Post by yancek on 2015-09-29
I don't know why it doesn't show there.  Check the /media/user directory (substitute your actual user name here) and see if you have any partitions listed there that might be the windows.   They might be there by UUID.

---

