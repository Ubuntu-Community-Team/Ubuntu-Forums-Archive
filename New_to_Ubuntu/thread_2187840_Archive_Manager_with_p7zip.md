---
title: "Archive Manager with p7zip"
date: 2013-11-14
forum: New to Ubuntu
---

### Post by sheldon-corey on 2013-11-14
From my understanding Archive manager is nothing more than an unzip application much like 7zip (p7zip) and I prefer 7zip interface and can't get 7zip to even work alongside Archive manager is there a way to make them co exist if now how do i purge archive manager so i may use only 7zip and what if any repercussions performance wise will that cause?


thanks

---

### Post by The Spectre on 2013-11-14
I think 7-Zip for Linux is only available in a Command Line Interface and adds 7-Zip capabilities into preexisting Archive Managers.

If you looking for an Archive Managers with more of a 7-Zip type of interface and more features try PeaZip...
[http://peazip.sourceforge.net/peazip-linux.html](http://peazip.sourceforge.net/peazip-linux.html)

[IMG]http://peazip.sourceforge.net/peazip-gtk2.png[/IMG]

---

### Post by oldos2er on 2013-11-14
Archive manager will act as a front-end for any compression/archiving programs you might have installed. From *apt-cache show file-roller* ```
File-roller supports the following formats:
  * Tar (.tar) archives, including those compressed with
    gzip (.tar.gz, .tgz), bzip (.tar.bz, .tbz), bzip2 (.tar.bz2, .tbz2),
    compress (.tar.Z, .taz), lzip (.tar.lz, .tlz), lzop (.tar.lzo, .tzo),
    lzma (.tar.lzma) and xz (.tar.xz)
  * Zip archives (.zip)
  * Jar archives (.jar, .ear, .war)
  * 7z archives (.7z)
  * iso9660 CD images (.iso)
  * Lha archives (.lzh)
  * Archiver archives (.ar)
  * Comic book archives (.cbz)
  * Single files compressed with gzip (.gz), bzip (.bz), bzip2 (.bz2),
    compress (.Z), lzip (.lz), lzop (.lzo), lzma (.lzma) and xz (.xz)
 .
 File-roller can extract following formats:
  * Cabinet archives (.cab)
  * Debian binary packages (.deb)
  * Xar archives (.xar)
 .
 File-roller doesn't perform archive operations by itself, but relies on
 standard tools for this.
```

*Moved thread to Absolute Beginners.

---

