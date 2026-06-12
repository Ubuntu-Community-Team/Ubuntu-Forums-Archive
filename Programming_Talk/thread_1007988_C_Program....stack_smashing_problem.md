---
title: "C Program....stack smashing problem"
date: 2008-12-11
forum: Programming Talk
---

### Post by ooobooontooo on 2008-12-11
I wrote this really simple code in C:
```
#include <stdio.h>
#include <string.h>

int main() {
  char message[10];
  int count, i;

  strcpy(message, "Hello, world!");

  printf("Repeat how many times? ");
  scanf("%d", &count);

  for(i=0; i < count; i++) printf("%3d - %s\n", i, message);
}
```
Yet, I'm getting an error that says stack smashing detected:
```
Repeat how many times? 2
  0 - Hello, world!
  1 - Hello, world!
*** stack smashing detected ***: ./a.out terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7f0d138]
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x0)[0xb7f0d0f0]
./a.out[0x80484ca]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7e36450]
./a.out[0x80483d1]
...
```
Can anyone tell me what's wrong?

---

### Post by skullmunky on 2008-12-11
I don't know what stack smashing is exactly but there's a problem with your string copy.  message[] is only 10 characters, but you're copying in a string with more, so it's overflowing the allocated memory for the array.  Give the array more space.

---

### Post by ooobooontooo on 2008-12-11
That's ingenious. I can't believe I mistyped 20... That seems to have solved the stack smashing problem. I guess that arises when there's problems with boundaries in strings.
But that does raise another interesting equation. How come it worked for the first tow cases. Shouldn't it have given me the error when I tried to do the strcpy?

---

### Post by mdurham on 2008-12-11
> **ooobooontooo said:**
> But that does raise another interesting equation. How come it worked for the first tow cases. Shouldn't it have given me the error when I tried to do the strcpy?
I think the stack error isn't detected until the function terminates, when some 'stack smash checker' checks the state of the stack. Maybe it finds an invalid return address or a missing marker that has been placed there to detect such things.

---

### Post by SeanHodges on 2008-12-11
> **ooobooontooo said:**
> That's ingenious. I can't believe I mistyped 20... That seems to have solved the stack smashing problem. I guess that arises when there's problems with boundaries in strings.
But that does raise another interesting equation. How come it worked for the first tow cases. Shouldn't it have given me the error when I tried to do the strcpy?

C doesn't perform array bounds checking, so if you write more data to the array than is allocated, it will put that data in it regardless. This is causing the buffer overflow.

The reason it doesn't report the error until the end is that the compiler has included a stack integrity check on the return of your main() function, which is flagging up the overflows at the end of your program.

From Wikipedia:

> Stack-smashing protection is used to detect the most common buffer overflows by checking that the stack has not been altered when a function returns. If it has been altered, the program exits with a segmentation fault. Three such systems are Libsafe,[18] and the StackGuard[19] and ProPolice[20] gcc patches.

---

### Post by ooobooontooo on 2008-12-11
That makes sense. I suppose that's why they called it stack smashing error instead of buffer overflow. Because they don't check the integrity of the stack until the very end. Thanks for all the help

---

### Post by meson2439 on 2008-12-11
Is there a reason for you to use strcpy(). You could just print the address after initializing message[20]="Hello, world.". I don't understand the reason you need to do strcpy. Isn't that just redundant. Sorry for the noob question...:confused:

---

### Post by PmDematagoda on 2008-12-11
You also could have used an unsized array along with what was suggested by meson2439, IMO it helps reduce such simple, yet serious(serious as in, the program can crash) errors.

---

### Post by dribeas on 2008-12-11
> **meson2439 said:**
> Is there a reason for you to use strcpy(). You could just print the address after initializing message[20]="Hello, world.". I don't understand the reason you need to do strcpy. Isn't that just redundant. Sorry for the noob question...:confused:

You might need to change the contents of the string after initialization, or you might not be using a literal for initialization but rather another zero terminated string. Those two reasons would force you to use strcpy (or better strncpy).

Now, if you are just initializing and with a literal, you can just write:
```

char message[] = "Hello, world";

```

Note that you are not providing a size for the array. The compiler will create an array of appropriate size (13: 12 chars + terminating 0). At any rate, it will not be much more efficient than using strcpy (only added cost of the function call). Then again, if you don't plan on changing the contents and just want a way to refer to the string you can use:
```

char *message = "Hello, world";

```

That will create a pointer variable pointing to the constant string "Hello, world". Note that in this last case, the string will be placed in a segment of your program that will not be modifiable, and that you cannot free that pointer either. This will also be the fastest bet (if your requirements allow you to), as only a pointer is assigned, and no memory is copied from one place to another.

---

### Post by ooobooontooo on 2008-12-12
There was no real reason I was using strcpy except for the fact that my book was using it. Thanks.

---

