---
title: "Lost source file after compilation with GCC"
date: 2010-04-14
forum: Packaging and Compiling Programs
---

### Post by Hayksk on 2010-04-14
[SIZE=2]Hello.
Please help.
I've a[/SIZE][SIZE=2]ccidentally executed a wrong command and lost one of my .cpp source files (file1.cpp).
[/SIZE][SIZE=1][SIZE=2]The command entered was the following:[/SIZE]

[/SIZE][SIZE=1][SIZE=2]gcc -g -o file1.cpp file2.cpp main.cpp

[SIZE=2]The compiler have probably deleted or overwritten the file.
Is it possible [/SIZE]to recover the lost file (file1)? I've been working on it about two weeks and it was a very important file.[/SIZE]
[/SIZE]

---

### Post by kramulous on 2010-04-14
Oh no!  Tell me you have a older copy in your recycle bin, you've emailed a copy to yourself, backup drives or have directories with different versions.

Unless there is some filesystem/kernel mastery that I don't know about, I think you've lost your file.

---

### Post by Hayksk on 2010-04-14
> **kramulous said:**
> Oh no!  Tell me you have a older copy in your recycle bin, you've emailed a copy to yourself, backup drives or have directories with different versions.


  
Unfortunately, no one of of these cases...
I don't have any copy of the code.

---

### Post by SevenMachines on 2010-04-14
If the source files gone theres not much that can be done i'm afraid, this is a good reason for makefiles, svn and such other ways to avoid this situation. i've certainly done it before myself. you could try decompiling the binary but the results are not likely to be great, you might recover something though. try [using boomerang]("http://boomerang.sourceforge.net/") for example

[EDIT] just to add theres obviously commercial decompilers like hex-rays(?) IDA Pro, if you have a job/university that can afford such things you might want to plead with them

---

### Post by Hayksk on 2010-04-14
Wow!!! Great!!! Grep command really did a great job. The 400-row code was recovered completely, without any damage!!!!

[http://www.cyberciti.biz/tips/linuxunix-recover-deleted-files.html](http://www.cyberciti.biz/tips/linuxunix-recover-deleted-files.html)
[http://www.datarecoverypros.com/non-ext2-recovery.html](http://www.datarecoverypros.com/non-ext2-recovery.html)

Thanks guys!!!

---

