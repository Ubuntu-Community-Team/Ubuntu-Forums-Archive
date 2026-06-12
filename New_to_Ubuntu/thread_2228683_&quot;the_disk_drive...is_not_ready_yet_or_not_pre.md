---
title: "&quot;the disk drive...is not ready yet or not present&quot; Ubuntu 14.04"
date: 2014-06-08
forum: New to Ubuntu
---

### Post by Justin.Daniels on 2014-06-08
Hi everyone and thank you in advance,

I just recently installed Ubuntu 14.04 Trusty, and I am very new to using linux.

When I boot my machine up, I get an error: The disk drive for /dev/mapper/ubuntu--vg-swap_1 is not ready yet or not present. Continue to wait, or Press S to skip mounting or M for manual recovery.

This error prompts me every time I boot up the computer. Additionally, I usually don't make it to my desktop when attempting to boot. It allows me to enter my password to sign into my account, then it usually just fades to my desktop and my mouse with no icons or status bar. If I shut my laptop lid and reopen it, it will usually let me to my desktop then.

Any help would be greatly appreciated!

Thanks,
Justin Daniels.

---

### Post by Bashing-om on 2014-06-08
Justin.Daniels; Hi ! My Welcome to the forum.

Look, do you really have a need to encrypt your file system ? It adds a level of complexity that sometimes there is no means at all to overcome these difficulties.

If I may, as this is a fresh install, suggest; how about (re-)installing - without adding that level of complexity that is 'encryption'. In many cases where there are problems there is no solution short of high dollar professional assistance to break that level of security.

As you are new to this operating system it will be much faster and a whole lot less aggravation to get a workable system by (RE-)installing.

[INDENT][INDENT][INDENT]this is but my thought
[/INDENT][/INDENT][/INDENT]

---

### Post by Justin.Daniels on 2014-06-08
lol I've probably re-installed this O.S. about a dozen times. Thank you very much for the quick and insightful reply. I do not have any reason to encrypt my system, I figured the additional feature would be neat...not knowing it would make my life so much more difficult. If I receive no other replies to fix the issue, I will reinstall my O.S. tonight. 

Once again, thank you,
Justin Daniels.

---

### Post by squakie on 2014-06-08
And a silly question - is this an external drive?  - or - did you split it and put swap on an external drive?  This error is usually seen with an external drive (be an actual disk or some sort of flash media) that the system is expecting to be present when it boots but isn't there.  Did you by chance install from an USB flash drive and maybe swap is showing pointing to it? 

Boot up using the install media and the "Try Ubuntu" option.  If the disk you installed Ubuntu to isn't automatically mounted you'll need to mount it.  Next use the file manager and explore the drive you installed to.   Double click on the /etc/fstab file on that drive and see where it expect swap to be.

---

### Post by Justin.Daniels on 2014-06-08
> **squakie said:**
> And a silly question - is this an external drive?  - or - did you split it and put swap on an external drive?  This error is usually seen with an external drive (be an actual disk or some sort of flash media) that the system is expecting to be present when it boots but isn't there.  Did you by chance install from an USB flash drive and maybe swap is showing pointing to it? 

Boot up using the install media and the "Try Ubuntu" option.  If the disk you installed Ubuntu to isn't automatically mounted you'll need to mount it.  Next use the file manager and explore the drive you installed to.   Double click on the /etc/fstab file on that drive and see where it expect swap to be.

This is not an external drive; however, I did install Ubuntu from a USB flash drive. I do not know what 'swap' is, so I did not, by my knowing, mess with it at all...

You want me to plug the flash drive back in and mount Ubuntu? How would I do that, and would I need to reinstall Ubuntu then? Additionally, sorry for the noobie questions, but how would I find the /etc/fstab file (where would it generally be located?), and when I find it lol how do I know where it expects swap to be?

Edit: While doing some research I came to this:
I plugged in the bootable flash drive with Ubuntu on it, and I selected 'Try Ubuntu' like you suggested. Then I opened up a terminal and enter:
```
sudo mkdir /media/newhd
sudo mount /dev/sdb1 /media/newhd

```
It printed back:
"mount: /dev/sdb1 already mounted or /media/newhd busy
mount: according to mtab, /dev/sdb1 is mounted on /cdrom"

Now, I believe that might be the issue, but I wouldn't know how to unmount /dev/sdb1 or how to remount it to the newhd.

Thanks again,
J.D.

---

### Post by Justin.Daniels on 2014-06-09
Further info:
when I type in ```

sudo fdisk -l

``` 
I get this output:
Device Boot     Start     End     Blocks     ID     System
/dev/sda1 *   2048  499711  248832     83     Linux
/dev/sda2   501758 156301311 77899777 5  Extended
/dev/sda5   501760 156301311 77899776 83 Linux

Device Boot     Start     End     Blocks     ID     System
/dev/sdb1 *   2048  3911679 1954816    c     W95 FAT32 (LBA)

when I type:
```
sudo umount /dev/sdb1
```
I get this output:
unmount: /cdrom: device is busy.

---

### Post by squakie on 2014-06-09
You're looking at a optical media device (CD, DVD, etc., drive) when you are trying /dev/sdbx.  We don't want that.

Do you get a GUI when you boot via the USB and select Try Ubuntu?  It should come up to a normal desktop screen.  From there, click on the "Home" button for Unity - the topmost button on the descending menu on the left.  type Files in the search string and it should show an icon with the name "Files".  Single-click it.  This is the file manager.  In "normal" Ubuntu (not xubuntu or lubuntu) this would be called Nautilus.  On the left side of that screen it should show any devices it knows - do you see another disk drive (not "Computer")?  If so, click on that drive, then click on the etc folder.  Once in that folder, scroll down until you find the fstab file.  Double-click it and it should open in an editor.  Highlight, right-click and select "copy", then come back here and reply back. 

Don't see another disk drive?  Then open a terminal, type the following and copy the outputs back here in a reply:

sudo blkid

df -h

---

### Post by Justin.Daniels on 2014-06-09
After opening the "Files", under devices I see:
80 GB Encrypted (Which should be what I'm trying to access?)
255 mb Volume
Computer

After I clicked on 80GB Encrypted I entered my password and received some error. It then changed the name to  78GB Volume. The fstab file reads as so:
```

# /etc/fstab: static file ststem information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disk are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <Pass>
/dev/mapper/ubuntu--vg-root /                    ext4   errors=remount-ro
0              1
# /boot was on /dev/sda1 during installation
UUID=0b5e7332-5b9d-4a77-a3e8-260f09abe390 /boot           ext2
defaults        0          2
/dev/mapper/ubuntu--vg-swap_1 none      swap         sw
0              0
/dev/mapper/cryptswap1 none swap sw 0  0

```

Anything else you would like me to post?

Note: I am retyping this into here and not copying and pasting. The laptop I am using does not have an internet connection when I boot up using the USB.

Thanks.

---

### Post by squakie on 2014-06-09
See my previous post - need 2 more items.

As a suggestion to perhaps make this easier for you:

cd ~

sudo blkid > dwetest.txt <press enter>  (puts the output in the file "dwetest.txt" in your home folder)

sudo df -h >> dwetest.txt  <press enter> (yes there are 2 ">" - says append to the file)

now use some form of removable media (if you have more than 1 USB port and another flash drive use those) and copy the file dwetest.txt from your home folder to that media.  That way when you reboot to post here you can just attach that file to your reply.

---

### Post by Justin.Daniels on 2014-06-09
Just a note: When I open my laptop lid, after having it asleep, it says "soft reset failed (device not ready). I am hoping this is related to the issue at hand.

The other two outputs are attached.

Thank you.

Edit: The attachment didn't keep its format after transferring it. The first output ends at "TYPE="vfat"" and the second output begins at "Filesystem" If it is too difficult to read I can try to recopy the outputs.
Thanks again.

EditEdit: Reuploaded the file, it seems to be formatted correctly now. Should be much easier to read :)

---

### Post by squakie on 2014-06-09
It looks like your installed ubuntu is 64GB or so - does that sound about right?  However, I'm not familiar with this "/dev/mapper/ubuntu--vg-xxxxx" references - perhaps that has something to do with your encryption or perhaps it's a result of looking at it when booted from USB.

My suggestion?  Follow what bashing-om posted quite a bit back - reinstall Ubuntu and don't use encryption.  Make sure you set up a swap partition during the install.  Also if you plan to suspend/hibernate, the rule of thumb has been swap size should be twice the size of your physical memory plus a little extra for overhead.  If your memory is something like 8GB or larger, I would think it might work with a swap size of say 4GB plus some extra for overhead - though I've never tried it that way.

---

### Post by Justin.Daniels on 2014-06-09
Hmm, I think it was 80GB but I could be wrong. I will re-install Ubuntu without encryption and post if the issue is resolved.

Thanks.

---

### Post by obake2 on 2014-06-09
This seems to be a bug with Ubuntu 14.04:

[http://ubuntuforums.org/showthread.php?t=2221067](http://ubuntuforums.org/showthread.php?t=2221067)

[http://ubuntuforums.org/showthread.php?t=2227525](http://ubuntuforums.org/showthread.php?t=2227525)




Please add yourself to the Launchpad Bug reports that are listen on the first link. :-)
I'm also affected by this bug and waiting for a proper fix.

---

### Post by squakie on 2014-06-10
And hence why reinstalling without the encryption would be a good thing to do ;)

---

### Post by Justin.Daniels on 2014-06-10
> **squakie said:**
> And hence why reinstalling without the encryption would be a good thing to do ;)

Installing without encrpytion did fix my issues. Thank you everyone!

---

### Post by Bashing-om on 2014-06-10
Justin.Daniels; Hey !

Outstandingly great .

[INDENT][INDENT]Happy Trails to You
[/INDENT][/INDENT]

---

### Post by Justin.Daniels on 2014-06-10
> **Bashing-om said:**
> Justin.Daniels; Hey !

Outstandingly great .
[INDENT][INDENT]Happy Trails to You
[/INDENT]
[/INDENT]


Thanks so much! I appreciate the openness of this forum! Everyone has been super kind and helpful, thank you!

---

