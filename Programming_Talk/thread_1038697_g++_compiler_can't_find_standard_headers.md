---
title: "g++ compiler can't find standard headers"
date: 2009-01-13
forum: Programming Talk
---

### Post by TheMyself on 2009-01-13
When compiling a C++ source file, g++ says it can't find iostream.h
This is weired. I copied iostream.h to all the directories that GCC documentation mentions it looks for header files in but nothing changed. I don't know what is wrong.:confused:

---

### Post by hayden92 on 2009-01-13
I always use
<iostream>
<cstdlib>
etc

Without the .h suffix

Also, are the headers enclosed in < > (that one caught me out once)

---

### Post by kjohansen on 2009-01-13
g++ is expecting the <iostream>, whereas gcc is expecting <iosteam.h>

---

### Post by kcode on 2009-01-14
Have you installed build-essential? If not, then execute this command and then try it again:
```

sudo apt-get install build-essential

```

Cheers

---

### Post by TheMyself on 2009-01-14
Thank you guys. At first it was 


#include <stdio.h>
#include <iostream.h>

And when I changed it to the following, it worked.


#include <stdio.h>
#include <iostream>
using namespace std;

This is a bit weird because the file was part of a package which had a make file. And yes, I have build-essentials installed but I thought it was for making .deb packages.

---

### Post by hayden92 on 2009-01-25
It would be good if you marked this thread as 'solved'.
It helps keep Ubuntuforums tidy and organised.

Hayden

---

### Post by aszxcv on 2009-01-25
> **hayden92 said:**
> It would be good if you marked this thread as 'solved'.
It helps keep Ubuntuforums tidy and organised.

Hayden

that function has been turned off

---

### Post by jespdj on 2009-01-25
> **TheMyself said:**
> And when I changed it to the following, it worked.


#include <stdio.h>
#include <iostream>
using namespace std;
If you are writing a C++ program, then you should use:
```
#include <cstdio>
```
instead of #include <stdio.h>.

---

