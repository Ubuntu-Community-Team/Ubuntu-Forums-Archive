---
title: "setting permissions for USB flashdrive"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by myotis on 2008-08-10
I am trying to use Unison to sync to a USB flash drive and getting a failed to set permissions error.

From the forum, I have found what seems to be a solution but as you can see below I seem to have a optionerror which I cannot identify.

graham@T42-Linux:~$ sudo chown graham /media/LEXAR -R, --recursive
chown: invalid option -- ,

I assume this is what I should be doing, to allow Unison to write to the root and subdirectories of the USB, but obviously there is something I am missing.

Can any one help.

Many thanks,

Graham

---

### Post by ajmorris on 2008-08-10
> **myotis said:**
> I am trying to use Unison to sync to a USB flash drive and getting a failed to set permissions error.

From the forum, I have found what seems to be a solution but as you can see below I seem to have a optionerror which I cannot identify.

graham@T42-Linux:~$ sudo chown graham /media/LEXAR -R, --recursive
chown: invalid option -- ,

I assume this is what I should be doing, to allow Unison to write to the root and subdirectories of the USB, but obviously there is something I am missing.

Can any one help.

Many thanks,

Graham

For your command, try this small modification:
```
sudo chown -R graham /media/LEXAR
```

---

### Post by myotis on 2008-08-10
> **ajmorris said:**
> For your command, try this small modification:
```
sudo chown -R graham /media/LEXAR
```

Thanks, that certainly ran without errors in terminal, but still not working in Unison.  I now see the full error in unison is:

Documents
Failed to set permissions of file /media/LEXAR/T42Docs/.unison.Documents.d0ba218a117cf7dd8077fc7cc64aa6e5.unison.tmp/TimeTo/timedata.x08 to rw-r--r--: the permissions was set to rw------- instead. The filesystem probably does not support all permission bits. You should probably set the "perms" option to 0o1733 (or to 0 if you don't need to synchronize permissions).

The bulk of the error ran off the screen and I didn't realise it was there.  I have tried changing permissions in Nautilis which allows me to change them, but then reverts back to no access when I reopen nautilis.

The properties say the flash drive is formatted as MSDOS (originally used on Windows and I want to move files between Ubuntu and XP).

Graham

---

### Post by northern lights on 2008-08-10
```
sudo chmod -R 664 /media/LEXAR/
```would theoretically set permissions to rw-r--r--

You can't do that on a FAT formatted drive though. What's the filesystem on the flashdrive?

---

### Post by myotis on 2008-08-10
> **northern lights said:**
> ```
sudo chmod -R 664 /media/LEXAR/
```would theoretically set permissions to rw-r--r--

You can't do that on a FAT formatted drive though. What's the filesystem on the flashdrive?

Ah, well maybe this is the answer, I'm not sure exactly but it will be FAT 16 I assume, Ubuntu just identifies it as MSDOS format.

I guess the solution for keeping Ubuntu and XP in sync is maybe more complex than I hoped.

Thanks,

Graham

---

### Post by northern lights on 2008-08-10
> **myotis said:**
> Ah, well maybe this is the answer, I'm not sure exactly but it will be FAT 16 I assume, Ubuntu just identifies it as MSDOS format.

To find out for certain, run```
sudo fdisk -l
```with a lower-case L and post the output.

---

### Post by myotis on 2008-08-10
> **northern lights said:**
> To find out for certain, run```
sudo fdisk -l
```with a lower-case L and post the output.

Yep, loks like FAT16

255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4533    36411291    7  HPFS/NTFS
/dev/sda2           14023       14593     4581360   12  Compaq diagnostics
Partition 2 does not end on cylinder boundary.
/dev/sda3            4534       14022    76220392+   5  Extended
/dev/sda5            4534       13630    73071621   83  Linux
/dev/sda6           13631       14022     3148708+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 519 MB, 519569408 bytes
129 heads, 32 sectors/track, 245 cylinders
Units = cylinders of 4128 * 512 = 2113536 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         246      507376    4  FAT16 <32M
Partition 1 has different physical/logical endings:
     phys=(249, 128, 32) logical=(245, 106, 32)


Graham

---

### Post by northern lights on 2008-08-10
mkey. Then chmodding is out of the question.

You have several options. For once, you could format the drive as ext2/ext3, setup unison and install ext2/ext3 support in your Windows OS.

Is the syncing going to be unidirectional only?

---

### Post by myotis on 2008-08-10
> **northern lights said:**
> mkey. Then chmodding is out of the question.

You have several options. For once, you could format the drive as ext2/ext3, setup unison and install ext2/ext3 support in your Windows OS.

Is the syncing going to be unidirectional only?

Ok thanks. It would need to be bidirectional.

Currently I use a 16gb USB flashdrive to keep 3 XP boxes and a MacBook Pro in sync (SyncbakSE on XP and Chronosync on the Mac). I sync everything onto the USB because I find it handy(sometimes essential)  to have all my files/reference material etc with me when I visit clients, so it needs to be a native Windows solution.

I am dual booting two of the XP boxes into Ubuntu, with the intention of replacing XP with Ubuntu. I will be stuck with one XP box,  which is my University machine, and will need to keep dual booting because some of my programs are Windows only.

At the moment, I am just experimenting with this USB stick and some dummy files before I try get it working for real.

Is this a Unison issue, or simply a Linux issue?

Graham

---

### Post by SlalomMan on 2008-08-10
I'm not sure how to help you with this, but I have a similar issue: my FAT microSD doesn't give me permission to edit files; the only thing I can do is run "gksudo nautilus" to edit files on there.

Have you tried running Unison as a super user?

---

### Post by northern lights on 2008-08-10
> **SlalomMan said:**
> the only thing I can do is run "sudo nautilus" to edit files on therePlease _never_ run graphical apps with 'sudo'. If they need to be run as superuser, use ```
gksu GRAPHICAL APP
```
For references, read [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by SlalomMan on 2008-08-10
I can't catch a break with that, can I? Haha...

Thanks for pointing it out, though.

---

### Post by myotis on 2008-08-10
> **SlalomMan said:**
> I'm not sure how to help you with this, but I have a similar issue: my FAT microSD doesn't give me permission to edit files; the only thing I can do is run "gksudo nautilus" to edit files on there.

Have you tried running Unison as a super user?

I'm having no problems reading and writing files to the USB flash drive or moving files around with OpenOffice/Nautilis its just with Unison I am having this problem :-(

Graham

---

### Post by myotis on 2008-08-11
Can I unmask these permissions  by addding this line to the ftstab file


/dev/sdb       /media/LEXAR     vfat umask=000 0 0

I don't know enough about this to know whether it is likely to cause problems or indeed will work, but its what I have gleaned from my searches.

Graham

---

### Post by myotis on 2008-08-25
Well, for reasons I don't understand, without me doing anything specific I am no longer having this permission problem.

Graham

---

### Post by borobudur on 2008-09-17
Check the solution of Toufik in this thread: [http://ubuntuforums.org/showthread.php?t=893365](http://ubuntuforums.org/showthread.php?t=893365)

Had the same problem with Unison and this works perfect for me!

---

### Post by myotis on 2008-09-17
> **borobudur said:**
> Check the solution of Toufik in this thread: [http://ubuntuforums.org/showthread.php?t=893365](http://ubuntuforums.org/showthread.php?t=893365)

Had the same problem with Unison and this works perfect for me!

Thanks, I will check this out, but for now as Hardy won't work with Skype, I have had to go back to Windows :-(

Graham

---

### Post by northern lights on 2008-09-17
I was under the impression Skype works with Hardy. How doesn't it?
I don't use it and don't like it, but I thought it worked.

It's been migrated to medibuntu repositories, did you try installing from there at the time?

P.S. Didn't think this archeology would ever get a response. Well, mistaken.

---

### Post by borobudur on 2008-09-17
Back to Windows!?!? Don't do that!!

I have skype and google-earth on hardy running. No problem! Even my webcam works fine with skype.

---

### Post by Orange_and_Green on 2008-09-17
> **myotis said:**
>  for now as Hardy won't work with Skype, I have had to go back to Windows :-(

Hi :)
I am reading on the newsgroups that skype did have a few problems just after Hardy was released, but the new updates seem to have fixed everything. Have you tried downloading the latest version (2.0.0.72)?

Cheers:KS

---

### Post by myotis on 2008-09-17
> **northern lights said:**
> I was under the impression Skype works with Hardy. How doesn't it?
I don't use it and don't like it, but I thought it worked.

It's been migrated to medibuntu repositories, did you try installing from there at the time?

P.S. Didn't think this archeology would ever get a response. Well, mistaken.

The webcam. 

Yes, tried all the options (including all three Medibuntu install options, but I didn't do a custom compile, as one person suggested), bought a new webcam  several threads started by me in this forum and Skype forums (largely unanswered) but conclusions from others seemed to be that there was a bug in either Skype or Hardy and I would just have to wait for it to be fixed. Gave up after weeks of trying.

So now just waiting, aS I could no longer afford the time, espacially as I was going through a phase of everything I tried (ie the USB question here, plus Broadband modem issues) to get working failed.

Eventually, I gave up with it all

Graham

---

### Post by myotis on 2008-09-17
> **borobudur said:**
> Back to Windows!?!? Don't do that!!

I have skype and google-earth on hardy running. No problem! Even my webcam works fine with skype.

Not for me it doesn't, but its specifically the webcam that is the problem.

Graham

---

### Post by myotis on 2008-09-17
> **Orange_and_Green said:**
> Hi :)
I am reading on the newsgroups that skype did have a few problems just after Hardy was released, but the new updates seem to have fixed everything. Have you tried downloading the latest version (2.0.0.72)?

Cheers:KS

I've only ever had that version, but also tried the three Medibuntu options, plus a whole list of suggestions form other threads.

However, for now I have had abandon it, and until I recover the time I have lost over the last few months trying to get things to work (the majority I have say were eventually fixed)I need to get on and do some work. I shall come back to it in a few months.

Graham

---

