---
title: "df command execution and segmentation fault"
date: 2023-01-10
forum: New to Ubuntu
---

### Post by rajeshraoshindhe on 2023-01-10
I get  segmentation fault when I try to execute commands like df, cal, etc. Why does this happen ? Can anyone please tell me how to overcome this ?

---

### Post by QIII on 2023-01-10
It would be quite helpful if you would post the entirety of the command issued and the results.

A segfault is most often raised by an attempt to access or write to an illegal memory location.

---

### Post by Impavidus on 2023-01-10
Segmentations faults are normally the result of a bug in the program, so that's an error made by the programmer. It's somewhat unlikely such an error would be present in such commonly used tools, so I think something else must be going on. Is the tool used with a different version of the library than it was compiled for? Shouldn't happen if you installed all from the official repos.

Could you tell which version of Ubuntu you have installed?

---

### Post by TheFu on 2023-01-10
If the disk used for temporary storage is 100% full, that can cause programs to crash.  Remove some times and check that you don't have run-away log files eating all the storage.
```
journalctl --disk-usage
sudo journalctl --vacuum-size=200M
```
will let you see and massively reduce log file storage use for a bit.  You'll need to figure out the root issue or later today, the same problem will happen.

Or it could be the other things mentioned above, but let's be optimistic and hope it is just huge log files.  It is possible to limit the number and sizes of log files, BTW.

---

