---
title: "difference between hexdump and objdump."
date: 2010-08-15
forum: Programming Talk
---

### Post by tapas_mishra on 2010-08-15
I am not clear with difference between hexdump and objdump and coredump.
I wrote a small program 
```
main (){
int a=2;
int b=4;
int k=b/a;
int m=9;
}

```and tried to compare its hexdump and objdump.
Here is a link to the [hexdump ]("http://pastebin.com/K6qkPYgb")
and [objdump.]("http://pastebin.com/tXVJVM8t")

I tried to search the instructions found in objdump with the numbers in hexdump I was expecting a line in objdump such as 
```

 8048398:    83 e4 f0                 and    $0xfffffff0,%esp
 804839b:    ff 71 fc                 pushl  -0x4(%ecx)
 804839e:    55                       push   %ebp
 804839f:    89 e5                    mov    %esp,%ebp
 80483a1:    51                       push   %ecx
 80483a2:    83 ec 1c                 sub    $0x1c,%esp
 80483a5:    c7 45 f8 02 00 00 00     movl   $0x2,-0x8(%ebp)
 80483ac:    c7 45 f4 04 00 00 00     movl   $0x4,-0xc(%ebp)
 80483b3:    8b 45 f4                 mov    -0xc(%ebp),%eax
 80483b6:    89 45 e0                 mov    %eax,-0x20(%ebp)
 80483b9:    8b 55 e0                 mov    -0x20(%ebp),%edx
 80483bc:    89 d0                    mov    %edx,%eax
 80483be:    c1 fa 1f                 sar    $0x1f,%edx
 80483c1:    f7 7d f8                 idivl  -0x8(%ebp)
 80483c4:    89 45 f0                 mov    %eax,-0x10(%ebp)
 80483c7:    c7 45 ec 09 00 00 00     movl   $0x9,-0x14(%ebp)

```Some of the above instructions such as 89 d0 should be present in hexdump.
What exactly is the hexdump ,objdump and coredump and what is their importance?
Why do scripting languages not have these or if I am wrong then correct me.

---

### Post by MadCow108 on 2010-08-15
hexdump just takes some file and displays its content.
You will not see much except you know exactly what your looking for.
e.g. right at the start 457f 464c the beginning of the ELF magic in little endian

objdump on the otherhand can read the ELF format and display specific decoded (disassembled) information.
So its output will be much more specific than that of hexdump.

another tool for looking at elf files is readelf
you may also be interested in this article:
[http://www.linuxjournal.com/article/1060](http://www.linuxjournal.com/article/1060)

scripting language files do mostly consist of just ascii files so there is no need to decode anything.
Although some scripting languages do have something similar to a compile step, but the result is no machine readable ELF file but some kind of bytecode which needs an interpreter.

---

