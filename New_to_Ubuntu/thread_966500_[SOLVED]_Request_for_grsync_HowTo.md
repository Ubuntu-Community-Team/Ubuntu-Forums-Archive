---
title: "[SOLVED] Request for grsync HowTo"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by Mega_Fauna on 2008-11-01
Hi,

I am trying to back up my data from one hard-drive to another and everytime I run grsync it deletes all the old data and rewrites it from scratch. I have googled and done everything I can think of trying. 

Can someone please write me a simple HowTo which will enable me to copy the data just once and then to update only those files which have changed, and to add only the newly added files to the backup?

Thanks, I am really beside myself with these grsync options.

---

### Post by nhasian on 2008-11-01
Hello,

see if this page will help you out.  it has an rsync script already that you can use in the body of the page

[http://sial.org/howto/rsync/](http://sial.org/howto/rsync/)

also here's a tutorial on rsync:

[http://everythinglinux.org/rsync/](http://everythinglinux.org/rsync/)

---

### Post by ajgreeny on 2008-11-01
> I am trying to back up my data from one hard-drive to another and everytime I run grsync it deletes all the old data and rewrites it from scratch. I have googled and done everything I can think of trying.Are you sure it deletes all the old files. If you have a large amount of data to backup it can still take a while to check everything to see if it has changed, but it shouldn't delete anything unless you tell it to.  If you are talking of deleting things on the destination partition, just make sure that the "Delete on destination" option is not checked on the opening window of grsync.  I use it all the time without problem, for backing up my home folder to a usb drive and it has not let me down yet.

I have the following options checked:-
*Basic options*
Preserve time
Preserve permissions
Verbose
Show transfer progress
*Advanced options*
Always checksum

The rest are not checked.  Give it a try again

---

### Post by Mega_Fauna on 2008-11-08
> **ajgreeny said:**
> Are you sure it deletes all the old files. If you have a large amount of data to backup it can still take a while to check everything to see if it has changed, but it shouldn't delete anything unless you tell it to.  If you are talking of deleting things on the destination partition, just make sure that the "Delete on destination" option is not checked on the opening window of grsync.  I use it all the time without problem, for backing up my home folder to a usb drive and it has not let me down yet.

I have the following options checked:-
*Basic options*
Preserve time
Preserve permissions
Verbose
Show transfer progress
*Advanced options*
Always checksum

The rest are not checked.  Give it a try again


Hi, Thanks for your settings. I tried them immediately and then messed around with things for quite a while. They don't quite work.

rync doesn't have permissions to delete the old unwanted files, they stay in the directory with a "Lock" symbol placed on them and I have to 'sudo Nautilus' and manually delete them, which defeats the purpose I think. 

I am opening rsync with 'sudo rsync'; the source drive is owned by me / group = root, the target drive is owned by root / group = plugdev.

---

### Post by Kellemora on 2008-11-08
Hi MF

I'm NOT going to be a whole lot of help here, as I'm a noob and just getting my feet wet myself trying to learn crontab.
I still have a couple of issues myself with the automation end of it, but I do have the manual way of doing it down pat quite well.

But I have noticed something interesting, which is what you seem to be describing in your question.

If I mirror to a local drive (meaning inside the computer or attached to it as an external, even though Linux is supposed to see all drives anywhere on the network as local if mounted).
Here is what happens.
If I run rsync to a local drive (must be mounted first), after the FIRST time, it only deletes files I deleted and only copies over files I have changed.  Very quick and efficient!  Corrupted files overwrite good files just as expected, hi hi....
However, if I'm running rsync to a drive not connected to the machine, even though mounted, it DOES delete the data in the backup file and then rewrites ALL the backup each time, which is very time consuming.

I have no idea why it is doing this either!  The code is identical!
I'm currently mirroring (because I don't like backup's) my entire /home directory, even though I only want to backup the data files.
It's ok when rsync works as it should and only copies changed files, it goes very fast.  But when I run the mirror over the LAN, I could hand write the info faster I think, hi hi..........

If it's TRUE that Linux sees ALL mounted hard drives as local files on a local hard drive, then there is no logical reason for it to delete the entire mirror and rewrite it each time.  Unless unmounting and remounting gives it a different ID number, the UUID is the same, but you never know with these confounded computin' contraptions, hi hi.......

Good Luck

TTUL
Gary

---

### Post by MrWES on 2008-11-08
Is the destination drive fat or fat32? If so, I believe that's a limitation of rsync. I could be wrong.

Bill

---

### Post by Mega_Fauna on 2008-11-27
> **MrWES said:**
> Is the destination drive fat or fat32? If so, I believe that's a limitation of rsync. I could be wrong.

Bill

Hi,

It was a vfat drive, that was the problem which caused nothing to work correctly. I'd assume that grsync would spit out a warning when using a file system like that, but no, it doesn't.

Now I've formatted to a solid ext3 system and grsync runs beautifully.

Thanks!

---

### Post by Mega_Fauna on 2008-11-27
> **ajgreeny said:**
> Are you sure it deletes all the old files. If you have a large amount of data to backup it can still take a while to check everything to see if it has changed, but it shouldn't delete anything unless you tell it to.  If you are talking of deleting things on the destination partition, just make sure that the "Delete on destination" option is not checked on the opening window of grsync.  I use it all the time without problem, for backing up my home folder to a usb drive and it has not let me down yet.

I have the following options checked:-
*Basic options*
Preserve time
Preserve permissions
Verbose
Show transfer progress
*Advanced options*
Always checksum

The rest are not checked.  Give it a try again


Hi,

Thanks for your advice, I am using your settings (but with 'Delete on Destination' checked as well). My problem was I was using a vfat file system which doesn't support file permissions so the system just failt whenever it ran. I have updated to an ext3 system and now have the perfect backup mirror.

Thanks again.

---

