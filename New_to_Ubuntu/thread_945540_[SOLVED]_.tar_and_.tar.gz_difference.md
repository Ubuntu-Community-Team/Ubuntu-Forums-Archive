---
title: "[SOLVED] .tar and .tar.gz difference"
date: 2008-10-12
forum: New to Ubuntu
---

### Post by psycoboy.ts on 2008-10-12
hey.. what's the actual difference between a .tar and a .tar.gz file??

---

### Post by gjoellee on 2008-10-12
the difference is like between everything else. just different file formats, if there is any big usability difference I don't know...

---

### Post by insane_alien on 2008-10-12
a .tar.gz is a tar file compressed with gzip. .tar.bz2 is a tar file compressed with bzip2 and .tar is just a tape archive file.

---

### Post by SunnyRabbiera on 2008-10-12
.tar files are for archiving and .tar.gz are for archiving with compression.

---

### Post by mc4100 on 2008-10-12
I believe .tar (Tar) is the archive for the files, and .gz (Gzip) is compression of that archive. Giving a tarball (.tar.gz)

---

### Post by paris_alex on 2008-10-12
.tar basically merges multiple files as a single file - there is no compression, but it captures all linux permission settings, etc. 

.gz provides compression. It can take single or multiple files, but it does not capture permission settings.

We use .tar.gz to create a zip file (i hope everyone knows what a zip file is {g}) that also maintain its original file permissions, etc.

This may not be very useful in Windows, but if we zip and unzip files marked as 'executable' in Linux, it will no longer be executable. The solution, use .tar.gz.

---

### Post by jerome1232 on 2008-10-12
sometimes tar.gz is abbreviated to .tgz
tar.bz2 is sometimes .tbz2

Just thought I'd add one more piece of info in :)

---

### Post by jemate18 on 2008-10-12
please mark this thread solved

Thanks...

---

