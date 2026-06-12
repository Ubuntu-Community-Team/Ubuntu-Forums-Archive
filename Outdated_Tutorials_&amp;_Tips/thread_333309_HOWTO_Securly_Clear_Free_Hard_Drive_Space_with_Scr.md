---
title: "HOWTO: Securly Clear Free Hard Drive Space with Scrub"
date: 2007-01-07
forum: Outdated Tutorials &amp; Tips
---

### Post by GrammatonCleric on 2007-01-07
This how to covers the use of SCRUB, developed by Jim Garlick, to securly clear free hard drive space.  Scrub uses user-selectable pattern  algorithms that are compliant with DoD 5520.22-M or NNSA NAP-14.x. 

----------------------------------------------------------------------------

**Step 1: Install Alien.**

   ```
sudo apt-get install alien
```**Step 2: Download Scrub.**

   ```
 

[Download Scrub]("http://sourceforge.net/project/showfiles.php?group_id=153984") 



```**Step 3:  Convert RPM file to DEP.**

    ```
sudo alien scrub_1.8-2_i386.rpm
```**Step 4: Install scrub**

    ```
sudo dpkg -i scrub_1.8-2_i386.deb
```**Step 5: Create a scratch directory for scrub.**

    ```
sudo mkdir /scratch
```**Step 6:  Run Scrub (as root).**

   ```
scrub -X /scratch/junk | sudo rm -f  /scratch/junk 
```
[B][COLOR=Red]
Updated[/COLOR][/B]: Updated download location.

---

### Post by xyz on 2007-03-05
Well it sure works but something got me very worried!
> /dev/hda2             10080520   9952800         0 **100%** /

I had to Ctrl + C to stop it because I have a 5.3 GB 'junk' file!!
I misunderstood you, I guess. I thought it would free up space (as in unnecessary files) not the whole drive.
Anyone has an idea as to what I'm supposed to do to revert back? Thnx in advance.

PS: My backup is for Dapper; just upgraded this here machine to Edgy and, therefore I have no Edgy backup to restore.

---

### Post by GrammatonCleric on 2007-03-05
Scrub is not use to free up hard drive space. It's used to "securely wipe" free hard drive space.   Say you have a bunch of sensitive data (i.e. patient files, financial data, deleted audio files before you send your hard drive to the RIAA =P, etc.) you may have deleted from your drive but you want to make sure the data is unrecoverable.  Just because you delete a file  does not mean it is  unrecoverable.  

_**How to recover deleted files:**_

```


[http://e2undel.sourceforge.net/recovery-howto.html](http://e2undel.sourceforge.net/recovery-howto.html)


```Scrub will fill a partition gradually expanding and filling a single file with random data thus over witting any deleted files in that partition.  If you read setup 7 you can simply delete the scrub junk file. =)

-GC

---

### Post by xyz on 2007-03-05
Yes indeed...I misunderstood you!
If you care to have a look:
[I 'scrubbed my Ubuntu...']("http://ubuntuforums.org/showthread.php?t=376611")
I explain what I did there.

For some reason I don't understand it doesn't look like I lost data??
Thanks for your reply.

---

### Post by bluebyt on 2007-03-11
Does this clear Free Hard Drive Space on /Home partition?

---

### Post by GrammatonCleric on 2007-03-11
> **bluebyt said:**
> Does this clear Free Hard Drive Space on /Home partition?

It will "Scrub" whatever partition you output the junk file to.  If your /home is in the same partition as your "/" then yes.  If you have your /home mounted to it's own partition then you could run scrub like.  

```

sudo scrub -X /home/junk

```[I][B]DON'T FORGET TO DELETE THE JUNK FILE WHEN SCRUB IS DONE.

[/B][/I]-GC

---

### Post by bluebyt on 2007-03-11
> **GrammatonCleric said:**
> It will "Scrub" whatever partition you output the junk file to.  If your /home is in the same partition as your "/" then yes.  If you have your /home mounted to it's own partition then you could run scrub like.  

```

sudo scrub -X /home/junk

```[I][B]DON'T FORGET TO DELETE THE JUNK FILE WHEN SCRUB IS DONE.

[/B][/I]-GC

I tried this "sudo scrub -X /home/junk" but I get this error:

scrub: scrub.c:204: scrub_free: Assertion `filetype(path) == NOEXIST || filetype(path) == REGULAR' failed.

---

### Post by GrammatonCleric on 2007-03-12
Can you post your partition layout?  Run...

```


df -h


```
...from the command line and post the output.


--GC

---

### Post by bluebyt on 2007-03-12
Here you go:

df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda4             7.2G  3.9G  3.1G  57% /
varrun                506M  212K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb            506M   88K  506M   1% /proc/bus/usb
udev                  506M   88K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   26M  481M   5% /lib/modules/2.6.20-9-generic/volatile
/dev/hda3              12G  4.6G  6.2G  43% /home
/dev/hda1              19G   15G  4.3G  78% /media/sda1

---

### Post by GrammatonCleric on 2007-03-12
When you run...

```
sudo scrub -X /home/junk
```Is a junk file created?   Scrub appears to be complaining about either the path/a missing output file (i.e. junk) or permissions to write to the path.

Try creating a junk file before running scrub....

```
sudo touch /home/junk 
```or try doing ....

```
sudo -i
```then run...

```
 scrub -X /home/junk 
```-GC

---

### Post by bluebyt on 2007-03-12
Didn't work same error message.

Thank you for helping me though!

---

### Post by arijarot on 2007-07-13
Thanks for this tutorial. Two questions. How can you tell if it did its job correctly. Is there a command to scrub the swap partition?

---

### Post by Canuckelhead on 2007-08-15
It's probably worth mentioning that if you happen to be using this on a FAT32 partition there is a 4 Gig - 1 byte file size limitation to consider.  You'll need to change file systems...

---

### Post by suba82 on 2007-09-21
Hi everyone, is it possible to use the same command line for a usb disk?
Cause I want to "scrub" free space on a usb disk plugged in my computer. 
How can I choose the disk to wipe? thanx

---

### Post by bigbooger on 2008-06-28
scrub has been updated:

[[COLOR="Blue"]Scrub2.0[/COLOR]]("http://sourceforge.net/project/showfiles.php?group_id=153984")

---

