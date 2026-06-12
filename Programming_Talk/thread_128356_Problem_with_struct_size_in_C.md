---
title: "Problem with struct size in C"
date: 2006-02-11
forum: Programming Talk
---

### Post by scourge on 2006-02-11
I'm using a simple struct in my app:
```
typedef struct _Position
{
    unsigned long long key;
    unsigned short score;
} Position;
```

The problem is that when I compile the code with gcc-4.0.2 in Ubuntu the size of the structure is 12 bytes while in Windows (compiled with MinGW gcc-3.4.4) it's 16 bytes. Unsigned long long is 8 bytes and unsigned short is 2 bytes in both versions.

Normally the size wouldn't matter because I can always use sizeof(Position) to get the correct size, but my app needs to be able to read this data from a binary file. That of course means that I can't use the same binary file in Linux and Windows.

So is there a way to keep the struct size always the same, or should I not use structs in binary files?

---

### Post by engla on 2006-02-11
Nope, there is not much you can do about it. There is something called padding that is both compiler and platform-dependent, so there is no portable way to directly read and write structs to binary files.

---

### Post by scourge on 2006-02-11
Thanks for the reply. I delved into using binary files a little more, and it seems that they are not portable unless I use a format like XDR. Using text files is absolutely out of the question because I need all the speed I can possibly get.

Oh well. I guess I'll just have to create separate binary files for both versions of my app.

---

### Post by LordHunter317 on 2006-02-11
[QUOTE=scourge]
The problem is that when I compile the code with gcc-4.0.2 in Ubuntu the size of the structure is 12 bytes while in Windows (compiled with MinGW gcc-3.4.4) it's 16 bytes. Unsigned long long is 8 bytes and unsigned short is 2 bytes in both versions.[/quote]Yep, because the standard allows for it.  A structure can be padded however the compiler feelds like.

> So is there a way to keep the struct size always the same, or should I not use structs in binary files?You should read and write them member-by-member, instead of  trying to do it as a whole object.

>  	Thanks for the reply. I delved into using binary files a little more, and it seems that they are not portable unless I use a format like XDR. Using text files is absolutely out of the question because I need all the speed I can possibly get.
If loading files is impacting performance-sensitive sections, you likely already have a problem, unless your data cannot possibly fit into memory.

---

### Post by mo_x on 2006-02-11
Maybe you could use a compiler directive
#pragma pack(n)
where n is the byte alignment.
I think gcc supports it, I know the Microsoft C compiler does.

---

### Post by LordHunter317 on 2006-02-11
That may, depending on platform, have a huge performance cost that will impact performance-sensitive sections of the code.

Far better to read/write memberwise.  That way, you're certain you won't run into those issues, now and in the future.

---

### Post by scourge on 2006-02-11
Thanks a lot for the suggestions. I tried #pragma pack, and it seemed to work okay. But then I found out that I can pack structures with gcc by using "__attribute__((__packed__))". I did a few tests and noticed a 1.5 % performance hit which is quite acceptable.

> If loading files is impacting performance-sensitive sections, you likely already have a problem, unless your data cannot possibly fit into memory.

The app I'm writing is a chess engine, and I'm using the binary files for the opening book and endgame tablebases. The opening book isn't usually that big (about 200KB - 10MB), but endgame tablebases can be huge and they are often accessed at performance-sensitive sections. Speed is only one of the reasons for using binary files instead of text files.

---

### Post by steve.horsley on 2006-02-12
It's not even enough to write them member by member because the byte order of ints etc. depends on the CPU type. For full portability, you must write byte bty byte.

---

### Post by LordHunter317 on 2006-02-12
No, you just have to pay attention to byte order and swab on one-side or another if necessary.  Swabbing can be done indepedent of the reading, and usually should be so.

---

