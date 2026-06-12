---
title: "Can't access files from live CD"
date: 2015-03-29
forum: New to Ubuntu
---

### Post by lascetic on 2015-03-29
First of all I am a really new with Ubuntu. I know almost nothing, so bare with me. I am trying to recover some files from a windows 8 laptop that won't start. So, after hours and hours of searching the internet someone proposed to do it through linux. So I made an Ubuntu live USB and loaded Ubuntu without installing it. The fdisk -l command gives this:

[http://i.imgur.com/zJ511EQ.jpg](http://i.imgur.com/zJ511EQ.jpg)

Then I am stuck, because I don't know how to access the hard disk files.

When trying to mount dev/sdb4 I get the following:
[http://i.imgur.com/ihb4ecV.jpg](http://i.imgur.com/ihb4ecV.jpg)

but chkdsk is what I did yesterday and ended up with an unusable (windows) partition as it got stuck for over a day at 28% and had to shut it down manually....

The worst is that the laptop belongs to my boss who trusted me to fix it cause it was really slow and because of its slowness it was impossible to back it up, so all is lost(?). I still have a couple of hours before he comes to pick it up (dead). Damn.

---

### Post by yancek on 2015-03-29
fdisk doesn't necessarily show accurate information with GPT partitioned disks.  This is shown in the image you posted.  You should be able to open a terminal in Ubuntu.  Hold down the Ctrl+Alt+t keys simultaneously to do that.  You can access GParted then by typing:

```
sudo gparted
``` 

Then hit the enter key and you should see a window showing your drive and partitions.  Make sure the windows partition is sdb1, you should see that in gparted.
In order to access windows, you would first need to create a mount point, then mount the partition.  Do the following steps consecutively, hit the enter key after each command:

```
sudo mkdir /mnt/windows8
```
```
sudo mount -t ntfs /dev/sdb1 /mnt/windows8
```

I'm not sure ntfs-3g is on the installation medium so if you get an error that it is not installed, it should show the command to enter to install.

---

### Post by lascetic on 2015-03-29
I can't run gparted, it says the process already running(?). However in Disks it is sdb4, unknown partition type, unknown contents. I used the commands you gave me (for sdb4) but I get the same message like in the second image (NTFS is either inconsistent or....). I believe that because chkdsk did not complete it is not closed properly.

Another issue: The HD was partitioned into C: & D:, and D: was empty, so I thought if I install windows 8 on D I may manage to see C as well and at least I wouldn't give a dead computer to my boss. But gparted hangs and Disk fails to format in NTFS. It formats in FAT but it is no good for windows 8. Man, this laptop is driving me crazy. Nothing works!

After gparted hangs forever I get the message "Libparted bug found, Input/outpout error during read on dev/sdb, Retry/Cancel/Ignore". Any of the three choices brings back the same message, very soon.

---

### Post by Vladlenin5000 on 2015-03-29
In order to reinstall Windows (or do a pararel installation) you don't need Ubuntu and certainly you don't need to partition in advance, the Windows installer can and will do it for you.
Another thing you - and most people dealing with Windows - must understand is that the default for Windows 8 is hibernation (*fastboot* or whataver) and NOT clean shutdown/reboot. As such - _and for your own good_ - hybernated NTFS (Windows) partitions CANNOT be mounted because they are "in use". This defeats the purpose of using a live session to try to recover files from those partitions. **The advice you've been given is OUTDATED and potentially DANGEROUS.** It made (some) sense up to Windows 7.

For your onw sake, please STOP whatever you're trying to do in the Linux live session, obtain an installation media for Windows 8 as well as **Windows recovery tools** and follow instructions that are all over the net. And considering you're trying to recover files from a non-booting Windows 8 I strongly suggest you to check the [http://www.eightforums.com](http://www.eightforums.com) . There's NOTHING you can (or should) do from a Linux live session.

---

### Post by lascetic on 2015-03-29
> **Vladlenin5000 said:**
> In order to reinstall Windows (or do a pararel installation) you don't need Ubuntu and certainly you don't need to partition in advance, the Windows installer can and will do it for you.
Another thing you - and most people dealing with Windows - must understand is that the default for Windows 8 is hibernation (*fastboot* or whataver) and NOT clean shutdown/reboot. As such - _and for your own good_ - hybernated NTFS (Windows) partitions CANNOT be mounted because they are "in use". This defeats the purpose of using a live session to try to recover files from those partitions. **The advice you've been given is OUTDATED and potentially DANGEROUS.** It made (some) sense up to Windows 7.

For your onw sake, please STOP whatever you're trying to do in the Linux live session, obtain an installation media for Windows 8 as well as **Windows recovery tools** and follow instructions that are all over the net. And considering you're trying to recover files from a non-booting Windows 8 I strongly suggest you to check the [http://www.eightforums.com](http://www.eightforums.com) . There's NOTHING you can (or should) do from a Linux live session.

Thanks a lot for your help. I was just slowly figuring out what you just said. However I ended up here because I couldn't boot into win 8 CD, even with updated suggestions of how to change things in BIOS. It seem that everything should be done after booting into windows 8, which I couldn't. So I try to recover files with linux, but as you say, can't be done.

---

### Post by Vladlenin5000 on 2015-03-29
UEFI is different... Sometimes you need to use ESC immediately after (or during) the first splash screen in order to access the UEFI menu from where you should be able to select a different boot device. You want something like UEFI: CD_ROM or similar.

---

### Post by lascetic on 2015-03-29
> **Vladlenin5000 said:**
> UEFI is different... Sometimes you need to use ESC immediately after (or during) the first splash screen in order to access the UEFI menu from where you should be able to select a different boot device. You want something like UEFI: CD_ROM or similar.

I've spend the whole day with the bloody thing, and on the way I think I found how to boot from USB (that's how I used Ubuntu live), otherwise it was just a blue screen with 3 options that were taking me nowhere. But when I try to install windows 8, it just stalls after the logo and nothing happens. I'm afraid it is a hardware failure and needs to be taken to a repair shop. I hope my boss doesn't ask me to pay for it, because new HD and Data recovery can go up to £500-1000 :(

---

### Post by Mark Phelps on 2015-03-30
My experience, and those of others who have tried the same thing, is that in the US, professional data recovery services generally start around $1000 USD for a single hard drive.  The capacity really doesn't matter much; what you're paying for is the labor to disassemble, repair, and reassemble the drive in a "clean room" environment.  So, those prices are about right.

What might work, if you have access to a working Windows 8 PC, is to connect the drive from the laptop via an adapter cable and see if Win8 can mount and read the drive.  If you see something in Win8 Disk Managment like "raw" instead of NTFS (for the partition type), that generally means it can't read the drive due to hardware failure.

---

### Post by leunam12 on 2015-03-30
This seems like either bad RAM, or bad HDD, maybe both. I would say it's a bad hard drive, they go bad so easily. I would try a commercial HDD repair and data recovery software.

---

### Post by lascetic on 2015-03-31
I have also come to this conclusion, that it is a faulty HD. If it was a software issue it shouldn't have stuck during chkdsk. Also, unless there is a new technology in win 8 that I am not aware of, it should have been able to read the drive with the live CD or USB. RAM might also be an issue. Anyway the laptop is back to my boss, who has probably lost his data, cause I don't think he will be willing to pay the prices they are asking for recovery. If the HD could be repaired then I'm sure I could pull out most of the staff with a good data recovery software. But I don't think he wants me near his laptop again....

---

### Post by Mark Phelps on 2015-03-31
> But I don't think he wants me near his laptop again.... That's unfortunate, because if there's anything you can count on with PCs, it's that every hard drive will ultimately fail -- some, sooner than others.  I had two Seagate hardrives fail on me last year, and it was not because of anything I did -- they just failed.  And in both cases, it was hardware failure.  That's where I got the info on the prices charged to recover hard drives due to hardware failure.

---

### Post by MartyBuntu on 2015-03-31
Why would your boss ask you to fix his computer?

Let me guess...you *volunteered*, right?

---

### Post by lascetic on 2015-04-01
> **MartyBuntu said:**
> Why would your boss ask you to fix his computer?

Let me guess...you *volunteered*, right?

Well, a friend told him that I'm "handy" with computers and he thought that his pc is slow because of a virus and I said that if that is the case I could probably fix it. When I cleaned it from whatever malware was there, it was still slow. So I did a system file check (in windows), but couldn't repair all files. Then I did DISM (which is another process to restore the original windows files), which also failed. Finally I did chkdsk and that's where it got stuck and died(?). These are the logical steps that one would take to repair damages done by viruses. But it was just a bad a HD. Now, I don't claim that I am good with computers myself, because there is so much to know that you can always be better, and whatever knowledge I have in dealing with software, I haven't got a clue about hardware. So, I didn't see it coming. I guess we were both unlucky. 

Anyway, thanks to everyone for their contributions and efforts to help. I really appreciate it.

---

