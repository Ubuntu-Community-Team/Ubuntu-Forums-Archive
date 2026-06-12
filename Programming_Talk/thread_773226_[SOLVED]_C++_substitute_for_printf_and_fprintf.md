---
title: "[SOLVED] C++ substitute for printf and fprintf"
date: 2008-04-28
forum: Programming Talk
---

### Post by WitchCraft on 2008-04-28
Hi! Question

static unsigned char image_png[] =
^M
{
0x89, 0x50, 0x4e, 0x47, 0x0d, 0x0a, 0x1a, 0x0a, 0x00, 0x00, 0x00, 0x0d,
0x49, 0x48, 0x44, 0x52, 0x00, 0x00, 0x02, 0x58, 0x00, 0x00, 0x01, 0xe0,
0x08, }

What does ^M mean in this context?
IMO must have something to do with the fact that the compiler doesn't output an error, although there is a comma before the closing bracket...

---

### Post by WW on 2008-04-28
You probably have an extraneous "carriage return" character in the file.  The ascii value is 13, which is also ctrl-M.  Did this file come from a Windows computer?



What does this have to do with the thread title?

---

### Post by WitchCraft on 2008-04-28
> **WW said:**
> You probably have an extraneous "carriage return" character in the file.  The ascii value is 13, which is also ctrl-M.  Did this file come from a Windows computer?

Yes it does. But that's new, never saw the ^M before...


> **WW said:**
> 
What does this have to do with the thread title?

Noting, I just solved that problem before anybody answered my question, and then changed the title.


But why is there no compiler error? There is a comma in the array after the last value, shouldn't it output something like primary-expression expected?

---

### Post by WW on 2008-04-29
> **WitchCraft said:**
> 
But why is there no compiler error? There is a comma in the array after the last value, shouldn't it output something like primary-expression expected?
I can't give a definitive answer, but after a little googling, it appears that allowing a trailing comma in an array initializer goes back to K&R C.  They can also be used in enum lists. For example,
[php]
#include <iostream>

enum Color {Red, Green, Blue, Cyan, Magenta, Yellow, };

int main(int argc, char *argv[])
    {
    Color c[] = {Green, Blue, Cyan, };
    std::cout << sizeof(c) << std::endl;
    return 0;
    }
[/php]
compiles with g++.

A couple interesting links:
[http://www.pluralsight.com/blogs/craig/archive/2006/05/08/23008.aspx](http://www.pluralsight.com/blogs/craig/archive/2006/05/08/23008.aspx)
[http://www.open-std.org/jtc1/sc22/wg21/docs/cwg_defects.html#518](http://www.open-std.org/jtc1/sc22/wg21/docs/cwg_defects.html#518)

---

### Post by dwhitney67 on 2008-04-29
If you ever transfer files from Windows to *nix, and you see a ^M at the end of each line, the simple way to correct this is to filter the file using the 'dos2unix' utility.

```
$ dos2unix myFile.cpp
```

P.S.  You may need to apt-get this utility.

---

