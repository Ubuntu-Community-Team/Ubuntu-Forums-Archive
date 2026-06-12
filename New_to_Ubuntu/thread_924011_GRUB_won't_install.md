---
title: "GRUB won't install"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by Anonono on 2008-09-19
For a little backstory on this: [http://ubuntuforums.org/showthread.php?p=5781150](http://ubuntuforums.org/showthread.php?p=5781150)

I have one hard drive, with three partitions. The first, dev/sda1, is a hidden partition on Acer systems used to restore the system by holding Alt+F10 during startup. The second, dev/sda2, has Windows XP Home installed on it, and the third (dev/sda3) is a blank partition that came with the computer that I want to install Ubuntu on. 
The first time I tried to install Ubuntu (8.04, LiveCD), I over-rid the default settings for GRUB, to install it on sda2. On 94% during the install, it came up with an error: "Cannot execute GRUB on dev/sda2. This is a fatal error'. I rebooted, got into Windows safely, and reformatted sda3.
I tried again, this time not touching the settings for GRUB. Same error. Got into Windows, and reformatted again.
Just now I tried following the steps outlined in [this post]("http://ubuntuforums.org/showpost.php?p=3900202&postcount=8"). I set GRUB to install on sda3, but the same error came up.
Now what?

---

### Post by tangibleorange on 2008-09-19
> **Anonono said:**
> For a little backstory on this: [http://ubuntuforums.org/showthread.php?p=5781150](http://ubuntuforums.org/showthread.php?p=5781150)

I have one hard drive, with three partitions. The first, dev/sda1, is a hidden partition on Acer systems used to restore the system by holding Alt+F10 during startup. The second, dev/sda2, has Windows XP Home installed on it, and the third (dev/sda3) is a blank partition that came with the computer that I want to install Ubuntu on. 
The first time I tried to install Ubuntu (8.04, LiveCD), I over-rid the default settings for GRUB, to install it on sda2. On 94% during the install, it came up with an error: "Cannot execute GRUB on dev/sda2. This is a fatal error'. I rebooted, got into Windows safely, and reformatted sda3.
I tried again, this time not touching the settings for GRUB. Same error. Got into Windows, and reformatted again.
Just now I tried following the steps outlined in [this post]("http://ubuntuforums.org/showpost.php?p=3900202&postcount=8"). I set GRUB to install on sda3, but the same error came up.
Now what?

it looks like you are trying to install GRUB to a partition rather than the MBR. is there a particular reason you are doing this? you will still be able to boot into windows with GRUB in the MBR...

---

### Post by Anonono on 2008-09-19
The default setting is to install to the MBR, isn't it?

---

### Post by tangibleorange on 2008-09-19
> **Anonono said:**
> The default setting is to install to the MBR, isn't it?

yeah. if i read correctly, you over-rode the default MBR settings to install to sda2 or sda3 both times. try installing with the default GRUB settings (but still put ubuntu on /dev/sda3). just make sure in the last install screen, under "advanced options", it says install grub to (hd0) rather than a partition or anything else.

good luck!

---

### Post by Anonono on 2008-09-19
No, the first time was to sda2, then to hd0, then sda3.

---

### Post by bumanie on 2008-09-19
Post the output of > cat /boot/grub/menu.lst

---

### Post by mcduck on 2008-09-19
You'll want to install Grub to the boot sector of sda (or hd0 as Grub sees it), not into any partition.

If you aren't able to do that check your BIOS settings, there might be an option to protect the boot sector. Disable that at least until you got tUbuntu installed. (not that there would be much boot sector viruses around these days anyway..)

If it still doesn't work you should check the CD you are using.

---

### Post by caljohnsmith on 2008-09-19
Having the Ubuntu installer fail at 94% with a Grub error is a known bug that can usually be circumvented by formatting your Ubuntu partition to ext2 instead of ext3, and then afterwards upgrading your ext2 file system to ext3. Try that, and if that lets you successfully install Ubuntu, you can easily "upgrade" your file system to ext3 with the following:
```
sudo tune2fs -j /dev/sdXY
```
Replace sdXY with your Ubuntu partition of course, which I assume for you will be sda3. After that, I believe the only thing you need to do is edit your /etc/fstab so that the Ubuntu partition is mounted with "ext3" instead of "ext2".

---

### Post by Anonono on 2008-09-21
> **caljohnsmith said:**
> After that, I believe the only thing you need to do is edit your /etc/fstab so that the Ubuntu partition is mounted with "ext3" instead of "ext2".
In laymans terms?

---

### Post by caljohnsmith on 2008-09-21
> **Anonono said:**
> In laymans terms?
Well before I step you through it, did you successfully install Ubuntu by first formatting its partition to ext2? Were you then able to upgrade the filesystem to ext3 with the command I gave?

---

### Post by Anonono on 2008-09-23
> **caljohnsmith said:**
> Well before I step you through it, did you successfully install Ubuntu by first formatting its partition to ext2? Were you then able to upgrade the filesystem to ext3 with the command I gave?
Yes, so how do I do the last thing you said?

---

### Post by Anonono on 2008-09-23
Anyone? I need help urgently.

---

### Post by caljohnsmith on 2008-09-23
OK, first do:
```
sudo blkid
```
And make sure that whichever is your Ubuntu partition is now "ext3" for the file system instead of "ext2". If not, you'll still need to run the command I gave in post #8. Once you've confirmed your Ubuntu partition is ext3, then first make a backup of your fstab:
```
sudo cp /etc/fstab /etc/fstab.bkp
```
Then open fstab up to edit:
```
gksudo gedit /etc/fstab
```
And then look for a line for your Ubuntu partition, similar to:
```
# /dev/sda2
UUID=77677cb5-6e56-4936-a373-80c15de06bca [COLOR="Red"]/ ext3[/COLOR] nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
```
Don't worry if your options nouser, defaults, etc are entirely different then the above, the important point is to find your Ubuntu partition by noticing that it is mounted on "/"; then make sure the file system is "ext3" as shown above. In other words, yours will probably say "ext2" I'm guessing, and you'll need to change it to "ext3". 

Save, and you should be good to go. Let me know how it goes or if you need more specific info, but if you have any problems, be sure to post your fstab file so we can see it. :)

---

