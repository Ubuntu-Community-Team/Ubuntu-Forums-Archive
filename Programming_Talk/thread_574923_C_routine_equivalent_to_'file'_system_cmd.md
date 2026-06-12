---
title: "C routine equivalent to 'file' system cmd?"
date: 2007-10-13
forum: Programming Talk
---

### Post by jmc1024 on 2007-10-13
Is there a C library call that is the equivalent to the 'file' system command?  I'm looking to process directories of files.  The process is different for different file types.  I'd rather not have to roll my own if I don't have to.
TIA,
Mark

---

### Post by gradedcheese on 2007-10-13
file just looks at the magic bitmasks, I think.  In some cases it does a little more analysis.  You could start by:

```

sudo apt-get source file

```

and seeing what it builds against (maybe there's a 'libmime' or something that you can link against).  That said, an strace shows it looking at text files for the magic number info:

> 
open("/etc/magic", O_RDONLY|O_LARGEFILE) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=111, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f83000
read(3, "# Magic local data for file(1) c"..., 4096) = 111


and I don't see it loading a shared library, at least.  /etc/magic is empty, but /usr/share/file/magic.mgc has what it needs, it seems.

---

### Post by Adnarim on 2007-10-13
What do you wanna achieve? Simple file-type checks can also be made with the C [file](http://www.opengroup.org/onlinepubs/009695399/utilities/file.html) command.

---

### Post by jmc1024 on 2007-10-13
I think I found what I was looking for in libmagic.  And it's already installed!
Thanks for all the help,
Mark

---

