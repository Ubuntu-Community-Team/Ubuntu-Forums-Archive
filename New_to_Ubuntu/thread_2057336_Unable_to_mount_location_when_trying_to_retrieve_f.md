---
title: "Unable to mount location when trying to retrieve files"
date: 2012-09-13
forum: New to Ubuntu
---

### Post by susanbrown on 2012-09-13
I am trying to retrieve my files on a failed hard drive.  When I click  on my "500 GB Hard Disk: 485 GB Filesystem" Icon I get an "unable to  mount location" error with the following:

DBus error org.freedesktop.DBus.Error.NoReply: Did not  receive a reply. Possible causes include: the remote application did not  send a reply, the message bus security policy blocked the reply, the  reply timeout expired, or the network connection was broken.

---

### Post by androssofer on 2012-09-13
> **susanbrown said:**
> I am trying to retrieve my files on a failed hard drive.  When I click  on my "500 GB Hard Disk: 485 GB Filesystem" Icon I get an "unable to  mount location" error with the following:

DBus error org.freedesktop.DBus.Error.NoReply: Did not  receive a reply. Possible causes include: the remote application did not  send a reply, the message bus security policy blocked the reply, the  reply timeout expired, or the network connection was broken.

if its a failed hard drive, then mounting it probably wont work :-(.

you could look into data recovery programs that will retrieve the files without mounting it..

there is info [here]("https://help.ubuntu.com/community/DataRecovery")

---

### Post by susanbrown on 2012-09-13
I clicked your link - and it says I can use a "An Ubuntu Desktop CD."  I thought that was what I was using.

---

### Post by androssofer on 2012-09-13
Thats the first step.. that allows you to do the rest. 

is the partition a windows partition? Linux? or just a file storage HDD?

---

### Post by susanbrown on 2012-09-13
I don't know how to answer your question.  I don't have these technical skills.  It is the hard drive/disk located on my HP Pavilion laptop.  

Something happened and my bios hard drive diagnosis said a hard disk 303 or 330 error. and that my hard drive was failing or failed.

---

### Post by susanbrown on 2012-09-13
It is windows 7.

---

### Post by androssofer on 2012-09-13
> **susanbrown said:**
> It is windows 7.

this means the partition will be ntfs.


unfortunately you cant recover ntfs from bad sectors with Linux without a rather annoying work around.

Although I may be wrong. 

if you can get an external hard drive.. you can image the drive onto that. The do what is called "zeroing" on the HD and it should clear the bad sectors. (usually what causes the 303 error). then put the image back onto the formerly broken hard drive. 

**note** that hard drives usually move data if they detect a bad sector. a 303 error usually indicates they have run out of good sectors to move it to. so might be worth getting a new HD.. and recovering what you can from the broken 1. instead of repairing it.. 

but the repair is worth a try first I guess.. provided you can get an external HD?

---

### Post by susanbrown on 2012-09-13
Ok - so I need to get a 500gb external hard drive (same size as the one on the computer) - right?

And then how do I do this zeroing?

---

### Post by susanbrown on 2012-09-13
I have no problem getting a total new hard drive - so If I can recover files via zeroing with an external hard drive - will then get a new internal hard drive.

---

### Post by androssofer on 2012-09-13
> **susanbrown said:**
> I have no problem getting a total new hard drive - so If I can recover files via zeroing with an external hard drive - will then get a new internal hard drive.

personally I would get a new internal HD, then get a usb Harddrive adaptor, and put the old broke 1 into that. Then recover the files from it. Then try and fix it. 

That way if you fix the old 1 you get a new internal HD and an external 1 for the price of a new internal and the adaptor. Which is cheaper than a new internal and external HD.. :-)

but if you can borrow an external, then use it and just buy a new internal once you have imaged the old 1.. 

also go here:

[http://partedmagic.com/doku.php?id=start](http://partedmagic.com/doku.php?id=start)

its a linux distro specifically for recovering partitions, so has all the tools installed for you. It boots the same as ubuntu would from a live cd or usb...

---

### Post by susanbrown on 2012-09-13
Thanks.  I have an external hard drive adapter so i will buy a hard drive for internal use.  then I will follow the link at partedmagic and go from there.  thanks.  If I get stuck, can I continue to ask you questions on this post ?

---

### Post by androssofer on 2012-09-13
> **susanbrown said:**
>  If I get stuck, can I continue to ask you questions on this post ?

But of course :-)

---

### Post by susanbrown on 2012-09-13
Ok.  Just bought an internal hard drive.  Going to go to the link you gave.  If I need help - can I come back here and ask you?

---

### Post by susanbrown on 2012-09-13
Sorry - posted again, without realizing my prior post actually posted.  Thanks.

---

### Post by susanbrown on 2012-09-13
So just for clarification.  I should use partedmagic to recover files - once I put in the new internal drive and have the old one connected via the adapter????

---

### Post by susanbrown on 2012-09-13
Which option from partedmagic should i pick.
 
***Most people will only need this file:***
[pmagic_2012_09_12.iso]("http://sourceforge.net/projects/partedmagic/files/partedmagic/Parted%20Magic%202012_09_12/pmagic_2012_09_12.iso/download") (md5sum: d17e92707fa6480bd48f96b4a1bca471)

 
***This file is for machines older than a Pentium III class, such as an i586 or a PII with only one processor.***
[pmagic_2012_09_12_i486.iso]("http://sourceforge.net/projects/partedmagic/files/partedmagic/Parted%20Magic%202012_09_12/pmagic_2012_09_12_i486.iso/download") (md5sum: e32a76d4b517d6186df4f7a22338e1a8)

 
***This file has an X86_64 kernel which is useful for rescue tasks on x86_64 machines. [COLOR=#ff0000]This is not an x86_64 OS[/COLOR]. For example, you cannot chroot into an x86_64 machine without this kernel:***
[pmagic_2012_09_12_x86_64.iso]("http://sourceforge.net/projects/partedmagic/files/partedmagic/Parted%20Magic%202012_09_12/pmagic_2012_09_12_x86_64.iso/download") (md5sum: 11986d94d1600e1fe0f480f70c17cdd6)

---

### Post by androssofer on 2012-09-14
> **susanbrown said:**
> Which option from partedmagic should i pick.
 
***Most people will only need this file:***
[pmagic_2012_09_12.iso]("http://sourceforge.net/projects/partedmagic/files/partedmagic/Parted%20Magic%202012_09_12/pmagic_2012_09_12.iso/download") (md5sum: d17e92707fa6480bd48f96b4a1bca471)

 
***This file is for machines older than a Pentium III class, such as an i586 or a PII with only one processor.***
[pmagic_2012_09_12_i486.iso]("http://sourceforge.net/projects/partedmagic/files/partedmagic/Parted%20Magic%202012_09_12/pmagic_2012_09_12_i486.iso/download") (md5sum: e32a76d4b517d6186df4f7a22338e1a8)

 
***This file has an X86_64 kernel which is useful for rescue tasks on x86_64 machines. [COLOR=#ff0000]This is not an x86_64 OS[/COLOR]. For example, you cannot chroot into an x86_64 machine without this kernel:***
[pmagic_2012_09_12_x86_64.iso]("http://sourceforge.net/projects/partedmagic/files/partedmagic/Parted%20Magic%202012_09_12/pmagic_2012_09_12_x86_64.iso/download") (md5sum: 11986d94d1600e1fe0f480f70c17cdd6)

if its a relatively new computer.. (with windows 7 i'd assume so)

the first option: 

[pmagic_2012_09_12.iso]("http://sourceforge.net/projects/partedmagic/files/partedmagic/Parted%20Magic%202012_09_12/pmagic_2012_09_12.iso/download")

---

### Post by mips on 2012-09-14
Ideally you should use [GNU ddrescue]("http://www.gnu.org/software/ddrescue/ddrescue.html") to image that failed drive to a file and then use recovery tools on the image file to extract data if possible. it's on the parted magic cd in case you are wondering.

---

### Post by shreepads on 2012-09-14
> **mips said:**
> Ideally you should use [GNU ddrescue]("http://www.gnu.org/software/ddrescue/ddrescue.html") to image that failed drive to a file and then use recovery tools on the image file to extract data if possible. it's on the parted magic cd in case you are wondering.

This...

- Connect both drives (internal/ external)

- Boot from PartedMagic CD

- Create a bit level copy of the old drive to new using ddrescue. You may have to run it several times using a logfile as outlined in the DataRecovery doc. Tweak the part mentioned below, replace '/dev/hda1' & 'imagefile' with the old and new drive devices (so /dev/sda, for example, not /dev/sda1) respectively.

> 
First you copy as much data as possible, without retrying or splitting sectors: 

ddrescue --no-split /dev/hda1 imagefile logfile  

Now let it retry previous errors 3 times, using uncached reads: 

ddrescue --direct --max-retries=3 /dev/hda1 imagefile logfile  

If that fails you can try again but retrimmed, so it tries to reread full sectors: 

ddrescue --direct --retrim --max-retries=3 /dev/hda1 imagefile logfile  

- Note that unless you are booting from a USB stick with persistence, 'logfile' (which is essential to the process) may grow to consume a lot of memory AND will be lost if you need to restart halfway thru. So try to boot from a USB stick with persistence if possible...

- Once you have the new drive created to the limits that ddrescue supports, you should have a workable drive or one with a few file system (rather than disk) errors that can be checked using other tools

See this:
[http://www.gnu.org/software/ddrescue/manual/ddrescue_manual.html](http://www.gnu.org/software/ddrescue/manual/ddrescue_manual.html)

---

### Post by susanbrown on 2012-09-14
ok - will try your instructions.

---

