---
title: "Disk cloning"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by TheSlipstream on 2008-08-19
Hi, all. My external USB disk caddy arrived today, so I've been attempting to transfer the data from my **laptop** HD to the new one. I've tried CloneZilla, (died of a strange bug that I got twice, telling me I had some sort of disk corruption) FOG, (wouldn't even start, informed of some weird error while booting) gParted Live Disk, (couldn't detect external drive) and Ubuntu 8.04 Live Disk (also couldn't detect external live disk.

As you might guess, I'm rather fed up, and would really appreciate some advice in this case, Google doesn't seem to have anything for me. This is quite important to me (don't want to lose the money I payed for the HD), so if I don't get responses, I'll bump.

Thanks!

---

### Post by mellowd on 2008-08-19
Do you want to make a copy of everything? You can use tar, it's pretty simple.

If you tar your entire system you can untar it on a new hard drive and it'll be the same as a clone.

---

### Post by forger on 2008-08-19
Have you tried rsync?
[http://samba.anu.edu.au/ftp/rsync/rsync.html](http://samba.anu.edu.au/ftp/rsync/rsync.html)

---

### Post by hyper_ch on 2008-08-19
do you want

(a) a 1:1 image that you just can put back or
(b) backup your files?

---

### Post by JohnGalt131 on 2008-08-19
I used Acronis TrueImage in my freedom hating, Windows days. Now If I just want Data backed up I use either

**tar** cvpfz /path/to/backup.tgz --exclude=/some/path/to/exclude /path/you/want/backed/up

or **rsync** for quick easily incremental backups

If I need MBR and everything exactly the same, I've really grown to love **Partimage**. You'll need to use a bootable USB or livecd to backup any disk which cannot be dismounted while you have your main system booted. i.e. your system partition.

Good Luck

---

### Post by TheSlipstream on 2008-08-19
> **hyper_ch said:**
> do you want

(a) a 1:1 image that you just can put back or
(b) backup your files?

The full data to a new hard drive one. Aka, a.

I attempted a full compression of my drive from a live disk. Well, it seemed busy, so I left it alone for a while. I come back, see no file or error message, boot back into main Ubuntu, search with Beagle, finds nothing. Something messed up clearly...not sure what. :/

---

### Post by hyper_ch on 2008-08-19
you still don't say wht kind of backup you want.

(a) do you want a 1:1 copy / clone / image of your harddisk as backup
or
(b) do you just want to save all your files and stuff as backup

---

### Post by ByteJuggler on 2008-08-19
Cloning your disk can be done from a booted LiveCD with the "dd" command.  Copying the contents of your disk (whilst not making a bit-perfect clone) can be done in various ways, using "tar", using "cpio" and several other methods.  You'll have to be more specific in order for us to be more helpful.  

Aside: What error messages *exactly* are you getting?  Are you sure there's no cable/hardware problems anywhere?  Sounds suspicious that you're having so many problems...

---

### Post by forger on 2008-08-19
ByteJuggler is right actually, you shouldn't have any problems by connecting..

1) What's your hard disk brand/model?
2) Boot using the Ubuntu hardy heron live CD
Connect your hard drive
Then open Applications > Accessories > Terminal and do the following commands:
```

sudo update-pciids
sudo update-usbids
lspci
lsusb
dmesg | tail

```

Reply and paste the output of the commands

---

### Post by TheSlipstream on 2008-08-20
> **hyper_ch said:**
> you still don't say wht kind of backup you want.

(a) do you want a 1:1 copy / clone / image of your harddisk as backup
or
(b) do you just want to save all your files and stuff as backup

How exactly would B be disk cloning? I want to move all the files (including the operating system, everything) from one hard drive to another hard drive. I'm not so stupid that I can't copy paste files. 

From the top. Everything in one drive to another, larger drive.

CloneZilla screws up and babbles about some sort of corruption about 4 gigs into the cloning. FOG just talks about Error 91 during bootup. The other two don't detect external devices. I honestly don't get how I'm being vague here.

My cables are fine. Ubuntu wouldn't boot if there was actually something wrong with the disk.

---

### Post by meanburrito920 on 2008-08-20
> **TheSlipstream said:**
> How exactly would B be disk cloning? I want to move all the files (including the operating system, everything) from one hard drive to another hard drive. I'm not so stupid that I can't copy paste files. 



The difference is as such: in A, you copy byte for byte every bit of data to the other drive, so it is for all intents and purposes an exact copy of the drive. In B, the files and everything are moved  to the other drive, but they are not an 'exact' image. both methods can be used as a full system backup in that you can copy everything back and it will work perfectly. That is a great advantage of linux. you dont need a disk image to recover from, you only need the files. For your case I would suggest option B, because you can tarball (the equivalent of zip) your entire disk to the backup disk, which saves space, plus is fully recoverable from (just unzip it as /).

---

### Post by TheSlipstream on 2008-08-20
Alright, I'll try archiving onto the disk, assuming it's actually possible to do that while the files run, something I know Windows could never do. Should I archive the filesystem, or what? I remind you, I'm not after a backup here. I'm actually planning to use the drive I'm copying into, and format the one I'm copying from. It needs to work as a full disk, as in, you can boot from it.

Edit: Eeek. I guess I never said I was going to use the new drive. Sorry. :/

---

### Post by Return Privacy on 2008-08-20
Hi all,
I also need to do a clone of my hard drive. 1=1, bit for bit, whatever you want to call it.  It is running Ubuntu 8.04. It is working fine, but the drive is starting to make noise. I want to clone it to another hard drive before it fails, and then just switch the hard drives out. I am new to Ubuntu, but have done this same thing in windoze machines using ghost before. 

I have the system drive connected by ide cable to mobo. I can put the "new" drive that I want to put the clone on, on the secondary ide plug on the same cable. Or I can plug the "new" drive on the secondary ide plug on the cable that goes to the dvd/cdr burner. 

This ubuntu setup is running well, with a lot of customization, and I don't want to loose it. I didn't set it up. 
Thank you in advance for you help.
:confused:

---

### Post by ByteJuggler on 2008-08-20
OK, if you want to use/boot the other (cloned) disk as a direct replacement for the original, then you do need to make a bit for bit clone.  I'll explain the process below, but you may also reference [this thread ]("http://ubuntuforums.org/showthread.php?t=874643&page=2")for background.

Note however as a word of warning, that if your source disk is having any kinds of issues (e.g. having trouble reading certain parts of the disk) then the below procedure may run into trouble/may take substantially longer than normal, as the cloning process will read every byte on the disk, whether its used or not.  Note also that, if your OS is still booting that does not neccesarily mean that the disk free from having problems. If your source disk does have significant problems impeding the below process, then an alternate process using a tool called "dd_rescue" would be needed, which I'll not cover now unless it turns out to be needed.

OK, so on to the process. Ideally you should perform this operation while booted from a LiveCD as you don't want open files on the disk being cloned causing an inconsistent state/problems on the clone.   

So firstly you have to identify which is the source disk and which is the target disk.  You can usually identify this using the output from e.g.

```
sudo fdisk -lu
```

The result should be two disk device identifiers, e.g. firstly the **[COLOR="Red"]source drive[/COLOR]**, say (for IDE):```
[COLOR="Red"]**/dev/hda**[/COLOR]
``` or (SATA)```
**[COLOR="Red"]/dev/sda[/COLOR]**
```

And secondly the [COLOR="Lime"]**desination drive**[/COLOR] (probably empty with no partitions) e.g. :
```
**[COLOR="Lime"]/dev/hdb[/COLOR]**
```
or (SATA)
```
**[COLOR="Lime"]/dev/sdb[/COLOR]**
```

**This is only an example, **if your current source disk is not the first disk in the system then the device identifier for the source will obviously be something else e.g. /dev/hdb or /dev/sdb etc.

Once you've established which is the source drive and which is the target drive, you can then proceed to cloning the disk using the "dd" command as follows:

```
sudo dd if=**[COLOR="Red"]/dev/hda[/COLOR]** of=**[COLOR="Lime"]/dev/hdb[/COLOR]** 
```
 
The "if" above stands for "Input file" and the "of" above stands for "Output File."  It means that "dd" will read from "if" and write to "of", thus copying the entire disk from one to the other.  So, **you need to substitute "/dev/hda" above with your source/original disk being cloned, and "/dev/hdb" with the target where you're cloning to.**  

[COLOR="DarkRed"]**A word of warning:  If you get the above mixed up/the wrong way round, you will destroy your existing data! _Be sure to have backups of anything you can't afford to lose before you start_ this, and _double check you've got the above command exactly right_ before you issue it!!!**[/COLOR]

Note: The command will run for a substantial while, copying the entire disk with no feedback about what its doing.  This is normal.  You can stop the copy if you want by pressing ctrl-c.

If you'd like some feedback while the copy happens, you can instead perform the copy as follows:

```
sudo -s
dd if=**[COLOR="Red"]/dev/hda[/COLOR]** of=**[COLOR="Lime"]/dev/hdb[/COLOR]** & pid=$!
while kill -USR1 $pid; do sleep 1; done
```

The above version of the dd command will put the copy into the background, and the following "while" line will then send a signal to the background copy to ask it report progress once every second.  To stop the monitoring you may press ctrl-c, and then to stop the background copy you can then issue "fg" to bring the background copy job to the foreground, followed by ctrl-c again to stop it.  

Finally, after copying, exit the root shell (started on the first line with the "sudo -s") by entering:

```
exit
```

This is very important, to prevent accidental damage by the use of the root shell.  (I used it above since the & symbol does not work well in conjunction with sudo on the same command.)

Once the copy has finished, you may shut down the machine, remove the original and place the clone drive in the place of the original. You should find you can now boot off the clone as though it's the original disk.  

Edit: After successful cloning, you can at your leisure resize the partitions on the cloned disk to make use of the full space on the target disk, or you can of course just create a new partition to make use of any space left over after the copy.

---

### Post by TheSlipstream on 2008-08-20
Hm. After some testing, I'm nearly 100% sure that my External Drive Holder is defective. I'm getting a new one, and when I do, I'll make sure to post if I was successful with your method. Have a gold star for effort. :)

---

### Post by Return Privacy on 2008-08-31
Bytejuggler,
I followed your post tonight. I used the commands to clone to a brand new WD 320 gb ide hd. The original is a WD 40 gb ide hd. It cloned with no problems, and I typed exit when it was done. I removed the live cd, and put in the new drive.
It attempted to start and it says DISK BOOT FAILURE, INSTALL SYSTEM DISK AND PRESS ENTER.
I tried several times. 
Like I said this new drive is right out of the box, I didn't do anything but clone to it. Is there some way I was supposed to prepare it before cloning?

---

### Post by ByteJuggler on 2008-09-01
> **Return Privacy said:**
> Bytejuggler,
I followed your post tonight. I used the commands to clone to a brand new WD 320 gb ide hd. The original is a WD 40 gb ide hd. It cloned with no problems, and I typed exit when it was done. I removed the live cd, and put in the new drive.
It attempted to start and it says DISK BOOT FAILURE, INSTALL SYSTEM DISK AND PRESS ENTER.
I tried several times. 
Like I said this new drive is right out of the box, I didn't do anything but clone to it. Is there some way I was supposed to prepare it before cloning?

No, doing a disk-to-disk clone copies *everything*, including partition table/master boot record and all the partitions on the original disk.  After that, it's generally putting it in the place of the original, which includes checking/setting up the BIOS boot order etc.  It sounds like either the clone operation was done somehow incorrectly somewhere or your BIOS boot order is somehow wrong currently.  How long did the copy process take?

Can you again connect both drives, then boot up with an Ubuntu LiveCD, then from a terminal window post the output of the following command:

```
sudo fdisk -lu
```

So we can see what partitions currently exist on all the disks.

If you don't know how to copy text from a terminal, then you may use the following commands instead, to get the text into an easy to copy from text editor.  Enter the following command into a terminal:

```

sudo fdisk -lu >/tmp/fdisk.txt; gedit /tmp/fdisk.txt

```

---

### Post by Return Privacy on 2008-09-01
Hi bytejuggler,
Thanks for responding quickly. I tried connecting both drives, and booting from the live cd. It boots, but the fdisk -lu brings up nothing. I then disconnected the "new" drive, and connected only the "old" drive and let it boot normally. I got the following from the fdisk -lu command. I attached the text file. 
When I connected only the "new" drive and booted from the live cd, the fdisk -lu does nothing. So, I guess the cloning didn't work. One strange thing though. I noticed when I booted from the "old" drive, it now has what appears to be another drive on the desktop that is named "media 2.0gb".
That was never there before. And I think it explains partially what happened? When I did the cloning, it said it completed and it had cloned 2.1gb. I had just assumed that was the size of the actual ubuntu install from the "old" drive and it cloned it to the new drive?
Remember when I first started to clone, you had me do a command that showed the two drives as /dev/hda (40gb) and /dev/hdb (320gb). I even wrote it down. When I did the cloning I specified 
if=/dev/hda and of=/dev/hdb, and it did do the cloning and finished? Maybe you can figure it out more than I can. I just know that the new drive doesn't show up at all when connected by itself and booting from the live cd? Oh, and if it matters, I did jumper the "new" drive as slave when I connected it to the "secondary" plug on the ide cable when I did the cloning. Now when I try connecting just the "new" drive I have tried with jumper, and without, as a master, and it doesn't show up. Hope this all makes sense to you, I'm stumped..:confused:

---

### Post by ByteJuggler on 2008-09-01
OK, something odd is then going on.  OK firstly, when you had both disks connected, did you run the "fdisk -lu" with "sudo"?  I ask, because fdisk behaves like (producing no or sometimes incomplete [depending on permissions] output) when you run it without "sudo" so I'm wondering if perhaps you left out the sudo that time.  Just a guess.  Anyway, when you have both disks connected, you really ***should ***see entries for both disks, even if the new disk contains no partition table yet, in the output of "sudo fdisk -lu".  

Also note for reference, because a cloning operation copies the *entire* disk regardless of what's on it, it should report that 40GB was copied if everything goes according to plan.  So, clearly the copy didn't work as planned for some (at present) unkown reason.  I'm guessing the problem crept in during your identification phase somehow. I notice the file you attached reference /dev/sda (which is normally indicative of SATA disks), whereas your post references /dev/hda, /dev/hdb and jumpers on a hard disk, which implies IDE disks.  So, please clarify exactly where you're copying from and to (and the disk types.)  

Anyway, I suggest we use an alternate method to do the disk identification for source/target:  Use "gparted", the partition editor.  Normally it's accesible from System->Administration->Partition Editor, if it's installed.  If it's not installed, then first install it, for example using Synaptic.  Go System->Administration->Synaptic   Package manager, then click "Search", enter "gparted", click it and click "Mark for Installation", then click "Apply" and wait for it to be installed.  (You can even do this while booted from the liveCD if needed, can't offhand remember if it has it installed or not.)  

Once you go into the Partition editor, it will list a screen something like this:
[[IMG]http://img398.imageshack.us/img398/7140/screenshotdevsdagpartediz8.png[/IMG]](http://imageshack.us)
Notice on the Gparted menu, there a submenu listing all the disks (devices) in the system.  Those are the identifiers you need for the cloning process.  In my system snapshotted above, there's a 320GB disk and an 8GB USB key (showing up as slightly less due to the differences between how manufacturers measure a GB vs. how a computer does.)  

So, get back to me on the drive id's and then we can try the cloning again.  :)

---

### Post by Return Privacy on 2008-09-02
Hi again bytejuggler,
When I did the fdisk -lu, I did use sudo in front of it. And I tried it several times to make sure. With both the "old" and "new" drives, booted from the Live cd, it returned nothing at all. Not even the "old" drive information? 
But, remember when I first connected the "new" drive and the old and new drives and did the sudo fdisk -lu, the old drive is /dev/hda 40gb, and the new drive is /dev/hdb 320gb.
This IS correct, I checked it and wrote it down. (this was before I did the clone)
Now, when I try to do the gpart with the machine booted from the Live cd, it returns nothing at all. It is blank. This is with both drives connected to the ide cable. 
So, I had to boot the machine with the old original drive connected, and with the new drive connected with the jumper on slave. Yes, to answer your question, the drives are both ide drives, not sata. 
Here is the result of the gpart scan window like you told me to do. (it took me a while to figure out how to do a screen capture) I just don't know how to paste it in here, so I'll attach the image. 
As you may have assumed, I paid a guy to set up this ubuntu system on this original drive. It works well, but I want to clone this to the new drive. And I want to learn to do this myself. I really do appreciate all your help in this.

---

### Post by ByteJuggler on 2008-09-02
> **Return Privacy said:**
> Hi again bytejuggler,
When I did the fdisk -lu, I did use sudo in front of it. And I tried it several times to make sure. With both the "old" and "new" drives, booted from the Live cd, it returned nothing at all. Not even the "old" drive information? 
But, remember when I first connected the "new" drive and the old and new drives and did the sudo fdisk -lu, the old drive is /dev/hda 40gb, and the new drive is /dev/hdb 320gb.
This IS correct, I checked it and wrote it down. (this was before I did the clone)
Now, when I try to do the gpart with the machine booted from the Live cd, it returns nothing at all. It is blank. This is with both drives connected to the ide cable. 
So, I had to boot the machine with the old original drive connected, and with the new drive connected with the jumper on slave. Yes, to answer your question, the drives are both ide drives, not sata. 
Here is the result of the gpart scan window like you told me to do. (it took me a while to figure out how to do a screen capture) I just don't know how to paste it in here, so I'll attach the image. 
As you may have assumed, I paid a guy to set up this ubuntu system on this original drive. It works well, but I want to clone this to the new drive. And I want to learn to do this myself. I really do appreciate all your help in this.

OK, part of the confusion is probably my fault, my apologies -- I'd forgotten about the fact that IDE disks are these days also specified using the "/dev/sdx" naming convention rather than the "/dev/hdx" convention as was the case previously.  They changed that relatively recently in a kernel update and I'd totally forgotten about it.  

In any case, as you can see from your screenshot, your disks is showing up as /dev/sda and /dev/sdb, which is then the names you must use in the cloning "dd" command, even though your disks are in fact IDE disks.  As an aside, I must say, whoever set up your machine did a neat job, partitioning everything into seperate partitions, which is generally a good thing.

There remains one mystery to solve however:  Why the drives don't show up when you boot off the liveCD. For reference: You should boot up off the liveCD, with the drives connected normally as though you want to boot off the old hard disk (e.g. with the jumpers set so that new drive is set to slave and the old drive is set to master), but with the CDRom set as the first boot device in the BIOS.  So firstly, the drives should show up on powerup on the BIOS screen.  If they do not, then the LiveCD won't see them either.  Secondly, you should then enter your BIOS, and ensure/change the boot order so the machine will attempt a boot from the CD before falling back to the first hard disk.  Once thats done, try booting again from the liveCD, after which the disks should be visible.  (I'm guessing here that the disks have been invisible when booted from the liveCD due to some jumper/hdd connection problems/differences between when booted from the liveCD and when booted from the old hard disk.)

Aside: The reason you should boot off the liveCD when doing the cloning is to prevent problems due to having your filesystem mounted while cloning the disk.  It may be possible to successfully clone your disk even while you're booted from it, by e.g. possibly switching to single user mode and/or mounting the root filesystem read-only while booted from your old hard disk, but this is a slightly tortuous/complicated path I'd rather avoid unless there's no alternative...

---

### Post by Return Privacy on 2008-09-02
bytejuggler,
I think I stumbled on part of the problem. The WD drives use no jumper for master, so that is what I was going by. Then I noticed on the drive, it said no jumper master if single, and it DOES use a jumper for master when there are two or more devices on the ide channels. I think that is why there was confusion on the drives not showing up. This time I jumped the old drive as master, jumped the new drive as slave, and jumped the dvd/cd burner as slave. Now, it boots from the Live cd and DOES show both drives. The real confusing part now......look at the new screenshot I've attached. Now, the drives show up as /dev/hda  & /dev/hdd.........? Remember this is booted from the Live cd with both drives connected as though I was going to boot from the old drive (like you told me to do). 
I will wait to do anything until I hear back from you.
Thanks again
RP

---

### Post by ByteJuggler on 2008-09-02
Ok thats great.  Glad you got the jumper settings sorted out.  As for the liveCD displaying as /dev/hda and /dev/hdb, that's fine.  It just means the kernel on the LiveCD did not yet have the patch/change in where the naming convention for IDE disks was changed to also use the "/dev/sdx" naming convention.  Really, the naming convention does not matter, what matters is that you're consistent: If you're running a kernel that uses "/dev/hdx" naming, then you must use that same names in the "dd" command and if it's "/dev/sdx" naming, then you must use that etc.

So, then, according to the screenshot you've sent, your source disk (the 40GB one) is /dev/hda, and the target disk is /dev/hdd.  Therefore, your copy command would be:

```
sudo dd if=/dev/hda of=/dev/hdd
```

When it's finished it should report that 40GB has been copied.  

So then, I would suggest you boot with the liveCD, then try the above command and verify it copies all 40GB of the source disk (it should report that.)  Then power down the machine, remove the 40GB master from the machine, connect the new disk in its place as primary master (adjusting its jumper as needed and updating the BIOS if required), and then try booting off it, which touch wood, should work (again providing the copy went according to plan.)

---

### Post by Return Privacy on 2008-09-02
Hi bytejuggler,
I did as instructed, and here is a screen shot of what happened. As you see, it didn't work. Maybe you can tell why? I don't understand.

---

### Post by Return Privacy on 2008-09-02
bytejuggler,
On a whim, I did the sudo fdisk -lu command to see what it would say after the failed dd attempt. Here is a screen shot of what it says. Does this make any sense to you???

---

### Post by ByteJuggler on 2008-09-03
> **Return Privacy said:**
> Hi bytejuggler,
I did as instructed, and here is a screen shot of what happened. As you see, it didn't work. Maybe you can tell why? I don't understand.

OK... I/O error literally means "Input/Output" error.  It means "dd" had a problem either reading from the original disk or writing to the target disk in the process of performing the copy.  "dd" by default will abort the copy operation at the first sight of trouble (so that you won't think that things went OK when they in fact did not.) 

The implication of this is that you may already have trouble brewing on your old disk, which you've been lucky enough not to run into yet as noticable problems (possibly the bad spot is located somewhere harmless), or the other alternative as I mentioned is that possibly your new disk has problems (in which case you need to send it back.)  

We have to identify which one, and then deal with whichever case it is appropriately.  To identify which,  I suggest the following: Try to copy your source disk to the so-called "null device", which is guaranteed to "work" and so will not itself generate an error, thereby allowing us to determine definitively if the problem ocurred on the source/old disk or not.   As an aside: The "null device" is a file/device to which you can write any amount of information and have it discarded/ignored without error or side effect.  It is, as you can see, useful in situations like this. :)

The command to do that is (somewhat predictably):

```
sudo dd if=/dev/hda of=/dev/null
```

This will copy all the information from /dev/hda to /dev/null, which is the null device.  If you again get an I/O error at 2.1GB then it means the problem occurred on your old disk in reading, 2.1GB into the disk.  If so then technically speaking we'll be doing a little bit of data recovery here and will have to modify the "dd" command to ignore read errors, or possibly use a different command to do the copy.

If however the above command runs through to 40GB, then it means that original error you saw happened in trying to *write *to the *new disk* (at 2.1GB into the disk obviously.)  Then it means there's something wrong with the new disk, and you should RMA it/send it back.

Let me know the output of the above and I'll help you recover.   (Ask if there's anything you don't understand, by the way.)

---

### Post by ByteJuggler on 2008-09-03
> **Return Privacy said:**
> bytejuggler,
On a whim, I did the sudo fdisk -lu command to see what it would say after the failed dd attempt. Here is a screen shot of what it says. Does this make any sense to you???

Yes, I suppose in copying the first 2.1GB the system managed to copy the primary partition table (and the first 2.1GB of data), but has missed off the extended partition table somehow/for some reason. (If the copy operation had succeeded you should've seen pretty much identical partitions on both disks.)

---

### Post by Return Privacy on 2008-09-03
Hi bytejuggler,
I have to go watch nephews for a few hours, so I'll give it a try when I get back. Just to let you know, late last night I tried to do the sudo fsck /dev/hda, and it returned "fsck.ext2 device busy and something about possibly being opened or filesystem mounted?. It didn't run. So, I did fsck separately on each partition. hda1 said clean. hda2 returned that it was busy or could possibly be a zero length partition?, hda5 clean, hda6 clean, hda7 clean, hda8 returned error 2 with executing fsck.swap, hda9 clean.
I don't know if that tells you anything?
Again, when I get back later, I will try the copy again with the null command you gave me.
Thank you so much for your help in this, I really do appreciate it!
Rp

---

### Post by ByteJuggler on 2008-09-03
> **Return Privacy said:**
> Hi bytejuggler,
I have to go watch nephews for a few hours, so I'll give it a try when I get back. Just to let you know, late last night I tried to do the sudo fsck /dev/hda, and it returned "fsck.ext2 device busy and something about possibly being opened or filesystem mounted?. It didn't run. So, I did fsck separately on each partition. hda1 said clean. hda2 returned that it was busy or could possibly be a zero length partition?, hda5 clean, hda6 clean, hda7 clean, hda8 returned error 2 with executing fsck.swap, hda9 clean.
I don't know if that tells you anything?
Again, when I get back later, I will try the copy again with the null command you gave me.
Thank you so much for your help in this, I really do appreciate it!
Rp

No problem with helping.  

On fsck'ing:  Did you do this while booted from the liveCD or while booted from the hard disk?  I presume the liveCD?  Anyway, /dev/hda2 isn't checkable with fsck as it's not a partition - /dev/hda2 is the entry in the primary partition that links off to the "Extended" partition area (where the entries for hda5 etc. is stored.)  The error with /dev/hda8 is probably just because that's the swap partition and that likewise has no filesystem to check, so trying to check it is a bit nonsensical.  Anyway, that means that the filesystem checks came back essentially clean, which is good as far as it goes, but that doesn't neccesarily mean the entire disk surface is free from problems.  To establish that one would need to do a test that examines the entire disk surface and not just the filesystem/used parts of it (which is more or less what we'll get in rough fashion with the /dev/null copy.)

---

### Post by Return Privacy on 2008-09-03
Hi again bytejuggler,
I booted from the Live cd and went into gpart and selected the new drive and set it to format in ext3 and erase everything on it.

Then, I did the sudo dd if=/dev/hda of=/dev/null    command. This time it did about the same thing as before, it copied for 69 seconds, and said input output error reading. It copied that same 2.1 gb and stopped. I am attaching two screen shots of the terminal for you. Notice now how it has the /hda1 partition on the new disk, like before, but it also has a fat32 small partition also! That must have happened when I formated it to ext3? It said you HAVE to set the "disklabel" and I told it yes, before it would let me format to ext3. I thought I was doing a good thing by trying to format the new disc to get rid of the failed attempted copies before? I guess I should not have done that. Sorry. I've got another new wd 320gb disc still in the box I can use if you want me to. I bought 2 of them last week in preparation for this.

---

### Post by ByteJuggler on 2008-09-03
OK, the /dev/null test outcome means your 40GB has some issue, hopefully in an area of disk that's unused.  

Don't worry about having formatted and whatnot the other disk.  It doesn't matter, once the clone operation is (successfully) finished everything will be as it should be. 

OK, I'm going to hope that the error is minor, given that you still use the 40GB disk successfully, and thus suggest you try copying again using "dd" but just telling it to ignore read errors, so it skips the bad block:

```
sudo dd if=/dev/hda of=/dev/hdd conv=noerror
```

Does that complete?  This should probably take roughly 30 minutes or so, at a rough guess.  If it takes much longer (hours and hours) and/or you see lots of funny error messages then it's possible there's more difficulty than we thought and might have to employ another command.  Let me know what happens.

---

### Post by Return Privacy on 2008-09-03
ok bytejuggler,
I'm getting to think this is impossible? It didn't work again, and here is what the terminal said.
Did I mention that the original disc DOES still work and boot up? I don't understand what is happening? I hope you can figure it out.
rp

---

### Post by ByteJuggler on 2008-09-04
> **Return Privacy said:**
> ok bytejuggler,
I'm getting to think this is impossible? It didn't work again, and here is what the terminal said.
Did I mention that the original disc DOES still work and boot up? I don't understand what is happening? I hope you can figure it out.
rp

Hey RP,

No it's not impossible, I'm sorry you're running into such problems.  We'll get it done, I've done this type of migration many times, it's just that you've gut unexpected complications which is causing trouble.  

And yes, I know that your install is still working -- I've put that down to the fact that the disk problems are located in an area not used by your existing system, however I'm beginning doubt/wonder whether that assumption is wrong, and whether there may be another reason for the apparent disk I/O errors.  The only I can think of is that there's possibly some sort of driver/kernel difference that causes the liveCD to have trouble dealing with your disks even though your existing system has no problem.  And although we know there is a difference already (the liveCD uses /dev/hdx and your existing system uses /dev/sdx), I hasten to say that this possibility is probably nevertheless an unlikely scenario.  Even so, I think I'd like to check that possibility, and the way to do it, is to repeat the "/dev/null" test *from your existing system.*  If that succeeds with no errors then it means your existing installation can successfully read the entire disk while the liveCD can not for some reason, as we've seen.  I'll then know to try a different tack (use a different LiveCD possibly, or I'll go down the road of cloning the disk while booted off it, which I mentioned earlier as an option, but which is slightly more prone to a few problems and is trickier to execute)

So can you please **boot up from your existing hard disk, then issue the command:**

```
sudo dd if=/dev/hda of=/dev/null
```

Let me know what that outputs.

Finally, I'm sorry this is taking so long, but I **will** stay until this is done, I know it must be getting frustrating, but I want to reassure you that it is possible.  We just have to work through the issues one by one.  Hopefully this is also somewhat of an educational experience(?)  (It doesn't help that we appear to be in different timezones judging by posting patterns...)  Good luck!

---

### Post by ByteJuggler on 2008-09-04
If you see me online feel free to message me about this so we can get this resolved in real time (might be quicker than playing tennis over the forum.)

---

### Post by Return Privacy on 2008-09-04
Hi bytejuggler,
I am going to try to connect to your msn messenger in a minute from my mac, using a web based thing. It will be from a different name.
I booted from the original disc, and did the sudo dd if=/dev/hda of=/dev/null, and it said there was nothing named /dev/hda? So, I did the sudo fdisk -lu command you told me about and it listed the old and new drives as /dev/sda and /dev/sdb. So I did the sudo dd if=dev/sda of=/dev/null, and it returned the same 2.1gb copied and the same input output error. I attached the copy of the terminal window pasted to a text page.
By the way, I really, really do appreciate all you time helping me with this. I am learning a lot, which is what I want to do. I used to use norton ghost to do this in windows, but I really have a desire to switch to ubuntu and linux in general. I am eager to learn this.

---

### Post by ByteJuggler on 2008-09-04
Hey RP,

Sorry I actually went out not long after posting my offer for contact, so you wouldn't have found me online.  Anyway, I've also now added you onto my MSN (I presume the add request was from you... lol)

Anyway, you were right to use /dev/sda when you did the check, as your install uses that naming convention.  The fact that it stopped again at 2.1GB suggests to me that my original suspicion that there's some sort of problem developing with your original disk is likely correct, and that it is not just a software issue with the kernel on the liveCD that manifests as that 2.1GB problem.

So, that being the case, cloning your disk now becomes a little more work since "dd" isn't really happy to deal with read problems.  Hence we have to use another tool called GNU ddrescue, a "dd" like tool specifically made for recovering data from problem drives/dics.  Firstly install it, enter (from the booted liveCD):
```
sudo apt-get install gddrescue
```
Then we tell it to clone your disk, by default it will skip error areas and not try too hard to read them, and since you've not seen any actual problems in your install I think that's sufficient for us (if need be we can come back later and rerun ddrescue to have it try harder on the problem areas):

```
ddrescue /dev/hda /dev/hdb logfile.txt
```

Notice, "ddrescue" depends on the order of the parameters to establish what the source disk/file is and what the target disk/file is.  The ***first *** parameter is always the source, the ***second ***is always the target.  The third parameter is an optional "logfile" parameter which it uses to keep track of progress and which also allows it to be interrupted and then restarted without having to redo work already done.  This it does by consulting the logfile to see what's already been done when subsequently restarted after an interruption.

It will also output statistics about what it had done when it runs/finishes.  Please post that back here.  Also save/copy the "logfile.txt" file somewhere if possible (post/attach it here if you cant put it anywhere else, if it's not too big) so we can re-use it again if needed, as described above.

If everything goes to plan, after the above command your disk will have been sufficiently enough cloned for you to swap the new disk to being the master and for it to boot.  You're welcome to try that if the output from ddrescue doesn't seem too bad.  

Anyway, let me know what happens.

---

### Post by linuxguymarshall on 2008-09-04
I use Synaptic Norton Ghost when upgrading or my customers want a back up

---

### Post by Return Privacy on 2008-09-04
Hi bytejuggler,
I got home and tried to im you, but it says your offline. Anyway, I booted from the Live cd, and did the command "sudo apt-get install gddrescue" and it returns the message:

Reading package lists.......Done
building dependancy tree
reading state information.....Done
E: couldn't find package gddrescue

I tried it with out the "g", just the ddrescue and it returned the same message.
I double checked everything and it is typed exactly like you said. I will wait for further instructions

---

### Post by ByteJuggler on 2008-09-05
> **Return Privacy said:**
> Reading package lists.......Done
building dependancy tree
reading state information.....Done
E: couldn't find package gddrescue


Lol from one obstacle to the next.  Well hopefully it's educational??? :lolflag:  OK, so the above says it's not finding the package for installation for some reason. Do you know if you have network access while booted from the LiveCD? (I've assumed you have so far.) Obviously that would be a problem if you don't and the package is not on the CD.   OK, assuming you've got network access, perhaps the package is not yet in the package list (due to package list being out of date/only reflecting what's on the CD), so let's try updating the packages list first then, before installation, to ensure apt-get will find it when you try to install it:

```
sudo apt-get update
```

Then try the installation again:

```
sudo apt-get gddrescue
```

The name of the package is "gddrescue" btw, although there's another similarish tool/package which confusingly is actually called "ddrescue" which contains a command "dd_rescue".  I know.  Slightly confusig.  But be assured I want "gddrescue" however.  

As a complete alternative to the above which uses the package management system to install gddrescue, you can download the package (.deb file) manually from [here]("http://packages.ubuntu.com/hardy/gddrescue").  It doesn't have major external dependencies so you should be ableo to just install it directly by right-click->"Open with GDebi package manager".
 
Another alternative would be do download the [Ubuntu Rescue Remix ]("http://ubuntu-rescue-remix.org/")LiveCD which is guaranteed to have "gddrescue" installed by default.  The [download link]("http://ubuntu-rescue-remix.org/Download") is here.  If you don't have any joy with the above 2 options then please download the Ubuntu rescue remix as it'll be a useful thing to have around anyway.

---

### Post by Return Privacy on 2008-09-05
Hi again,
I just downloaded and burned the Ubuntu Rescue Remix CD. I booted from it, and will try to see if I can find the gddrescue on the disc and use that with the command you gave me?
RP

---

### Post by Return Privacy on 2008-09-05
ByteJuggler,
I am doing the "sudo ddrescue /dev/sda /dev/sdb logfile.txt" command from the Ubuntu Rescue Remix CD I downloaded. It worked fine until the 2.1gb again, then found errors on the original disc, spit out numbers and codes for a while, and then resumed. It is still going so I guess it is working ok? Yeah! I'll let you know if it does the whole disc, and if it will boot from the new disc or not.
I sent you an im but you're offline.

---

### Post by Return Privacy on 2008-09-05
Bytejuggler,
It was doing fine, at around 6gb the screen went blank. It still sounds like it is writing to the new disc though? I checked the monitor cables and it's ok. I moved the mouse, but the screen is still blank? I'm going to let it be for a while in case it's still writing.

---

### Post by ByteJuggler on 2008-09-05
> **Return Privacy said:**
> Bytejuggler,
It was doing fine, at around 6gb the screen went blank. It still sounds like it is writing to the new disc though? I checked the monitor cables and it's ok. I moved the mouse, but the screen is still blank? I'm going to let it be for a while in case it's still writing.

Probably just screen saver, and still working, just leave it be.  I'd leave this for a few hours if I was you, until the hard drive stops working probably.  You can also try pressing space if you want, or even press ctrl-c to stop it.  With ddrescue you can restart the process without losing previously done work, using the logfile. :)

BTW, do you have a USB flash drive?  If so perhaps we should have the logfile be written to that by default so it doesn't get lost.

---

### Post by ByteJuggler on 2008-09-05
> **Return Privacy said:**
> ... and then resumed....

Yes this is the whole point of ddrescue, to deal with problem disks basically.  :)  It'll finish if you let it.  :) But it might take a while.

---

### Post by Return Privacy on 2008-09-05
Hi again,
The screen won't come on by moving the mouse, but I'm letting it continue anyway. I put my ear up to the new drive and it is making very small sounds, I think it is writing?
It's been going for an hour and 15 minutes so far.
I'll let it go for several hours per your instructions. I'll get back to it later tonight. I will probably post again tomorrow night to let you know the outcome. I will be gone during the day tomorrow. I really hope you know how much I appreciate all your help with this. 
RP

---

### Post by Return Privacy on 2008-09-05
Hi,
I clicked send just about the time you sent the last. I do have a USB thumb drive I can use, but how do I write the logfile to the USB drive?
RP

---

### Post by ByteJuggler on 2008-09-05
> **Return Privacy said:**
> I really hope you know how much I appreciate all your help with this. 

No problem really, I'm just glad you've not given up on it!  Soon you'll be helping others here do similar things. :)

By the way your monitor going out might be some power save thing that's kicked in out of which its for whatever reason not resuming.    Anyway, if the HDD led is still on, then its likely still working and I'd leave it be.  It *should* finish and then leave the drive idling.  Alternatively we can restart the process with the screen on, and make sure to save the logfile somewhere permanent in case this happens again so you can resume without loss of work done later.

---

### Post by dudude on 2008-09-05
About a week ago I tried cloning a disk with Windows installed on. First I used Clonezilla, which I believe uses ntfsclone, and that gave me error messages (I think it was something about unreadable sectors). It finally finished, but the disk "clone" was only about 4 GB even though the information on the disk was about 40 GB.
I then tried ntfsclone off of the Ubuntu live CD with the same error messages. The resultant "clone" was also about 4 GB.
After that, I tried using dd to clone the disk, but that gave me the I/O error.

Finally, I tried copying the files directly via Nautilus, and there were no error messages.

I was trying to copy from the computer to an external hard drive.

I never did try copying to /dev/null, but I don't think the external drive has anything wrong with it.

Any ideas on what was happening?

---

### Post by ByteJuggler on 2008-09-05
> **dudude said:**
> Any ideas on what was happening?

Yes, in short, probably the same as with RP.  The normal clone tools are being thrown by Input/Output errors (I/O errors) causing them to abort at the 4GB mark which is probably where your disk has its first error.  Without doing some tests it's impossible to know whether the problem lies with your source or target disk.  I suggest you download the Ubuntu Rescue Remix and then try copying your source disk to /dev/null.  If the copy operation still runs into errors then there's a problem with your source disk.  If it copies successfully then there's a problem with your target disk. 

If there's a problem with your source disk, then boot with the Ubuntu Rescue remix and try to clone the disk using it, as described above, which will skip any badblocks on the disk surface and copy the rest of the disk.

---

### Post by dudude on 2008-09-06
> **ByteJuggler said:**
> Yes, in short, probably the same as with RP.  The normal clone tools are being thrown by Input/Output errors (I/O errors) causing them to abort at the 4GB mark which is probably where your disk has its first error.  Without doing some tests it's impossible to know whether the problem lies with your source or target disk.  I suggest you download the Ubuntu Rescue Remix and then try copying your source disk to /dev/null.  If the copy operation still runs into errors then there's a problem with your source disk.  If it copies successfully then there's a problem with your target disk. 

If there's a problem with your source disk, then boot with the Ubuntu Rescue remix and try to clone the disk using it, as described above, which will skip any badblocks on the disk surface and copy the rest of the disk.

Thanks for the information.

I can't currently get to the disks that were giving me the problems with the cloning, but I will try the copying to /dev/null when I get a chance.

---

### Post by Return Privacy on 2008-09-08
Hi all, 
First, I want to thank ByteJuggler publicly for all his help. He really had a lot of patience with me and hung in there until we got my problem figured out. 

ByteJuggler is THE only reason my drive is now cloned and working!

As you noticed regular dd wouldn't clone my drive, it stopped at 2.1gb every time. It didn't matter what you told it to do. There was an error reading past that on the original drive.
Bytejuggler had me download and burn a _Ubuntu Remix Rescue CD_. It has gddrescue on it. We booted from that CD, and used gddrescue to make the clone. It had to have the command to ignore errors anyway, and it copied.(a Live CD was tried, but it only had the standard dd on it)  I am using a brand new WD 320 (ide) caviar drive. The original drive was a WD 40 drive (old). No matter what we did, the new clone drive would not boot. Everything was there, bit for bit. We, actually Bytejuggler, tried everything to no avail. Did I mention he knows everything?...REALLY. Anyway, the only way the clone drive would boot is if it was jumped as "slave" and connected to the primary plug (end) on the 2 plug ide cable, with another (totaly blank, never formatted) drive on the secondary plug of the ide cable. And the blank drive had to be jumped as "master". I know what you are thinking.....it didn't matter what drive we used in place of the blank drive, it had to have something on the cable as a master. Obviously, the blank drive wasn't doing anything. The bios had to be set to boot from the second drive, hdd01. The first drive in the bios normally is hdd00. I set the first boot device to be hdd01, and the second boot device to be CDROM (which was on a separate ide cable by itself, and set to slave). 
So, the setup is: new clone drive is "slave" on primary plug of ide cable, with any blank or old used drive on the secondary plug of the ide cable, and set as "master".  Believe me we tried just having the new clone drive on a single ide cable by itself. And no matter how we jumped it, it would not boot. I don't remember all the different things we tried but it was "everything". Bytejuggler finally figured out that the problem exists with the new WD drive. For whatever reason, it will NOT boot by itself. It is something I will send to WD. Their website only says they support M$ installs so that should be of no help at all. 
Make no mistake, this new clone drive is a bit for bit copy of the old one. But there is something about the new WD drives that cause a problem with Ubuntu booting from them. 

Bytejuggler should come up with a way to do paid support for Ubuntu/linux, he IS that good!:guitar:

---

### Post by ByteJuggler on 2008-09-08
I'm just happy RP's setup is working, it was a rather trying case.  On the whole WD drive thing -- I might add that (as far as I can tell) it's something to do with the particular combination of hardware in the mix --  I've once or twice had similar problems making certain IDE drives play together on certain motherboards with certain WD drives.  Very confusing/frustrating when you run into something like this.

BTW RP, you can mark the thread as "Solved" by using the "Thread tools".

---

### Post by Return Privacy on 2008-09-09
Bytejuggler, I looked in "thread tools" but it only has "show printable version, email this thread, or subscribe to this thread". I wasn't the first post on this question. I just jumped in and asked the same type of question. 
:popcorn:

---

### Post by ByteJuggler on 2008-09-09
> **Return Privacy said:**
> Bytejuggler, I looked in "thread tools" but it only has "show printable version, email this thread, or subscribe to this thread". I wasn't the first post on this question. I just jumped in and asked the same type of question. 
:popcorn:

Ah of course you weren't...  my bad... ;)

---

### Post by dudude on 2008-09-10
What is the difference between the ddrescue and the gddrescue packages?

In the past I have usually just used either dd or dd_rescue to attempt to recover stuff, but I just skipped over gddrescue. I know that dd_rescue is faster than dd in some cases because it skips bad sectors, but is gddrescue the same/different better/worse?

---

### Post by ByteJuggler on 2008-09-10
> **dudude said:**
> What is the difference between the ddrescue and the gddrescue packages?

In the past I have usually just used either dd or dd_rescue to attempt to recover stuff, but I just skipped over gddrescue. I know that dd_rescue is faster than dd in some cases because it skips bad sectors, but is gddrescue the same/different better/worse?

gddrescue is better, as far as I know.  gddrescue is roughly equivalent in function to dd_rescue + dd_rhelp script.

---

### Post by uscpsycho on 2008-12-04
Sorry to bump this old thread, but it's good context for my questions.

I'm in the middle of trying to salvage a hard drive with ddrescue. The first time I ran it I had the same problem as RP with my screen going blank about 20 minutes into it. RP overcame the problem but never explained how. Did it just come back on on its own?

I also had a problem with the drive/enclosure combination I was using (target drive is in a USB enclosure). Turns out that the enclosure didn't play well with the drive and the combo just stopped working together. It got to the point where the drive wasn't even being recognized. I switched enclosures and things are running much more smoothly with the new combo.

At this point I'm not confident that the data copied with the first enclosure is good. Is that a possibility?

I used the log option when I ran ddrescue the first time and so now it seems like ddrescue is picking up where it left off. How do I make it start from scratch instead of picking up where it left off? Is starting from scratch even necessary or should I trust that the data copied during the first run is good?

When I ran ddrescue the second time it started with 18 errors, which is where it left off the first time around. However, the amount of rescued data was reset to zero. So those two bits conflict, did it actually start over or pick up where it left off?

First time poster here and appreciate all the helpful posts I've read in my short time exploring this site! Thanks in advance for your help!

---

### Post by ByteJuggler on 2008-12-04
> **uscpsycho said:**
> I'm in the middle of trying to salvage a hard drive with ddrescue. The first time I ran it I had the same problem as RP with my screen going blank about 20 minutes into it. RP overcame the problem but never explained how. Did it just come back on on its own?

I believe it did yes, after the command had finished, although I can't remember details.  I suspect it might've been screen/powersave, but that should normally resume on VT switch or keyboard action...

> 
I also had a problem with the drive/enclosure combination I was using (target drive is in a USB enclosure). Turns out that the enclosure didn't play well with the drive and the combo just stopped working together. It got to the point where the drive wasn't even being recognized. I switched enclosures and things are running much more smoothly with the new combo.

At this point I'm not confident that the data copied with the first enclosure is good. Is that a possibility?

It's possible although perhaps not that probable.  Even so, it's best to redo the clone I think, to eliminate doubt, if you can.

> 
I used the log option when I ran ddrescue the first time and so now it seems like ddrescue is picking up where it left off. How do I make it start from scratch instead of picking up where it left off? Is starting from scratch even necessary or should I trust that the data copied during the first run is good?

To be safe, I'd start from scratch.  To force a restart, just get rid of the logfile, which is how ddrescue decides what's been done already.

> 
When I ran ddrescue the second time it started with 18 errors, which is where it left off the first time around. However, the amount of rescued data was reset to zero. So those two bits conflict, did it actually start over or pick up where it left off?


Are you running it with a logfilename parameter every time you're running it?  Without a logfilename parameter it will restart from scratch everytime you run it.  (Or, of course, if a log file doesn't yet exist.)

> 
First time poster here and appreciate all the helpful posts I've read in my short time exploring this site! Thanks in advance for your help!

No problem.  Hope you get it sorted.

---

### Post by uscpsycho on 2008-12-05
> **ByteJuggler said:**
> I believe it did yes, after the command had finished, although I can't remember details.  I suspect it might've been screen/powersave, but that should normally resume on VT switch or keyboard action...
I figured it out. So if anyone is wondering about this and stumbles upon this thread... While doing ddrecover the screen will eventually go blank. Just press enter and the screen will come back to life with all the information you expect to see. Then it will go blank again. That's all there is to it.

> **ByteJuggler said:**
> It's possible although perhaps not that probable.  Even so, it's best to redo the clone I think, to eliminate doubt, if you can.
I didn't know how to start from scratch so I just ran it again with the same log file and it's been running for about two days now. I hope I don't have to start ddrescue over from scratch because it's taking an eternity.

> **ByteJuggler said:**
> To be safe, I'd start from scratch.  To force a restart, just get rid of the logfile, which is how ddrescue decides what's been done already.
Where is the logfile? Does it save it on the target (I hope so!) and where would it be? In the root directory?

Can I also specify a different logfile name to get it to start from scratch?

Just thought of something though... If it writes the log to the source drive that's very bad because writing to a failing drive can cause more damage. But if the logfile is written to the target then you're not ending up with an exact clone of the original drive?

I'm really concerned now because I'm getting lots of errors now (see below) and there is no writing on my target drive. So this log file is being written to the source drive? YIKES!


> **ByteJuggler said:**
> Are you running it with a logfilename parameter every time you're running it?  Without a logfilename parameter it will restart from scratch everytime you run it.  (Or, of course, if a log file doesn't yet exist.)
Yes. I'm using a logfile parameter. I've only run ddrescue twice, the first time where the process crapped out on account of the enclosure I was using and the second time which has been going for 36 hours or so.

Everything seemed to be going fine with the new enclosure, then after about 24 hours I started getting the problem I reported here: [http://ubuntuforums.org/showthread.php?t=769898](http://ubuntuforums.org/showthread.php?t=769898)

Basically an endless stream of errors that look like this:
(numbers.numbers) end_request: I/O error, dev hda sector (numbers)

The numbers on the left and right side increment by one on each line.  This has been going on for at least 12 hours now. I was once optimistic about success but if there's an error on every stinking sector then I'm a lot less optimistic.

---

### Post by ByteJuggler on 2008-12-05
> **uscpsycho said:**
> 
I didn't know how to start from scratch so I just ran it again with the same log file and it's been running for about two days now. I hope I don't have to start ddrescue over from scratch because it's taking an eternity.


Well depending on the command/switches you're using it may.  It does not mean that it needs to neccesarily.  The whole point of ddrescue is to copy the easily copiable stuff first, often providing you with a mostly complete/usable image (albeit with some "holes") more quickly than "dd" by effectively allowing you to skip this "hard" part on a first pass.  However, once that's done, ddrescue will go back and do its damndest (with appropriate switches, or try at least once on every re-run/restart) to get data off the bad sectors.  This can take ages but is by no means obligatory and does not mean that you don't already have a near "as good as it's gonna get" clone of your failing disk.  If you decide the bad sectors appear too bad to try to recover, then its your prerogative so skip it and check out what *has* been successfully recovered in the image so far. (Which  may already be the case if ddrescue's been at it 36h in your case.)

> 
Where is the logfile? Does it save it on the target (I hope so!) and where would it be? In the root directory?


Um, no, it's where you specify it to be, on the local filesystem (or for that matter, any other mounted filesystem...)

> 
Can I also specify a different logfile name to get it to start from scratch?


Of course, that's the whole point of the logfile parameter: that you're able specify a logfilename (and location) yourself  :)

> 
Just thought of something though... If it writes the log to the source drive that's very bad because writing to a failing drive can cause more damage. But if the logfile is written to the target then you're not ending up with an exact clone of the original drive?


No, you're not clear on how Linux/Unix filesystem/partitions work.  You can only ever write files to partitions (containign filesystems) if the filesystem on that partition is mounted somewhere in the filesystem tree.  An unmounted partition itself  looks like a big huge file and you therefore cant accidentally write anything to it (except if you directly write the the "partition file", but you're not doing that against your source/failing disk and youre only copying into your target/recovery disk/image using ddrescue, which is all legit.) So, if you're not mounting the original and target disks (are you?) then you can't possibly be writing the log to either the source or the target.  Therefore, their filesystems are not being written to and you're writing your log file to whatever is the current local root filesystem (or if you've mounted another disk/partition and are specifying a location on that disk/partition), e.g. in the path and filename you specify on the logfile parameter.

> 
I'm really concerned now because I'm getting lots of errors now (see below) and there is no writing on my target drive. So this log file is being written to the source drive? YIKES!

Yes. I'm using a logfile parameter. I've only run ddrescue twice, the first time where the process crapped out on account of the enclosure I was using and the second time which has been going for 36 hours or so.


Exactly what is the command line you're using?  What is the retry limit set to?  I get the feeling you're generally not fully understanding the meaning of the parameters you're giving the ddrescue command:  The logfile name parameter is a normal filesystem path, e.g. a folder path and filename.  If you leave off a path specifier, then the implication is that the name given is that its written in the current folder.  If you've just opened a terminal, then the current folder is the user's home folder (e.g. /home/user.) The "cd" changes the current folder.  This is standard lay of the land linux stuff.  Please enter "info man" and possibly "info info" at a command prompt (terminal) and/or search in the Ubuntu help for the info pages on the "ddrescue" command to clarify the command line parameters for the "ddrescue" command.

> 
Everything seemed to be going fine with the new enclosure, then after about 24 hours I started getting the problem I reported here: [http://ubuntuforums.org/showthread.php?t=769898](http://ubuntuforums.org/showthread.php?t=769898)

Basically an endless stream of errors that look like this:
(numbers.numbers) end_request: I/O error, dev hda sector (numbers)

The numbers on the left and right side increment by one on each line.  This has been going on for at least 12 hours now. I was once optimistic about success but if there's an error on every stinking sector then I'm a lot less optimistic.

The errors you're seeing is probably nothing to do with your enclosure, but everything to do with your failing disk.  The kernel (or dd) is reporting the read errors, that's all.  The numbers being in sequence means there's probably large areas/tracks that have been damaged. 

I suspect given that ddrescue's been at it 36h that your current image is probably as close to complete as you're likely gonna get it and all that's left is the hard work -- sectors that are damaged.  So you may want to skip that slog first, and just try mounting your recovered disk/partition (**_*readonly *_**of course!!!)to see whether it's mountable.  If it is you may already be able to rescue some of your files. If you then find that things are not good, you can always unmount the fileystem and restart ddrescue.

---

### Post by uscpsycho on 2009-02-12
Sorry to bump but figure it's best to pick up where I left off.

The ddrescue process literally took weeks before it ended. It got to the point where I would just check every few days and it was still going and going. I think it took three weeks or so.

There came a point at which I thought it might never finish but it finally did. However, the disk access light on my source drive (the damaged drive) is constantly on. Should that happen? I booted into Ubuntu from CD so there's no need for the hard drive to be accessed by the OS while idly sitting at the command line prompt. Is there?

As I explained before, my target drive was in a USB enclosure. What is the best way to check it now? Should I plug it into my laptop and see how much data was recovered and copy over critical files that were rescued? Are there any utilities I can run that would check to see if the drive is bootable? Or should I just plug it into the IDE and see if I can boot from it?

TIA

---

### Post by ByteJuggler on 2009-02-12
> **uscpsycho said:**
> Sorry to bump but figure it's best to pick up where I left off.

The ddrescue process literally took weeks before it ended. It got to the point where I would just check every few days and it was still going and going. I think it took three weeks or so.

There came a point at which I thought it might never finish but it finally did. However, the disk access light on my source drive (the damaged drive) is constantly on. Should that happen? I booted into Ubuntu from CD so there's no need for the hard drive to be accessed by the OS while idly sitting at the command line prompt. Is there?

As I explained before, my target drive was in a USB enclosure. What is the best way to check it now? Should I plug it into my laptop and see how much data was recovered and copy over critical files that were rescued? Are there any utilities I can run that would check to see if the drive is bootable? Or should I just plug it into the IDE and see if I can boot from it?

TIA

Normally you would not bother letting ddrescue run that long - it can usually get most of the data off in dramatically shorter timeframe.  I'm not sure why yours took so long, it may be that your dead disk is very damaged (the light staying on kind of suggests that.) 

I would now try to see if I can access the filesystem on the mirrored/cloned disk from another PC.  If it's a Windows filesystem on there, I would try from a Windows box and run chkdsk /f if required.  If it's linux then try mounting it from Linux.  You can also do just 

"sudo fdisk -lu" 

From a command prompt (whether liveCD or otherwise) to see all partitions on your system, which should include the recovered disk if its connected.  (So, do this first before connecting the USB disk, and again after, then you'll see what gets added as a result of connecting the drive, to the output.)

If the drive mounts without problems in the usb caddy and you can see all the files and so on, you might try removing the disk from the enclosure and swapping it with the failed disk, and see if you can boot from it. (It likely wont boot while in the caddy if Windows due to drivers differences and so on.  )

---

### Post by uscpsycho on 2009-02-14
> **ByteJuggler said:**
> Normally you would not bother letting ddrescue run that long - it can usually get most of the data off in dramatically shorter timeframe.  I'm not sure why yours took so long, it may be that your dead disk is very damaged (the light staying on kind of suggests that.) 

I would now try to see if I can access the filesystem on the mirrored/cloned disk from another PC.  If it's a Windows filesystem on there, I would try from a Windows box and run chkdsk /f if required.  If it's linux then try mounting it from Linux.  You can also do just 

"sudo fdisk -lu" 

From a command prompt (whether liveCD or otherwise) to see all partitions on your system, which should include the recovered disk if its connected.  (So, do this first before connecting the USB disk, and again after, then you'll see what gets added as a result of connecting the drive, to the output.)

If the drive mounts without problems in the usb caddy and you can see all the files and so on, you might try removing the disk from the enclosure and swapping it with the failed disk, and see if you can boot from it. (It likely wont boot while in the caddy if Windows due to drivers differences and so on.  )
OK - I plugged the USB enclosure with the target drive into my laptop and the results are mixed. A lot of files were saved but my Windows folder is inaccessible (I can see it but I get an error when I try to access it) and my Outlook pst files are nowhere to be found.

The absolute most important thing for me to recover were my PST files but they are huge and less likely to be recovered from a failure. I'm going to end up losing several weeks worth of email and calendar updates since my last backup. Unless there's something else I can try to salvage those files.

Any suggestions for recovering the PST files? Or making the clone drive bootable? Can I do a repair installation or anything like that?

---

### Post by ByteJuggler on 2009-02-16
> **uscpsycho said:**
> OK - I plugged the USB enclosure with the target drive into my laptop and the results are mixed. A lot of files were saved but my Windows folder is inaccessible (I can see it but I get an error when I try to access it) and my Outlook pst files are nowhere to be found.


What's the exact error message?

> **uscpsycho said:**
> 
The absolute most important thing for me to recover were my PST files but they are huge and less likely to be recovered from a failure. I'm going to end up losing several weeks worth of email and calendar updates since my last backup. Unless there's something else I can try to salvage those files.

Any suggestions for recovering the PST files? Or making the clone drive bootable? Can I do a repair installation or anything like that?

Well.  I would actually recommend to ideally get another disk same size as the one you cloned to and make another clone from the current one.  Reason being, you're now at a point where further attempts at recovery will need to either read/write to the disk to attempt filesystem repair, and/or you'll need a further area to which to dump recovered files retrieved from the clone. Having another disk gives you room to maneuver and try things with the option of rolling back and trying again.  Would this be possible?

I would (in no particular order) suggest (on a secondary clone, as explained above, so that if any particular attempt goes bad and makes things worse, then you can start again from your original clone.):
1.) Running Window's "chkdsk /f" on the recovered filesystem 
2.) Try something like "GetDataBack" or "FileScavenger", to see what they turn up. 
3.) Try one of the file carving recovery tools, e.g. [PhotoRec]("http://www.cgsecurity.org/wiki/PhotoRec") or [Magic rescue]("http://www.student.dtu.dk/~s042078/magicrescue/").  Photorec is included on the [Ubuntu Rescue Remix]("http://ubuntu-rescue-remix.org/").

---

