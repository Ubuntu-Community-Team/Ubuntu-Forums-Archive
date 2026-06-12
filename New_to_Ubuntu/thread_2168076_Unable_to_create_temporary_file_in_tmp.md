---
title: "Unable to create temporary file in /tmp"
date: 2013-08-16
forum: New to Ubuntu
---

### Post by deeppow on 2013-08-16
Ubuntu 12.04 LTS on my laptop

Was trying to run NVIDIA driver install from console startup using
"sudo sh ./NVIDIA-...."  Yes, I was doing it in the correct directory to run and file was set to +x.

Get the message "Unable to create temporary file in /tmp"

?

---

### Post by GwL3eNC on 2013-08-16
Hello,

is it possible that you got not enough space on tmp? you can try

sudo mount -t tmpfs -o remount,size=5m,mode=1777 tmp /tmp

to change the size of tmp without restart. Here to 5MB. Hope it helps.

---

### Post by tgalati4 on 2013-08-16
Try the following:

```
free
cd /tmp
sudo su
./NVIDIA*
```

First determine that you have enough free space on your disk.  I presume that this is not a virtual machine.  Otherwise, make a directory in your directory, copy the file over and run it from there.

---

### Post by deeppow on 2013-08-16
> **GwL3eNC said:**
> Hello,

is it possible that you got not enough space on tmp? you can try

sudo mount -t tmpfs -o remount,size=5m,mode=1777 tmp /tmp

to change the size of tmp without restart. Here to 5MB. Hope it helps.

When I try the command, it says "mount: /tmp not mounted or bad option".  While I'm not expert with Ubuntu, I don't see anything wrong with the command.

Doing a "sudo du -hs /tmp" it shows the size of 44K.  And doing a  "sudo du -hs /tmp/*" shows the folders with /tmp being a total of 28K so  appears to me that /tmp has some free space.  I'm not sure if that is enough or not.

---

### Post by GwL3eNC on 2013-08-16
Hello,

please forgive me, i believe my idea was wrong. Can you post me the link to your driver.
I would like to know if it have some command line options. I cant promise something. Hopefully
some other people also take a look on your problem.

PS: No error, but it wont work like i thought 

sudo mount -t tmpfs -o size=5m mode=1777 /tmp

---

### Post by deeppow on 2013-08-16
The driver was download from [http://www.geforce.com/drivers](http://www.geforce.com/drivers) using the following manual search input:
GeForce
GeForce 600M Series (Notebooks)
GeForce GTX 675M
Linux 64-bit
English (US)
All

I then downloaded "NVIDIA-Linux-x86_64-319.32.run" and stored it for execution.

---

### Post by GwL3eNC on 2013-08-16
phu, i found something. For the installation it's importand that you read that

[http://us.download.nvidia.com/XFree86/Linux-x86_64/319.32/README/installdriver.html](http://us.download.nvidia.com/XFree86/Linux-x86_64/319.32/README/installdriver.html)

If i use

./NVIDIA-Linux-x86_64-319.32.run --advanced-options

i can see a list of all otions the script provide. One is:

 --tmpdir=TMPDIR
      Use the specified directory as a temporary directory when
      downloading files from the NVIDIA ftp site; if not given,
      then the following list will be searched, and the first one
      that exists will be used: /tmp, /tmp, ., /home/fidel.

I realy hope this solves your problem. But also, if you dont shutdown X like mentiond in
the readme the create error can appear (i think). If this not work i'm out of range.

---

### Post by deeppow on 2013-08-16
Thanks GwL3eNC, I'll give that a try.

---

### Post by deeppow on 2013-08-17
OK, got the Nvidia setup installed.  Thanks GwL3eNC.

But I have another problem.  I'll post that as a new thread.

---

