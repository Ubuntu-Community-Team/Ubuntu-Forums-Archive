---
title: "Is there a way to generate a temporary pseudo filesystem like procfs in the userland?"
date: 2009-04-12
forum: Programming Talk
---

### Post by Jiraiya_sama on 2009-04-12
I'm wanting to create a program that you assign a default directory in your /home folder. Once it starts I want it to create something like /proc in that directory where you can interact with it by changing the values in the files.

---

### Post by EnglishSparrow on 2009-04-12
Why not just a folder? Or create a filesystem file that can be mounted into a directory, like a .ext3.

---

### Post by Jiraiya_sama on 2009-04-12
I don't want to read and write to files on the disk at all times. I want my program to be easily extensible via bash and perl scripting via editing files while not doing unnecessary writes to the disk.

---

### Post by EnglishSparrow on 2009-04-12
> **Jiraiya_sama said:**
> I don't want to read and write to files on the disk at all times. I want my program to be easily extensible via bash and perl scripting via editing files while not doing unnecessary writes to the disk.

**Then do it!** :D

Mount the fake filesystem, run program, then unmount it. Although this would be like running a Livecd and then removing the ram...

---

### Post by Jiraiya_sama on 2009-04-12
The program needs to do it without mount. I found an example of what I'm talking about: [II]("http://en.wikipedia.org/wiki/Ii_(IRC_Client)"). Downloading and compiling it now. Hopefully it does everything I want it to do. Then I can create my program.

---

### Post by jimi_hendrix on 2009-04-12
you cant read from a file without reading from disk...

---

### Post by sujoy on 2009-04-12
sounds like plan9 (the one in wmii).

---

### Post by EnglishSparrow on 2009-04-12
> **Jiraiya_sama said:**
> The program needs to do it without mount. I found an example of what I'm talking about: [II]("http://en.wikipedia.org/wiki/Ii_(IRC_Client)"). Downloading and compiling it now. Hopefully it does everything I want it to do. Then I can create my program.

You NEED a mounted filesystem for the application to reside lol.


The program can simply load into memory if thats what you want -but thats all on the program side.

Perhaps do it like I said, with a filesystem located inside a file, similar to what wubi does.

Good luck...

---

### Post by jpkotta on 2009-04-12
If you don't want to write to the disk, use tmpfs.
```
mount -t tmpfs none /mountpoint
```

---

### Post by stroyan on 2009-04-12
You can use "FUSE: Filesystem in Userspace" to make a program present a directory of files without any disk involved.
See [http://fuse.sourceforge.net](http://fuse.sourceforge.net).
On ubuntu you can use "sudo apt-get install libfuse-dev"
and then look at examples and documentation in
/usr/share/doc/libfuse-dev/ .

---

### Post by slavik on 2009-04-12
tmpfs that is stored in ram?

---

### Post by soltanis on 2009-04-12
If you're talking about the ii program from suckless.org, they use mkfifo to create named pipes, I believe. I'm 99% sure they don't use fuse (how else could you fit all that into 500 lines of code?).

[man mkfifo]("http://linux.die.net/man/3/mkfifo")

---

### Post by Jiraiya_sama on 2009-04-12
> **soltanis said:**
> If you're talking about the ii program from suckless.org, they use mkfifo to create named pipes, I believe. I'm 99% sure they don't use fuse (how else could you fit all that into 500 lines of code?).

[man mkfifo]("http://linux.die.net/man/3/mkfifo")

That looks like what I was looking for, thanks much.

EDIT: It wasn't exactly what I was looking for, but it's still very cool and useful. Thanks.

---

