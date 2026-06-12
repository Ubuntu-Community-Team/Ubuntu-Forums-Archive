---
title: "A problem with code blocks"
date: 2012-08-11
forum: Programming Talk
---

### Post by radwa mohamed on 2012-08-11
I installed code blocks and wrote a very simple program
but it has a problem in running...


I get  
[COLOR="RoyalBlue"][SIZE="3"][FONT="Times New Roman"]
checking for existence: /media/DEFE10D5FE10A833/NEw/Hello/bin/Debug/Hello
Executing: xterm -T Hello -e /usr/bin/cb_console_runner LD_LIBRARY_PATH=$LD_LIBRARY_PATH:.  /media/DEFE10D5FE10A833/NEw/Hello/bin/Debug/Hello    (in /media/DEFE10D5FE10A833/NEw/Hello/.)
process terminated with status 0 (0 minutes, 1 seconds) [/FONT][/SIZE][/COLOR]

I checked for Hello file and found it 
and I have xterm program that is coming with ubuntu 12.04 without installing

so what is the problem ? 

and also when I checked setting of toolchain executables, I found the resource compiler is empty !! is this ok ? 


& I'm new on linux system so I want a simple explanation so that I can understand.


Thanks in advance

---

### Post by SuperCamel on 2012-08-11
What is the problem? The output you have posted appears normal. It looks like your 'Hello' program ran and then closed normally.

---

### Post by spjackson on 2012-08-11
It isn't clear from your post that anything is wrong.

Can you run the program successfully from a terminal window? Is  /media/DEFE10D5FE10A833/NEw/Hello/bin/Debug/Hello on a non-Linux filesystem e.g. FAT or NTFS USB device? This can be problematic - see many threads on this topic.

---

### Post by lisati on 2012-08-11
When running a command-line program, such as "Hello World", from a GUI-based IDE such as Code Blocks, it's sometimes useful to have a couple of lines asking you to "press any key to continue". This will help avoid having the output window disappear before you have a chance to read it.

---

### Post by radwa mohamed on 2012-08-13
I didn't mean that xterm is opened and closed quickly.
no, it's opened and shown the following

sh: 1: /media/DEFE10D5FE10A833/NEw/hello/bin/release/hello: Permission denied
process returned 126 ( 0X7E)             execution time : 0.002 s
press Enter to continue 

?!

---

### Post by spjackson on 2012-08-13
> **radwa mohamed said:**
> 
sh: 1: /media/DEFE10D5FE10A833/NEw/hello/bin/release/hello: Permission denied
process returned 126 ( 0X7E)             execution time : 0.002 s

As I said, is  /media/DEFE10D5FE10A833/NEw/Hello/bin/Debug/Hello on a non-Linux  filesystem e.g. FAT or NTFS USB device? This can be problematic.

Ditto for /media/DEFE10D5FE10A833/NEw/hello/bin/release/hello

The fact  that there are differences in case between your first post and this one suggests that the filesystem may well be FAT or NTFS.

Please post the output of
```

mount | fgrep /media/DEFE10D5FE10A833

```

---

### Post by radwa mohamed on 2012-08-14
the differences return to if I choose to create "debug" configuration or not.
I don't know if I should create that ot not !!

my windows depends on NTFS 


the output :
/dev/sda3 on /media/DEFE10D5FE10A833 type fuseblk ( rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)

---

### Post by spjackson on 2012-08-14
> **radwa mohamed said:**
> the output :
/dev/sda3 on /media/DEFE10D5FE10A833 type fuseblk ( rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
Ok, so you are building Linux binaries on an NTFS filesystem. As I said, this is problematic, though perhaps less so than FAT. There are many many threads about this. Personally, I like to avoid making things unnecessarily difficult for myself, so I would build somewhere below my home directory. I recommend that you do this.

However, if you want to do it the hard way, there are plenty of threads on this topic which you can read. They are beyond my comprehension. As far as I understand this minefield, I think those mount parameters are meant to be OK, i.e. it should be working, so I'm afraid that I don't know why it isn't.

---

