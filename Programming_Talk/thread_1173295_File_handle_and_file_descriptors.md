---
title: "File handle and file descriptors"
date: 2009-05-29
forum: Programming Talk
---

### Post by Rij on 2009-05-29
Hello,

It seems that there are certain file operations that require a file descriptor while others require a file handle. Is there a way to convert one to the other? Or are the same st of operations available with both handle and descriptor?

As an example. consider a looging function. I need to maintain a temp file where I log some messages continuously. Every 5 mins, I dump the tmp file into a permanent file.

My idea is to have one tmp file for this purpose. And after the dump, start using the same tmp file from the beginning. Now my limited knowledge told me that I should truncate the file (to make sure all previous data is erased) and set the file offset to the beginning (for obvious reasons). But while the former takes a dscriptor, the latter takes a handle. 

So what do I do?

As an aside, do you suppose that instead of doing the above, if I just closed and repoened the tmp file, it would be just as fast, if not faster?

---

### Post by decoherence on 2009-05-29
Sorry, are you talking about file operations in C?

If you're talking about shell scripting, I think perhaps you've over-complicated it or I don't understand what you're trying to do. Code samples would help, even if you think they're broken.

---

### Post by Rij on 2009-05-29
I am speaking of C. 

Sorry, I should have made that clear.

---

### Post by decoherence on 2009-06-01
> **Rij said:**
> I am speaking of C. 

Sorry, I should have made that clear.

Hi Rij. Sorry for the delayed response.

If you haven't already, I suggest you ask the question in the programming section of the forum. You're more likely to get a response there.

---

### Post by nvteighen on 2009-06-01
> **Rij said:**
> Hello,

It seems that there are certain file operations that require a file descriptor while others require a file handle. Is there a way to convert one to the other? Or are the same st of operations available with both handle and descriptor?

As an example. consider a looging function. I need to maintain a temp file where I log some messages continuously. Every 5 mins, I dump the tmp file into a permanent file.

My idea is to have one tmp file for this purpose. And after the dump, start using the same tmp file from the beginning. Now my limited knowledge told me that I should truncate the file (to make sure all previous data is erased) and set the file offset to the beginning (for obvious reasons). But while the former takes a dscriptor, the latter takes a handle. 

So what do I do?

As an aside, do you suppose that instead of doing the above, if I just closed and repoened the tmp file, it would be just as fast, if not faster?
Er... what you could do is use **freopen()**... Look at its manpage. Or **tmpfile()**...?

Of course, using file descriptor functions will always be faster, as those are much lower level than their file handle counterparts.

Anyway, there might be some design issue. I don't see why you have to clear the temp file after each dump; just leave it there... If you use tmpfile() (which generates a file in "w+b" mode with some non-clashing random name at /tmp), it will be destroyed when closing the file or the application. You'll have to use binary read/write functions, fread() and fwrite(), but you could also create some temp file in a regular way using fopen() in a place different to /tmp.

---

### Post by Reiger on 2009-06-01
This is all IIRC stuff, but here goes:

File descriptors are essentially a pointer/OS-generated-index to the corresponding I/O buffers for use with/by I/O device drivers (could be a shared memory manager, could be a file system driver, could be any other IO device). A typical use case of file descriptors is implementing Inter Process Communication with pipes (like the shell does): routing input and output of processes to other processes by means of shared memory resources.

File handles are an abstraction which move away from the concept of (possibly shared) buffers, towards the concept of arbitrarily user-defined and named streams: the entire memory management component is simplified to the point of open-a-stream and close-a-stream.

---

