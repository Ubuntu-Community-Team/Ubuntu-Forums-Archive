---
title: "[SOLVED] &amp;quot;Can't find stdio.h&amp;quot;"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by Neureo on 2008-06-04
I'm a Linux newbie and I was trying out Ubuntu using the Live CD. I had been reading a book about C, which said that most Linux distributions came with the C compiler GCC and gave instructions for using it. After ensuring that I was in the right directory (/ubuntu/prog/c/learn/), I tried to compile & link the following file by typing "gcc hello.c -o hello"...the code is straight from the book.

```
#include <stdio.h> 

int main() 
{
   printf("Hello, world!"); 
   return(0);
}
```

But the compiler says that it cannot find stdio.h while my book seemed to think that it would exist somehow. Why not? Is this something that I need to obtain myself? Is it not included on the Live CD? Please pardon me if the answer is really obvious -- as I said, I'm pretty new (to both Ubuntu *and* C). Thanks for your time.

---

### Post by sam_delta on 2008-06-04
i believe you need to install build essentials which contains basic c libraries

open a terminal and type

```
sudo apt-get install build-essential
```

sam

---

### Post by starcannon on 2008-06-04
+1 to installing build-essential that should get you going.

> **sam_delta said:**
> i believe you need to install build essentials which contains basic c libraries

open a terminal and type

```
sudo apt-get install build-essential
```

sam

---

### Post by Neureo on 2008-06-06
Excellent! Thank you.

---

