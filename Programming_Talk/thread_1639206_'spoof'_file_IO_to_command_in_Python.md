---
title: "'spoof' file I/O to command in Python"
date: 2010-12-06
forum: Programming Talk
---

### Post by TiBaal89 on 2010-12-06
For commands that can operate in this way

```
$ ./command < infile > outfile
```

i'm having great success using the subprocess module, making stdin/stdout into PIPE's, using subprocess.popen.communicate, etc.

This is great because I can invoke these commands without going to disk - which is my goal here.

Say I have a command I need to run that is not programmed to use stdin/stdout but rather only operates as

```
$ ./command infile outfile
```

where the files are arguments.  Is there a way to invoke these commands using Python in such a way that I can avoid having to actually use an input and output file? 

Let me know if that didn't make any sense... :lol:

---

### Post by Zugzwang on 2010-12-06
Hmm, named pipes might do the trick:

[http://www.linuxjournal.com/article/2156](http://www.linuxjournal.com/article/2156)

This still needs a "little bit" of disk writing, but the actual communication between the processes will not go to disk if I see it correctly.

---

### Post by ssam on 2010-12-06
i have code that runs like that.
(see the Line.run() function at line 418 of [http://pyzgoubi.bzr.sourceforge.net/bzr/pyzgoubi/trunk/annotate/head%3A/zgoubi/core.py](http://pyzgoubi.bzr.sourceforge.net/bzr/pyzgoubi/trunk/annotate/head%3A/zgoubi/core.py) if you are interested)

i don't do anything clever with spoofing or pipes (this probably would not work if the program tries to seek.)

my advice would be to write the files to /dev/shm this is a ramdisk on the linux systems i have used, so there is no writes to disk.

---

### Post by roccivic on 2010-12-06
You could just write to RAM, not as fast as a pipe, but surely faster than the hard drive.

```
mkdir foo
sudo mount -t tmpfs -o size=1G,nr_inodes=10k,mode=0700 tmpfs foo
command infile foo/outfile
sudo umount foo

```

---

### Post by Arndt on 2010-12-06
> **TiBaal89 said:**
> For commands that can operate in this way

```
$ ./command < infile > outfile
```

i'm having great success using the subprocess module, making stdin/stdout into PIPE's, using subprocess.popen.communicate, etc.

This is great because I can invoke these commands without going to disk - which is my goal here.

Say I have a command I need to run that is not programmed to use stdin/stdout but rather only operates as

```
$ ./command infile outfile
```

where the files are arguments.  Is there a way to invoke these commands using Python in such a way that I can avoid having to actually use an input and output file? 

Let me know if that didn't make any sense... :lol:

An often used convention is to use a single hyphen for meaning stdin or stdout. For example grep and xmllint do this. But it has to be programmed - it's not automatic, so if you want it to happen to every command you invoke, this doesn't help.

---

