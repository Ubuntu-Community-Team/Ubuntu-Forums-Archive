---
title: "Ubuntu 12.04 consuming too much space"
date: 2012-06-12
forum: New to Ubuntu
---

### Post by sudokurubik on 2012-06-12
Using the 11.10 version I did not have any problem concerning space -I had more than 4GiB free but since I started with 12.04 it has been consuming more and more space and now I just have 1,5GiB left. I've used cleaner apps and the recovery menu as well in order to solve this problem but it is not enough.What can I do?

---

### Post by BarfBag on 2012-06-12
Good grief!  That's terrible!  Would you please list your processes?

---

### Post by Randy M on 2012-06-12
I had the same problem. I used this command to find the large log files that had been created during installation.
 
find ~ -size +500M
 
I'd ask the experts here before deleting anything, but this will at least tell you where the space is going.

---

### Post by VE6EFR on 2012-06-12
Out of curiosity, how large is your drive?

---

### Post by sudokurubik on 2012-06-12
> **VE6EFR said:**
> Out of curiosity, how large is your drive?
Is 31,1 GiB enough for Ubuntu? :( I installed it in one disk apart from others I'm using

---

### Post by sudokurubik on 2012-06-12
> **Randy M said:**
> I had the same problem. I used this command to find the large log files that had been created during installation.
 
find ~ -size +500M
 
I'd ask the experts here before deleting anything, but this will at least tell you where the space is going.
Thank you! :)

---

### Post by sudokurubik on 2012-06-12
What do you mean by 'processes'? The apps which are working?

---

### Post by steeldriver on 2012-06-12
you probably want something more like

```
sudo find / -type f -size +500M
``````
find ~
```only looks in your home dir

I had the same issue after a recent install and it turned out to be /var/log/kern.log filling with errors from a graphics driver

---

### Post by VE6EFR on 2012-06-12
> **sudokurubik said:**
> Is 31,1 GiB enough for Ubuntu? :( I installed it in one disk apart from others I'm using

So what you are saying is that Ubuntu is taking up 27 GB of space just for the operating system?

---

### Post by sudokurubik on 2012-06-12
> **VE6EFR said:**
> So what you are saying is that Ubuntu is taking up 27 GB of space just for the operating system?
Yes :( I blame 12.04 updates, I always accept them

---

### Post by steeldriver on 2012-06-12
you could also use 'du' to find the disk usage by directory, e.g.

```
sudo du -h --exclude='proc' / | sort -hr | head -20
```for a list of the top 20 biggest directories in descending order

---

### Post by mutap on 2012-06-12
This sound very strange(or maybe you /home is on the same partition?)...
Post output of 
df -h

---

### Post by drs305 on 2012-06-12
It's most likely not updates. It could be duplicity/deja-dup doing automatic backups.

In most cases, the loss of disk space is due to undeleted trash remaining the trash bins (yours and roots), large log files, and backups made to the / partition instead of to a backup partition.

The commands to find large files should help, but won't detect all the problems above.

I created a thread about vanishing disk space a while ago that still should be helpful finding out what is happening.

[HowTo: Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

---

