---
title: "Help me with getting back my disappeared file !"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by shahab.fm on 2008-10-01
Hi,

I really need an urgent help.

I was programing C in my Ubuntu and suddenly when I ran : 

 cc -o Oblig1-2.c Oblig1-2

suddenly a lot of weired errors came on screen() and my c file disappeared !!!!! Can anyone help me with this ? It was my school project ... Is there any backup system that I can use to restore the file ?

Thank you

Shahab,

P.S. :
shahab@LinLap:~/c_workspace/Oblig1/src$ cc -o Oblig1-2.c Oblig1-2
Oblig1-2: In function `_start':
(.text+0x0): multiple definition of `_start'
/usr/lib/gcc/i486-linux-gnu/4.2.3/../../../../lib/crt1.o:(.text+0x0): first defined here
Oblig1-2:(.rodata+0x0): multiple definition of `_fp_hw'
/usr/lib/gcc/i486-linux-gnu/4.2.3/../../../../lib/crt1.o:(.rodata+0x0): first defined here
Oblig1-2: In function `_fini':
/build/buildd/glibc-2.7/build-tree/i386-libc/csu/crti.S:41: multiple definition of `_fini'
/usr/lib/gcc/i486-linux-gnu/4.2.3/../../../../lib/crti.o:/build/buildd/glibc-2.7/build-tree/i386-libc/csu/crti.S:41: first defined here
Oblig1-2:(.rodata+0x4): multiple definition of `_IO_stdin_used'
/usr/lib/gcc/i486-linux-gnu/4.2.3/../../../../lib/crt1.o:(.rodata.cst4+0x0): first defined here
Oblig1-2: In function `__data_start':
, ...

---

### Post by jamesrl on 2008-10-01
If you haven't figured out what seems to have happened, is that you told the compiler 'cc' to write to the output file (-o Oblig1-2.c) after compiling Oblig1-2 (which was an executable so you got error messages).

The correct command would be
```
cc -o Oblig1-2 Oblig1-2.c
```
or just
```
cc Oblig1-2.c
``` (and then you would have a compiled program called Oblig1-2.out that you can then rename).

So basically you started to save over the file with nonsense, which cc then used to delete it.

It is possible to recover the file off the hard disk, however it is not a simple task.  

If you are lucky the file is still open somewhere:
[URL="http://www.cyberciti.biz/tips/linux-recover-deleted-files-with-lsof-command.html"]http://www.cyberciti.biz/tips/linux-recover-deleted-files-with-lsof-command.html
[/URL]
Otherwise, read up here:
[http://www.xs4all.nl/~carlo17/howto/undelete_ext3.html]("http://www.xs4all.nl/~carlo17/howto/undelete_ext3.html")

Actually this seems a better method than the above:
[http://tips-debian.blogspot.com/2008/04/recover-erased-data-ext2ext3.html](http://tips-debian.blogspot.com/2008/04/recover-erased-data-ext2ext3.html)

---

### Post by niteshifter on 2008-10-01
Hi,

shahab.fm's problem is not a deleted file, it's been overwritten: cc (gcc) did precisely what it was told to do.

Depending upon the editor used and how much work was done after the last save in that editor this file might be available to him:

Oblig1-2.c~

I suggest looking for that file. Assuming Ubuntu (GNOME & Nautilus) via the GUI by opening the folder where Oblig1-2.c was and using Ctrl+H to show the hidden files. Or via the command line with:
```
ls *c~
```

---

