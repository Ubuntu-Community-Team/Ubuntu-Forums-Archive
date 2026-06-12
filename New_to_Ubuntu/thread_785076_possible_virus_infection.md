---
title: "possible virus infection??"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by omkarwagh on 2008-05-07
i have a system partition and a home partition on my hard drive.
all of a sudden my home partition now shows several folders with names like
97ff2696e7b5ce8d367e97dca323eb2b
824b22e8317ed6c07c04dc
etc etc
there are quite a number of these rather empty folders being created. is this normal? could it be a virus or something? the only drop in performance seems to be that evolution hangs when i boot up which means i have to kill that process every time. in fact it not just hangs but hogs the entire processor time.

ive never seen this happen in the past one year that ive used ubuntu. anybody has any pointers? most of these problems have appeared when i tried to upgrade from gutsy to hardy.

thanks in advance.

---

### Post by tamoneya on 2008-05-07
I woudlnt say that is a virus.  It doesn't seem like it is anything dangerous since they are located in the home directory.  The program that is doing this seems to only be running with your user privileges.  Most importantly, it doesnt have root privileges so even if it was malicious it couldnt do anything bad to your system.  I do not however have any idea what it is.  Post the result of top.  Maybe we can find something odd in there.

---

### Post by omkarwagh on 2008-05-07
well they are not in my home directory but they are in my /home so its obviously something with root privileges. well im currently using windows(when will we have games like crysis on ubuntu?) ill reboot and post top's o/p.

---

### Post by tamoneya on 2008-05-07
okay if it is just in /home then it could be pretty nasty.  Ive never really done much on virii in linux so I really don't know where to go from here unless you can catch it in the act through something like top.

---

### Post by tjwoosta on 2008-05-07
do you have clamav ?

ive heard that clamav mostly only picks up windows viruses but i believe there are some linux viruses that it will pick up too

---

### Post by Monicker on 2008-05-07
How frequently are they being created?  To what owner and group do they belong?

Could you post the results of ls -lh /home ?

---

### Post by enoughsaid05 on 2008-05-07
I share my same sentiments....don't think virus can be present in your system unless you have downloaded and installed software from dubious sources.

ClamAV might help though.

---

### Post by scorp123 on 2008-05-07
> **omkarwagh said:**
>  all of a sudden my home partition now shows several folders with names like
97ff2696e7b5ce8d367e97dca323eb2b
824b22e8317ed6c07c04dc
etc etc Please copy & paste the output of these commands here (and please: I'd need the complete output of each command!):
```
cat /etc/fstab
mount
df -ah

```

---

### Post by omkarwagh on 2008-05-07
well here's the outputs of top before killing evolution and after killing it. (any ideas on why evolution keeps doing that? it slows the whole comp down)

i'll try out clamav. 

i guess part of the problem seems to be that i do install software that are not in the repository(say software for other distros which i have to compile first) as root. but these are mostly well-known things like xampp etc etc. 

as to how frequently they get created,...well i noticed them only today.

---

### Post by Xiong Chiamiov on 2008-05-07
AFAIK, there are no Linux viruses in the wild, only those created in labs and patched out of existence.  There is always the possibility though...

Avast! also has a Linux anti-virus.

---

### Post by omkarwagh on 2008-05-07
@Monicker well the output to ls -lh /home is in op1.txt

@scorp123 the output you asked for is in op2.txt

---

### Post by Xiong Chiamiov on 2008-05-07
Just a side note: so that people who aren't registered to this forum can see your output, you might consider using a service like [pastebin.com]("http://pastebin.com/").

---

### Post by scorp123 on 2008-05-07
> **omkarwagh said:**
>  @scorp123 the output you asked for is in op2.txt I suspect you have a corrupted filesystem ... did you have any crashes, or did you do any unclean shutdowns?

I'd recommend these steps:

- boot your system with a **Live CD**, e.g. the Ubuntu Installer CD
- once you're in the live system, open a terminal
- and then type this command to have your /home checked (might take a while):
```
sudo fsck.ext3 -f /dev/sda5
```

... and then let it do its job. It might take a while. It could happen that it will ask you a few "scary" things if it encounters errors, e.g. stuff such as "Block 49454f56d checksum mismatch. Fix (y/n)?"

Usually it will ask for your permission if you want to fix errors, so it's usually desirable to answer "y" ... But in case you're not sure I suggest you come back here and ask.

**_[COLOR="Red"]Very important:[/COLOR]_** **[COLOR="DarkRed"]Please make sure that the filesystem IS NOT MOUNTED when you run a filesystem check on it.[/COLOR]** That would be ***BAD***. That's why I recommended booting off the Live CD so we can be sure the OS did not boot off the harddisk.

---

### Post by omkarwagh on 2008-05-07
well yes we do have a number of power outages lately and my laptop battery is non-functional...
i dont have a live cd but i do have seperate /home and / as two different physical partitions.
can i run fsck from the failsafe terminal session? i dont have a live cd. i have noted that the failsafe terminal session allows one to unmount the /home directory.

---

### Post by scorp123 on 2008-05-07
> **omkarwagh said:**
>  well yes we do have a number of power outages lately and my laptop battery is non-functional...  That might explain it. If it happens too often it can cripple your filesystems. Journalling (such as in Ext3) usually helps to prevent the worst (the OS is supposed to know what has failed when and why), but it is no 100% guarantee against filesystem corruptions.

> **omkarwagh said:**
>  i dont have a live cd  How did you install Ubuntu then? Just curious ...

> **omkarwagh said:**
>  but i do have seperate /home and / as two different physical partitions.  Good!

> **omkarwagh said:**
>  can i run fsck from the failsafe terminal session?  Yes. Same commands. Just prior to executing the "fsck" command above you could check if /home is mounted or not:
```
mount
``` .. If it's not mounted then it should not be listed. If it is mounted you can unmount it, e.g. as "root":
```
umount /home
``` ... and then execute the "fsck" as I wrote above.

---

### Post by omkarwagh on 2008-05-08
well thanks. turns out it was corrupted. most weird things seem to have gone to /lost+found. i dunno what to do about this though. from googling a bit it seems that fsck moves something called inodes to /lost+found. not too sure what that means though i hope my system is not too damaged.

as for the abscence of live cds, well i do have a dapper cd that looks more like a cat's claw-sharpening tool than a livecd. 

could this also be the reason why hardy seems soooo much slower than dapper? i thought it slowed down due to quite the same reasons that vista behaves like a snail compared to XP(though i never really expected linux to go the "upgrade your hardware or go to hell" way). would you recommend a clean install?

---

### Post by sujoy on 2008-05-08
I know I would recommend a clean install, but only if you have a separate /home partition, otherwise just try a bit more to resolve the problems.

---

### Post by scorp123 on 2008-05-08
> **omkarwagh said:**
>  well thanks. turns out it was corrupted. most weird things seem to have gone to /lost+found. i dunno what to do about this though. from googling a bit it seems that fsck moves something called inodes to /lost+found. Read here:
[http://en.wikipedia.org/wiki/Inode](http://en.wikipedia.org/wiki/Inode)

Basically "inodes" are like small phone books, but instead of phone numbers and the names of the people who own that phone number "inodes" contain lists of file fragments that would tell the filesystem which piece of which file is on which part of which disk. Like small roadmaps.

When filesystems on UNIX-like operating systems such as Linux get corrupted it can happen that all of a sudden there might be inodes which are pointing to locations that according to the filesystem should be empty ... or should be occupied by something else. Or the journal says that file "A" got written to inodes e.g. "1+2+3", but the filesystem check finds inodes e.g. "4+5+6" who too claim that they belong to file "A".

So your OS is trying to be nice to you and instead of simply deleting those fragments without giving you a chance to at least look at them it moves those fragments into the "lost+found" directory where you could take a look and try to find out if anything important was lost.

So what you should do now is to go into that "lost+found" directory and look at the files there. Who knows? Maybe you lost some MP3's and don't know it yet? Or you lost photos from your "Pictures" folder and just don't know it yet? .... That's why there is this "lost+found" folder so you have a chance to find out if anything important was lost in the corruption.

I'd suggest you first find out what the filenames are and then use the "file" utility to find out what they are, e.g.
```
sudo ls -al /home/lost+found
sudo file /home/lost+found/replace_with_filename_here
``` .... "file" should recognise most file types and will tell you what it has found, possible answers are e.g.: ```
JPEG image data, JFIF standard 1.01
``` ... that would be a picture!
```
Audio file with ID3 version 23.0 tag, MP3 encoding
``` ... that would obviously be a MP3 file!
```
UTF-8 Unicode text
``` ... this might be a text file written in a foreign (= not English) language containing non-English characters, e.g. maybe containing Russian-Cyrillic or Asian letters ...

If it just responds like this: ```
... binary data ...
``` then you probably just caught garbage and can safely ignore whatever that file is.

Once you salvaged everything that you wanted to salvage you can safely delete the files underneath "lost+found" if you are really really sure you don't need them anymore.

---

