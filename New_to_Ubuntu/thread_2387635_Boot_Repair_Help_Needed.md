---
title: "Boot Repair Help Needed"
date: 2018-03-21
forum: New to Ubuntu
---

### Post by tomfrankel on 2018-03-21
Hi,

I have Ubuntu 17.10.1 working as a file server in our office.  I thought I was being slick and added a 1.5TB SSD this afternoon and tried to mount the new drive.  Our accounting file resides on the existing spinner drive.

When it prompted me to reboot, I did, and could not get back into Ubuntu.  I kept getting the emergency prompt.   So I got the installation DVD and followed directions to Try Ubuntu and run the Boot Repair application.  It did its thing and I rebooted but no luck.   I still get taken right to the emergency prompt and can't get in to Ubuntu.

Here is the pastebin link:  [http://paste.ubuntu.com/p/NxWJRmhPPJ/](http://paste.ubuntu.com/p/NxWJRmhPPJ/)

These are some of the things I had done before the crash:

sudo gparted (to create a partition on the new drive)
sudo fdisk -l
sudo mkdir /hdd
sudo nano /etc/fstab and updated it to /dev/....   * Note I tried to remove this from the prompt after the emergency and reboot with no change
mount /hdd  *This didn't work very well

I could see the new drive in the file explorer but it was still under the control of root not administrator.  It was at that point that I rebooted.

Any help is greatly appreciated!

Thanks
Tom

---

### Post by tomfrankel on 2018-03-21
Nevermind - I decided to copy the important file to Dropbox, unplug the spinner, and reinstall Ubuntu on the SSD.  It's in progress now.

---

### Post by TheFu on 2018-03-22
For a "server" in a business, it would be best to use 16.04.  17.10 isn't LTS and support for it ends in July 2018.  Hardly enough time for a supported business need/requirement.

Also, if you feel this is solved, please mark it so in the "thread tools" - so others don't waste time.

---

### Post by serapis5 on 2018-03-24
I had the same issue when I did a fresh install of 17.10.  I went into BIOS and changed the boot drive priority and I was then able to boot into both Ubuntu and windows from GRUB2 menu.  Hope this helps.

---

### Post by oldfred on 2018-03-24
Your report showed a "Wubi" install. Which is just a file inside the NTFS partition.
That has not been supported since 12.04, although the files were there in some newer versions.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

If installing directly to a partition that is the correct choice.

---

