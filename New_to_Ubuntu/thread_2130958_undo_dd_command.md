---
title: "undo dd command?"
date: 2013-03-31
forum: New to Ubuntu
---

### Post by DarrenVortex on 2013-03-31
I just ran:
dd if=/dev/zero of=/swapfile bs=1024 count=8388608
And pressed ctrl+c in the middle of it. Got output:
742213+0 records in
742213+0 records out
760026112 bytes (760 MB) copied, 9.10778 s, 83.4 MB/s
There are not many beginner-friendly documentations out there for dd command, so even though I know what dd does, i don't know what it would do in this case: 
/swapfile partition doesn't exist by default
/dev/zero is not a real partition (or at least I don't know what it really is...) 
Can someone tell me what exactly happened here or how can I undo this?

---

### Post by ViliX64 on 2013-03-31
I don't think you can undo this command, because there is no backup for that.

---

### Post by DarrenVortex on 2013-03-31
but what happened here? Did I just create a new partition? was any data lost?

---

### Post by The Cog on 2013-03-31
dd is a utility for reading/writing data, often direct to disk hardware but also regular files. But I guess you knew that.

/dev/zero is being used as the input file. But in fact, /dev/zero is a dummy device driver that simply yields zero bytes for as long as you keep reading from it.

/swapfile would be a regular file located in the root directory. It's not normal to have such a file, so you would have created it.

The overall effect of the command is to create a file called /swapfile which contains 83 megabytes of zeros. I guess you are thinking of using it as swap space rather than using a normal swap partition.

P.S. this command would undo it:
```
sudo rm /swapfile
```

P.P.S:
For anyone else reading: 
**NEVER** use a dd command without understanding what it will do. It is most commonly used for directly writing to hard disks and this cannot be undone. This case is unusual in merely creating a regular file which can be deleted again.

---

### Post by DarrenVortex on 2013-03-31
Hello The Cog,
Just wanted to say thanks for the help. Ubuntu Forums is just such a warm and welcoming place!

---

