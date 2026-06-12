---
title: "how to zip files"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by Andrew U.K. on 2008-09-16
Hi,

How do I zip a file so I can add it to a forum post?
I´ve done it once and can´t for the life of me work it out again. I did it in the terminal with a simple command.

Cheers 
Andrew

---

### Post by OutOfReach on 2008-09-16
You can right click on the file and press 'Create Archive'.
You can also do it from the terminal, I just forget the commands.

---

### Post by p221072 on 2008-09-16
Hi, you can use **gzip **command to compress and **gunzip **to exctract.
Type *man gzip* to read all the options.
You can also use the **tar **command to create [/exctract] an archive, using the -z option to compress the archive

---

### Post by dualpretop on 2008-09-16
Good program - PeaZip!

[http://www.kde-apps.org/content/show.php/PeaZip?content=52805&PHPSESSID=83995b4404187744fbdd8a715c706d20](http://www.kde-apps.org/content/show.php/PeaZip?content=52805&PHPSESSID=83995b4404187744fbdd8a715c706d20)

Download:
[http://sourceforge.net/project/downloading.php?groupname=peazip&filename=peazip_2.2.bin.LINUX.GTK2.i586-1.deb&use_mirror=dfn](http://sourceforge.net/project/downloading.php?groupname=peazip&filename=peazip_2.2.bin.LINUX.GTK2.i586-1.deb&use_mirror=dfn)

---

### Post by Mornedhel on 2008-09-16
Better program - 7zip ('cause it's in the repositories, and integrates with file-roller).

If you're overwhelmed by the complexity of tar+gzip, you can also use zip to produce the .zip archives common in the Windows world.

---

### Post by myidbe on 2008-09-16
You can also use the **zip** (and **unzip**) commands.

Example:
```
malcolm@espresso:~/Desktop$ zip zipfile.zip file_i_want_to_zip.txt

```

---

### Post by WRDN on 2008-09-16
**_Creation_**

To create a tar containing "files":

```
tar cf file.tar files
```

To create a tar with Gzip compression:

```
tar czf file.tar.gz files
```

To create a tar with Bzip2 compression:

```
tar cjf file.tar.bz2 files
```

**_Extraction_**

To extract files from tar:

```
tar xf file.tar
```

To extract files from tar using Gzip:

```
tar xzf file.tar.gz
```

To extract files from tar using Bzip2:

```
tar xjf file.tar.bz2
```

For a tar, "f" is used, for Gzip "zf" is used, and for Bzip2 "jf" is used. Place a "c" before each of those to use the compression, and an "x" to extract from the compressed file(s).

---

### Post by HousieMousie2 on 2008-09-16
WRDN,

Nicely done, covered a lot of bases, thanks.  This page is now bookmarked!

---

### Post by pudgypaw on 2010-07-09
as an aside, if you want to zip the file and all the subdirectories under it, use [-r]:

$ zip -r destination.zip cowfile/

---

### Post by Mat11 on 2010-07-26
> **WRDN said:**
> **_Creation_**

To create a tar containing "files":

```
tar cf file.tar files
```To create a tar with Gzip compression:

```
tar czf file.tar.gz files
```To create a tar with Bzip2 compression:

```
tar cjf file.tar.bz2 files
```**_Extraction_**

To extract files from tar:

```
tar xf file.tar
```To extract files from tar using Gzip:

```
tar xzf file.tar.gz
```To extract files from tar using Bzip2:


My terminal just went crazy adding in laptop twice command line which i didn't type in in the first place where did the tar xflattop come from i have not entered that at all ??????
The only entry i made was the tar xvjf ...bz2 i feel i have no control over my terminal at the moment got any idea ????
thanks:(

 laptop:~$ tar xflaptop:~$ tar xvjf naev-0.4.2.tar.bz2
tar: You may not specify more than one `-Acdtrux' option
Try `tar --help' or `tar --usage' for more information.
matt@matt-laptop:~$ tar: naev-0.4.2.tar.bz2: Cannot open: No such file or directory
No command 'tar:' found, did you mean:
 Command 'tar' from package 'tar' (main)
 Command 'tart' from package 'tart' (universe)
tar:: command not found
matt@matt-laptop:~$ tar: Error is not recoverable: exiting now
No command 'tar:' found, did you mean:
 Command 'tar' from package 'tar' (main)
 Command 'tart' from package 'tart' (universe)
tar:: command not found
matt@matt-laptop:~$ tar: Child returned status 2
No command 'tar:' found, did you mean:
 Command 'tar' from package 'tar' (main)
 Command 'tart' from package 'tart' (universe)
tar:: command not found


```
tar xjf file.tar.bz2
```For a tar, "f" is used, for Gzip "zf" is used, and for Bzip2 "jf" is used. Place a "c" before each of those to use the compression, and an "x" to extract from the compressed file(s).


```
tar xjf file.tar.bz2
```For a tar, "f" is used, for Gzip "zf" is used, and for Bzip2 "jf" is used. Place a "c" before each of those to use the compression, and an "x" to extract from the compressed file(s).[/QUOTE]

---

### Post by linxiarain on 2011-01-01
Thanks a lot.

---

