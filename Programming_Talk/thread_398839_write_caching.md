---
title: "write caching"
date: 2007-04-01
forum: Programming Talk
---

### Post by cdenley on 2007-04-01
I have a problem with USB drives that I believe is related to write caching.  My application writes binary data to the drives block device, which is unmounted. It thinks all the data has been written, but the filestream takes a while to close. I'm assuming this is because the data is still in cache waiting to be written. This is a problem because I need the actual writing progress, and it causes the application to become unresponsive even though the function is threaded.

I'm trying to find a way to disable write caching.  I would prefer a permanent solution that will prevent caching for all USB storage devices attached. These commands finish running after a few seconds, but don't seem to have any effect:
```
sdparm --clear=WCE=0 /dev/sdb
blktool /dev/sdb wcache off
```

It is a C# application running on Feisty. When writing to a file instead of a device, I don't have this problem.

In case it helps...
```
sdparm /dev/sdb
    /dev/sdb: LEXAR     JUMPDRIVE ELITE   2000
Read write error recovery mode page:
  AWRE        0  [cha: n, def:  0, sav:  0]
  ARRE        0  [cha: n, def:  0, sav:  0]
  PER         0  [cha: n, def:  0, sav:  0]
Caching (SBC) mode page:
>>> warning: mode page seems malformed, try '--flexible'
  WCE         0  [cha: n, def:  0, sav:  0]
  RCD         1  [cha: y, def:  1, sav:  1]
Control mode page:
>>> warning: mode page seems malformed, try '--flexible'
  SWP         0  [cha: n, def:  0, sav:  0]
Informational exceptions control mode page:
>>> warning: mode page seems malformed, try '--flexible'
  EWASC       0  [cha: n, def:  0, sav:  0]
  DEXCPT      0  [cha: n, def:  0, sav:  0]
  MRIE        3  [cha: y, def:  3, sav:  3]
```

---

### Post by cdenley on 2007-04-02
I figured it out. I think caching is used for all drives, it is just more apparent on USB flash drives because of the slow write speed. In order to make sure the data is physically written to the drive before it starts writing the next chunk of data, I needed to use the fsync system call.

Here is an example of my C# code I needed to add to wait for the cache to be written:
```
using Mono.Unix.Native;
...
int fd = Syscall.open ("/dev/sdc",
			OpenFlags.O_WRONLY | OpenFlags.O_CREAT | 
			OpenFlags.O_APPEND | OpenFlags.O_LARGEFILE);
Syscall.fsync(fd);
```

---

