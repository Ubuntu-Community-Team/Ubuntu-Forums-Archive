---
title: "[SOLVED] can't login"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by ginestre on 2008-09-04
I can't login as 'username' of this morning, and get the following error

mkdirtemp: private socket dir: No space left on device

However, I can start the recovery mode, as root I can launch the windows and gnome managers, and from there I'm told I have 1.7GB free space in my username home dir. 

What am I doing wrong?

TIA

---

### Post by HunterA3 on 2008-09-04
Since you can log in as root, you could change your password for the given username, and try logging in again. I'n not sure if that addresses the underlying issue, but You may be able to log in again.

---

### Post by Peter09 on 2008-09-04
In safe mode do

```
df
```

at the prompt and paste the output here.

---

### Post by halitech on 2008-09-04
in recovery mode, open a terminal and post the results of```
df -h
```

---

### Post by ginestre on 2008-09-04
First, thanks for the replies. Second, here is the output of df -h:

root@kids:~# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2             4.0G  3.9G     0 100% /
varrun                363M   12K  363M   1% /var/run
varlock               363M     0  363M   0% /var/lock
procbususb            363M  100K  363M   1% /proc/bus/usb
udev                  363M  100K  363M   1% /dev
devshm                363M     0  363M   0% /dev/shm
lrm                   363M   33M  330M  10% /lib/modules/2.6.20-17-generic/volatile
/dev/hda5             4.9G  2.9G  1.7G  64% /home
/dev/disk/by-uuid/58580A93580A7054
                       25G   15G  9.5G  61% /media/hda1
/dev/hda4             3.4G  3.2G  228M  94% /media/hda4
root@kids:~# 


From this I can see that hda2 (where /home is) is full: but if I go in Nautilus to the /home place, it tells me 1.7GB is free. Presumably the first (df -h) is true? And so do I just free up space by deleting stuff?

I did wonder if it might be a problem of a full trash can, but as root I can't seem to find the username .Trash. Or is that a red herring?

---

### Post by Peter09 on 2008-09-04
May be true that its your trash that's full, but it could be that something has dumped a large file in your /home directory. See if there is anything that you can delete or move to somewhere else. Once your in you can have a better look.

---

### Post by halitech on 2008-09-04
> **ginestre said:**
> First, thanks for the replies. Second, here is the output of df -h:

root@kids:~# df -h
Filesystem            Size  Used Avail Use% Mounted on
[color="red"]/dev/hda2             4.0G  3.9G     0 100% /[/color]
varrun                363M   12K  363M   1% /var/run
varlock               363M     0  363M   0% /var/lock
procbususb            363M  100K  363M   1% /proc/bus/usb
udev                  363M  100K  363M   1% /dev
devshm                363M     0  363M   0% /dev/shm
lrm                   363M   33M  330M  10% /lib/modules/2.6.20-17-generic/volatile
/dev/hda5             4.9G  2.9G  1.7G  64% /home
/dev/disk/by-uuid/58580A93580A7054
                       25G   15G  9.5G  61% /media/hda1
/dev/hda4             3.4G  3.2G  228M  94% /media/hda4
root@kids:~# 


From this I can see that hda2 (where /home is) is full: but if I go in Nautilus to the /home place, it tells me 1.7GB is free. Presumably the first (df -h) is true? And so do I just free up space by deleting stuff?

I did wonder if it might be a problem of a full trash can, but as root I can't seem to find the username .Trash. Or is that a red herring?

I'm nore concerned over the fact that the / folder is full. Root usually has a small reserve that will always allow root to log in (doesn't matter to Ubuntu cause it doesn't use root) so I'm wondering if its a case that / has no room at all and that is whats actually preventing you from logging in

---

### Post by ginestre on 2008-09-04
> **Peter09 said:**
> May be true that its your trash that's full, but it could be that something has dumped a large file in your /home directory. See if there is anything that you can delete or move to somewhere else. Once your in you can have a better look.

Well, logged in as root and using nautilus everything looks OK. If I go home, and then up a level, and right click for the properties of home I get 1776 files for 650MB and 1.7 GB free, Which is about right.There's nothing untowardly large anywhere that I can see.  The .Trash folder in my home/username is empty. The .Trash folder for root is also empty. 

So what gives?

---

### Post by Peter09 on 2008-09-04
goto / and do

```
ls -alg
```

may get a clue from that.

---

### Post by ginestre on 2008-09-04
> **halitech said:**
> I'm nore concerned over the fact that the / folder is full. Root usually has a small reserve that will always allow root to log in (doesn't matter to Ubuntu cause it doesn't use root) so I'm wondering if its a case that / has no room at all and that is whats actually preventing you from logging in

This seems likely: but I don't understand why it should be full, and with what,  if Nautilus says it isn't, and has 1.7GB free. How can I get a listing of /dev/hda2 in a terminal, so I can check? ls cat dir just give me /dev/hda2

---

### Post by halitech on 2008-09-04
in a terminal do
```
df /dev/hda2
```

/home is a different partition (/dev/hda5) so its not included in /

besides, its not saying /home is full, its saying no room on disk and unless you didn't post a part of the message its not saying which disk but / is showing as full

---

### Post by ginestre on 2008-09-04
> **Peter09 said:**
> goto / and do

```
ls -alg
```

may get a clue from that.

This gives me 
```

root@kids:/home# ls -alg
total 60
drwxr-xr-x 10 root      4096 Sep  4 22:16 .
drwxr-xr-x 21 root      4096 Jul  1 08:13 ..
drwx------  2 root      4096 Sep  4 23:30 .Trash-root
drwxr-xr-x  2 alex      4096 May 29  2007 alex
drwxr-xr-x 13 federico  4096 May 29  2007 federico
drwxr-xr-x 31 guest     4096 Nov  2  2007 guest
drwx------  2 root     16384 May 20  2007 lost+found
drwxr-xr-x  2 mirella   4096 Dec 30  2007 mirella
drwxr-xr-x 80 richard  12288 Sep  4 22:57 richard
drwxr-xr-x  2 virginia  4096 May 29  2007 virginia
root@kids:/home# cd /
root@kids:/# ls -alg
total 92
drwxr-xr-x  21 root  4096 Jul  1 08:13 .
drwxr-xr-x  21 root  4096 Jul  1 08:13 ..
drwxr-xr-x   2 root  4096 Mar 28 07:42 bin
drwxr-xr-x   3 root  4096 Aug 31 09:35 boot
lrwxrwxrwx   1 root    11 May 29  2007 cdrom -> media/cdrom
drwxr-xr-x  13 root 13700 Sep  4 23:00 dev
drwxr-xr-x 129 root 12288 Sep  4 22:59 etc
drwxr-xr-x  10 root  4096 Sep  4 22:16 home
drwxr-xr-x   2 root  4096 Apr 15  2007 initrd
lrwxrwxrwx   1 root    33 Jul  1 08:13 initrd.img -> boot/initrd.img-2.6.20-17-generic
lrwxrwxrwx   1 root    33 May 29  2007 initrd.img.old -> boot/initrd.img-2.6.20-16-generic
drwxr-xr-x  16 root  4096 Mar 28 07:42 lib
drwx------   2 root 16384 May 29  2007 lost+found
drwxr-xr-x   7 root  4096 Sep  4 22:27 media
drwxr-xr-x   2 root  4096 Apr 12  2007 mnt
drwxr-xr-x   4 root  4096 Oct  1  2007 opt
dr-xr-xr-x  73 root     0 Sep  5  2008 proc
drwxr-xr-x  18 root  4096 Sep  4 23:00 root
drwxr-xr-x   2 root  4096 Jul  1 08:10 sbin
drwxr-xr-x   2 root  4096 Apr 15  2007 srv
drwxr-xr-x  11 root     0 Sep  5  2008 sys
drwxrwxrwt  10 root  4096 Sep  4 23:17 tmp
drwxr-xr-x  12 root  4096 Sep  3  2007 usr
drwxr-xr-x  16 root  4096 Oct 20  2007 var
lrwxrwxrwx   1 root    30 Jul  1 08:13 vmlinuz -> boot/vmlinuz-2.6.20-17-generic
lrwxrwxrwx   1 root    30 May 29  2007 vmlinuz.old -> boot/vmlinuz-2.6.20-16-generic
root@kids:/# 


```
but I don't know what to do with this info

---

### Post by Peter09 on 2008-09-04
Have you tried 

Applications->accessories->disk usage analyser

---

### Post by ginestre on 2008-09-04
> **halitech said:**
> in a terminal do
```
df /dev/hda2
```

/home is a different partition (/dev/hda5) so its not included in /

besides, its not saying /home is full, its saying no room on disk and unless you didn't post a part of the message its not saying which disk but / is showing as full

I thought (apparently mistakenly) that home was on hda2... but your suggestion to
```
df /dev/hda2
```
gives me the confirmation that something is full: 
```

root@kids:/# df /dev/hda2
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda2              4150732   4010420         0 100% /
root@kids:/# 


```


This must be the problem. Is there some way to go to /dev/hda2 in nautilus, and empty it some? Or do I have to do it (nervously) from a terminal?

---

### Post by halitech on 2008-09-04
I would be very careful to delete anything in / as it is mostly your operating system files.

try this before we delete anything
```
sudo ls /root/.Trash
```
if it just drops a line then the root trash is empty, if it lists files, we can try going there and deleting the files.

---

### Post by ginestre on 2008-09-04
> **halitech said:**
> 
if it just drops a line then the root trash is empty, if it lists files, we can try going there and deleting the files.

It just drops a line.

---

### Post by halitech on 2008-09-04
ok, so no files in the trash we can delete from root

you can also try with /tmp and see if there is anything there to delete

---

### Post by ginestre on 2008-09-04
> **halitech said:**
> ok, so no files in the trash we can delete from root

you can also try with /tmp and see if there is anything there to delete

```

root@kids:/# sudo ls /tmp     
gconfd-root  keyring-bwoexa  mapping-root  orbit-root  ssh-FwhkZs4520  virtual-root.ICUsxj
root@kids:/# sudo ls /root/.Trash

```

Can I just get rid of these, do you think? and would that be 

sudo rm /tmp/*.*

---

### Post by halitech on 2008-09-04
yes you should be safe deleting those files and correct on the code to remove them

---

### Post by ginestre on 2008-09-04
> **Peter09 said:**
> Have you tried 

Applications->accessories->disk usage analyser

NO, I'd never noticed this before. But I've just launched it and it confirms that / is 100% full....

---

### Post by Peter09 on 2008-09-04
It will allow you to dig down to find where the usage is.

I been following the conversation - its a bit of a puzzle where the usage is.

---

### Post by MasterSander on 2008-09-04
You can try enlarging your ubuntu partition with the gparted live cd, and although this doesn't solve the problem, this is a step forward if it works.

---

### Post by halitech on 2008-09-04
> **Peter09 said:**
> It will allow you to dig down to find where the usage is.

I been following the conversation - its a bit of a puzzle where the usage is.

not really much of a puzzle, / is only 4 gig in size and a fresh install will take over 3 and I think I read in another thread where a fresh install with nothing else done was 3.6 gig so thats only 400meg of extras installed to file the drive

---

### Post by ginestre on 2008-09-05
- Thanks for all the advice, guys! Had to break off last night unexpectedly, unannounced and rather rudely as my little daughter woke from a nightmare...

- The story so far: it would seem that 4 giga for my / is too little,  because it got filled up with 'extras and such' since the initial install a year ago. The / is on hda2, (which isn't where /home is, that was my initial confusion), and hda2 is now 100% full.  The disk usage analyser tells me that I have overall used 2/3 of the available disk space, which is 36GB, leaving 11 available. For the record there is just one physical hd which is partitioned into XP (hda1), / (hda2), shared data (hda4) and presumably swap (would this be hda3, therefore?)

- So it would seem the solution is to make / bigger, and something else smaller. This involves using a partition editor, and can be done from a live disk. 

-QUERIES: a) Clearly I'll need to back up first. Just /home, or everything? Shall I also bite the bullet at the same time and move on from Feisty- or would that overcomplicate life with other factors at the same time. I need to solve this quickly as I have work deadlines to meet.
b) However, when I initially set this system up, I thought I'd left lots of extra space for growth: I don't remember what figures I found in the install howtos, but I left 30% more than was recommended at that time. How much space do you think / should need?
c) What should I have been monitoring (and how, and how often) so as either to avoid this problem, or at least be able to cope with it at an earlier and less inconvenient moment of my choosing?

---

### Post by halitech on 2008-09-05
what are your specs on the computer? If you have to reinstall it might be worth it to move up to 8.04 to get all the newest software. Also, for / it is usually a good idea to give at least 8gig (can be down with less but 8gig will give lots of room to expand.

I run a program called conky which allows you to have a display of your harddrive space (among other things) right on your desktop for easy and instant knowledge of your hard drive state.

---

### Post by ginestre on 2008-09-06
SOLVED

Thanks to everyone for helping me get to the bottom of this.

The problem was (as is so often the case) a mis-reading of the situation by the user (me). I continued wrongly to read error messages of lack of space on / as meaning lack of space on /home. This fundamental error led me to do irrelevant things.

The solution was firstly and most importantly to understand the error (big thanks to halitech), then to back up everything, and finally to use the GParted live cd to resize all of my partitions, and then bob was my uncle.

Thanks once again to everyone for help, encouragement and ideas.

---

### Post by halitech on 2008-09-06
glad we were able to get you back up and running without loosing any data and sometimes it takes an outside eye to see the actual problem when you've looked at something long enough and convinced yourself it is 1 problem when it is actually something else :)

---

