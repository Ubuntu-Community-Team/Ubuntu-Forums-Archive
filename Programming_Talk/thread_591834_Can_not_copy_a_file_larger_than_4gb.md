---
title: "Can not copy a file larger than 4gb"
date: 2007-10-25
forum: Programming Talk
---

### Post by lsutiger on 2007-10-25
I am bringing this to the programming forum in hope of getting a true logical answer.

I have a hard drive connected via usb that is 60gb (EXT3). I have a file that was created by simple backup on the internal drive that is 26gb.

When I try to copy the file to the external drive, I get an error using the CLI:
```
root@complexity-laptop:/var/backup/Backup# cp * /media/disk/
File size limit exceeded (core dumped)
```

When I tried it with the GUI It just stopped. IN both instances the file size that was transferred was truncated to 4gb.

Why is this?
This is the return from ulimit -a:
```
complexity@complexity-laptop:~$ ulimit -a
core file size          (blocks, -c) 0
data seg size           (kbytes, -d) unlimited
scheduling priority             (-e) 20
file size               (blocks, -f) unlimited
pending signals                 (-i) unlimited
max locked memory       (kbytes, -l) unlimited
max memory size         (kbytes, -m) unlimited
open files                      (-n) 1024
pipe size            (512 bytes, -p) 8
POSIX message queues     (bytes, -q) unlimited
real-time priority              (-r) 0
stack size              (kbytes, -s) 8192
cpu time               (seconds, -t) unlimited
max user processes              (-u) unlimited
virtual memory          (kbytes, -v) unlimited
file locks                      (-x) unlimited
```
Thanx for any replies!

PS - I am trying to do a clean instal of Gutsy, but need a backup of my home folder.

---

### Post by LaRoza on 2007-10-25
Is this a FAT32 partition? If so, it can not store files larger than 4 GB - 1 Byte.

[This]("http://en.wikipedia.org/wiki/File_Allocation_Table#FAT32") explains it.

Of course, I am assuming this is a FAT32 partition. Could you tell us a little more if it is not?

---

### Post by lsutiger on 2007-10-25
I seriously doubt it, but just to be for sure, how do I tell? Whats the command for that?

I had several hard drives laying around here ( notebook drives) and this one was my former Ubuntu drive before switching laptops. When I installed Ubuntu on that drive I formatted and set it up with the install program, which if I remember correctly, formatted it as an EXT3 drive...but like I said, I have several here and could be wrong.
If it is FAT32, how do I format it EXT3?

---

### Post by LaRoza on 2007-10-25
> **lsutiger said:**
> If it is FAT32, how do I format it EXT3?

With GParted.

How to tell: Right Click, Choose Properties->Volume

---

### Post by lsutiger on 2007-10-25
GEEZ..I need to convert my work PC to Ubuntu. Dealing with MS all day makes me loose thought of Linux.
I guess I will have to get rid of that shirt that says "I could be wrong...but I doubt it"

Thanx for the help!

---

### Post by LaRoza on 2007-10-25
> **lsutiger said:**
> GEEZ..I need to convert my work PC to Ubuntu. Dealing with MS all day makes me loose thought of Linux.
I guess I will have to get rid of that shirt that says "I could be wrong...but I doubt it"

Thanx for the help!

Was it FAT32, if it wasn't my responses will not apply.

---

### Post by lsutiger on 2007-10-25
yeah,  but asking how to tell...thats the geez. appreciated though

---

### Post by ryanVickers on 2007-10-25
yeah, I would guess that it's FAT 32 - it can only address up to 4GB of memory with 32 bit, and thus the max file size for fat **32** is 4GB (minus one byte ;))

If it's not fat 32, perhaps this is 32 bit Ubuntu, and you have some serious other problem... ;) (because normally this would be fine :D)

---

### Post by LaRoza on 2007-10-25
> **ryanVickers said:**
> yeah, I would guess that it's FAT 32 - it can only address up to 4GB of memory with 32 bit, and thus the max file size for fat **32** is 4GB (minus one byte ;))

If it's not fat 32, perhaps this is 32 bit Ubuntu, and you have some serious other problem... ;) (because normally this would be fine :D)
I know, I already addressed the limit of FAT32. I never had trouble with 32 bit Ubuntu and large file transfers (+ 4 GB).

Is 64 bit better than 32 bit, in your experience?

---

### Post by ryanVickers on 2007-10-25
well ,yes, 32 bit can address 4GiB, and 64 can address 16EiB (16 x 1000 x 1000 x 1000 GiB) ;)

---

### Post by jpkotta on 2007-10-26
Filesystem "bit size" has essentially nothing to do with architecture "bit size".  IIRC, ext3 is 32-bit, ZFS is 64-bit.  The architecture only determines how much memory you can address, not how much data your filesystem can address.

Edit: fs bit sizes were definately wrong

---

### Post by mridkash on 2007-10-26
I dont know why this is happening but, file splitting is a solution. 
Recently, I had to move home folder (11gb) to dvd disks for backup. I used the split command in terminal to split the tar file in 500 mb packets. Burned the dvds and recombined the files using the cat command. All went well.
make absolutely sure that you'll check md5sum of individual packets before and after copying to avoid any loss.

---

### Post by ryanVickers on 2007-10-26
> **jpkotta said:**
> Filesystem "bit size" has essentially nothing to do with architecture "bit size".  IIRC, ext3 is 32-bit, ZFS is 64-bit.  The architecture only determines how much memory you can address, not how much data your filesystem can address.

Edit: fs bit sizes were definately wrong

yes, but let's say you have a 128 bit filesystem, just for the heck of it.  If you only have a 32 bit OS, then it's still a bottle neck, even though the filesystem may not be.  I'm not saying this is the cause, just that it's something to alway consider when doing anything with stuff around 4GiB in size...

---

### Post by happysmileman on 2007-10-26
> **ryanVickers said:**
> yes, but let's say you have a 128 bit filesystem, just for the heck of it.  If you only have a 32 bit OS, then it's still a bottle neck, even though the filesystem may not be.  I'm not saying this is the cause, just that it's something to alway consider when doing anything with stuff around 4GiB in size...

No, because it doesn't load the full 2^128 bytes at once, it does it bit by bit, otherwise RAM would be a bottleneck, I'm pretty sure I've used 8GB files on both Linux and Windows 32 bit

---

### Post by ryanVickers on 2007-10-26
yes, that's true - I'm not saying that's the problem - it most likely isn't, but I'm just saying it may affect some things, like I've heard stuff like you can't burn a single file larger than 4GB with 32bit OS (Ubuntu).  Do you have any thoughts on that?  Right?  Wrong?...

---

### Post by HermanAB on 2007-10-26
The 'mount' command will tell you what file systems are used.  USB drives are frequently formatted as VFAT (FAT32).

Cheers,

Herman

---

### Post by lsutiger on 2007-10-26
Hey peeps! Thanx for the input. I got that figured out. Now I have a new problem.
I backed up my home folder using sbackup. I installed Gutsy ( wiping the drive of course) and now I am trying to import my back up. 
When I try to use Simple backup restore, I point it to the drive where the backup files are, but it states that no backup files can be found. But they are there.Here is the listing of the directory:
```
complexity@complexity-laptop:/media/disk/backup$ ls -l
total 27422224
-rwxrwxrwx 1 complexity root         144 2007-10-25 21:38 excludes
-rwxrwxrwx 1 complexity root 28049908684 2007-10-25 22:53 files.tgz
-rwxrwxrwx 1 complexity root     2154723 2007-10-25 21:39 flist
-rwxrwxrwx 1 complexity root      802886 2007-10-25 21:39 fprops
-rwxrwxrwx 1 complexity root       34320 2007-10-25 22:53 packages
-rwxrwxrwx 1 complexity root           4 2007-10-25 22:53 ver
```
Any ideas?

---

### Post by ryanVickers on 2007-10-26
could you not simply move them yourself?
And then extract them, as it seems it's created a massive targz file..., which tend to randomly corrupt if they are over 2GiB, so I *hope* that it all works out well for you *biting nails*... ;)

---

### Post by lsutiger on 2007-10-26
Well, I listed the file and everything seems to be there. I left it at lunch extracting all of the files to my hd. We shall see!
Why ya making me nervous?

---

### Post by lsutiger on 2007-10-26
WHEW!  Well the file is intact, but I learned that I couldn't tar it directly into my current home folder. It jacked up some settings and compiz stopped working. But evolution's mail is there and all of my firefox setting are working.

I am re-installing right now, will unzip the file to a directory on my hard drive and move the files to here respective places.

Any input would be appreciated!

---

### Post by ryanVickers on 2007-10-26
didn't mean to scare you, that's just what I've found, twice, and read on wikipedia ;)

Well, I think it should all be pretty strait forward - just put your files back and install however you want... :)

---

### Post by lsutiger on 2007-10-26
HAHA! Thanx for the nail biter! J/J I am sure I can configure this thing well.
I am completely amazed at how fast this thing runs with all the eye candy!

I deal with Dell Vista machines almost daily. In fact I have kick butt desktop with the same exact specs of those Dell machines.

I am dumbfounded at the speed difference between Vista and Gutsy! Gutsy rips! Vista...click and wait.

This is not to rip on MS, because I use their products everyday at work , but you need a workhorse just to run Vista, and if you enable the 3D desktop....don't want to go there. With Gutsy, compiz is quick, file access is quick, over all - it's a Ford pinto vs Chevy 'Vette.

Not to mention the ease and speed of the install. In my line of work, I have to "restore" the vista machines on a regular basis. When I do it through Dell's "restore to Dell Factory.." program and restoring directly from dvd...the Gutsy install is at least half the time ( I did not clock it, but I can guarantee).

All in all I am impressed!
Thanx for all of your help guys and gals ( is there are any gals replying to this post)

---

### Post by jpkotta on 2007-10-27
> **ryanVickers said:**
> yes, that's true - I'm not saying that's the problem - it most likely isn't, but I'm just saying it may affect some things, like I've heard stuff like you can't burn a single file larger than 4GB with 32bit OS (Ubuntu).  Do you have any thoughts on that?  Right?  Wrong?...

Technically, wrong.

[http://en.wikipedia.org/wiki/Ext3#Size_limits](http://en.wikipedia.org/wiki/Ext3#Size_limits)

In practice, however, you need applications that handle large files.  The standard syscall for seeking around in a file uses 32-bit integers (unless you deliberately compile it to use 64-bit ints or on a 64-bit arch), thus a maximum addressable space of 4GB.  If you write your application correctly (using the 64-bit version, llseek(), syscall), you can access large files on any architecture.

---

### Post by ryanVickers on 2007-10-27
Fascinating! :p

By the way, is ext4 (which apparently exists now ;)) a little better, worse, tons better, etc. and if it is a lot better with no problems, why is it not included as an option!?!

---

