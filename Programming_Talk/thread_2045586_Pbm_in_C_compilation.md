---
title: "Pbm in C compilation"
date: 2012-08-21
forum: Programming Talk
---

### Post by sbub07 on 2012-08-21
i am using ubunut 11.10,i am trying to compile a c program
but i got a error like

bash: ./new.c: Permission denied

please help me to solve this problem

thank you

---

### Post by spjackson on 2012-08-21
```

gcc -o new new.c
./new

```

---

### Post by lisati on 2012-08-21
*Thread moved to **Programming Talk**.*

I'm not sure what you're trying to do here, compile the program or run it. 
To compile the program, the usual way is to do something like:
```
gcc new.c -o new
```
Assuming the compilation works, you'd then do something like:
```
./new
```

---

### Post by sbub07 on 2012-08-22
gcc new.c -o new 

this command is working

when i run the pgm

./new

i got the error like this

bash: ./new: Permission denied

---

### Post by trent.josephsen on 2012-08-22
Run `ls -l new`. Is it executable?

Are you working on a file system that's mounted without execute permission, like on a USB flash drive, or that doesn't support UNIX permissions, like FAT or NTFS?

---

### Post by sbub07 on 2012-08-22
yes i got the msg like this

-rw------- 1 sbalasubramonian sbalasubramonian 7157 2012-08-22 19:57 new

the file(new.c) is in ntfs file system.

---

### Post by spjackson on 2012-08-22
```

gcc -o ~/new new.c
~/new

```

---

### Post by sbub07 on 2012-08-22
It is working now

Thank you very much

---

