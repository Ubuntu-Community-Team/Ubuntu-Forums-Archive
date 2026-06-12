---
title: "Problem with objective-c"
date: 2012-09-21
forum: Programming Talk
---

### Post by AADAS on 2012-09-21
When  I try to compile a program on objective-c with

```
gcc -o hello hello.m -I /usr/include/GNUstep/ -L /usr/lib/GNUstep/ -lgnustep-base -fconstant-string-class=NSConstantString
```
 I get ```
hello.m:1:34: fatal error: Foundation/Foundation.h: No such file or directory compilation terminated.
```
Here is the code:```
#import <Foundation/Foundation.h>

int main (int argc, const char * argv[])
{
        NSAutoreleasePool * pool = [[NSAutoreleasePool alloc] init];

        NSLog (@"hello world");
        [pool drain];
        return 0;
}

```

---

### Post by sandyd on 2012-09-21
**moved to programming talk**

---

### Post by einonm on 2012-09-23
The gcc param '-I /usr/include/GNUstep/' tells gcc where to look for include files, so it would be looking for a directory 'Foundation' in the /usr/include/GNUstep/ directory, in which should be the file Foundation.h.

So does the file /usr/include/GNUstep/Foundation/Foundation.h exist, and is it readable by you?

---

### Post by Tallee on 2012-11-14
may be the cause of the issue is that you terminal is at your home directory, you can try following:
cd ..
cd ..
and then, your compiling command.
hope this will help!

---

