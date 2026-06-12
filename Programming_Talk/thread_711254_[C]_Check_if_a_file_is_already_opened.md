---
title: "[C] Check if a file is already opened"
date: 2008-02-29
forum: Programming Talk
---

### Post by Cene on 2008-02-29
Hello,

How can I check if a certain file is already opened via fopen() in C?

I know there is is_open() for C++. What is the equivalent for C?

---

### Post by kaens on 2008-02-29
I'm not entirely sure, but I don't think you can in standard C.

---

### Post by Kazade on 2008-02-29
I guess you could use ftell to get the current position in the stream. If it returns -1L then I think you can assume that it's closed (or there is something wrong anyway)

[http://www.cplusplus.com/reference/clibrary/cstdio/ftell.html](http://www.cplusplus.com/reference/clibrary/cstdio/ftell.html)

---

### Post by kaens on 2008-02-29
I'm not really a C coder, so I could be wrong on this, but that seems like that could get a bit sketchy.

---

### Post by Kazade on 2008-02-29
Yeh, it's not perfect. I guess it depends on the situation...

Obivously you can do this:

FILE* myFile = 0;
myFile = fopen(blah);
if (myFile == 0) {
   //something went wrong while opening
}

then when you close the file do this:

if (fclose(myFile) == 0) { //close was successful 
    myFile = 0;
}

So checking if myfile != 0 would be a check for openess. Unless of course something happened to the file between open and close (which will almost certainly leave a broken stream) in which case ftell would work. ftell returns -1 on error, if that happens then the file is not open and valid. 

It's not quite the same, you are assuming that a non valid stream is closed (which is not exactly what we want) but I believe that should be adequate.

---

### Post by Mr. C. on 2008-02-29
There is no way to know that another file is fopen'ed this way.  The same file may be opened by many processes.

ftell reports on the open stream supplied via the fp argument; it is not global and has no knowledge of other file pointers.

---

### Post by fyplinux on 2008-02-29
> **Mr. C. said:**
> There is no way to know that another file is fopen'ed this way.  The same file may be opened by many processes.

ftell reports on the open stream supplied via the fp argument; it is not global and has no knowledge of other file pointers.

Agree, you could use the file locking mechanism to keep the file synchronized globally.

---

### Post by mssever on 2008-02-29
Check out inotify. I'm not a C programmer, but it looks like inotify will tell you what you want. Note, however, that it's Linux-specific, so your program won't be portable.

---

### Post by Mr. C. on 2008-02-29
fopen calls are buffered.  They do not affect the file system immediately, and a file opened that has no writes or change activity will not yield a notification.

Inotify is useful to monitor changes in file system objects - not streams.

There is no simple way to do this, short of interrogating kernel data structures and following per-process structures (such as those present in /proc).

---

### Post by Kazade on 2008-03-01
Um, I don't think the OP needs to know whether *any* global file is open, they just need to do the equivalent of is_open() in C++. Which I would assume means they have  a FILE pointer and wants to know if it is open or not.

---

### Post by Mr. C. on 2008-03-01
That's a tough call to know what the OP meant.  I read it differently than you.

Asking if a stream to a given file is already open doesn't really make sense to me; the program(mer) should KNOW what streams it has successfully opened,and know the names of the files that correspond to the given file pointer.  So, I read this the other way.

In the case of the current process, you can use ftell to check for a -1 return, but must *also check errno* as -1 is a valid file position!

---

### Post by Kazade on 2008-03-01
"If an error occurs, -1L is returned, and the global variable errno is set to a positive value. This value can be interpreted by perror."

So it is, nice catch ;)

---

### Post by popch on 2008-03-01
Can one try and open the file for exclusive use?

---

### Post by the_unforgiven on 2008-03-01
> **popch said:**
> Can one try and open the file for exclusive use?
Yes, using the [flock(2)]("http://linux.die.net/man/2/flock") system call.

However, this is just **advisory** lock. I presume you know about advisory and mandatory locking in UNIX. If not, google for it.

---

### Post by Mr. C. on 2008-03-01
> **popch said:**
> Can one try and open the file for exclusive use?

Hmmm - that's odd.  I know I responded to this last night.  I guess my post failed to complete from the browser.

flock takes an FD, not FP, and is advisory as noted in the previous post.  Advisory means co-operative; processes must implement an agreed upon strategy for both using flock, and flock does not work over network file systems.

One could do an exclusiive access open() call, and then use fdopen() to associate a FILE * stream with the opened FD.

---

### Post by the_unforgiven on 2008-03-01
> **Mr. C. said:**
> Hmmm - that's odd.  I know I responded to this last night.  I guess my post failed to complete from the browser.

flock takes an FD, not FP, and is advisory as noted in the previous post.  Advisory means co-operative; processes must implement an agreed upon strategy for both using flock, and flock does not work over network file systems.

One could do an exclusiive access open() call, and then use fdopen() to associate a FILE * stream with the opened FD.
OR, you could simply do [fileno(3)]("http://linux.die.net/man/3/fileno") on the FILE* fp ;)
something like:
```

FILE *fp = fopen(file_path, "w+");
if(flock(fileno(fp), LOCK_EX) < 0)
{
    // exclusive lock failed
    // handle the condition
}

```
Also, as per the man page, flock() doesn't work for NFS. You should use fcntl() with F_SETLK instead.
But, the problem with fcntl() locking is that it's record-based. So, you need to wrap it to lock the entire file with proper l_whence, l_start and l_len params of the flock struct that goes as the argument to F_SETLK command.

---

