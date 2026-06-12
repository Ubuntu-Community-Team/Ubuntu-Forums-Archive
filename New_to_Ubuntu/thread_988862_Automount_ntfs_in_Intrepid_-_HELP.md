---
title: "Automount ntfs in Intrepid - HELP"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by brentwomble on 2008-11-20
So I just upgraded from Hardy to Intrepid and I am trying to figure out how to automount an internal ntfs partition.

sudo blkid gets me

###@###:~$ gedit /etc/fstab
###@###:~$ sudo blkid
/dev/sda1: UUID="C8EC32F1EC32DA00" TYPE="ntfs" 
/dev/sda5: UUID="7db3a063-6f89-4b16-b4db-f2868c16eb46" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="8e337002-26af-4b53-88fb-e3eb141f8164" 
###@###p:~$ 

I have read all the guides and other topics and still can't figure this out. I also tried installing ntfs-config, it worked at first but I think I messed something up because I get through the dialog box with the check marks then it stops.

Any help would be greatly appreciated.

---

### Post by nhasian on 2008-11-20
make a backup copy of /etc/fstab first, then edit it with:


```
sudo gedit /etc/fstab
```

append the line:
```

/dev/sda1	/media/DriveC ntfs defaults,umask=007,gid=46 0 1
```

then save and reboot!

---

### Post by iaculallad on 2008-11-20
Drop to your terminal and issue the command to create your mountpoint:

```
sudo mkdir /media/NTFS
```

Open your fstab file for editing:

```
gksudo gedit /etc/fstab
```

And try to insert the following text below on the end-part of the fstab file:

```
/dev/sda1 /media/NTFS     ntfs    defaults,umask=007,gid=46 0       1
```

Save and Close. While on your terminal:

```
sudo mount -a
```

No need to reboot.

HTH.

---

### Post by iaculallad on 2008-11-20
> **nhasian said:**
> make a backup copy of /etc/fstab first, then edit it with:


```
sudo gedit /etc/fstab
```

append the line:
```

/dev/sda1	/media/DriveC ntfs defaults,umask=007,gid=46 0 1
```

then save and reboot!

It's better if you let the OP know that he must manually create the mountpoint DriveC as stated in your solution. And there's no need to reboot, just issue the command: **sudo mount -a**

```
sudo mkdir /media/DriveC
```

---

### Post by nhasian on 2008-11-20
thanks iaculallad,

i did it so long ago, i forgot that first step :)

---

### Post by brentwomble on 2008-11-20
I followed the second post, naming the drive NTFS and got the following. Could my problem be that I had run ntfs in the past?

###@###:~$ sudo mount -a
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 /media/PC Partition -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 /media/PC Partition ntfs-3g force 0 0
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 /media/NTFS -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 /media/NTFS ntfs-3g force 0 0
###@###:~$

---

### Post by taurus on 2008-11-20
Do you have windows on /dev/sda1?  Looks like you didn't shut it down cleanly the last time you used it so now Ubuntu can't mount it unless you use the force option.  If you have windows on /dev/sda1, I recommend you boot into windows and run scandisk.  Then, shut it down cleanly which means no hibernation or sleep.  

Ubuntu should be able to mount it now.

---

### Post by iaculallad on 2008-11-20
The problem arose when you did not properly shutdown you PC, Ubuntu detected an unclean shutdown thus it does not perform the mount command. Try the solution as stated:

```
sudo mount -t ntfs-3g /dev/sda1 /media/NTFS -o force
```

or

```
sudo mount -t ntfs-3g /dev/sda1 /media/PC\ Partition -o force
```

*At you own risk

---

### Post by tvtech on 2008-11-20
this is way easier 

```
sudo apt-get install ntfs-config
```

it shows up under Applications>System Tools

so easy so happy it was discovered by me in this [[COLOR="Red"]Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?p=6120833")

hope this makes life easier

---

### Post by taurus on 2008-11-20
> **tvtech said:**
> this is way easier 

```
sudo apt-get install ntfs-config
```

it shows up under Applications>System Tools

so easy so happy it was discovered by me in this [[COLOR="Red"]Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?p=6120833")

hope this makes life easier

You should read the OP again.

---

### Post by brentwomble on 2008-11-21
Ok, that force command fixed it, I didn't even realize that I did an unclean shutdown. Restarting and checking to see if it will automount.

Thanks guys.

---

