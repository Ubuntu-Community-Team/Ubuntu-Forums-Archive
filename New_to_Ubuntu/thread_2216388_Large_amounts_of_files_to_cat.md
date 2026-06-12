---
title: "Large amounts of files to cat"
date: 2014-04-11
forum: New to Ubuntu
---

### Post by Zorna on 2014-04-11
I have a requirement to cat multiple multi-page tiff files. They are approximatel 200KB in size and are in multiple direcotories. I have been trying this in windows and the file keeps stopping without completing the cat, even shutting down the OS, black screen. I am pretty sure that unix can cat them all. Approximately 30000 files in all. I would welcome some starting points on how to achieve this.

---

### Post by pfeiffep on 2014-04-11
I might be off base here, but using "cat" in linux will read the contents of files. Not certain that you really want to try to display the contents of Tagged Image File Format (tiff) which are generally graphics.
> ~$ cat newfile
1
2
3


What is the intended output of "cat" multiple page tiff files?

---

### Post by steeldriver on 2014-04-11
Agreed - if you are streaming binary files to standard output it's quite easy to screw up the terminal and make it appear like the system has hung up.

The only limitation that comes to mind is the length / number of file arguments on the cat  command line - if you have 1000s of files, you may need to use xargs to split the argument list down  into smaller chunks. But it all depends on how you are assembling the list of files (from a shell glob? from a pre-prepared list of filenames in a separate file? using the 'find' command?).

---

### Post by Impavidus on 2014-04-11
++the previous answers.
One other thing that could go wrong: If you write the file to a fat32 partition (like most thumb drives), you have a limit of 4GiB file size. All these files concatenated will produce something of about 6GB.

---

