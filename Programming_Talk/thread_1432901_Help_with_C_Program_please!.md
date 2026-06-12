---
title: "Help: with C Program please!"
date: 2010-03-18
forum: Programming Talk
---

### Post by napz on 2010-03-18
Im still new to C programming. I just checked out google for examples of mkstemp but i still dun understand how to use it.

will someone tell me 

1) if i use mkstemp to make a temporary file from the original copy how do i read from it? 
2) to read do i need to store the value in a memory buffer?
3) if so how can i make my program works even if malloc allocate a size smaller than the file?

thanks lot advance

---

### Post by MadCow108 on 2010-03-18
first of all:
you should use tmpfile() or tmpname() defined in the C standard and thus more portable
[http://www.cplusplus.com/reference/clibrary/cstdio/tmpfile/](http://www.cplusplus.com/reference/clibrary/cstdio/tmpfile/)
[http://www.cplusplus.com/reference/clibrary/cstdio/tmpnam/](http://www.cplusplus.com/reference/clibrary/cstdio/tmpnam/)
tmpfile deletes the temporary file when its closed again.
if you want to keep it use tmpname and open it yourself.

1. mkstemp does not make a copy from anything. it modifies the char buffer you provide and creates a file with the name saved in the modified buffer.
it returns a file descriptor, so you should make a stream from it with fdopen
with that stream reading/writing is identical normal C file handling (fopen, fgets fwrite fclose etc.)

2. yes to read something from a file you need a location to save the read data.
note when you create a temporary file it is empty at first, so there is nothing to read

3. read from the file in chunks the size of your buffer until the file is read. if the filesize is unknown (e.g. your reading from a stream) either resize your buffer dynamically (realloc, only recommended for small files as this is slow and wastes memory) or make a new buffer when the current one is full.
How you handle buffering in detail is strongly dependent on what you actually want to read and how that data is handled.

if you don't need portability and just want to quickly read a small file, you can use the gnu extension getline
it reads data up to a delimiter and handles buffer sizing for you (by using realloc).
see:
man 3 getline

---

### Post by Compyx on 2010-03-18
> **MadCow108 said:**
> 
3. read from the file in chunks the size of your buffer until the file is read. if the filesize is unknown (e.g. your reading from a stream) either resize your buffer dynamically (realloc, only recommended for small files as this is slow and wastes memory) or make a new buffer when the current one is full.


How would creating a new buffer each time the old buffer is full speed up stuff? You'd still need to copy the contents of the old buffer into the new buffer, so you're basically doing what realloc does by hand and most probably slower since if realloc can resize the buffer without moving it, there's virtually no overhead.

Don't optimize things until you've shown they need to be optimized (by measuring), worry about writing clear and bug-free code first.

---

### Post by dwhitney67 on 2010-03-18
> **Compyx said:**
> How would creating a new buffer each time the old buffer is full speed up stuff? You'd still need to copy the contents of the old buffer into the new buffer, so you're basically doing what realloc does by hand and most probably slower since if realloc can resize the buffer without moving it, there's virtually no overhead.

Don't optimize things until you've shown they need to be optimized (by measuring), worry about writing clear and bug-free code first.

I agree, but I don't think that was what MadCow was implying, but I could be wrong.

If all the OP wants to do is make a copy of a file, then using a fixed-sized buffer would suffice.  There would be no need to use an allocation function, unless the buffer will be defined to be unusually large.

Something like this would suffice:
```

...

char buf[1024] = {0};
int  bytes = 0;

while ((bytes = fread(buf, 1, sizeof(buf) - 1, orig_file)) > 0)
{
   fwrite(buf, 1, bytes, tmp_file);
}

...

```

---

### Post by MadCow108 on 2010-03-19
> **Compyx said:**
> How would creating a new buffer each time the old buffer is full speed up stuff? You'd still need to copy the contents of the old buffer into the new buffer, so you're basically doing what realloc does by hand and most probably slower since if realloc can resize the buffer without moving it, there's virtually no overhead.

Don't optimize things until you've shown they need to be optimized (by measuring), worry about writing clear and bug-free code first.

not necessarily.
you could just swap the pointer of the full buffer with that of an uninitialized new buffer and placing the full buffer in some kind of list of full buffers.
Then you aren't copying anything and another thread could handle the list of buffers as they get available.
You could even skip the repetitive memory allocation if the handling thread gives back the handled buffers for reuse in the reading thread.
But this is a rather specialized case.

Dwhitney's point is probably the most important case next to reading it all in one chunk.
handle the buffer directly in the reading loop (and just copying the result of that) and reuse the same buffer in the next iteration.

---

### Post by Compyx on 2010-03-19
> **MadCow108 said:**
> not necessarily.
you could just swap the pointer of the full buffer with that of an uninitialized new buffer and placing the full buffer in some kind of list of full buffers.
Then you aren't copying anything and another thread could handle the list of buffers as they get available.
You could even skip the repetitive memory allocation if the handling thread gives back the handled buffers for reuse in the reading thread.
But this is a rather specialized case.

After I posted my answer I looked at your response again and got a feeling that's what you meant by allocating new buffers. That would indeed save you from realloc calls which may have to relocate chunks of memory. Although I think such an algorithm would be way too complicated for someone just starting to learn C and its standard library, such as the OP.

> **MadCow108 said:**
> 
Dwhitney's point is probably the most important case next to reading it all in one chunk.
handle the buffer directly in the reading loop (and just copying the result of that) and reuse the same buffer in the next iteration.

Yes, that's the way I'd do it, except I'd change the 'sizeof(buf) - 1' to simply 'sizeof buf': fread() doesn't read more than you tell it to, so the '-1' is unnecessary. Perhaps Dwhitney was thinking along the lines of strncpy which doesn't terminate a string with '\0' if there isn't room.

---

### Post by dwhitney67 on 2010-03-19
> **Compyx said:**
> 
Yes, that's the way I'd do it, except I'd change the 'sizeof(buf) - 1' to simply 'sizeof buf': fread() doesn't read more than you tell it to, so the '-1' is unnecessary. Perhaps Dwhitney was thinking along the lines of strncpy which doesn't terminate a string with '\0' if there isn't room.

For file copying purposes you are correct; the -1 was overkill.

However, if I wanted to perform string operations on the data, or even just print it, then one would want to preserve one-byte at the end of the buffer because a null-character would need to be inserted.
```

...

char buf[1024] = {0};
int  bytes = 0;

while ((bytes = fread(buf, 1, sizeof(buf) - 1, orig_file)) > 0)
{
   buf[bytes] = '\0';
   printf("%s", buf);
}

...

```

---

### Post by Compyx on 2010-03-19
> **dwhitney67 said:**
> For file copying purposes you are correct; the -1 was overkill.

However, if I wanted to perform string operations on the data, or even just print it, then one would want to preserve one-byte at the end of the buffer because a null-character would need to be inserted.
```

...

char buf[1024] = {0};
int  bytes = 0;

while ((bytes = fread(buf, 1, sizeof(buf) - 1, orig_file)) > 0)
{
   buf[bytes] = '\0';
   printf("%s", buf);
}

...

```

For reading character data (text files) I would use fgets(3). I use fread for binary data, e.g. data that can contain nul's ('\0'). But using fread on text files is fine if you don't need to do some line-based operations on the data. It's probably a bit faster than fgets, since fread doesn't have to check for '\n' on each call.

---

### Post by napz on 2010-03-23
> **dwhitney67 said:**
> For file copying purposes you are correct; the -1 was overkill.

However, if I wanted to perform string operations on the data, or even just print it, then one would want to preserve one-byte at the end of the buffer because a null-character would need to be inserted.
```

...

char buf[1024] = {0};
int  bytes = 0;

while ((bytes = fread(buf, 1, sizeof(buf) - 1, orig_file)) > 0)
{
   buf[bytes] = '\0';
   printf("%s", buf);
}

...

```

Thank you all for the advises :popcorn:
I'm thinking if it's possible to get the file size of a file? Then with the file size I make a copy using mkstemp? Then read the data from the copy file and write new data to the original file?

but in this case, there's still a need for me to use malloc right? in order to read()/ write() or I can just use an array[filesize]??

---

### Post by Compyx on 2010-03-23
You get the size of a file with stat(3), type 'man 3 stat' for more information. You would still need malloc to aquire a buffer to hold the file contents, or use C99's variable-length arrays.

Note that the information provided by stat cannot always be relied on, such as the size of special files in /proc:
```

compyx@aspire7730g:~$ ls -l /proc/cpuinfo 
-r--r--r-- 1 root root **0** 2010-03-23 18:15 /proc/cpuinfo
compyx@aspire7730g:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 Duo CPU     T5800  @ 2.00GHz
stepping	: 13
cpu MHz		: 800.000
cache size	: 2048 KB
...

```

So in my opinion the most reliable method of copying a file would be using the buffer approach. Reading an entire file into memory would be done using either realloc or just malloc using some data structure to keep track of where the chunks of the file are. (Which most likely would involve more malloc calls, since a linked list would be a good candidate for such a structure).

In the end, doing any serious work in C will require you to use malloc and friends at some point.

---

### Post by dwhitney67 on 2010-03-23
@ the OP -

IMO, it is not necessary to know the length (size) of a file in order to make a copy of such.  Just open the file, and read it's data into a comfortably-sized buffer, and then write this buffer to the destination file.  Repeat this process until you have reached the EOF marker of the source file.

You should not rationalize that there is any relationship between mkstemp() and making a copy of a file.  The former is merely a utility to create a 'unique' file.  What you do with the file is entirely up to you.

For the exercise you are discussing, usage of malloc() and calloc() are not necessary.  Use either if you wish, as an educational activity.


P.S.  If you are developing an elaborate application in which you may want to compare a file's size with the remaining space available on the HDD, then perhaps obtaining the file size would be in order.  As mentioned earlier, stat() is a handy tool for this.

---

