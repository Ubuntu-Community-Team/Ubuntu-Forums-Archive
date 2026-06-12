---
title: "Ubuntu 12.04 took more space"
date: 2012-09-01
forum: New to Ubuntu
---

### Post by chitragurung on 2012-09-01
Hello,

I have dell mini netbook with 160 gb HD. After installing 12.04 it took almost 60 gb space. Is it because of installation error or it is normal ?

How to check this issues ?

---

### Post by Bashing-om on 2012-09-01
chit---

 Short answer is NO ! Here is what my fresh install of 12.04 looks like.
sysop1@1204-a:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdc1       462G  9.6G  429G   3% /
udev            1.9G  4.0K  1.9G   1% /dev
tmpfs           792M  864K  791M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G  156K  2.0G   1% /run/shm

As you can see around 10 gigs. use code:
```
df -h
```to see where all the space is used up on.
also take a look at your log files in /var/log/ for any large files.
[INDENT]regards <==BDQ
[/INDENT]

---

### Post by chitragurung on 2012-09-02
chitra@chitra-Inspiron-1011:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       148G   30G  111G  22% /
udev            489M  4.0K  489M   1% /dev
tmpfs           199M  812K  198M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            497M  224K  496M   1% /run/shm

this is the result of my space

---

### Post by Bodsda on 2012-09-02
> **chitragurung said:**
> chitra@chitra-Inspiron-1011:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       148G   30G  111G  22% /
udev            489M  4.0K  489M   1% /dev
tmpfs           199M  812K  198M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            497M  224K  496M   1% /run/shm

this is the result of my space

That output suggests you're actually using about 30GB of disk space, and I'll bet the majority of that is mainly installed programs and personal files

Bodsda

---

### Post by Bashing-om on 2012-09-02
chitragurung;

In regards to Bodsda's response (above) You can look at system resource usage with variations on this code:
```
du -h /home | sort -nr | less
``` The du command list disk usage for the /home directory (where user files are stored).
The -h option makes the size more readable. The output is fed into sort (piping) which organizes the output of du numerically (-n) and reverses the order to see what is largest first (-r). Finally,  this output is fed into less which allows you to scroll up and down through this large listing.
see:
```
man less
```for a good read.

  Remember to check your /var/log/ files for inordinate large volumes and ~/home/.xsessions -errors as well.
[INDENT]HTH <==BDQ
[/INDENT]

---

### Post by chitragurung on 2012-09-02
log folder has to be some system files or empty ? I confused which kind of files should delete from log folder  and home/xsession

---

### Post by Bashing-om on 2012-09-02
We are concerned for what is taking up space. As advised a fresh install should only consume about 10 gigs//all else is one of two things.
  1. lots of additional programs and/or files installed/loaded
   2. Faults in the system, reflected in LARGE sizes of various log files.

What I suggest is look at the file sizes in  the directory located at /var/log/ and also inspect the file located at ~/.xsession-errors (note the "." on .xsession); The dot makes this file as hidden, you can enable "show hidden files" from the "view" option in the task bar menu.

delete log files: If a new install, will not be required. If older install, the higher order files ending in .gz may safely be deleted (if there are no reasons to be troubleshooting).
The .xsession file is rewritten each boot(no delete).
[INDENT]regards <==BDQ
[/INDENT]

---

