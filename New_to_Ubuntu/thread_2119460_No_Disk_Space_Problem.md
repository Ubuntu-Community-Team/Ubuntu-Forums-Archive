---
title: "No Disk Space Problem"
date: 2013-02-23
forum: New to Ubuntu
---

### Post by c5vetter on 2013-02-23
Okay, login to Thunderbird to read some email and when I go to delete the email I have just read get the following error message:

The messages could not be moved or copied to folder 'Trash' because writing to folder failed. To gain disk space, from the File menu, first choose Empty Trash, and then choose Compact Folders, and then try again.

Well, I have attempted to do that and nothing happens! So, WTFO, where do I go from here to correct this problem? Checked email this morning and no problems with deleting, etc.

Just now attempted to "GET MAIL" and got the following error:

Unable to write the email to the mailbox. Make sure the file system allows you write privileges, and you have enough disk space to copy the mailbox.

---

### Post by c5vetter on 2013-02-23
Okay, problem is beyond Thunderbird and being able to delete email! Just started Ubuntu and now get error that DROPBOX can not sync because there is no more disk space! When I run Disk Usage Analyzer, I get the follownig:

Total filesystem capacity 117.3 gb (35.9gb, available 81.4gb)

/ Usage is RED 100% 36.0GB 21 items
host is YELLOW 54% 19.4GB 14 items
var is GREEN 17.9% 6.4GB 11 items
usr is GREEN 15.6% 5.6GB 9 items
lib is GREEN 5.3% 1.9GB 53 items
home is GREEN 5.0% 1,8GB 1 item
boot 1.1% 411.7MB 79 items
dev 0% 4.1KB 15 items
etc 0% 17.6MB 273 items
media 0% 8.2KB 1 item
mnt 0% 4.1KB 0 items
opt .9% 340.2MB 2 items
run 0% 1.4MB 37 items
bin 0% 10.4MB 133 items
sbin 0% 10.5MB 152 items
selinux 0% 4.1KB 0 items
srv 0% 4.1KB 0 items
tmp 0% 12.3KB 16 items

So, what do I need to do!? Obvious "/" is 100% and RED and that needs to be changed, but how!?

---

### Post by mamamia88 on 2013-02-23
> **c5vetter said:**
> Okay, problem is beyond Thunderbird and being able to delete email! Just started Ubuntu and now get error that DROPBOX can not sync because there is no more disk space! When I run Disk Usage Analyzer, I get the follownig:

Total filesystem capacity 117.3 gb (35.9gb, available 81.4gb)

/ Usage is RED 100% 36.0GB 21 items
host is YELLOW 54% 19.4GB 14 items
var is GREEN 17.9% 6.4GB 11 items
usr is GREEN 15.6% 5.6GB 9 items
lib is GREEN 5.3% 1.9GB 53 items
home is GREEN 5.0% 1,8GB 1 item
boot 1.1% 411.7MB 79 items
dev 0% 4.1KB 15 items
etc 0% 17.6MB 273 items
media 0% 8.2KB 1 item
mnt 0% 4.1KB 0 items
opt .9% 340.2MB 2 items
run 0% 1.4MB 37 items
bin 0% 10.4MB 133 items
sbin 0% 10.5MB 152 items
selinux 0% 4.1KB 0 items
srv 0% 4.1KB 0 items
tmp 0% 12.3KB 16 items

So, what do I need to do!? Obvious "/" is 100% and RED and that needs to be changed, but how!?  maybe your dropbox account is maxed out and that's what is causing it?

---

### Post by c5vetter on 2013-02-24
Nope - Dropbox has about 350MB of files and have 5 gb space available total so not even close to being maxed out!

---

### Post by mamamia88 on 2013-02-24
Hmm try either clearing out some space in / or expanding it.   But dropbox ususally uses a folder in home which that shouldn't be a problem then.

---

### Post by Impavidus on 2013-02-24
Those percentages and colours in disk usage analyser are a bit misleading. / is always red and at 100%, even on my computer, on which I use only about 10% of my disk space. This is because the percentage is the size of each directory compared to its parent directory. This can be useful to find out where to do some cleanup.

You have a directory called /host. This means this is a wubi install (unless you tried to decieve us by making such a directory yourself, of course). The /host is on a separate partition, so the only way to use the space available there is to move data to that directory. For some data this may be possible. You may also be able to increase the size of your (virtual) ubuntu partition. I don't know much about wubi, so I cannot help you with that. Your ubuntu partition, if indeed full, is now about 16GB in size, you may be able to increase that to 30GB maximum.

However, I see that your /var is relatively large. It should be on the order of 1GB. Check for large log files in /var/log. If there are repeating error messages, post them here. There may be some problem that generates lots of error messages. Solving it may free about 5GB. In the meantime, you can simply delete the old logs to free up some space and keep your computer working.

---

### Post by prodigy_ on 2013-02-24
Run **df -h** command in Terminal to check free space. If **Use%** for any filesystem is 100% or close to that, you need to clear up some space.

Otherwise the issue is caused by something else, most likely insufficient permissions.

---

### Post by centaurusa on 2013-02-24
> **c5vetter said:**
> Okay, problem is beyond Thunderbird and being able to delete email! Just started Ubuntu and now get error that DROPBOX can not sync because there is no more disk space! 

Try using the BleachBit utility to identify (in preview mode) files that can potentially be deleted.  If you are satisfied that the program has identified redundant items you can then opt to actually delete them.  Even things like (multiple, archived) log files can take surprisingly large amounts of space.  For further details see: [http://linuxnorth.wordpress.com/2012/11/09/low-disk-space-warning/](http://linuxnorth.wordpress.com/2012/11/09/low-disk-space-warning/)

---

### Post by TheFu on 2013-02-24
> **prodigy_ said:**
> Run **df -h** command in Terminal to check free space. If **Use%** for any filesystem is 100% or close to that, you need to clear up some space.

Otherwise the issue is caused by something else, most likely insufficient permissions.


There are 2 different things that can run out of space. Sectors and inodes.  Check each with:
```
$ df -kh
$ df -i
```

Please post the results here.

---

### Post by Mark Phelps on 2013-02-24
> **Impavidus said:**
> You have a directory called /host. This means this is a wubi install (unless you tried to decieve us by making such a directory yourself, of course). The /host is on a separate partition, so the only way to use the space available there is to move data to that directory. For some data this may be possible. You may also be able to increase the size of your (virtual) ubuntu partition. I don't know much about wubi, so I cannot help you with that. Your ubuntu partition, if indeed full, is now about 16GB in size, you may be able to increase that to 30GB maximum.
This is REALLY important! Because, this means Ubuntu is NOT installed in a separate Linux filesystem partition; thus, you can NOT use any of the standard filesystem tools to change its size.

The link below has a section that describes how to increase the size of the virtual space allocated to a Wubi install:

[https://wiki.ubuntu.com/WubiGuide]("https://wiki.ubuntu.com/WubiGuide")

---

### Post by c5vetter on 2013-02-24
Okay, ran df -h and here is the result

Filesystem      Size  Used Avail Use% Mounted on
/dev/loop0       17G   15G  659M  96% /
udev            1.5G  4.0K  1.5G   1% /dev
tmpfs           605M  1.1M  604M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.5G  460K  1.5G   1% /run/shm
/dev/sdb1        94G   19G   75G  20% /host


So, what do I need to do to free up space? Need step-by-step

---

### Post by c5vetter on 2013-02-24
Okay, ran df -i and here are the results

Filesystem       Inodes  IUsed    IFree IUse% Mounted on
/dev/loop0      1073152 705586   367566   66% /
udev             210705    600   210105    1% /dev
tmpfs            215546    521   215025    1% /run
none             215546      3   215543    1% /run/lock
none             215546      7   215539    1% /run/shm
/dev/sdb1      78640440   1677 78638763    1% /host

Tried df -kh and was told no such command

---

### Post by Impavidus on 2013-02-25
Here are some instructions for enlarging your virtual partition: [https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk](https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk)

But still, I think that your /var is larger than it should be. Can you post the output of```
sudo du -s /var/* | sort -nr
```

---

### Post by TheFu on 2013-02-25
> **Impavidus said:**
> Here are some instructions for enlarging your virtual partition: [https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk](https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk)

But still, I think that your /var is larger than it should be. Can you post the output of```
sudo du -s /var/* | sort -nr
```

+1.

/var and 
/boot 
seem to be bloated. Your /var is much larger than most.

For /boot, you'll want to clean up old linux kernel images by removing them through** synaptic**. Be sure to keep the current kernel AND the prior one that works.  I retain the current and 2 prior kernels for safety.  To give you an idea of sizes, here are mine:
76M     /boot
781M    /var

I'm developing a ruby app, so my /var/www has more stuff than normal.

---

