---
title: "Does the OS automatically calculate and store file checksums?"
date: 2010-07-22
forum: Programming Talk
---

### Post by ownaginatious on 2010-07-22
Currently I'm trying to make a program to back up files and create a log of what it did.

Right now I'm comparing files blocks at a time, which I feel may be more work than I need to make the computer do.

So my question is, does Linux (or UNIX in general I guess) store a checksum for a file as soon as it's created/modified? If it does, and is accessible through C/C++, I think that would be a lot faster than my current solution (just compare the checksums rather than reading both files through the RAM).

Thanks!

**EDIT:** Come to think of it, what I'm thinking of may not be called a checksum. What I mean is maybe some finite-length hexidecimal number or something calculated based on the contents of the file (maybe the sum of all the bytes, skipping every X-th byte to make the sum unique to files of the same size?).

---

### Post by nebu on 2010-07-22
from what i understand of the unix file structure, the only thing the operating system keeps track of when it comes to individual files is this data structure called the inode u can have a look [here]("http://en.wikipedia.org/wiki/Inode")

the closest thing the inode stores to what you are asking is the size of the file...

---

### Post by moma on 2010-07-22
Hello,

Unix/Linux does not generate or save md5sum or similar checksums for files.  

I had a similar question couple of years ago. I needed to check if two files (their contents) were equal.

My first solution simply checked file size + file modification time, but this did not work well because the application could change the file content several times within a 1 second. The file modification timestamp cannot track time-span less than a second. 

So I simply landed to use the Unix's diff command. It's very quick.

See: [http://code.google.com/p/gscreendump/source/browse/trunk/src/sd_misc_utils.c](http://code.google.com/p/gscreendump/source/browse/trunk/src/sd_misc_utils.c)

Look for function: gboolean compare_files_are_equal(gchar *file1, gchar *file2)

Used from "sd_rev_control.c" module.
--
I do not know if you can access the diff-command from a library. I just execute/shell the "diff" command from the c-code and test its return code (echo $?).
Like:
$ diff file1 file2 
$ echo $?
--
The diff comes from the "diffutils" package. Add it to your app's dependency list.
See: [http://packages.ubuntu.com/lucid/diffutils](http://packages.ubuntu.com/lucid/diffutils)

---

### Post by ownaginatious on 2010-07-22
Thanks for both your answers. After reading nebu's post, I was actually thinking of doing the exact same thing as moma mentioned (comparing size + modification date). For my purposes, the files are probably going to almost never change, so I think that should be sufficient.

I'll keep that diff command in mind though. Sounds like it might be useful in the future.

Thanks!

---

### Post by Milliways on 2010-07-22
> **ownaginatious said:**
> Thanks for both your answers. After reading nebu's post, I was actually thinking of doing the exact same thing as moma mentioned (comparing size + modification date). For my purposes, the files are probably going to almost never change, so I think that should be sufficient.

I'll keep that diff command in mind though. Sounds like it might be useful in the future.

Thanks!

I have done quite a bit of file comparison.
Calculating checksums (of any kind) for comparison is inefficient, as you have to read both files, and might as well do a straight binary comparison.

If you have a lot of files to compare, firstly check filesize.
Only for same file size, read and compare the 1st 4K.
Only if these are identical compare the whole file.

Timestamps are not reliable as they can be changed by lots of things, although this depends on application.

---

### Post by slavik on 2010-07-22
have you looked at rsync?

---

### Post by ownaginatious on 2010-07-23
> **Milliways said:**
> I have done quite a bit of file comparison.
Calculating checksums (of any kind) for comparison is inefficient, as you have to read both files, and might as well do a straight binary comparison.

If you have a lot of files to compare, firstly check filesize.
Only for same file size, read and compare the 1st 4K.
Only if these are identical compare the whole file.

Timestamps are not reliable as they can be changed by lots of things, although this depends on application.

Ya, I know calculating checksums is rather inefficient. I was just hoping that maybe the system calculates a checksum as it writes/modifies a file (since it isn't really much extra work for the computer a that point) and stored it in a tag on the file. It would make this sort of thing much easier :p.

I think maybe I'll compare blocks at a time (depending on the block size used in the file system) and keep going until two differ.

> have you looked at rsync?
Well that's no fun. Haha, what I'm using now is rsync. It's okay, but my main problem with it is it seems rather difficult to get information about what it actually did in a presentable form. Right now I run it as rysync ... > log.txt, and then have a program sort through the log and try and make it presentable. There are irregularities that show up at times and it's overall generally a pain in the ***.

Plus, I'm currently learning C++, and this seems like a good learning exercise :p.

---

