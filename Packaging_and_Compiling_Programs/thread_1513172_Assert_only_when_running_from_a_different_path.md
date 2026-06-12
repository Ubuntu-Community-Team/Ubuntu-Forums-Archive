---
title: "Assert only when running from a different path"
date: 2010-06-19
forum: Packaging and Compiling Programs
---

### Post by supremo316 on 2010-06-19
I have a problem when running a program on Lucid LTS. 

The PC has two installs with dual boot: 8.10 ubuntu studio and Lucid LTS (gnome).

The programs were originally compiled on 8.10 and run fine there. I tried building and running on Lucid and I get the following assertion *after* a few memory allocs have already occurred:

malloc.c:4628: _int_malloc: Assertion `(unsigned long)(size) >= (unsigned long)(nb)' failed

The funny thing is I can run the same binaries (on Lucid) if I run them from the folder that was created in 8.10 but not if I copy them over to a folder I created on Lucid.

Any help will be appreciated.

---

### Post by SevenMachines on 2010-06-19
hi, is there any chance you could post/link to the code? this might be a bug in your code but could easily be a bug in the underlying libraries, its impossible to tell just from the description. if thats not possible if you could post a gdb backtrace of the crash, with your code compiled with debugging information.

---

### Post by supremo316 on 2010-06-19
> **SevenMachines said:**
> hi, is there any chance you could post/link to the code? this might be a bug in your code but could easily be a bug in the underlying libraries, its impossible to tell just from the description. if thats not possible if you could post a gdb backtrace of the crash, with your code compiled with debugging information.

I'm sorry but the code is proprietary to the company I work for. When I look at the backtrace using gdb it tells me about a 'new' call that ends up in malloc and finally crashes. But this new is only about the 5th in a series of memory allocs.

I find it really strange that the same binary will run from a different folder.

Here's the setup:
1. Folder *\home\myusername\project_bin* in one hard drive (this \home folder exists because of the ubuntu 8.10 installation.
2. Folder *\home\myusername\copy_bin* in the other hard drive. This /home folder exists because of the lucid installation.

The folders contain the same files (copy and paste not links). 
I log on to the lucid install and try to run the binary from 
the *\home\myusername\copy_bin* and this assert occurs. But when I run it from *\home\myusername\project_bin* while still logged in on lucid, it runs fine.

Maybe some hidden file wasn't copied. I'll try to make the copy again while logged in as root in the 8.10 install.

---

### Post by SevenMachines on 2010-06-19
i've seen the exact same error (i think) but for a number of fairly unrelated bugs which is why its hard to know without a stacktrace or something, though i totally understand thats not possible in this case.
if you find a small code test case that causes the same problem  you can post though i'll have another look though.
Aside from that I can only recommend that you look for some sort of directory 'hard wiring' in your code, obviously if theres something looking for 'project_bin' when you're now in 'copy_bin' then something not good is bound to ensue :)

---

### Post by supremo316 on 2010-06-22
The problem's narrowed down now. But that only makes it even more weird.

If the binaries and its shared objects (.so) are in ***any*** folder on the ext3 FS (the 8.10 install), then they run fine in Lucid. But if they are run from a FAT32 SD card or a ext4 FS (the Lucid install itself) the 'malloc' assertion occurs.:confused:

But the 8.10 install can run it from anywhere (ext3 or FAT32 SD card). It can't, of course, mount the ext4 FS to try and run it from there.

I guess I'll have to reinstall Lucid on an ext3 FS and try again. Sigh!

---

### Post by SevenMachines on 2010-06-22
curious, if you find out whats causing it or find the problem in something else i could look at please post your progress, i'd be interested to see the cause

---

