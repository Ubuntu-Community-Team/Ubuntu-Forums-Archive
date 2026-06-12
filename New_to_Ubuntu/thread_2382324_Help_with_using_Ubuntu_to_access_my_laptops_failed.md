---
title: "Help with using Ubuntu to access my laptops failed hard drive"
date: 2018-01-11
forum: New to Ubuntu
---

### Post by rickytherockstar on 2018-01-11
Hey there, I really hope someone can help me out here
i woke up today and my laptop wouldn’t start to Windows, just was in a “automatic repair” loop
i did a system test and it came back “hard drive short DST check failed”, so after googling I figured there must be a problem with my hard drive and that it must have failed?
I found this page ([https://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer]("https://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/")/) and thought it was easily enough to follow, with my main goal being that I need to be able to get to and save the files on my drive.
the version I downloaded I assume is the newest version and it doesn’t look like the one on the page I posted, so I’m not sure if I’m going to the right spot, but I found a place that said “computer” and there is a “media” folder, but when I click on it i get “cdrom” “disk” and “Ubuntu” I assumed disk is the one I want but when I click on it it’s empty.
does this mean my hard drive is too damaged and I can’t get to the files? Is there anything else I can try? Other programs?
its really important that I get to my files, most importantly my pictures/documents 
any help would be appreciated 
thanks

---

### Post by yancek on 2018-01-11
Which version of windows are you using?
Boot Ubuntu and when you get to the Desktop, open a terminal (hold down the Ctrl+Alt+t keys simultaneously) and type the following:  cat /etc/issue This will tell us which version of Ubuntu you have and the command is case-sensitive.  While you are in the terminal also run this command and post the output:  sudo parted -l(Lower Case Letter L in the command).  This should show information on drives/partitions/filesystems.

---

### Post by 1clue on 2018-01-11
You might try system rescue cd rather than pulling the drive to plug into another box.

[http://www.system-rescue-cd.org/](http://www.system-rescue-cd.org/)

This cd will run on just about any x86 or x86-64 hardware, and has drivers for pretty much everything. And you can work it in-place.  There's a CD image and a usb stick image if your system can boot from those.

---

### Post by rickytherockstar on 2018-01-12
> **yancek said:**
> Which version of windows are you using?
Boot Ubuntu and when you get to the Desktop, open a terminal (hold down the Ctrl+Alt+t keys simultaneously) and type the following:  cat /etc/issue This will tell us which version of Ubuntu you have and the command is case-sensitive.  While you are in the terminal also run this command and post the output:  sudo parted -l(Lower Case Letter L in the command).  This should show information on drives/partitions/filesystems.

Im pretty sure I’m using 8, or 8.1 honestly not sure 
okay I did the first part and I got: Ubuntu 16.04.3 Lts 
And for the second part I got:
[ATTACH=CONFIG]278158[/ATTACH]
(Hope the picture attaches correctly)

thanks for for replying

---

### Post by rickytherockstar on 2018-01-12
> **1clue said:**
> You might try system rescue cd rather than pulling the drive to plug into another box.

[http://www.system-rescue-cd.org/](http://www.system-rescue-cd.org/)

This cd will run on just about any x86 or x86-64 hardware, and has drivers for pretty much everything. And you can work it in-place.  There's a CD image and a usb stick image if your system can boot from those.

Not sure what this method is, but I will look into it, thanks

---

### Post by Impavidus on 2018-01-12
You have a number of partitions on that hard drive. The Windows data is in a 978GB partition that is known to Ubuntu as /dev/sda4. You can open your file manager. At the left it should show a list of devices, including one marked as a 978GB partition. The size may be a bit off because of confusion between gigabytes and gibibytes. It may also have a label. Click on that device and it should get mounted, that is, attached to the file system, somewhere in /media. The file manager then brings you there.

Mounting of the file system may fail, for example, when the file system isn't clean. You can then try via the terminal:```
sudo mount -t ntfs -o ro /dev/sda4 /mnt
```That should make the files available read-only at /mnt, where you can find them using the file manager. If that fails too, there's so much file system damage that you first need some repair. Ubuntu is not very good at repairing Windows file systems.

---

### Post by rickytherockstar on 2018-01-12
> **Impavidus said:**
> You have a number of partitions on that hard drive. The Windows data is in a 978GB partition that is known to Ubuntu as /dev/sda4. You can open your file manager. At the left it should show a list of devices, including one marked as a 978GB partition. The size may be a bit off because of confusion between gigabytes and gibibytes. It may also have a label. Click on that device and it should get mounted, that is, attached to the file system, somewhere in /media. The file manager then brings you there.

Mounting of the file system may fail, for example, when the file system isn't clean. You can then try via the terminal:```
sudo mount -t ntfs -o ro /dev/sda4 /mnt
```That should make the files available read-only at /mnt, where you can find them using the file manager. If that fails too, there's so much file system damage that you first need some repair. Ubuntu is not very good at repairing Windows file systems.


Thanks for replying, 
does trying to mount the files have any risking of hurting the hard drive or files in the process?
and if the mount does work and the files are read only, how do i get them to be regular files?

---

### Post by Impavidus on 2018-01-12
If there's physical damage to the hard drive, any access may make it worse. If you suspect that may be the case, you have to carefully clone the drive and try to recover as much as you can from the cloned image. That can be a bit of a nightmare so I hope you have good backups of most of your data. If no physical damage, there isn't much that can go wrong and if you mount read-only no damage to the file system should happen. That's the point of read-only.

Mounting the file system read-only doesn't change anything to the files. And Windows and Linux permission systems are incompatible anyway. You can simply backup the files to a usb drive or the cloud and access them in the normal way there.

I never had to do any file recovery myself, but this link might help. Even if you need Windows tools for recovery (recovery from Windows systems works best with Windows tools), you have to begin with cloning the drive.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by 1clue on 2018-01-12
> **rickytherockstar said:**
> Not sure what this method is, but I will look into it, thanks

It's a bootable Linux cd much like the Ubuntu live CD, but  rather than experiencing a demo of Ubuntu you get tools specifically for rescuing a broken computer.

It's not Ubuntu, it's actually based on Gentoo but that doesn't really matter. It focuses on drivers for pretty much anything, and on repairing disks and recovering data.

If you only have one computer you should always have a copy of this either burned to CD/DVD, or to a USB stick if your computer boots this way. If you have more than one computer and can burn a cd/dvd on either, or usb stick, then you can always get the latest copy.

---

### Post by ajgreeny on 2018-01-12
You may also find that it is not easy to moujnt your Windows ntfs partitions using a live Linux repair system as I think the default for Windows 8 was to use the same hibernation system as Windows 10 does.

This may mean that when you click on that volume icon in the file manager to mount the partition, you see errors about the partition still being in use.

If you do see those errors try using commands ```
sudo mkdir /media/windrive
sudo mount -o ro /dev/sda4 /media/windrive
``` as the command line allows you to add the ro option for read-only, which the file manager does not.

---

### Post by rickytherockstar on 2018-01-12
> **1clue said:**
> It's a bootable Linux cd much like the Ubuntu live CD, but  rather than experiencing a demo of Ubuntu you get tools specifically for rescuing a broken computer.

It's not Ubuntu, it's actually based on Gentoo but that doesn't really matter. It focuses on drivers for pretty much anything, and on repairing disks and recovering data.

If you only have one computer you should always have a copy of this either burned to CD/DVD, or to a USB stick if your computer boots this way. If you have more than one computer and can burn a cd/dvd on either, or usb stick, then you can always get the latest copy.

okay I read through the walkthrough ([http://www.system-rescue-cd.org/manual/Backup_data_from_an_unbootable_windows_computer/](http://www.system-rescue-cd.org/manual/Backup_data_from_an_unbootable_windows_computer/) ) and seems easy enough, I’m just not sure what to do when it comes to part 3 on that page, the actual backup, it shows how to do it via a network and onto another computer, but I was hoping to back up the files on to my extra hard drive, would I just plug in my external and have to type a certain command?  
I will burn this program to a cd later when I am able to (my mom has a computer that I can use) and try this.
thanks again for your help this far, I really appreciate it

---

### Post by rickytherockstar on 2018-01-12
> **ajgreeny said:**
> You may also find that it is not easy to moujnt your Windows ntfs partitions using a live Linux repair system as I think the default for Windows 8 was to use the same hibernation system as Windows 10 does.

This may mean that when you click on that volume icon in the file manager to mount the partition, you see errors about the partition still being in use.

If you do see those errors try using commands ```
sudo mkdir /media/windrive
sudo mount -o ro /dev/sda4 /media/windrive
``` as the command line allows you to add the ro option for read-only, which the file manager does not.

Good to know, thanks,
will try this later

---

### Post by rickytherockstar on 2018-01-12
> **Impavidus said:**
> You have a number of partitions on that hard drive. The Windows data is in a 978GB partition that is known to Ubuntu as /dev/sda4. You can open your file manager. At the left it should show a list of devices, including one marked as a 978GB partition. The size may be a bit off because of confusion between gigabytes and gibibytes. It may also have a label. Click on that device and it should get mounted, that is, attached to the file system, somewhere in /media. The file manager then brings you there.

Mounting of the file system may fail, for example, when the file system isn't clean. You can then try via the terminal:```
sudo mount -t ntfs -o ro /dev/sda4 /mnt
```That should make the files available read-only at /mnt, where you can find them using the file manager. If that fails too, there's so much file system damage that you first need some repair. Ubuntu is not very good at repairing Windows file systems.


When I went into “disks” I found the 978gb section (I’m assuming the self test failure is not a good sign)
[ATTACH=CONFIG]278166[/ATTACH]
 
I tried to mount it from there, and I got an error (picture attached? I think)

then an I tired the terminal with the commands you gave and the ones Ajgreeny gave and I got the same errors (picture attached hopefully)

i dont know where where to go from here, is my drive that damaged? Is there anything else to try?
would this ([https://www.quora.com/How-do-I-mount-a-drive-in-read-only-mode-in-Ubuntu](https://www.quora.com/How-do-I-mount-a-drive-in-read-only-mode-in-Ubuntu))be some thing to try or would it not matter since my drive seems to be damaged? 

I see see someone else had a similar problem ([https://askubuntu.com/questions/500647/unable-to-mount-ntfs-external-hard-drive](https://askubuntu.com/questions/500647/unable-to-mount-ntfs-external-hard-drive)), and there seems to be some solutions, but they are a bit over my head 

I also purchased from amazon a kit to hook up my laptop’s hard drive to another computer, does that sound like that might work? 

Let me know if you have any suggestions

---

### Post by rickytherockstar on 2018-01-12
> **1clue said:**
> It's a bootable Linux cd much like the Ubuntu live CD, but  rather than experiencing a demo of Ubuntu you get tools specifically for rescuing a broken computer.

It's not Ubuntu, it's actually based on Gentoo but that doesn't really matter. It focuses on drivers for pretty much anything, and on repairing disks and recovering data.

If you only have one computer you should always have a copy of this either burned to CD/DVD, or to a USB stick if your computer boots this way. If you have more than one computer and can burn a cd/dvd on either, or usb stick, then you can always get the latest copy.

I downloaded it and burned it to a disk, but it won&#8217;t run/open on my computer 
I did the same steps like i did the Ubuntu disk, and that one works fine,  it I tried 4 times shutting off my computer and turning it on again, and the bios settings has the CD to boot first, the disk spins then stops and nothing happens 
the file is SystemRescueCd-x86-5.1.2 (if that helps at all)

---

### Post by 1clue on 2018-01-12
> **rickytherockstar said:**
> okay I read through the walkthrough ([http://www.system-rescue-cd.org/manual/Backup_data_from_an_unbootable_windows_computer/](http://www.system-rescue-cd.org/manual/Backup_data_from_an_unbootable_windows_computer/) ) and seems easy enough, I’m just not sure what to do when it comes to part 3 on that page, the actual backup, it shows how to do it via a network and onto another computer, but I was hoping to back up the files on to my extra hard drive, would I just plug in my external and have to type a certain command?  
I will burn this program to a cd later when I am able to (my mom has a computer that I can use) and try this.
thanks again for your help this far, I really appreciate it

Just copy the files using the Linux command line or, if you boot into a GUI, you could copy using the GUI file browser. For example, ```
cp -rax /mnt/brokendrive/path/to/my/dir /mnt/newdrive/path/to/my/dir
```

> **ajgreeny said:**
> You may also find that it is not easy to moujnt your Windows ntfs partitions using a live Linux repair system as I think the default for Windows 8 was to use the same hibernation system as Windows 10 does.

This may mean that when you click on that volume icon in the file manager to mount the partition, you see errors about the partition still being in use.

If you do see those errors try using commands ```
sudo mkdir /media/windrive
sudo mount -o ro /dev/sda4 /media/windrive
``` as the command line allows you to add the ro option for read-only, which the file manager does not.

It's been some years since I had a system with under 16g RAM, but I believe system rescue CD won't swapon until you tell it to. Which means that the swap partitions won't be in use.  I think.

---

### Post by Impavidus on 2018-01-13
> **rickytherockstar said:**
> When I went into “disks” I found the 978gb section (I’m assuming the self test failure is not a good sign)
 
I tried to mount it from there, and I got an error (picture attached? I think)

then an I tired the terminal with the commands you gave and the ones Ajgreeny gave and I got the same errors (picture attached hopefully)

i dont know where where to go from here, is my drive that damaged? Is there anything else to try?
would this ([https://www.quora.com/How-do-I-mount-a-drive-in-read-only-mode-in-Ubuntu](https://www.quora.com/How-do-I-mount-a-drive-in-read-only-mode-in-Ubuntu))be some thing to try or would it not matter since my drive seems to be damaged? 

I see see someone else had a similar problem ([https://askubuntu.com/questions/500647/unable-to-mount-ntfs-external-hard-drive](https://askubuntu.com/questions/500647/unable-to-mount-ntfs-external-hard-drive)), and there seems to be some solutions, but they are a bit over my head 

I also purchased from amazon a kit to hook up my laptop’s hard drive to another computer, does that sound like that might work? 

Let me know if you have any suggestions
Not looking good...

You already tried to mount it read-only and it failed.

I suggest you image your hard drive (also known as cloning), or at least your /dev/sda4 partition, which contains all your documents. You can use Ubuntu to clone it to an external drive. Then try to recover files from that clone. As it's a Windows file system, Windows tools may be more effective. I've never done such things myself, on the one hand because I've been lucky to encounter very few broken drives, on the other hand because I keep backups of all important stuff.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by rickytherockstar on 2018-01-13
So I took the advice to clone it, the way with Ubuntu from the page that was linked confused me a bit, so I googled to maybe find a simpler way, I found this forum ([https://www.sevenforums.com/general-discussion/331869-best-method-tool-cloning-failing-hdd-data-recovery-3.html](https://www.sevenforums.com/general-discussion/331869-best-method-tool-cloning-failing-hdd-data-recovery-3.html)) and the directions on the first few pages seemed easy enough, and I saw it was using SystemRescueCd, since it wouldn’t load with a cd I tried it on a usb like the forum posts suggested, after burning it onto a usb it still wouldn’t open.
so after some more googling, I figured out that I needed to go to system configuration and turn “legacy support” on, once I did and restarted the usb finally loaded and I finally was able to use the SystemRescueCd.
i hooked up my external hard drive, entered the first command: fdisk -l
and it showed my hard drive (with a different, smaller, gig number, but I think that’s normal? Or fine? Or did I loose some data?), showed my usb and my external, so I entered the next command: Ddrescue -d -f -r3 /dev/sda /dev/sdc recovery.log  and now it’s doing its thing

So I guess I just leave this running till it says it’s done or something? Which could take hours or days?

---

### Post by rickytherockstar on 2018-01-14
So the test finished, 
[ATTACH=CONFIG]278184[/ATTACH]

can anyone help me with what to do next?
can I just shut down this computer and remove the external hard drive that I cloned to? Or do I need to input a command before turning off this computer?

and then what would come next, would I hook the external hard drive that i cloned to to a working computer and run some recovery software?

---

### Post by rickytherockstar on 2018-01-14
Just an update, it looks like the cloning worked, I haven&#8217;t checked everything, but it looks like I got all my files back, well the important files I was really looking to get back are all back.
so thanks everyone for your input and suggestions, they were very appreciated

---

