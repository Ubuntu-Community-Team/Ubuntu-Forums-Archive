---
title: "External Hard Drive Read Only"
date: 2012-04-20
forum: New to Ubuntu
---

### Post by freeztar on 2012-04-20
I have a HD hooked up via USB and it mounts fine and I can view the root directory, but when I try to go into subdirectories, it says I don't have permission.

I tried doing 'chown -R username /dev/sdf2' but it doesn't work, saying that it is a read only file system. I tried to change permissions in nautilus, but I get the same error.

What am I doing wrong and how do I fix this?

---

### Post by audiomick on 2012-04-20
What is the file system on the drive? You can only do a chown on a linux file system. NTFS and the other Windows formats don't accept Linux permissions.

If it is an NTFS drive, is it possible that it had an unclean unmount? I'm hazy on the details, but there is a protection mechanism that makes Linux systems see improperly unmounted NTFS drives read only. I believe you have to plug them in to a windows machine and run the windows Check Disk thing across them to free them up again.

---

### Post by freeztar on 2012-04-20
The drive was initiated on a Mac, so the file system is HFS.

---

### Post by audiomick on 2012-04-20
Ahh. I have a vague recollection of having heard/ read somewhere that this can be difficult, but cannot remember any details. Sorry. 

Wait a bit and see if someone else comes along. Maybe bump the thread tomorrow evening if no-one has answered.

I found this by searching the Ubuntu documentation. It doesn't look all that helpful, but does mention a couple of packages. Perhaps that will give you something to go on.

[http://askubuntu.com/tags/hfs%2B/new]("http://askubuntu.com/tags/hfs%2B/new")

---

### Post by freeztar on 2012-04-20
Thanks Michael! :)

I found a workaround by hooking it up to a Windows 7 machine and running a free program I found called 'HFS Explorer'. From there, I can export the files onto a NTFS drive so Windows can see it (and Linux too).

But I'd still like to know how to fix this within Linux. 

From the discussion from the link you posted, it seems like Linux is not supporting HFS that well. Just a matter of time I suppose...

I'll look for those hfs packages in the repository. Maybe that'll do the trick.

---

### Post by audiomick on 2012-04-21
> **freeztar said:**
> 
I'll look for those hfs packages in the repository. Maybe that'll do the trick.
Good luck with that. Mac stuff can be a bit tricky, I believe. They are, if anything, even more zealous than Microsoft about Client binding. On the other hand, there are a lot of people out there who are determined to make things work. ;)

---

### Post by mcduck on 2012-04-22
> **freeztar said:**
> Thanks Michael! :)

I found a workaround by hooking it up to a Windows 7 machine and running a free program I found called 'HFS Explorer'. From there, I can export the files onto a NTFS drive so Windows can see it (and Linux too).

But I'd still like to know how to fix this within Linux. 

From the discussion from the link you posted, it seems like Linux is not supporting HFS that well. Just a matter of time I suppose...

I'll look for those hfs packages in the repository. Maybe that'll do the trick.

Linux supports HFS very well, but HFS+ with journaling enabled is only supported in read-only mode.

---

