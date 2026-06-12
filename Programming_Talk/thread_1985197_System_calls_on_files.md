---
title: "System calls on files"
date: 2012-05-23
forum: Programming Talk
---

### Post by glugT on 2012-05-23
Hi,

Some syscalls take file name as parameter and some syscalls take file descriptor as parameter.I would like to know why??

Thanks :)

---

### Post by roelforg on 2012-05-23
For the kernel, the name means nothing.
Every file has an inode (i don't feel like explaining how the kernel manages filesystems so you'll have to look that one up).
If you call "open", it'll go to the filesystem module and the inode corresponding to the path will be assigned an id, the fd.
This is because it's slow to lookup the inode by name, an id corresponding to a pointer to the inode is much faster.
The more fs operations you do, the more important that speed is.
That's why.

---

### Post by Bachstelze on 2012-05-23
A file descriptor is used only for I/O-related operations. Syscalls like execve() and friends have no use for it, and so they simply take the path.

---

### Post by glugT on 2012-05-23
> **Bachstelze said:**
> A file descriptor is used only for I/O-related operations. Syscalls like execve() and friends have no use for it, and so they simply take the path.



Can you elaborate.Open syscall uses file name and it returns the file descriptor.
Every other operation on file can be don with this fd.When and why will we need the file name(path)

---

### Post by roelforg on 2012-05-23
> **glugT said:**
> Can you elaborate.Open syscall uses file name and it returns the file descriptor.
Every other operation on file can be don with this fd.When and why will we need the file name(path)
 
Because there's a difference between editing files and executing them.
It's that when editing, a file lock needs to be held and lookup by name is too slow for the huge amount of fileops you do behind the screens.
When executing a filelock isn't desired and you read into mem at once.
It all has to do with what you're doing with a file.

---

### Post by glugT on 2012-05-24
> **roelforg said:**
> Because there's a difference between editing files and executing them.
It's that when editing, a file lock needs to be held and lookup by name is too slow for the huge amount of fileops you do behind the screens.
When executing a filelock isn't desired and you read into mem at once.
It all has to do with what you're doing with a file.


Executing a file meaning??
i saw that open,creat uses file name whereas read ,write uses file descriptor

---

### Post by Bachstelze on 2012-05-24
open() creates a file descriptor! Of course it can't use one, since none is available before it is called... creat() is obsolete and has been replaced by open(), the same applies to it.

---

### Post by ofnuts on 2012-05-24
> **glugT said:**
> Executing a file meaning??
i saw that open,creat uses file name whereas read ,write uses file descriptorYou can look at it another way. You use the name when you are only dealing with the "container" (moving it around, erasing it, etc...), and opening it to access its contents. You need a file descriptor when you deal with the "contents" (read/write), if only because this requires additional data structures (bufffers, read & write indexes) and the file descriptor can give access to them. 

A files descriptor also lets handle file contents that do not have any name associated to it (pipes, typically: stdin, stdout, sderr). 

Another advantage of the file descriptor is that even if the contents have a named container, an application can open the same file several times (think about an image viewer that displays an image and prepares thumbnails for all images in the same directory,  for instance) and obtain a different file descriptor so that each usage of the file will have its own set of associated data.

---

### Post by glugT on 2012-05-24
Thank you :)

---

### Post by glugT on 2012-05-25
> **Bachstelze said:**
> open() creates a file descriptor! Of course it can't use one, since none is available before it is called... creat() is obsolete and has been replaced by open(), the same applies to it.

i Know wrong mention of syscall,chmod and chown

---

### Post by glugT on 2012-05-25
i mean file is used in syscall chown and chmod

---

### Post by Bachstelze on 2012-05-25
Then refer to what ofnuts wrote.

---

