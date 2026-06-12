---
title: "man tar"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by poldie on 2008-10-23
I typed man tar to find out how to decompress an archive.  This is the first example:

 tar -xvvf foo.tar
              extract foo.tar


But I see no reason why vv would be different to v.  It just means verbose, doesn't it? Aren't you more likely to want -zxvf ?

---

### Post by jerome1232 on 2008-10-23
edit: lol yeah that's what I meant to say... :) z for gunzip, I always forget and have to check the man page

You can go up to 2 levels of verbosity in tar, one v just lists files, two v's lists files, permissions and the owner of the files. The z just tells tar to uncompress the archive using gunzip and wouldn't be needed unless the archive was created using that option.

---

### Post by snova on 2008-10-23
Actually, the 'z' option decompresses with Gzip and 'j' decompresses with Bzip2. The same options can be used when creating archives, with the same meanings.

You can also decompress it manually before invoking tar, but why add an extra step? It's also probably faster.

---

### Post by poldie on 2008-10-23
> **snova said:**
> Actually, the 'z' option decompresses with Gzip and 'j' decompresses with Bzip2. The same options can be used when creating archives, with the same meanings.

You can also decompress it manually before invoking tar, but why add an extra step? It's also probably faster.

Cheers. I'm sure I'll get the hang of it eventually.  If a file is zipped, can't tar just unzip it - why do I have to tell it which format to use? Isn't it in the header of the file?

---

### Post by snova on 2008-10-23
First of all, "zip" shouldn't be used as a generic term, use it only to refer to files that are actually .zip archives.

Secondly, there's a difference between archivers, that combine several files into one; and compressors, that make them smaller.

Tar is *only* an archiver. The files it creates are no smaller than the ones it included in the archive. Sometimes the resulting archives are even larger.

Gzip and Bzip2 are *only* compressors. They do not combine files. They take one file as input and create one (smaller) file as output, nothing more.

Zip is both. It compresses files with an internal algorithm (I think it has another name, but I don't know it) and then archives them, and the resulting file is a .zip.

If you use a graphical archiver, the differences in file formats should be transparent, as it will choose the correct tool to use automatically. Command line tools are usually specialized, however, to their purpose- and tar is no exception. Tar was created to manipulate tar archives; options were added to support the most common compression formats only for convience. The zip format has its own tools. 7zip has its own tool. Every compression algorithm and archiver in existence has its own tool.

There are programs for the command line that do the same thing as graphical archivers (select appropriate tools automatically), but I don't know what they are called. There's also probably more than one.

---

### Post by markbuntu on 2008-10-23
I use archive manager.

---

### Post by poldie on 2008-10-24
> **snova said:**
> First of all, "zip" shouldn't be used as a generic term, use it only to refer to files that are actually .zip archives.

Secondly, there's a difference between archivers, that combine several files into one; and compressors, that make them smaller.

Tar is *only* an archiver. The files it creates are no smaller than the ones it included in the archive. Sometimes the resulting archives are even larger.

Gzip and Bzip2 are *only* compressors. They do not combine files. They take one file as input and create one (smaller) file as output, nothing more.

Zip is both. It compresses files with an internal algorithm (I think it has another name, but I don't know it) and then archives them, and the resulting file is a .zip.

If you use a graphical archiver, the differences in file formats should be transparent, as it will choose the correct tool to use automatically. Command line tools are usually specialized, however, to their purpose- and tar is no exception. Tar was created to manipulate tar archives; options were added to support the most common compression formats only for convience. The zip format has its own tools. 7zip has its own tool. Every compression algorithm and archiver in existence has its own tool.

There are programs for the command line that do the same thing as graphical archivers (select appropriate tools automatically), but I don't know what they are called. There's also probably more than one.

Thanks for clearing that up.   I just need to get used to the command line more in Linux than I'm used to.

---

### Post by grg_gre on 2008-10-30
Hi,

I am using ubuntu 8.04 desktop, and upon trying to read the tape drive containing a tar archive, I get the following error:-
#tar: /dev/st0: Cannot read: Cannot allocate memory
#tar: At beginning of tape, quitting now
#tar: Error is not recoverable: exiting now

Can anyone suggest a solution?

Thanks and regards,
grg_gre

---

### Post by hyper_ch on 2008-10-30
actually, I don't think you should use a "-"... I always do:

```

tar xvfz file.tar.gz

```

---

