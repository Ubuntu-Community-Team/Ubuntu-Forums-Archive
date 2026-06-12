---
title: "Write binary file for output instead of ASCII (C++)?"
date: 2012-11-06
forum: Programming Talk
---

### Post by Kdar on 2012-11-06
I am writing some C++ program that writes some tracing data to a file. Eventually, this file can get very large (few gigabytes).

How can I, to reduce the size of output file on disk, write this data as binary instead of ascii?

---

### Post by bird1500 on 2012-11-06
I'm not sure, off the top of my head:
- use a filesystem mounted with compression enabled (btrfs)
- use a compression library to compress the data (say in .zip or .xz format) on the fly and write it to the disk.

---

### Post by ofnuts on 2012-11-07
> **Kdar said:**
> I am writing some C++ program that writes some tracing data to a file. Eventually, this file can get very large (few gigabytes).

How can I, to reduce the size of output file on disk, write this data as binary instead of ascii?
Use ofstream::write(memoryblock,size) or ostream::write(memoryblock,size)

This will sort of dump the memory bytes your are pointing to to the file. You save disk space, and also some processing time (no formatting). On the other hand the trace data should be read using an equivalent method. You may also want to organize the data somewhat, for instance adding some info so that the file contents can be navigated more easily.

---

### Post by SuperCamel on 2012-11-07
You may also want to look into the zlib library. It's quite simple to use and could potentially save a lot of disk space, at the cost of some processing time of course.

---

