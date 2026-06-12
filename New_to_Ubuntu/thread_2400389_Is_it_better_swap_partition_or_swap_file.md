---
title: "Is it better swap partition or swap file?"
date: 2018-09-05
forum: New to Ubuntu
---

### Post by rocco.martinello on 2018-09-05
I have dual boot: Windows 10 and Ubuntu 18.04.1.
I deleted swap file and I created a swap partition instead.
Is it better a swap file or a swap partition?

---

### Post by #&amp;thj^% on 2018-09-05
Actually it doesn't make a lot of difference as long as you don't use sparse files. 
[http://en.wikipedia.org/wiki/Sparse_file](http://en.wikipedia.org/wiki/Sparse_file)

On hard disks, throughput and seeking is often faster towards the beginning of the disk, because that data is stored closer to the outer area of the disk, which has more sectors per cylinder. Thus, creating the swap at the beginning of the disk might improve performance.
One might get better performance, since there's less seeking to swap.
IMHO a partition is probably the better way, performance wise, though a file is more flexible. Just make sure that it's on a 7200+ RPM spindle. 

About the only benefit of a dedicated swap partition is guaranteed un-fragmentation when you need to expand it; if your swap will never be expanded, a file created on a fresh filesystem doesn't require an extra partition.
Just my 2 cents worth.

---

### Post by oldrocker99 on 2018-09-05
In many Ubuntu installations over the last 10 years, a swap partition is created by default. I prefer a swap partition, as it has a different file system for speed. Swap files can be messy.

---

### Post by oldfred on 2018-09-05
You do not want to actually use either one. 
So if you have 4GB of RAM or more, it will make little difference unless you like to keep every program you have running at same time or want to edit large videos in RAM.

---

### Post by #&amp;thj^% on 2018-09-05
> **oldfred said:**
> You do not want to actually use either one. 
So if you have 4GB of RAM or more, it will make little difference unless you like to keep every program you have running at same time or want to edit large videos in RAM.

+1 :)
```
free
              total        used        free      shared  buff/cache   available
Mem:       12207872     2033616     8837220      196988     1337036    10254592
Swap:             0           0           0

Now with swap:
me on Wed Sep 05 at 01:36 PM in ~ branch: (HEAD) 
>> sudo swapon -a


me on Wed Sep 05 at 01:36 PM in ~ branch: (HEAD) 
>> free
              total        used        free      shared  buff/cache   available
Mem:       12207872     2036764     8833952      197000     1337156    10251444
Swap:       3145724           0     3145724

```
Agree with oldfred unless like myself you edit large videos in RAM>>>and I still haven't touched swap yet. (Please Note: I have 12 Gigs of RAM)

---

### Post by Tadaen_Sylvermane on 2018-09-11
I keep a 2gb partition for swap. Only reason i dont use a swapfile is i have multiple installs sharing the same swap partition. Better than having 5 swapfiles. 

I dont know if i need swap. I know some things expect it still. No sense doing that equal to ram thing though imo.

---

