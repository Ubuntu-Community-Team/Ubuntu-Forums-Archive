---
title: "Can't Extract Archive"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by Sinkingships7 on 2008-06-06
I created a backup of my system, and made a couple archives as my backup. I had a media backup in a tar.gz format. Well, it failed the CRC and won't let me view the files inside or extract. I don't particularly care if some files are lost, I need to recover what I can: it's the only backup of my music, videos, and most importantly, pictures that I have.

My question: Is there a way to force extract the archive? Any other alternative? Please help... I can't lose those pictures :(

---

### Post by cariboo on 2008-06-06
So are you saying that the data is unavailable on your hard disk?

---

### Post by Sinkingships7 on 2008-06-06
The data is in a compressed tar.gz format in my Home folder. When trying to extract the tar.gz, it spits out an error message saying:
```
An error occurred while extracting files.

tar: Skipping to next header

gzip: stdin: invalid compressed data--crc error

gzip: stdin: invalid compressed data--length error
tar: Child returned status 1
tar: Error exit delayed from previous errors

```

I get the same error if I only try to open it, so I can't view the files inside.

---

### Post by omi291 on 2008-06-06
would this be any help?

[http://ubuntuforums.org/showthread.php?t=271655](http://ubuntuforums.org/showthread.php?t=271655)

---

### Post by Sinkingships7 on 2008-06-06
> **omi291 said:**
> would this be any help?

[http://ubuntuforums.org/showthread.php?t=271655](http://ubuntuforums.org/showthread.php?t=271655)

No... I'm very familiar with creating and extracting archives... I'm fairly good at Linux in general... 

The archive failed the CRC (cyclical redundancy check) and fails to open for me. I can't open or extract by default, so I was wondering if there was perhaps a command line method of forcing it to extract whatever it can.

---

### Post by Sinkingships7 on 2008-06-08
Bump for my beloved lost pictures...

---

### Post by bruce89 on 2008-06-08
See if it is really a gzipped tarball by invoking
```
file filename.tar.gz
```

If it says "POSIX tar archive" it's only a tar file, if it says something like "gzip compressed data...", then there's something wrong.

---

### Post by Sinkingships7 on 2008-06-09
> **bruce89 said:**
> See if it is really a gzipped tarball by invoking
```
file filename.tar.gz
```

If it says "POSIX tar archive" it's only a tar file, if it says something like "gzip compressed data...", then there's something wrong.

This is what I got:
```

christopher@compy:/media/disk/BACKUP/christopher$ file media_6-6-08.tar.gz
media_6-6-08.tar.gz: gzip compressed data, was "media_6-6-08.tar", from Unix, last modified: Fri Jun  6 18:20:02 2008

```
Does that mean something's wrong?

---

