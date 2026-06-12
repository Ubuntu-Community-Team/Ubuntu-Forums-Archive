---
title: "What is the different&amp;contact between directory and file in Linux&amp;Unix?"
date: 2010-01-23
forum: Programming Talk
---

### Post by ~0o0~ on 2010-01-23
The first thread with my sorry english......(I am Chinese)
 
By reading the book, i knew that the function opendir() can be use to open a directory,and it will return a point of DIR.
 
Go on reading, i was tole that the function open() which action on files can also action on directory and it will return a descriptor form a directory. 
 
I am confused.
 
waiting and thanks for your answers....

---

### Post by user1397 on 2010-01-23
> **~0o0~ said:**
> The first thread with my sorry english......(I am Chinese)
 
By reading the book, i knew that the function opendir() can be use to open a directory,and it will return a point of DIR.
 
Go on reading, i was tole that the function open() which action on files can also action on directory and it will return a descriptor form a directory. 
 
I am confused.
 
waiting and thanks for your answers....well in theory, all folders/files in *nix are treated as files only...aka everything is a file.

if someone can elaborate on this, please do.

---

### Post by doorman on 2010-01-23
> **ubuntuman001 said:**
> well in theory, all folders/files in *nix are treated as files only...aka everything is a file.


That's true. The system makes no distinction between files, directories, sockets, etc. Everything is a file - they're just different types of files.

While a regular file's contents is "the usual stuff" - the data somebody wrote in it (eg. a text document), the contents of a "directory" (called directory file) is the list of files belonging to that particular directory. More precisely, it contains the inodes of the files.

You might find the book "Understanding the Linux kernel" really helpful in this matter ([http://oreilly.com/catalog/9780596000028](http://oreilly.com/catalog/9780596000028))

---

### Post by samjh on 2010-01-23
> **~0o0~ said:**
> By reading the book, i knew that the function opendir() can be use to open a directory,and it will return a point of DIR.
 
Go on reading, i was tole that the function open() which action on files can also action on directory and it will return a descriptor form a directory. 
 
I am confused.

**opendir(const char* name)** will return a pointer to a directory specified by *name*.  This pointer is an object type, DIR.  The pointer can be used to perform actions on the opened directory, similar to how FILE is used to perform actions on opened files.

**open(const char* pathname, int flags, mode_t mode)** will return a non-negative integer value called a "file descriptor".  A file descriptor is used to uniquely identify the opened file or directory (therefore, no two file descriptors will be the same).  You can supply this file descriptor to other functions such as fopendir.

---

### Post by denarced on 2010-01-23
there is another difference when comparing to windows
this might not be directly related to your question but here goes:
usually when you install something in linux, a bunch of files are created
if you install through apt for example, it creates files
In practise: pretty much all the system/software settings are in text files as oppose to window registry.

I might be a little off with this, so PLEASE correct me if I am.

---

### Post by ~0o0~ on 2010-01-23
:)
i think i will love this forum~.

thanks everybody...

---

### Post by ~0o0~ on 2010-01-23
Now, I know that the directory is only a different type of files. 

Then i view the directory like this :"vim directory", i had got something i had never seen befor.

It is a strange file i think.

&#12290;&#12290;..&#12290;&#12290;&#12290;&#12290;

in Cylinder group , there i node array , data block  and directory block , is the "directory block" equal the "directory" here?(sorry, some word translate from google...sorry....and thanks)

---

