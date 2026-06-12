---
title: "cdrom not working in Xubuntu 12.10"
date: 2013-06-02
forum: New to Ubuntu
---

### Post by Hermenegilde on 2013-06-02
Hello,

I have just intalled Xubuntu 12.10 on an old Dell Latitude C610 laptop.  It works great, except that I can't seem to make the cdrom work.  I did search the web but was unable to find a solution.  So now I am here, needing help.

One interesting piece of information I got was the following:[INDENT]
patrick@Serenity:/media$ wodim --devices
wodim: Overview of accessible drives (1 found) :
-------------------------------------------------------------------------
 0  dev='/dev/sg1'    rwrw-- : 'SAMSUNG' 'CD-ROM SN-124'
-------------------------------------------------------------------------

[/INDENT]
And if I try to mount any of /dev/cdrom1, /dev/sr0 or /dev/sg1, I get the following:

[INDENT]patrick@Serenity:/dev$ sudo mount /dev/sg1
[sudo] password for patrick: 
mount: can't find /dev/sg1 in /etc/fstab or /etc/mtab
[/INDENT]

Some more info that could be useful:


[LIST]
[*] The /etc/fstab and /etc/mtab do not have a cdrom entry
[*]I can see the following in /dev/:
[LIST]
[*]/dev/cdrom1
[*]/dev/sr0
[*]/dev/sg1
[/LIST]

[*]The only thing appearing in /media/ is /media/floppy0 and /media/floppy (the funny thing is, I don't have a floppy on this laptop)
[*]The cdrom eject button does not work
[*]I don't see the cdrom even with a cd inserted
[*]The cdrom eject button actually works before Xubuntu gets loaded (i.e. if I choose to boot from CD)
[/LIST]

Any help will be greatly appreciated.  

Thanks in advance!

---

### Post by Feathers McGraw on 2013-06-04
Hi Hermenegilde,

What is on the CD rom? Is it the CD you used to install Xubuntu? Are you sure you really installed it and didn't just "try Xubuntu"?

If you installed it then during the installation you should have seen a prompt that said something along the lines of "installation complete. Remove CD from drive then press ENTER to continue", after which the computer reboots.

I have a feeling you may have missed this, and when you boot the computer you're still booting from the CD, not from the newly installed Xubuntu on your hard drive.

Have a look at your CD drive, it should have a small hole next to the eject button. Get a paperclip or something similar and push it in the hole, this will release the catch in the drive and eject the CD. Take the CD out and boot the computer.

If Xubuntu is installed then it should boot up fine; if you were only "trying Xubuntu" by loading it into your RAM then you'll get Windows or whatever other OS was installed previously.

Let us know what happens!

Feathers

---

### Post by Hermenegilde on 2013-06-04
Hi Feathers,

I am booting Xubuntu from the hard-drive.  I did try inserting a CD using a paperclip, thinking that maybe the CD drive would get recognize with a disk in, but nothing happened.


P.S. Big fan of Wallace & Gromit :)

---

### Post by Feathers McGraw on 2013-06-05
Glad to hear it! Cracks me up every time :D. Seemed appropriate for the forum, seeing as Feathers McGraw is a penguin...

That's really strange, if you used the drive to install Xubuntu then it must have been working at the time:confused:

Perhaps you're missing a driver. Are you dual booting? If so does the drive work properly under Windows? That would at least tell us it isn't a hardware problem.

Feathers

---

### Post by Hermenegilde on 2013-06-05
Yep, I just confirmed the drive is working properly.  I booted using my Xubuntu CD without problem.  So definitely not a hardware issue.  

As you said, I might be missing a driver.  What I find strange is that I get the floppy drive icon on the desktop when I don't even have one on the laptop.  Is it possible Xubuntu is confusing my cdrom for a floppy drive?

Is there a way to verify my cdrom driver is installed properly?

---

### Post by Feathers McGraw on 2013-06-06
Right, I've been rummaging on Google and have two things we can try...

1) Try moving the CD drive after the hard drive in the BIOS boot order.

If that doesn't work, then:
 
2) open the file /etc/fstab and comment out the lines relating to your CD drives

i.e.
```
sudo leafpad /etc/fstab
```

add a # at the start of the lines with cdrom in them

Also, just out of interest if you open something like VLC can you navigate to the CD drive and get it to play the disk?

Feathers

---

### Post by Hermenegilde on 2013-06-06
Hi Feathers,

1) That's how I was already setup.  So doesn't seem to be that.

2) I don't have a line for my cdrom in /etc/fstab.  Here is what it looks like:

[FONT=courier new]patrick@Serenity:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=8e9d5408-e0d9-4458-95c0-2f9bd9627a6c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=de1faef6-8ae0-42fa-886a-d5662e6b6c1a none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
patrick@Serenity:~$ [/FONT]

While playing around a bit, trying what you suggested with using an app to try and access the CD, I was finally able to access the content of a music disk.  Here is what I did, step by step:

1- I inserted a music CD in the drive using a paper clip.
2- I commented out the floppy line in /etc/fstab (as mentioned previously, I am having doubt about my system mixing up the cdrom for a floppy, and since I didn't have a cdrom line, thought why not comment out the floppy instead).
3- I rebooted.
4- The CD icon appeared on the desktop and I was able to access the content.

Now, the thing is, after ejecting the CD and re-inserting it, nothing happened.  So I tried pushing the eject button on the drive itself, and that got Parole to launch with an error: "GStreamer backend error Could not open CD device for reading.".  But then, the CD icon re-appears on the desktop.

After that, I removed the "#" in front of the floppy line in /etc/fstab, rebooted, and still got the same behavior, with the eject button bringing up Parole. 

It kindda looks like a driver issue to me since closing the drive with a disk in doesn't get it to start reading, and the button doesn't eject the disk, but acts like closing the tray instead.  What do you think?

---

### Post by Feathers McGraw on 2013-06-07
Hmm

This thread: [<here>](http://ubuntuforums.org/showthread.php?t=2007669) for xubuntu 12.10 suggests that installing "udisks2" helped someone mount an external hard drive.

Worth a shot but I'm just guessing now :P

Feathers

---

### Post by Hermenegilde on 2013-06-07
It looks like I already have udisks2 installed if I look in the Ubuntu Software Center.

I did run a few udisks commands in a terminal window to see if I could eject or mount using that, but both failed:

[FONT=courier new]patrick@Serenity:~$ udisks --mount /dev/sr0
Mount failed: Error mounting: mount: no medium found on /dev/sr0

patrick@Serenity:~$ udisks --eject /dev/sr0
Eject failed: Error ejecting: eject exited with exit code 1: eject: unable to eject, last error: Inappropriate ioctl for device[/FONT]

Any other idea?

---

### Post by Feathers McGraw on 2013-06-09
Sorry, I'm all out of ideas :(

[This](http://ubuntuforums.org/showthread.php?t=1178855) may be what's causing the problem, but the thread doesn't provide a solution :(

Hopefully someone else who actually knows what they're talking about can help you!

Feathers

---

### Post by Hermenegilde on 2013-06-09
Hi Feathers,

Thanks so much for taking the time to try and solve my problem.  I really appreciate it!

I haven't abandoned yet.  I'll keep searching and see if I can get my cdrom to work properly.

Just FYI, I was able to get something out of it using Xubuntu 12.04.  I actually installed it along my Xubuntu 12.10.  The basic behavior remained the same (i.e. the only way to open the tray is with a paperclip, and to get the drive to start spinning, I have to push the eject button).  But once the disk is recognized, I can actually use applications to browser the content of the disk and play songs if it's an audio disk.

Again, thanks for you help!

-Hermenegilde

---

### Post by Hermenegilde on 2013-06-10
Hi Feathers,

Thanks for taking the time to try and help me, I really appreciate it!

I haven't abandoned yet.  I tried installing Xubuntu 12.04 and Lubuntu 13.04, and I had some form of success with them.  I could at least get an app to play songs out of an audio CD, though the eject button was still acting kindda of weird.

And then I found this thread on another forum: [http://www.linuxquestions.org/questions/linux-mint-84/can%27t-open-cd-drive-in-mint-14-a-4175438294/](http://www.linuxquestions.org/questions/linux-mint-84/can%27t-open-cd-drive-in-mint-14-a-4175438294/)

It looks like a bug was filed on launchpad.  But using the following command, I was able to get my cdrom working almost normally in Xubuntu 12.04 and Lubuntu 13.04 (but not in Xubuntu 12.10):

[FONT=courier new]sudo eject -i off
[/FONT]
Again, thank you for your help and guidance!


-Hermenegilde

---

### Post by Feathers McGraw on 2013-06-11
Brilliant, glad to hear you found a solution (kind of).

Feathers

---

### Post by MirrorUniverse on 2013-06-13
Something that may or may not help...I found this post for antiX, which is Linux based.  The first post by BitJam looked interesting to try to find a kernel module that worked while using the liveCD.  The original poster had the same CDrom you do.  [http://antix.freeforums.org/laptop-cd-rom-issue-t3944.html](http://antix.freeforums.org/laptop-cd-rom-issue-t3944.html)

---

