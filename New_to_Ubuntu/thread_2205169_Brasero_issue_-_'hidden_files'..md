---
title: "Brasero issue - 'hidden files'."
date: 2014-02-12
forum: New to Ubuntu
---

### Post by charmingnathan2 on 2014-02-12
Hello everyone,

I am quite new to Ubuntu, and have run into this problem, which I am sure is straightforward to more experienced users.

I burnt some pictures to a CD-R, then went to burn some .mp3's; before doing so I received a message stating something about it wasn't advisable to do so, and my previous session may not be visible - I did this sometime ago, so my memory has faded somewhat.

The issue is (as you can probably guess), the .mp3's can be detected, the pictures cannot.

I have even tried using Easy Recovery within a Windows environment to attempt to save the pictures, but not even this software detects them (Easy Recovery is a data recovery software).

I'd really like these pictures back, any ideas please?

For your information, I am using an old version of both Ubuntu and Brasero, namely 9.10 The Karmic Koala and 2.28.2.

I'd really appreciate your help in resolving this.

Thank you.

---

### Post by tomearp on 2014-02-12
You should be able to mount the previous sessions with the mount command.

I don't have a multisession cd around anywhere to try it but something like this will probably work:
```
sudo mount /dev/cdrom /mnt/somedir -o session=0
```
and you can try with increasing numbers to mount the different sessions

---

### Post by whitesmith on 2014-02-12
> **charmingnathan2 said:**
> I have even tried using Easy Recovery within a Windows environment to attempt to save the pictures, but not even this software detects them (Easy Recovery is a data recovery software).Windows applications normally can't be used as a recovery tool with *nix files, and their use frequently corrupts data beyond recovery. If nothing else works, use a Live CD (or USB) of the same version used when burning and attempt recovery from that.

---

### Post by Dennis N on 2014-02-13
It's possible you burned the pictures as a data CD project, then afterward tried to add the mp3s but chose audio CD project.  If this is what happened, your pictures were erased when you burned the audio CD.

---

### Post by charmingnathan2 on 2014-02-19
> **Dennis N said:**
> It's possible you burned the pictures as a data CD project, then afterward tried to add the mp3s but chose audio CD project.  If this is what happened, your pictures were erased when you burned the audio CD.

Hello Dennis N, whitesmith, and tomearp for your replies, I shall try your suggestions.

Regarding what you state Dennis N., I wouldn't have thought that was likely or even technically possible, even if I had burnt the pictures as a Data C.D. Project - which I can't remember, but probably did - as the disks I were using were C.D.- R.'s?

Just a thought...

As far as whitesmith's comment is concerned, I thought Easy Recovery could detect all files - even if Widows couldn't identify them, obviously I was wrong on that!

I appreciate your help, thanks, and will let you know how I get on.

---

### Post by charmingnathan2 on 2014-03-06
> **tomearp said:**
> You should be able to mount the previous sessions with the mount command.

I don't have a multisession cd around anywhere to try it but something like this will probably work:
```
sudo mount /dev/cdrom /mnt/somedir -o session=0
```
and you can try with increasing numbers to mount the different sessions

Tomearp,

Thanks for your advice.

I have tried today using the command you have offered, but get an error, which is probably a syntax problem, rather than anything else!!!? I have assumed that "somedir" is meant to be replaced with the actual directory of where the C.D. rom is located?

I have also tried leaving "somedir" in and get essentially, the same error message, stating that the directory does not exist:

nathan@nathan-desktop:~$ nathan@nathan-desktop:~$ sudo mount /dev/cdrom /mnt/media/cdrom0 -o session=0mount: mount point /mnt/media/cdrom0 does not exist

I should state that the C.D. R.O.M. is working, and the disk and some of its contents are readily detected by Ubuntu 9.10.

What am I doing wrong?

Nathan.

---

### Post by tomearp on 2014-03-06
/mnt/somedir is the location where you would like to mount the cdrom. It can be anywhere you like (within reason, an empty directory is best). If the directory doesn't exist you will need to create it first:
```
mkdir /mnt/cdrom
```
If it says permission denied then put sudo on the front of it

---

### Post by charmingnathan2 on 2014-03-06
> **tomearp said:**
> /mnt/somedir is the location where you would like to mount the cdrom. It can be anywhere you like (within reason, an empty directory is best). If the directory doesn't exist you will need to create it first:
```
mkdir /mnt/cdrom
```
If it says permission denied then put sudo on the front of it

I tried that Tomearp, and did have to put sudo in front of the command.

However, it still wouldn't let me create the Directory - not that I could find or it would admit to! Anyway, I created a directory on the Desktop instead using a right-click of the mouse, called C.D. R.O.M. and tried your command again, this was the result:

sudo mount /home/nathan/Desktop/cdrom /mnt/cdrom -o session=0
mount: /home/nathan/Desktop/cdrom is not a block device

Any ideas please?

---

### Post by tomearp on 2014-03-06
The device you want to mount comes first, then the empty directory you want to mount it to, e.g.:
```
sudo mount /dev/cdrom /home/nathan/Desktop/cdrom -o session=0
```

---

### Post by charmingnathan2 on 2014-03-07
> **tomearp said:**
> The device you want to mount comes first, then the empty directory you want to mount it to, e.g.:
```
sudo mount /dev/cdrom /home/nathan/Desktop/cdrom -o session=0
```

Thanks Tomearp for that, the output I get from that command is as follows:

nathan@nathan-desktop:~$ sudo mount /dev/cdrom /home/nathan/Desktop/cdrom -o session=0
mount: special device /dev/cdrom does not exist

Any ideas?

---

### Post by tomearp on 2014-03-07
If you put some other CD in the drive does it auto mount and can you browse the contents in Nautilus? 
If so, if you open a terminal and issue mount with nothing else after it you'll get a list of currently mounted drives etc, the bottom entry should be the CDROM drive.
It'll be /dev/something on /media/something with some other stuff after it. The /dev/something is your CDROM drive and you can use that in the other mount command.

Sorry for the vague instructions, not in front of a computer right now, typing on a phone is rubbish!

---

### Post by charmingnathan2 on 2014-03-12
> **tomearp said:**
> If you put some other CD in the drive does it auto mount and can you browse the contents in Nautilus? 
If so, if you open a terminal and issue mount with nothing else after it you'll get a list of currently mounted drives etc, the bottom entry should be the CDROM drive.
It'll be /dev/something on /media/something with some other stuff after it. The /dev/something is your CDROM drive and you can use that in the other mount command.

Sorry for the vague instructions, not in front of a computer right now, typing on a phone is rubbish!

I have no idea as to what Nautilus is and cannot find it! If I put a C.D. into the drive, it not only spins up, and Ubuntu reads it contents, but opens a window automatically to display them.

I've tried doing what I think you wanted me to do, (open a terminal and issue mount with nothing else after it), and get this result:

nathan@nathan-desktop:~$ sudo mount /dev/cdrom
[sudo] password for nathan: 
mount: can't find /dev/cdrom in /etc/fstab or /etc/mtab
nathan@nathan-desktop:~$ 

I'll let you off the vague instructions using your phone (they are awful to use to send long sentences), if you accept my apology for lack of knowledge in this subject! :(

---

### Post by sotiris2 on 2014-03-13
I can't help you a lot but when he said issue mount with nothing after it he meant without any option as in 

mount 

I didn't even have to use sudo.

---

### Post by charmingnathan2 on 2014-03-14
> **sotiris2 said:**
> I can't help you a lot but when he said issue mount with nothing after it he meant without any option as in 

mount 

I didn't even have to use sudo.

Thanks very much sortiris2!

I followed your advice, and as you and Tomearp suggested, I did receive a list which gave me the drive allocation code I required, listed as "sr0", so I entered it, and this is what I got:

nathan@nathan-desktop:~$ sudo mount /dev/sr0 /mnt/cdrom -o session=0 (the command line I entered, which gave...)
mount: block device /dev/sr0 is write-protected, mounting read-only
nathan@nathan-desktop:~$ 

I hope this is some form of 'progress'? The C.D. R.O.M. which has the pictures on which I want to try and retrieve is a C.D. - R.

So, what's next?

---

### Post by tomearp on 2014-03-14
Thanks for helping out sotiris2, been moving offices the last couple of days so haven't been anywhere near my computer.

That output looks good, you should hopefully see some files in /mnt/cdrom. Now you can try looking at different sessions.

First you need to unmount it:
```
sudo umount /dev/sr0
```
Then try incrementing the session number and remounting, e.g.:
```
sudo mount /dev/sr0 /mnt/cdrom so session=1
```
Then look again in /mnt/cdrom, hopefully you'll see some different files.

---

### Post by charmingnathan2 on 2014-03-18
> **tomearp said:**
> Thanks for helping out sotiris2, been moving offices the last couple of days so haven't been anywhere near my computer.

That output looks good, you should hopefully see some files in /mnt/cdrom. Now you can try looking at different sessions.

First you need to unmount it:
```
sudo umount /dev/sr0
```
Then try incrementing the session number and remounting, e.g.:
```
sudo mount /dev/sr0 /mnt/cdrom so session=1
```
Then look again in /mnt/cdrom, hopefully you'll see some different files.

Emphasis on the word hopefully there, I think, Tomearp!

Okay, I did see the files in the cdrom folder as you suggested, that are currently on the C.D., but not the ones I wanted, of course. So I entered the code you suggested, and this is what I saw after pressing return:

nathan@nathan-desktop:~$ sudo mount /dev/sr0 /mnt/cdrom so session=1
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
nathan@nathan-desktop:~$ sudo mount /dev/sr0 /mnt/cdrom so session=2
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

Answers on a postcard?!

---

### Post by tomearp on 2014-03-18
Sorry, typo on the phone,
```
sudo mount /dev/sr0 /mnt/cdrom -o session=1
```
will work better!

---

### Post by charmingnathan2 on 2014-03-19
> **tomearp said:**
> Sorry, typo on the phone,
```
sudo mount /dev/sr0 /mnt/cdrom -o session=1
```
will work better!

Actually Tomearp, no it won't/didn't!!! Tried changing session numbers too...

nathan@nathan-desktop:~$ sudo mount /dev/sr0 /mnt/cdrom -o session=1
[sudo] password for nathan: 
mount: block device /dev/sr0 is write-protected, mounting read-only
nathan@nathan-desktop:~$ sudo mount /dev/sr0 /mnt/cdrom -o session=2
mount: block device /dev/sr0 is write-protected, mounting read-only
mount: /dev/sr0 already mounted or /mnt/cdrom busy
mount: according to mtab, /dev/sr0 is already mounted on /mnt/cdrom

---

### Post by tomearp on 2014-03-19
You need to unmount between each mount command, e.g.
```
sudo mount /dev/sr0 /mnt/cdrom -o session=0
ls /mnt/cdrom
sudo umount /dev/sr0
```
then increment the session number,
```
sudo mount /dev/sr0 /mnt/cdrom -o session=1
ls /mnt/cdrom
sudo umount /dev/sr0
```
then increment the session number,
```
sudo mount /dev/sr0 /mnt/cdrom -o session=2
ls /mnt/cdrom
sudo umount /dev/sr0
```
and so on. I guess there will come a point where it will throw an error because the session doesn't exist.

---

### Post by charmingnathan2 on 2014-03-21
> **tomearp said:**
> You need to unmount between each mount command, e.g.
```
sudo mount /dev/sr0 /mnt/cdrom -o session=0
ls /mnt/cdrom
sudo umount /dev/sr0
```
then increment the session number,
```
sudo mount /dev/sr0 /mnt/cdrom -o session=1
ls /mnt/cdrom
sudo umount /dev/sr0
```
then increment the session number,
```
sudo mount /dev/sr0 /mnt/cdrom -o session=2
ls /mnt/cdrom
sudo umount /dev/sr0
```
and so on. I guess there will come a point where it will throw an error because the session doesn't exist.

Thanks Tomearp, for that clarification of the syntax, I believe we are now getting somewhere although the result I wanted has not been achieved - yet.

However, I think I am using the right syntax to interrogate the disk. I have put the results below, most of which you don't need to see, but I followed your directions and went to - what I presume would be - 10 sessions; as you will see, all of them show the same audio files rather than the pictures I wanted to recover. For ease of reading, I have separated the sessions, but they are all a repeat of each other:

nathan@nathan-desktop:~$ sudo mount /dev/sr0 /mnt/cdrom -o session=0
[sudo] password for nathan: 
mount: block device /dev/sr0 is write-protected, mounting read-only
nathan@nathan-desktop:~$ ls /mnt/cdrom
100. Different What's Your Point.mp3   94. Dont Surprise Try Harder.mp3
101. Home Of The Strange.mp3           95. Home Of The Strange 1.mp3
102. Keep It Strange.mp3               96. Listening to SFR stick around.mp3
103. Listening to SFRadddioooo.mp3     97. NN Different Like It That Way.mp3
104. Stick Aound Stay Strange.mp3      98. That was Strange.mp3
105. Wondering what's going on.mp3     99. Different is Norm.mp3
92. Aint Like Everyone Else Great.mp3  Tickturds - Fire Inside.mp3
93. Different Way Enjoy Music.mp3

nathan@nathan-desktop:~$ sudo umount /dev/sr0
nathan@nathan-desktop:~$ sudo mount /dev/sr0 /mnt/cdrom -o session=1
mount: block device /dev/sr0 is write-protected, mounting read-only
nathan@nathan-desktop:~$ ls /mnt/cdrom
100. Different What's Your Point.mp3   94. Dont Surprise Try Harder.mp3
101. Home Of The Strange.mp3           95. Home Of The Strange 1.mp3
102. Keep It Strange.mp3               96. Listening to SFR stick around.mp3
103. Listening to SFRadddioooo.mp3     97. NN Different Like It That Way.mp3
104. Stick Aound Stay Strange.mp3      98. That was Strange.mp3
105. Wondering what's going on.mp3     99. Different is Norm.mp3
92. Aint Like Everyone Else Great.mp3  Tickturds - Fire Inside.mp3
93. Different Way Enjoy Music.mp3

nathan@nathan-desktop:~$ sudo umount /dev/sr0
nathan@nathan-desktop:~$ sudo mount /dev/sr0 /mnt/cdrom -o session=2
mount: block device /dev/sr0 is write-protected, mounting read-only
nathan@nathan-desktop:~$ ls /mnt/cdrom
100. Different What's Your Point.mp3   94. Dont Surprise Try Harder.mp3
101. Home Of The Strange.mp3           95. Home Of The Strange 1.mp3
102. Keep It Strange.mp3               96. Listening to SFR stick around.mp3
103. Listening to SFRadddioooo.mp3     97. NN Different Like It That Way.mp3
104. Stick Aound Stay Strange.mp3      98. That was Strange.mp3
105. Wondering what's going on.mp3     99. Different is Norm.mp3
92. Aint Like Everyone Else Great.mp3  Tickturds - Fire Inside.mp3
93. Different Way Enjoy Music.mp3

nathan@nathan-desktop:~$ sudo umount /dev/sr0
nathan@nathan-desktop:~$ sudo mount /dev/sr0 /mnt/cdrom -o session=2
^[[Dmount: block device /dev/sr0 is write-protected, mounting read-only
nathan@nathan-desktop:~$ sudo mount /dev/sr0 /mnt/cdrom -o session=3
mount: block device /dev/sr0 is write-protected, mounting read-only
ls /mnt/cdrom
mount: /dev/sr0 already mounted or /mnt/cdrom busy
mount: according to mtab, /dev/sr0 is already mounted on /mnt/cdrom
nathan@nathan-desktop:~$ ls /mnt/cdrom
100. Different What's Your Point.mp3   94. Dont Surprise Try Harder.mp3
101. Home Of The Strange.mp3           95. Home Of The Strange 1.mp3
102. Keep It Strange.mp3               96. Listening to SFR stick around.mp3
103. Listening to SFRadddioooo.mp3     97. NN Different Like It That Way.mp3
104. Stick Aound Stay Strange.mp3      98. That was Strange.mp3
105. Wondering what's going on.mp3     99. Different is Norm.mp3
92. Aint Like Everyone Else Great.mp3  Tickturds - Fire Inside.mp3
93. Different Way Enjoy Music.mp3

nathan@nathan-desktop:~$ sudo umount /dev/sr0
nathan@nathan-desktop:~$ sudo mount /dev/sr0 /mnt/cdrom -o session=4
mount: block device /dev/sr0 is write-protected, mounting read-only
nathan@nathan-desktop:~$ ls /mnt/cdrom
100. Different What's Your Point.mp3   94. Dont Surprise Try Harder.mp3
101. Home Of The Strange.mp3           95. Home Of The Strange 1.mp3
102. Keep It Strange.mp3               96. Listening to SFR stick around.mp3
103. Listening to SFRadddioooo.mp3     97. NN Different Like It That Way.mp3
104. Stick Aound Stay Strange.mp3      98. That was Strange.mp3
105. Wondering what's going on.mp3     99. Different is Norm.mp3
92. Aint Like Everyone Else Great.mp3  Tickturds - Fire Inside.mp3
93. Different Way Enjoy Music.mp3

nathan@nathan-desktop:~$ sudo umount /dev/sr0
nathan@nathan-desktop:~$ sudo mount /dev/sr0 /mnt/cdrom -o session=5
mount: block device /dev/sr0 is write-protected, mounting read-only
nathan@nathan-desktop:~$ ls /mnt/cdrom
100. Different What's Your Point.mp3   94. Dont Surprise Try Harder.mp3
101. Home Of The Strange.mp3           95. Home Of The Strange 1.mp3
102. Keep It Strange.mp3               96. Listening to SFR stick around.mp3
103. Listening to SFRadddioooo.mp3     97. NN Different Like It That Way.mp3
104. Stick Aound Stay Strange.mp3      98. That was Strange.mp3
105. Wondering what's going on.mp3     99. Different is Norm.mp3
92. Aint Like Everyone Else Great.mp3  Tickturds - Fire Inside.mp3
93. Different Way Enjoy Music.mp3

nathan@nathan-desktop:~$ sudo umount /dev/sr0
nathan@nathan-desktop:~$ sudo mount /dev/sr0 /mnt/cdrom -o session=6
mount: block device /dev/sr0 is write-protected, mounting read-only
nathan@nathan-desktop:~$ ls /mnt/cdrom
100. Different What's Your Point.mp3   94. Dont Surprise Try Harder.mp3
101. Home Of The Strange.mp3           95. Home Of The Strange 1.mp3
102. Keep It Strange.mp3               96. Listening to SFR stick around.mp3
103. Listening to SFRadddioooo.mp3     97. NN Different Like It That Way.mp3
104. Stick Aound Stay Strange.mp3      98. That was Strange.mp3
105. Wondering what's going on.mp3     99. Different is Norm.mp3
92. Aint Like Everyone Else Great.mp3  Tickturds - Fire Inside.mp3
93. Different Way Enjoy Music.mp3

nathan@nathan-desktop:~$ sudo mount /dev/sr0 /mnt/cdrom -o session=7
mount: block device /dev/sr0 is write-protected, mounting read-only
mount: /dev/sr0 already mounted or /mnt/cdrom busy
mount: according to mtab, /dev/sr0 is already mounted on /mnt/cdrom
nathan@nathan-desktop:~$ sudo umount /dev/sr0
nathan@nathan-desktop:~$ sudo mount /dev/sr0 /mnt/cdrom -o session=7
mount: block device /dev/sr0 is write-protected, mounting read-only
ls /mt/cdrom
nathan@nathan-desktop:~$ ls /mnt/cdrom
100. Different What's Your Point.mp3   94. Dont Surprise Try Harder.mp3
101. Home Of The Strange.mp3           95. Home Of The Strange 1.mp3
102. Keep It Strange.mp3               96. Listening to SFR stick around.mp3
103. Listening to SFRadddioooo.mp3     97. NN Different Like It That Way.mp3
104. Stick Aound Stay Strange.mp3      98. That was Strange.mp3
105. Wondering what's going on.mp3     99. Different is Norm.mp3
92. Aint Like Everyone Else Great.mp3  Tickturds - Fire Inside.mp3
93. Different Way Enjoy Music.mp3

nathan@nathan-desktop:~$ sudo umount /dev/sr0
nathan@nathan-desktop:~$ sudo mount /dev/sr0 /mnt/cdrom -o session=8
mount: block device /dev/sr0 is write-protected, mounting read-only
nathan@nathan-desktop:~$ ls /mnt/cdrom
100. Different What's Your Point.mp3   94. Dont Surprise Try Harder.mp3
101. Home Of The Strange.mp3           95. Home Of The Strange 1.mp3
102. Keep It Strange.mp3               96. Listening to SFR stick around.mp3
103. Listening to SFRadddioooo.mp3     97. NN Different Like It That Way.mp3
104. Stick Aound Stay Strange.mp3      98. That was Strange.mp3
105. Wondering what's going on.mp3     99. Different is Norm.mp3
92. Aint Like Everyone Else Great.mp3  Tickturds - Fire Inside.mp3
93. Different Way Enjoy Music.mp3

nathan@nathan-desktop:~$ sudo umount /dev/sr0
nathan@nathan-desktop:~$ sudo mount /dev/sr0 /mnt/cdrom -o session=9
mount: block device /dev/sr0 is write-protected, mounting read-only
nathan@nathan-desktop:~$ ls /mnt/cdrom
100. Different What's Your Point.mp3   94. Dont Surprise Try Harder.mp3
101. Home Of The Strange.mp3           95. Home Of The Strange 1.mp3
102. Keep It Strange.mp3               96. Listening to SFR stick around.mp3
103. Listening to SFRadddioooo.mp3     97. NN Different Like It That Way.mp3
104. Stick Aound Stay Strange.mp3      98. That was Strange.mp3
105. Wondering what's going on.mp3     99. Different is Norm.mp3
92. Aint Like Everyone Else Great.mp3  Tickturds - Fire Inside.mp3
93. Different Way Enjoy Music.mp3

nathan@nathan-desktop:~$ sudo umount /dev/sr0
nathan@nathan-desktop:~$ sudo mount /dev/sr0 /mnt/cdrom -o session=10
mount: block device /dev/sr0 is write-protected, mounting read-only
lnathan@nathan-desktop:~$ ls /mnt/cdrom
100. Different What's Your Point.mp3   94. Dont Surprise Try Harder.mp3
101. Home Of The Strange.mp3           95. Home Of The Strange 1.mp3
102. Keep It Strange.mp3               96. Listening to SFR stick around.mp3
103. Listening to SFRadddioooo.mp3     97. NN Different Like It That Way.mp3
104. Stick Aound Stay Strange.mp3      98. That was Strange.mp3
105. Wondering what's going on.mp3     99. Different is Norm.mp3
92. Aint Like Everyone Else Great.mp3  Tickturds - Fire Inside.mp3
93. Different Way Enjoy Music.mp3
nathan@nathan-desktop:~$ sudo umount /dev/sr0

---

### Post by tomearp on 2014-03-27
That's annoying, I'll try burning a multi-session disc at some point today and see if I can repeat the issue.

I had a bit of a search around and some people are reporting that a piece of windows software, [IsoBuster]("http://www.isobuster.com"), can read the previous session(s). If you have access to a windows machine it might be worth a try. The free version should be sufficient.

---

### Post by charmingnathan2 on 2014-04-10
> **tomearp said:**
> That's annoying, I'll try burning a multi-session disc at some point today and see if I can repeat the issue.

I had a bit of a search around and some people are reporting that a piece of windows software, [IsoBuster]("http://www.isobuster.com"), can read the previous session(s). If you have access to a windows machine it might be worth a try. The free version should be sufficient.

Yes Tomearp, it most certainly was!

What was even worse though from the point of view of a Windows user trying to migrate to a Linux platform, such as Ubuntu, was that your suggestion to try [COLOR=#0000ff]IsoBuster[/COLOR] proved to work!

The photographs were indeed tucked away in a previous session, but more embarrasingly obviously, was that it was a previous session that Brasero within Ubuntu actually burnt, but not could see whereas IsoBuster on a Windows platform could!

But listen, thanks for bearing with me and sorry for the delay in coming back to you, had a very bad bout of upset stomach for the last couple of weeks, but the problem is as Inspector Clouseau might say, is sol-ved!

Thanks again, and well done Tomearp.

---

### Post by tomearp on 2014-04-12
No problem, glad you got your files back :)

---

### Post by HC48 on 2014-06-13
Hi,
I tried the terminal solutions after a problem with 'lost' files when trying to add some more photos to a non-finalized CD. I'm still not sure what happened as I'm used to Brasero. Anyway Isobuster works a charm with Wine in Ubuntu 13.10. I retrieved all my files from the previous sessions.

---

