---
title: "7-Zip"
date: 2014-10-15
forum: New to Ubuntu
---

### Post by Prime624 on 2014-10-15
What is the difference between 7-Zip and the default compression tool that comes with Ubuntu?

---

### Post by craig10x on 2014-10-16
Perhaps someone here could post about the difference...i myself have never used anything but 7z to unzip files and it's always worked great...

---

### Post by 1clue on 2014-10-16
7zip gives better compression.  Other than that I don't know much about it.  We use it all the time for my job.

---

### Post by mcduck on 2014-10-16
There is a large list of different compression formats supported by default, so it really depends on which one you want to compare to (And in how much detail)

In general 7z format gives high compression, but is also very slow and uses lots of CPU power & memory to process the files.

for more detailed comparision, you'd better just look at this: [http://en.wikipedia.org/wiki/Comparison_of_archive_formats]("http://en.wikipedia.org/wiki/Comparison_of_archive_formats"). Or the numerous articles around th web discussing which one is fastest or best in which situations.

(My personal preference is to use *.zip* when I need to be sure anyone I send the file to can open it without installing extra programs, *.tar.gz* for all Linux use as it's really, really quick compared to anything else and the difference in archive size isn't that big, and *.7z* when I need to send really large archives over Internet (to people I know can open .7z) and want to get as small as possible archive file even if it takes long to pack & unpack the files...)


..or are you talking about the difference between the *Archive Manager*, and the graphical user interface that you can install with 7zip?

---

### Post by Prime624 on 2014-10-16
I did mean Ubuntu Archive Manager. I didn't know it had a name. I not real concerned about the GUI as I generally use the right-click menu. What is the difference between compressing/uncompressing a .tar.gz for example with Archive manager vs 7-Zip?

---

### Post by mcduck on 2014-10-16
probably nothing, apart from the fact that you have the archive manager by default and it's pretty well integrated with the system, while 7zip is something you'd have to install separately.

So basically, if you prefer 7zip's user interface, the install & use it. If not, stick with Archive Manager since it's already there by default. (also the default archive manager supports some formats 7zip doesn't have, as it's able to use various command-line archive managers available from repositories to add support for different archive types)

---

### Post by nerdtron on 2014-10-16
.tar.gz uses the gzip compression algorithm while 7-zip uses, well... 7-zip.

There are differences in syntax on the command line when you compress/decompress each.
And a comparison of compression ratio and speed can be seen here : [https://blogs.reucon.com/srt/compression-gzip-vs-bzip2-vs-7-zip-8296/](https://blogs.reucon.com/srt/compression-gzip-vs-bzip2-vs-7-zip-8296/)

---

### Post by Prime624 on 2014-10-16
Thanks mcduck, and interesting article nerdtron.

---

### Post by mcduck on 2014-10-16
.7z format uses [LZMA]("http://en.wikipedia.org/wiki/Lempel%E2%80%93Ziv%E2%80%93Markov_chain_algorithm") compression.

Here's another pretty good comparison of different formats and how well they deal with various types of data (noth in compression ration and speed): [http://bashitout.com/2009/08/30/Linux-Compression-Comparison-GZIP-vs-BZIP2-vs-LZMA-vs-ZIP-vs-Compress.html]("http://bashitout.com/2009/08/30/Linux-Compression-Comparison-GZIP-vs-BZIP2-vs-LZMA-vs-ZIP-vs-Compress.html")

(If you use 7-Zip as your user interface, it'll probably use it's own code to handle various compression types, but in general the performance should be more or less same as with the Archive Manager, and the actual compression type you choose makes much bigger difference)

---

