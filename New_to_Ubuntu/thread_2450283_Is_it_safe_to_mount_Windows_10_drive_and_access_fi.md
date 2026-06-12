---
title: "Is it safe to mount Windows 10 drive and access files?"
date: 2020-09-10
forum: New to Ubuntu
---

### Post by j2ee on 2020-09-10
Any possible way that the Windows 10 drive would infect Ubuntu? Any suggestion?

---

### Post by CelticWarrior on 2020-09-10
Infection not a problem.

It isn't safe for Windows. Always avoid accessing the Windows system partition. If you need to share data use another NTFS formated partition and, of course, always disable Fast Startup in Windows.

---

### Post by j2ee on 2020-09-10
> **CelticWarrior said:**
> Infection not a problem.

It isn't safe for Windows. Always avoid accessing the Windows system partition. If you need to share data use another NTFS formated partition and, of course, always disable Fast Startup in Windows.

Thx for sharing. Why not safe for Windows?

---

### Post by CelticWarrior on 2020-09-10
Windows often interprets those accesses as suspicious or file/file system corruption. Most of the times - with Fast Startup disabled - nothing happens but sometimes it creates a problem and in extreme cases Windows may not boot. 

As there's really no need to do that we strongly recommend against it. Again, use a separated NTFS partition that can be read by both OSes.

---

### Post by j2ee on 2020-09-10
> **CelticWarrior said:**
> Windows often interprets those accesses as suspicious or file/file system corruption. Most of the times - with Fast Startup disabled - nothing happens but sometimes it creates a problem and in extreme cases Windows may not boot. 

As there's really no need to do that we strongly recommend against it. Again, use a separated NTFS partition that can be read by both OSes.

Only if I update files in Windows drive? How about just read files?

So safe to access ntfs partitions that were created by windows as long as I dont update files in the partition with Windows in it?

---

### Post by CelticWarrior on 2020-09-10
Reading shouldn't be a problem but any change can be.

It doesn't matter "who" created the partitions. Whether it's a system partition or just a data partition matters. This really shouldn't be hard to understand.

---

### Post by j2ee on 2020-09-10
> **CelticWarrior said:**
> Reading shouldn't be a problem but any change can be.

It doesn't matter "who" created the partitions. Whether it's a system partition or just a data partition matters. This really shouldn't be hard to understand.

How about updating files in the windows partition but not the windows folder?

---

### Post by CelticWarrior on 2020-09-10
> **j2ee said:**
> How about updating files in the windows partition but not the windows folder?

Already answered.
I've said my piece and gave you sound advice according to the "best practices" everybody who knows a little bit of this uses.

From now on you do what you want and if problems arise you should now be aware of the reason. Nothing else to discuss here.

---

### Post by Impavidus on 2020-09-10
Any modification in the file system can be problematic, including changes to file access times. It is possible to mount the C partition read-only, but there shouldn't really be a need for that. See [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab). If it sounds hard, don't try.

---

