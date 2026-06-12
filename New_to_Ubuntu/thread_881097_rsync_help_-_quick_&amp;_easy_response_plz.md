---
title: "rsync help - quick &amp; easy response plz"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by Syndacate on 2008-08-05
Hey,

I just got a new hard drive and want to replace one of the drives in my dual drive enclosure (no, they're not raided).

I should be able to hook this up (to an internal SATA controller), and after it's mounted 'n all, simply go:

```
rsync -av /mnt/sdd5/* /mnt/sde5
```

Right?

I do believe that will work, but what I'm more concerned about is errors.  I don't want it to come into an error half way through like "*help, help, I can't read this one file*" and abort the process, as what tends to happen.  Though I do realize there's probably a "*don't stop on error*" option I rather have it do a direct copy, bit for bit, instead of each file, just in case it has trouble reading one.

So will rsync do a direct bit for bit copy, or is it more of a "file1, file2, file3,.." kind of deal?

Also, is there anyway (any option) that rsync can do a checksum on what it just copied (to make sure there were no errors while copying and that it matches up 100%)?

And is this better/worse than the command:

```
dd if=/mnt/sdd5/* of=/mnt/sde5
```

I do realize dd is bit for bit, which is probably better, but I hear so much good word about rsync.  Anybody know the good word on my situation, here?

---

### Post by pytheas22 on 2008-08-05
I'd use rsync over dd unless I were dealing with a corrupted file system.  Why:
> 
I don't want it to come into an error half way through like "help, help, I can't read this one file" and abort the process, as what tends to happen.

I believe that rsync calculates the list of all files that it needs to copy before it starts copying them--so if there's going to be a problem with some file, it will tell you before it starts copying, not in the middle.  I'm not positive that that's the way it works, but I'm pretty sure...I do know that it says something "generating file list" (which can take several minutes if you're copying a lot of stuff) before it starts any transfers.
> 
Also, is there anyway (any option) that rsync can do a checksum on what it just copied (to make sure there were no errors while copying and that it matches up 100%)?

I'm pretty sure that it does this automatically :)

In my experience, rsync is really smart and robust.  And in a worst case, if the transfer stops in the middle or some files don't get copied over properly (I guess you could do an md5 of the whole partition later on to check), just run rysnc a second time--the beauty of rsync is that it only copies over what's different, so it's not like you have to start the whole process over from the beginning if something goes wrong the first time.  It would only have to recopy what didn't get transferred successfully the first time.

---

### Post by Syndacate on 2008-08-05
> **pytheas22 said:**
> I'd use rsync over dd unless I were dealing with a corrupted file system.  Why:


I believe that rsync calculates the list of all files that it needs to copy before it starts copying them--so if there's going to be a problem with some file, it will tell you before it starts copying, not in the middle.  I'm not positive that that's the way it works, but I'm pretty sure...I do know that it says something "generating file list" (which can take several minutes if you're copying a lot of stuff) before it starts any transfers.


I'm pretty sure that it does this automatically :)

In my experience, rsync is really smart and robust.  And in a worst case, if the transfer stops in the middle or some files don't get copied over properly (I guess you could do an md5 of the whole partition later on to check), just run rysnc a second time--**the beauty of rsync is that it only copies over what's different,** so it's not like you have to start the whole process over from the beginning if something goes wrong the first time.  It would only have to recopy what didn't get transferred successfully the first time.

That's kick-***.

Anybody else have clarity on the parts he's not sure about?

---

