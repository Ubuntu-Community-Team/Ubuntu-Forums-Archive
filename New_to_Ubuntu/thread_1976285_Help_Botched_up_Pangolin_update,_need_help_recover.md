---
title: "Help: Botched up Pangolin update, need help recovering files"
date: 2012-05-08
forum: New to Ubuntu
---

### Post by RygonChem on 2012-05-08
I somehow messed up the update because I couldn't get back to the login screen after the restart. It just stayed for hours on the screen that says "Ubuntu 11.10" and has the dots underneath that change colors. I was desperate and had to reinstall Ubuntu on a new partition on the same hard drive.
 
I don't mind the new install, and I think it's a little bit cleaner now too. But I had a couple dozen files on the original Ubuntu partition that I don't know how to transfer to the new partition. I know they are there because I can start in manual recovery mode in the terminal and see the directories with the files.
 
Is there some easy way to transfer those files over to a CD/USB/other partition? I don't care about recovering the original OS since I already installed a clean copy. Unless recovering the original OS might be easy.
 
I'm not a complete noob, and I can type commands in the terminal as long as I know what the quickest/easiest solution is.
 
Any help is appreciated!

---

### Post by Enigmapond on 2012-05-08
You can use the liveCD (or USB) to view and move files.

---

### Post by RygonChem on 2012-05-08
Thanks! That's what I orginally thought, but it wasn't obvious to me where that functionality is located. After booting with the LiveCD, I just didn't see an option for moving files. Is there instructions anywhere?

---

### Post by RygonChem on 2012-05-08
I think I just found the answer. Sounds like I need to use the demo tool on the LiveCD in order to install a program to retrieve data on the existing partition.
 
[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)
 
The instructions don't seem very simple, but it's a start. Perhaps "foremost" is a good way to go. 
 
[https://help.ubuntu.com/community/DataRecovery#Software_choices](https://help.ubuntu.com/community/DataRecovery#Software_choices)

---

### Post by cryptotheslow on 2012-05-08
You shouldn't need foremost.

Just boot the LiveCD and take the "Try Ubuntu" option - then open the usual file browser (easiest to click on the Home Folder icon near the top of the launcher). At the top left of that window you should see your hard drive partitions listed (e.g. 50GB File system). You can just click on them to access them and browse to /home/*username* to find your files to copy and paste to the new installation partition.

If the file browser gives you permissions related errors when trying to copy the files, close it, then open it with administrative permissions by pressing Alt and F2 (to open the run command dialogue) and entering **gksu nautilus**. You should then be able to copy the files using the file browser window that opens.

---

### Post by jtarin on 2012-05-08
ChRoot

This method of installation uses the chroot command to gain access to the _**broken system's files**_. Once the chroot command is issued, the LiveCD treats the broken system's / as its own. Commands run in a chroot environment will affect the broken systems filesystems and not those of the LiveCD.

    Boot to the LiveCD Desktop. The CD should be the same release and architecture (32/64 bit).

    Open a terminal - Applications, Accessories, Terminal.

    _**Only If the normal system partition(s) are on a software RAID (otherwise skip this step):**_ make sure the mdadm tools are installed in the Live CD environment (e.g. by executing sudo apt-get install mdadm). Then assemble the arrays:

   ```
 sudo mdadm --assemble --scan
```

    Determine your normal system partition (the switch is a lowercase "L"):

    ```
sudo fdisk -l
```

    If you aren't sure, run df -Th. Look for the correct disk size and ext3 or ext4 format.
    Mount your normal system partition:
        Substitute the correct partition: sda1, sdb5, etc. 

    ```
sudo mount /dev/sdXX /mnt

        Example 1: sudo mount /dev/sda1 /mnt

        Example 2: sudo mount /dev/md1 /mnt
```
    Mount the critical virtual filesystems. 
    Run the following as a single command:

    ```
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done
```

    Chroot into your normal system device:

    ```
sudo chroot /mnt
```

    _**Only if (some) of the system partitions are on a software RAID (otherwise skip this step):**_ make sure the output of mdadm --examine --scan agrees with the array definitions in /etc/mdadm/mdadm.conf.

    Only if you have a separate boot partition (where sdYY is the /boot partition designation):

   ```
sudo mount /dev/sdYY /boot

        Example 1: sudo mount /dev/sdb6 /boot

        Example 2: sudo mount /dev/md0 /boot 
```

  _** Recover your files to another partition or external device.**_

    Exit chroot: 
```
CTRL-D on keyboard
    Reboot.

    sudo reboot
```

---

### Post by Senior_Buckethead on 2012-05-08
If you cant get anywhere with the live CD option, there is a little bootable distribution called Pmagic that I use if I need to get files from a partition I cant normally access, for example, files on a windows machine that wont boot etc.
[http://partedmagic.com/doku.php?id=start](http://partedmagic.com/doku.php?id=start)

Ive heard it said that its just for partitioning, but its more than just that.

Just a thought.
Glenn.

---

### Post by jtarin on 2012-05-09
> **Senior_Buckethead said:**
> If you cant get anywhere with the live CD option, there is a little bootable distribution called Pmagic that I use if I need to get files from a partition I cant normally access, for example, files on a windows machine that wont boot etc.
[http://partedmagic.com/doku.php?id=start](http://partedmagic.com/doku.php?id=start)

Ive heard it said that its just for partitioning, but its more than just that.

Just a thought.
Glenn.+1 Partion Magic:p

---

### Post by RygonChem on 2012-05-09
Thanks for the help! I had no idea it would be this easy and the drive would just appear when doing the demo CD. I ran into some permission problems when copying also, but it was only on one folder that I really didn't want anyhow. I'll eventually clean everything up so the partitions are merged, and sounds like Partition Magic is the way to go with that.
 
On the same note, the fresh install is working fantastic! I *heart* Ubuntu!

---

### Post by jtarin on 2012-05-09
Great! Your welcome. Mark the thread as solved.

---

