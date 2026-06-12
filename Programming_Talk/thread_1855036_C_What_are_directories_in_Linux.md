---
title: "C: What are directories in Linux?"
date: 2011-10-05
forum: Programming Talk
---

### Post by Pithikos on 2011-10-05
I am trying to list out the files in a directory in pure C. From one book I read(Linux Kernel Development) the idea that I got is that every file we see is just a string and every directory is a longer string with the names of the files that are inside that directory.

Then in my C program I  have this:
```

    DIR* dir_p;
    struct dirent *dir_meta_p;
    
    // open dir
    dir_p=opendir(dirname);

    // read dir
    dir_meta_p=readdir(dir_p);
    
    // show something so I know it works
    puts(dir_meta_p->d_name);
```To be honest I was expecting to see the directory name on the screen but instead I see a single file printed out in terminal. Running the last command twice gives the same file which I find even more puzzling. Can anyone explain this behaviour? If a directory is indeed just a string with the filenames shouldn't then I get the second file when running a second read?

---

### Post by karlson on 2011-10-05
> **Pithikos said:**
> 
Then in my C program I  have this:
```

    DIR* dir_p;
    struct dirent *dir_meta_p;
    
    // open dir
    dir_p=opendir(dirname);

    // read dir
    dir_meta_p=readdir(dir_p);
    
    // show something so I know it works
    puts(dir_meta_p->d_name);
```
To be honest I was expecting to see the directory name on the screen but instead I see a single file printed out in terminal. Running the last command twice gives the same file which I find even more puzzling. Can anyone explain this behaviour? If a directory is indeed just a string with the filenames shouldn't then I get the second file when running a second read?

Why would running "puts" give you different output the second time from the first time?  You haven't updated the struct.  When you opendir and then readdir you are returned the pointer to the first element stored in the "directory".

I suggest you do: 
```

man readdir

```
it has a pretty good example.

---

### Post by Pithikos on 2011-10-05
> **karlson said:**
> Why would running "puts" give you different output the second time from the first time?  You haven't updated the struct.  When you opendir and then readdir you are returned the pointer to the first element stored in the "directory".

I suggest you do: 
```

man readdir

```it has a pretty good example.

Well if the readdir() function gives me the first file in that directory I thought that the function has a buffer and thus running it again would give me the second file in the directory.
I read the manpage but it doesn't have any explaining besides this:
```
d_name[256]; /* filename */
```Which doesn't tell me much. Is it the filename of a file in the directory or the filaname of the directory itself? Because from an other resource I read that indent is just metadata for a directory. I have a hard time to grasp the bigger picture of what is going on :(

---

### Post by Arndt on 2011-10-05
> **Pithikos said:**
> Well if the readdir() function gives me the first file in that directory I thought that the function has a buffer and thus running it again would give me the second file in the directory.
I read the manpage but it doesn't have any explaining besides this:
```
d_name[256]; /* filename */
```Which doesn't tell me much. Is it the filename of a file in the directory or the filaname of the directory itself? Because from an other resource I read that indent is just metadata for a directory. I have a hard time to grasp the bigger picture of what is going on :(

You are meant to call 'readdir' repeatedly, until it returns NULL. Each time, it will return another filename.

What does "indent" mean here, by the way?

---

### Post by karlson on 2011-10-05
> **Pithikos said:**
> Well if the readdir() function gives me the first file in that directory I thought that the function has a buffer and thus running it again would give me the second file in the directory.

Right.
> 
I read the manpage but it doesn't have any explaining besides this:
```
d_name[256]; /* filename */
```
Which doesn't tell me much. Is it the filename of a file in the directory or the filaname of the directory itself? Because from an other resource I read that indent is just metadata for a directory. I have a hard time to grasp the bigger picture of what is going on :(

The readdir will return you "a pointer to the structure representing the element at the current position in the directory stream".  So the first call will return the first element, second will return the next, etc, etc.

Not sure what metadata your other source was referring to.

---

### Post by nvteighen on 2011-10-05
Directory manipulation works basically as file manipulation: each new call to readdir() iterates the directory until NULL is found... like when you do fgets() to get a line from a file. There's rewinddir() to "rewind" the structure back to the start if needed, exactly like files are rewinded by using rewind().

---

### Post by Pithikos on 2011-10-05
> **Arndt said:**
> You are meant to call 'readdir' repeatedly, until it returns NULL. Each time, it will return another filename.

What does "indent" mean here, by the way?

I'm sorry. I meant "dirend" which is just some datastructure. A pointer to that struct is returned when running readdir().

Still kind of confusing why the thing is called readdir. It should be called readfile if my intuition is correct.

---

### Post by Bachstelze on 2011-10-05
> **Pithikos said:**
> 
Still kind of confusing why the thing is called readdir. It should be called readfile if my intuition is correct.

Of course not. It reads the directory, not the file...

---

### Post by Arndt on 2011-10-06
> **Pithikos said:**
> I'm sorry. I meant "dirend" which is just some datastructure. A pointer to that struct is returned when running readdir().

Still kind of confusing why the thing is called readdir. It should be called readfile if my intuition is correct.

It's fully possible for you to read the directory itself as a file, but the format is very much platform-dependent. So yes, readdir reads a file, but it only handles the binary format of one particular sort of file, namely a directory.

How would you like to do it instead?

---

### Post by Pithikos on 2011-10-06
Well if everything is a file in linux.. then I expect to be able and cat a directory. In the book it says that a directory is nothing more than a string that contains all the files that reside in it(or at least that's what I understood). So I would expect to
```
cat directory
```and getting something like this
```
\STARTfile1\0file2\0file3\0\END
```Here is a quote from the book:
> A file is an ordered string of bytes. The first byte marks the beginning of the file and the last byte marks the end of the file.
..
In Unix, directories are actually normal files that simply list the files contained therein.From what I have understood so far *inode* is the core of the file. What we see in nautilus is just the file names(assuming dirs are also files). But when we cat a file.. what do we get then? It goes filename->inode->filedata? And why can't we cat a directory then?

---

### Post by Pithikos on 2011-10-06
> **Arndt said:**
> It's fully possible for you to read the directory itself as a file, but the format is very much platform-dependent. So yes, readdir reads a file, but it only handles the binary format of one particular sort of file, namely a directory.

How would you like to do it instead?

Forgot to answer that. Well if a directory is just a string that contains filenames, I would expect to ```
readfile(directory)
``` Then I would expect there to be a function that can get each filename from that string.

---

### Post by karlson on 2011-10-06
> **Pithikos said:**
> Forgot to answer that. Well if a directory is just a string that contains filenames, I would expect to
```
readfile(directory)
```
Then I would expect there to be a function that can get each filename from that string.

Technically you might be able to "open" and read the directory as a file although I haven't tried doing it this way and read it.  The directory is not actually a string containing names of the files in it.

At the very least it contains file names associated with it and the starting inode of each file.  In fact it actually contain more information but let's just stick with this.  So if you choose to read the directory as a file you would need a way to interpret that data to actually be able to get to the files, which dirent presents to you.

---

### Post by Bachstelze on 2011-10-06
> **karlson said:**
> Technically you might be able to "open" and read the directory as a file although I haven't tried doing it this way and read it.

You have to go very low-level if you want to read a directory. Even read() will not let you. Generally you would do a dump of the filesystem and read in in a hex editor.

---

### Post by Arndt on 2011-10-06
> **Bachstelze said:**
> You have to go very low-level if you want to read a directory. Even read() will not let you. Generally you would do a dump of the filesystem and read in in a hex editor.

I didn't know that. It used to be possible (and maybe still is, in other flavors of Unix), which is why I gave the answers I did. One reason for the change might be not to encourage unportable code.

---

### Post by karlson on 2011-10-06
> **Bachstelze said:**
> You have to go very low-level if you want to read a directory. Even read() will not let you. Generally you would do a dump of the filesystem and read in in a hex editor.

For my taste I am sticking with readdir. :)

---

### Post by Bachstelze on 2011-10-06
> **Arndt said:**
> It used to be possible (and maybe still is, in other flavors of Unix)

Maybe, POSIX actually leaves it implementation-defined.

[http://pubs.opengroup.org/onlinepubs/9699919799/functions/read.html](http://pubs.opengroup.org/onlinepubs/9699919799/functions/read.html)

> [EISDIR]
    [XSI] [Option Start] The fildes argument refers to a directory and the implementation does not allow the directory to be read using read() or pread(). The readdir() function should be used instead. [Option End]

I could only test on Ubuntu and OS X and neither works, so it's probably the same on all recent Linux and BSD.

---

### Post by karlson on 2011-10-06
> **Bachstelze said:**
> Maybe, POSIX actually leaves it implementation-defined.

[http://pubs.opengroup.org/onlinepubs/9699919799/functions/read.html](http://pubs.opengroup.org/onlinepubs/9699919799/functions/read.html)



I could only test on Ubuntu and OS X and neither works, so it's probably the same on all recent Linux and BSD.

RedHat doesn't allow this either.
Based on my reading what XSI stands for any system implementing X/Open Systems Interfaces would exhibit this behavior.

Which these days I think would be every major.

---

