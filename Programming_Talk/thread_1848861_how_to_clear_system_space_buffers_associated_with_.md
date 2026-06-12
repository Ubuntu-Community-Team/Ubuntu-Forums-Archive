---
title: "how to clear system space buffers associated with read() call ?"
date: 2011-09-23
forum: Programming Talk
---

### Post by avee137 on 2011-09-23
I have a code that reads a file descriptor in an infinite loop.
like :
```

{
   int fd ;
   char buf10[10] = {'\0'} ;
   fd = open ("/dev/somePort",O_RDWR);
   while(1){
       read(fd ,buf10,5 );
       //do some operation on buf10


       //here i want to clear the system space buffer/cache associated   
       //with read()     
       } 
}

```

Is there any system call available in linux which could do that?

Any relevant help would be greatly appreciated.

---

### Post by karlson on 2011-09-23
> **avee137 said:**
> I have a code that reads a file descriptor in an infinite loop.
like :
```

{
   int fd ;
   char buf10[10] = {'\0'} ;
   fd = open ("/dev/somePort",O_RDWR);
   while(1){
       read(fd ,buf10,5 );
       //do some operation on buf10


       //here i want to clear the system space buffer/cache associated   
       //with read()     
       } 
}

```

Is there any system call available in linux which could do that?

Any relevant help would be greatly appreciated.

If you are talking about buf10 then
```

memset(buf10, 0, 10);

```

If you are talking about the underlying buffers on the device you are trying to read I suggest looking at the device driver for that device if there is an explicit buffer flush required or even possible.  Normally you don't need to do that.

---

