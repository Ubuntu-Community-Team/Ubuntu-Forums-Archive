---
title: "Getting pics from windows to lubuntu"
date: 2014-05-03
forum: New to Ubuntu
---

### Post by Ben_Cook on 2014-05-03
So, I am reasonably new to linux, but I have been using it off and on for a little over a year now.  I have lubuntu installed on my wife's old netbook and it's working great.  My inlaws old pc is riddled with viruses (running xp I believe).  After seeing me using linux I offered to install it on their computer for them.  They said sure, they need something simple and fast (basically to stream shows online and look at pictures).  They said they were going to get the pics off it first, but now they are unable to even login, other than with a guest profile, which does not allow them access their pictures :confused:.  My question is, when I install lubuntu, will I be able to save their pics and bring them over?  They want to get rid of windows completely, not dual boot.  And it's going to be a huge fight to try and get into windows to get their pics off it anyway.

---

### Post by SeijiSensei on 2014-05-03
Is this a regular desktop machine or a laptop?  If it's a desktop machine, and you know your way around one of them, I'd suggest:

1) Remove the Windows drive entirely and install a new drive.  Maybe you have a spare drive around somewhere.  If the machine is old enough, you'd need an IDE drive rather than a SATA.  Use the same connector as before so the boot order will remain the same.

2) Replace the Windows drive temporarily and cable it to a different connector on the motherboard.

3) Boot the machine and check the BIOS to make sure it sees both drives, and that the new drive will be the boot device.

4) Disconnect the Windows drive.

5) Install Ubuntu on the new drive.

6) After you've rebooted and checked everything out, reconnect the Windows drive and reboot.

7) You should be offered the ability to mount the Windows drive into the Linux filesystem, probably under /media.  If you do that, you'll be able to access the entire disk.  Copy the photos off.  If you're ready to get rid of Windows entirely, have Linux format the Windows disk to its native ext4 format.  Now you'll have both the new disk and the old disk for storage.  Read [this document](https://help.ubuntu.com/community/Fstab) to learn how to tell Linux to mount the old Windows drive automatically at boot.

Do they watch Netflix?  If so, you'll need to install [pipelight](http://fds-team.de/cms/articles/2013-08/pipelight-using-silverlight-in-linux-browsers.html).  Works with Amazon Instant, too.  Services like Hulu just use Flash.  Here's a [quick overview](http://www.webupd8.org/2013/08/pipelight-use-silverlight-in-your-linux.html) for installing pipelight.

If you know how to use [cron]("https://help.ubuntu.com/community/CronHowto"), you can tell it to automatically back up the pictures and anything else important from the Ubuntu drive to the newly-reformatted backup drive.  Then there will be another copy just in case.  Something like this in /etc/crontab
```
0 4 * * * root rsync -a /home/family/Pictures/ /media/windows/backup/
```
That runs rsync at 4 am every day to backup the Pictures directory to the backup location.

If they turn the machine off at night, read the section in the cron documentation about anacron or use the [at](http://manpages.ubuntu.com/manpages/trusty/man1/at.1posix.html) to run backups.

---

### Post by Ben_Cook on 2014-05-03
I don't really know my way around a computer that well.  It is a desktop, but I'm not sure I would be capable of doing what you said :o.  So basically, if I overwrite windows with lubuntu, I won't have the option of saving the pictures?  Or will I?  Thanks in advance!

---

### Post by Ben_Cook on 2014-05-03
I'm afraid this is all over my head:(

---

### Post by ian-weisser on 2014-05-03
If you overwrite Windows, you will certainly DESTROY ALL DATA on the Windows drive, including the pictures.

SeijiSensei has, as usual, proposed a simple, sensible, safe, cheap, and easy way to save the data.
It may _seem_ long and complicated at first read, but it's not. Read it again tomorrow.
Try his way. He's right.

---

### Post by SeijiSensei on 2014-05-03
The problem as Ian observes is that installing Lubuntu will destroy all the existing data on the drive.  So we need to find a strategy to copy the files before installation.  Since your inlaws cannot log into the machine, that strategy has to do an end-run around Windows.  Mounting the drive in Linux is the easiest solution to that problem.

Trying to install Ubuntu before copying the pictures is tricky since it depends on how much free space there is on the drive.  If, as is likely, the drive has a Windows partition that fills the entire device, then you will need to start with a dual-boot arrangement.  You would have to run the repartitioner during installation to preserve Windows and create space for Linux.  If you can do that successfully, then the Windows partition will be available to Ubuntu just like it would be in the two-disk method.  The obvious danger is that something might go wrong during the installation, and you lose the Windows partition.

Can you get the Windows machine to boot into Safe Mode?  You should have the equivalent of "root" privileges that way.  If so, you could plug in a USB pendrive and copy the photos to it.  I'd probably want to do this from a command prompt in Windows with something like xcopy rather than booting the GUI, but I haven't used Safe Mode in such a long time that I'm not sure what options are available to you.  

Another option if you have a pendrive, is to boot the Lubuntu installation disk and choose Try Ubuntu.  You should be able to mount the entire Windows drive that way, too.  Then use Lubuntu to copy the photos to the pendrive.  You can try this method right away if you have a device to copy the photos to.  If you built a USB boot device for Lubuntu instead of using a CD, and you had it create "reserved extra space," you could boot from that in Try Ubuntu mode, mount the Windows drive and copy the photos into the reserved space.  Personally I'd go with the CD and just use the USB device for storage.

If you open the file manager in Lubuntu, you should see the Windows drive listed in the left-hand panel.  Double-clicking it should mount it so you can copy the files.

---

### Post by Ben_Cook on 2014-05-03
OK, I'm going to give this a try.  I think what I'll do is install lubuntu and partition it.  Then I can worry about the pictures.  At this point, their computer is virtually unusable.  So if there is a small risk of losing the pics I think they would be willing to take it.  Thank you so much for your help.  I will let you know how it goes, although it won't be for a few days since they live almost an hour away.  Thanks again for all your help!

   By the way, I only have access to a flash drive install as I am using netbook to get lubuntu

---

### Post by monkeybrain20122 on 2014-05-03
If the hard drive is not fried you should be able to access the pictures from a  lubuntu live usb. So boot to a live usb, attach another hard drive big enough to hold the picture and simply copy them over with the live usb.

---

### Post by LastDino on 2014-05-03
> **Ben_Cook said:**
> OK, I'm going to give this a try.**  I think what I'll do is install lubuntu and partition it.**  Then I can worry about the pictures.  At this point, their computer is virtually unusable.  So if there is a small risk of losing the pics I think they would be willing to take it.  Thank you so much for your help.  I will let you know how it goes, although it won't be for a few days since they live almost an hour away.  Thanks again for all your help!

   By the way, I only have access to a flash drive install as I am using netbook to get lubuntu

Wait! This will certainly erase everything on the drive/partition so be sure to not do it on the partition they have saved pictures. If you've access to flashdrive install, why not just run it in live mode and copy things on some other flash drive? You can do it on the one you're installing Lubuntu from as well but that will require you to prepare that flashdrive in advance.

---

### Post by mansonfan78 on 2014-05-03
+1

> **monkeybrain20122 said:**
> If the hard drive is not fried you should be able to access the pictures from a  lubuntu live usb. So boot to a live usb, attach another hard drive big enough to hold the picture and simply copy them over with the live usb.

This would be easiest, you could copy them over to a flash drive or external hard drive.

---

### Post by Ben_Cook on 2014-05-03
Thanks for your concern Goten0007 and monkeybrain....I will give this live mode a try, as SeijiSensei mentioned as well I believe.  I'm off to bed now, but I will update as soon as I am able to try this

---

### Post by Ben_Cook on 2014-05-04
So, my father in law booted up his computer in safe mode, did a system restore and was able to get back into windows.  I put all important info on an sd card and installed 14.04.  Thank you again for all your help everybody.  Especially SeijiSensei, you went to a lot of work to type all that out.  I have their computer for the week, so now all that remains is getting it ready so it's easy to use for them to stream their shows.  I am also wondering if I should keep 14.04, or downgrade to kubuntu or lubuntu.  The computer has a 1.6 Ghz dual core processor, 1 GB of RAM, 320 GB hard drive.  Any opinions? Or should I ask this question in a new post?  I really want it to be fast, but user friendly (they have never used linux before).  And I would like it to look good.  A lot to ask, I know.

---

### Post by LastDino on 2014-05-04
Well, you should either get upgrade in RAM or use Xubuntu. Your processor is more than fine, but even if Linux says it is fine running on 256 (or was it 512) MB RAM or something like that, it is better to use more than 2GB, or at least 2GB.

And yeah, make a separate thread. Not sure about the section of the forum though, try ''Linux chat'' one.

---

### Post by mansonfan78 on 2014-05-04
The other versions of Ubuntu (kubuntu, xubuntu, lubuntu) aren't downgrades - they're just different desktop environments.  Lubuntu would be the fastest, but also the most "bare-bones".  Xubuntu is faster than regular ubuntu and kubuntu, but with more features and more "user-friendly-ness" than lubuntu.

---

### Post by Ben_Cook on 2014-05-04
OK, thanks guys (or girls).  I'll mark this thread as solved and move on.  Appreciate the advice!

---

### Post by SeijiSensei on 2014-05-05
I'd double the memory to 2 GB and install a [decent video card]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007709%20600030348&IsNodeId=1&bop=And&Order=PRICE&PageSize=20") if the machine relies on Intel motherboard graphics.

---

