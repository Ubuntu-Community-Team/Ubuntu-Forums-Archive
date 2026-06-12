---
title: "compile error with hello word c++ program"
date: 2007-04-25
forum: Programming Talk
---

### Post by fxckkonka on 2007-04-25
$cat hello.cpp 


#include <iostream>

using namespace std;


int main(int argc, char *argv[])
{
  std::cout << "Hello, world!" << std::endl;

}

$ c++ -o hello hello.cpp 
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/cstdlib:135: error: &#8216;::system&#8217; has not been declared


-------------------
I searched the forum, and found a few errors like this, but nobody gave the correct answer.
Any ideas?

---

### Post by fxckkonka on 2007-04-25
I found some links
[http://lists.debian.org/debian-gcc/2006/12/msg00244.html](http://lists.debian.org/debian-gcc/2006/12/msg00244.html)

Problem is resolved when following that.

comment out 
/usr/include/c++/4.1.2/cstdlib
line 135
using ::system

But I can not finger out what stranger things would be happened.

Sigh!

---

### Post by Darkness3477 on 2007-04-25
You have the using namespace std, but then using std::cout << ... That's not needed. Don't know if it would cause any problems, but yeah.

Also, when posting code, use the code tags. just enter your code inbetween [ code] and [/code ] just without the spaces.

---

### Post by fxckkonka on 2007-04-25
That has nothing to do with it.

---

### Post by hod139 on 2007-04-25
What version of Ubuntu are you running?  

What arch?  

What is the c++ alternative set to?
```

update-alternatives --list c++

```

If you use g++ instead of c++ do you still get the error? 
  
If you remove ```
 using namespace std;
``` does the error go away?  

Have you installed the package build-essential?  

Do you you have any 3rd party repositories?  Especially any repositories that have affected libc?

main should return 0, but that is probably not your error.

---

### Post by talowe on 2007-04-25
> **fxckkonka said:**
> I found some links
[http://lists.debian.org/debian-gcc/2006/12/msg00244.html](http://lists.debian.org/debian-gcc/2006/12/msg00244.html)

Previous message: [ http://lists.debian.org/debian-gcc/2006/12/msg00243.html]( http://lists.debian.org/debian-gcc/2006/12/msg00243.html) seems to provide a better solution, unless you NEED libpthread.   Code compiled fine on my system, installed lipthread-dev and got same error.  Purged libthread-dev, compiles fine.

> 
comment out 
/usr/include/c++/4.1.2/cstdlib
line 135
using ::system

But I can not finger out what stranger things would be happened.

Sigh!

Probably not a real good idea to change header files without REAL good reason.

---

### Post by fxckkonka on 2007-04-26
Maybe, I reinstall libc6-dev,  and it modifed something....

so now I change the header back, it worked again.

PS: xubutun 7.04

---

