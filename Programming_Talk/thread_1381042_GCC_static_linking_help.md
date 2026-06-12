---
title: "GCC: static linking help"
date: 2010-01-14
forum: Programming Talk
---

### Post by nmccrina on 2010-01-14
I built a linked list in C. I ended up having four files: linked_list.h, linked_list.c, node.h, and main.c Everything worked when all the files were together and I just compiled everything every time, but now I want to mess around with creating and using libraries. So I thought I would put the linked list code in a static library using ar. 
```
ar rcs linked_list.a linked_list.o
``` 
seemed to work. Then I moved linked_list.h and node.h to /usr/include and linked_list.a to /usr/lib. The #include in main.c still works, but compilation fails with a

```
/usr/bin/ld: cannot find -llinked_list
collect2: ld returned 1 exit status
```

The compilation command I used was gcc main.c -L/usr/lib -static -llinked_list. I've just been trying different things I got from teh interwebs. 

How do I link my library using gcc?

---

### Post by Hyporeal on 2010-01-14
The -llinked_list parameter causes gcc to search for a file called "liblinked_list.a". Use this as your library name and it should link.

---

### Post by nmccrina on 2010-01-14
Perfect, thank you!

:popcorn:

---

