---
title: "gcc compiler help"
date: 2011-05-10
forum: Programming Talk
---

### Post by hugom on 2011-05-10
Hi there,

When I try and compile a program through the terminal it says...

/usr/lib/gcc/i686-linux-gnu/4.4.5/../../../../lib/crt1.o: In function `_start':
(.text+0x18): undefined reference to `main'
collect2: ld returned 1 exit status

Any help on how to fix this problem would be hugely appreciated. \
cheers.

---

### Post by Tony Flury on 2011-05-10
what is the command line that you use to compile your code ?

Does it happen with even the simplest program ?

Do you have build-essentials installed : 

```

sudo apt-get install build-essential

```

---

### Post by hugom on 2011-05-10
Its been working fine for the past month and its now doing this.

Yep, got the build essential and it does it with the simplest programs.

I usually just the ... gcc "file name" -o "output name" .... If that makes any sense. It's been working fine for months but now it doesn't.

---

### Post by Tony Flury on 2011-05-10
can you post the simplest code snippet (something like Hello world) that recreates the problem.

The error is a linker problem (not the compiler) and it suggests that the module you are trying to compile does not have a "main" defined.

---

### Post by hugom on 2011-05-10
#include <stdio.h>
int main()
{
printf(“Hello world.\n”);
return(0);
}

Even something like that gives that response.

---

### Post by hugom on 2011-05-10
Fixed the problem was just me doing something stupid!

Thanks all for your help though

---

### Post by Tony Flury on 2011-05-10
What was the problem, you could help others ?

---

### Post by hugom on 2011-05-10
It was actually me just consistently doing a typo the entire time, problem with the new keyboard.

Sorry didn't think it was necessary to post because it was purely my bad.

---

### Post by Tony Flury on 2011-05-10
It happens - no worries. Glad you got it sorted :-)
I spent a couple of days at work isolating what i thought was bad code across 20 modules, which turned out to be a simple typo in our build system.

Did you want to mark this thread as Solved ?

---

