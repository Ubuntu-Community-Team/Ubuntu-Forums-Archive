---
title: "Compressor (file security)"
date: 2011-02-15
forum: Programming Talk
---

### Post by Zaycev on 2011-02-15
Hi,

Is it possible in anyway to load a file into memory and then run it
from there? I am working on a file compressor, that can compress and encrypt and save
multiple files as an exe file that can then run the compressed files
after unpacking them to a temp folder. The problem is that I have to
unpack the files to the hard-disk and then run them from there, making
them vulnerable to user that may try to get the original (unprotected)
files.

So the user shouldn't have access to the file operations in the
background. So I need to keep the original unpacked files hidden from
the user, until after they are opened by the unpacker and then deleted.
So users should have no kind of access to the files (should not see
them, open them, should not be able to modify or copy them) but the
unpacker should be able to run them. (that is why I think that the
memory is the best solution)

So is there any way to protect them, like unpacking them directly to
memory and then run them from there? Something like a virtual disk in
memory?

Thanks.

---

### Post by Zugzwang on 2011-02-15
I don't think that you can do what you want with 100% security in Linux, but here are are two hints for your further research on this subject matter that should get you started on your search:

[LIST]
[*]Perhaps you can use [FUSE]("http://fuse.sourceforge.net/") somehow to do what you want.
[*]There's also the possibility of running your program with LD_PRELOADing. Then you can reroute all accesses to file open/read/close functions to custom ones. Then, you would only need to extract the main program and leave it visible, but not the data files.
[/LIST]

---

### Post by juancarlospaco on 2011-02-15
You can read RAM on Linux.

Everything is a file on Linux, RAM too.

---

### Post by MadCow108 on 2011-02-15
why do you need to uncompress to hard disk in the first place?

all compression libraries should allow to decompress without actually saving the output to disk.
but even this is not really save, some systems can be setup to allow memory and fd dumps as unprivileged users with ptrace (e.g. older ubuntu versions)
To get relative save ram you probably need to use a managed environment like .net (for some examples see the keepass program).

So this can be a case of security theater. You might be better of using an unnamed tempfile.
create a temporary file with mkstemp and immediately unlink the file to remove it from the filesystem directory (or use tmpfile).
But its also not foolproof you should still be able to read the file with root privileges. But root can also read the ram so its the same.
also it is not portable

---

### Post by juancarlospaco on 2011-02-15
Doesn't matter if the file is on hard disk or ram, or compressed or not, 
but if its not encrypted it can be accessed anyways.

Theres a FUSE program that mounts a Encrypted Loop Filesystem,
it can be mounted on the hard disk or ram, but still encrypted, just best bet.

---

### Post by PaulReaver on 2011-02-15
exactly as juancarlospaco says

although if you want to have it memory you could copy it to /dev/shm (the ram disk)
but it will be readable until you either delete it from /dev/shm or power off the machine

---

### Post by worksofcraft on 2011-02-15
> **Zaycev said:**
> Hi,

Is it possible in anyway to load a file into memory and then run it
from there? I am working on a file compressor, that can compress and encrypt and save
multiple files as an exe file that can then run the compressed files
after unpacking them to a temp folder. The problem is that I have to
unpack the files to the hard-disk and then run them from there, making
them vulnerable to user that may try to get the original (unprotected)
files.

So the user shouldn't have access to the file operations in the
background. So I need to keep the original unpacked files hidden from
the user, until after they are opened by the unpacker and then deleted.
So users should have no kind of access to the files (should not see
them, open them, should not be able to modify or copy them) but the
unpacker should be able to run them. (that is why I think that the
memory is the best solution)

So is there any way to protect them, like unpacking them directly to
memory and then run them from there? Something like a virtual disk in
memory?

Thanks.

If I understand what you are trying to do is to make something like a self extracting executable.

I would look at the compression library known as [zlib]("http://en.wikipedia.org/wiki/Zlib"). I believe it may even have it's own encryption but failing that there was someone posted about their really nice encryption library right here on this forum and I'll try finding the link momentarily (*).

Now what you really seem to want is to build the encrypted and compressed data right into your executable ant that is quite easy just using standard tools:  See here is the command I use to convert a text file named "former.glade" into a linkable object module and then link it into former executable so it never needs to open a file for it's glade gui interface and I'm sure the same technique could be used for your application...
```

ld -r -b binary former.glade -o glade.o
g++ $CFLAGS -DTEST glade.o former.cpp -o former

```
anyway if that is what you need help with let me know and I'll get you some more info ;)

* p.s. flipping typical I just can't remember the guys name and I can't find the post or where I downloaded his source code from... but I can post the full archive that has all the usual auto tools and README malarkey... just nothing to say where it came from :(

---

### Post by slavik on 2011-02-16
Stop trying to invent new DRM, it will fail.

As for virtual disk, see ramdisk.

---

