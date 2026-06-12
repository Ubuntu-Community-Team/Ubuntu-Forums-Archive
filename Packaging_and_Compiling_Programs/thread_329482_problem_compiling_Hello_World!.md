---
title: "problem compiling Hello World!"
date: 2007-01-01
forum: Packaging and Compiling Programs
---

### Post by AnotherWay83 on 2007-01-01
lol...so yeah im a n00b to ubuntu!! i just tried to get my very first hello world program to compile using gcc, and here is the code:

#include <stdio.h>

int main() {
printf("Hello World!");
return 0;
}

and I tried compiling it using 'gcc -o test test.c' but it complained that it couldn't find stdio.h....i think i need to specify where the includes are, but where are they? i dont know myself! someone pls. hellllllllllppppppppppppp

fanks!

---

### Post by chipdip on 2007-01-01
Try to remove the .h on the include, so it looks like:
#include <stdio>
that should fix it. I dont believe that you need the .h at the end in Linux.

---

### Post by AnotherWay83 on 2007-01-01
hi,

thanks for the reply, i tried that and it still doesn't work.  it says 'error: stdio: No such file or directory'

what should i do???

---

### Post by wehttamb on 2007-01-01
Hi

I also have the same problem. I think we need to install stdio but i dont know how.
:confused: PLEASE HELP!!!:confused:

---

### Post by wehttamb on 2007-01-01
:) :) :) I just found someone else who had the same problem and got an anser. We have to install another thing. have a look at the post [http://ubuntuforums.org/showthread.php?t=325742&highlight=stdio]("http://ubuntuforums.org/showthread.php?t=325742&highlight=stdio")

I am installing it now.:)

---

### Post by ElysianEagle on 2007-01-02
hi,

thanks for that...so i did the updates and it works!! many many fanks...and i guess we do have to add the ".h" because otherwise it complains that it cannot find the file

---

### Post by hod139 on 2007-01-02
You keep the .h in the header, but make sure you install the package 
```

build-essential

```

which will actually install the missing headers.  The only time you drop the .h is for certain standard C++ includes, never for a C include.

---

### Post by invalid on 2007-01-02
It sounds like you all only installed the compiler, but no other necessary files for building and compiling software.
```
sudo apt-get install build-essential
```will install all the important files for you.

---

