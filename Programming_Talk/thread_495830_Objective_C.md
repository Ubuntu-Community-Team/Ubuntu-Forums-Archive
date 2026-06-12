---
title: "Objective C"
date: 2007-07-08
forum: Programming Talk
---

### Post by Note360 on 2007-07-08
Yeah, i started learning objective C on my fathers macintosh, but then when I came back and I tried to run my hello world which uses Foundation/Foundation.h and NSLog it wont run. It used to say Foundation not found, but i fixed that.

now i get this

```

/tmp/cct8XzTP.o: In function `main':
hello.m:(.text+0x1a): undefined reference to `NSLog'
/tmp/cct8XzTP.o: In function `__objc_gnu_init':
hello.m:(.text+0x35): undefined reference to `__objc_exec_class'
/tmp/cct8XzTP.o:(.data+0x208): undefined reference to `__objc_class_name_NXConstantString'
collect2: ld returned 1 exit status

```

This is my hello world

```
#include <Foundation/Foundation.h>

int main (int argc, const char * argv[]) 
{
    NSLog (@"Hello World!");
}


```


I cant seem to figure out what my problem is. Does GNUstep use a different library than Foundation? or is NSLog Cocoa only?

---

### Post by Note360 on 2007-07-09
I hate kinda bumping, but all help is appreciated =)

---

### Post by WebDrake on 2007-07-09
> **Note360 said:**
> I hate kinda bumping, but all help is appreciated =)
People may not know ...  I hate to suggest the obvious but you have read through the documentation here?
[http://www.gnustep.org/](http://www.gnustep.org/)

Can't suggest more as I'm not familiar with ObjC or GNUstep.  But it might be that NSLog has a different name in GNUstep.

How did you "fix" Foundation.h not being found?

---

### Post by bashologist on 2007-07-09
Could it be that there's no prototype in the header? I don't know.

---

### Post by Note360 on 2007-07-09
I fixed Foundation not being found by installing it via synaptic.

---

### Post by winch on 2007-07-09
What commands are you using to build it?
See this for an example.
[http://www.gnustep.org/resources/documentation/Developer/Base/ProgrammingManual/manual_1.html#SEC11](http://www.gnustep.org/resources/documentation/Developer/Base/ProgrammingManual/manual_1.html#SEC11)

---

### Post by Note360 on 2007-07-09
Odd. Using the make file works, but using just plain old gcc didnt work. I wonder why? Sorry, guys problem solved I guess. It is a nice language though.

---

### Post by stchman on 2007-07-09
> **Note360 said:**
> Yeah, i started learning objective C on my fathers macintosh, but then when I came back and I tried to run my hello world which uses Foundation/Foundation.h and NSLog it wont run. It used to say Foundation not found, but i fixed that.

now i get this

```

/tmp/cct8XzTP.o: In function `main':
hello.m:(.text+0x1a): undefined reference to `NSLog'
/tmp/cct8XzTP.o: In function `__objc_gnu_init':
hello.m:(.text+0x35): undefined reference to `__objc_exec_class'
/tmp/cct8XzTP.o:(.data+0x208): undefined reference to `__objc_class_name_NXConstantString'
collect2: ld returned 1 exit status

```

This is my hello world

```
#include <Foundation/Foundation.h>

int main (int argc, const char * argv[]) 
{
    NSLog (@"Hello World!");
}


```


I cant seem to figure out what my problem is. Does GNUstep use a different library than Foundation? or is NSLog Cocoa only?

You need to use ANSI C.

Your program will look like this when done:
```

#include <stdio.h>

int main (int argc, char * argv[])
{
      printf("Hello World\n");
      return 0;
}

```

I am not really familiar with C implementation on a Mac with Foundatiuon but for Ubuntu you must install build-essential

sudo apt-get -y install build-essential

This is all the headers for gcc/g++

---

### Post by Note360 on 2007-07-09
> **stchman said:**
> You need to use ANSI C.

Your program will look like this when done:
```

#include <stdio.h>

int main (int argc, char * argv[])
{
      printf("Hello World\n");
      return 0;
}

```I am not really familiar with C implementation on a Mac with Foundatiuon but for Ubuntu you must install build-essential

sudo apt-get -y install build-essential

This is all the headers for gcc/g++

The point was to do it in pure Obj C to see if it works. I got it workign if i use the makefile listed on that page. I already know basic C and I installed build-essentials a long time ago. Objective C and Ansi C are two different languages and Objective C works on all machines if you can get GNUstep working (which wasn't too hard) Any way it works now. Now no more NSLog (because it really kinda sucks with the timestamps). Basically the problem was I didnt have the Headers for Objective C and gcc wasnt comiled with objective C support (I think).

---

### Post by Note360 on 2007-07-09
That NSLog thing was just to see if I was making contact with the library. Here is some real Objective C (which compiles fine). Its just a simple little thing.

```

#include <stdio.h>
#include <Foundation/Foundation.h>

@interface Tire : NSObject

- (void) description;

@end

@implementation Tire

- (void) description
{
    printf ("I am a tire. I make contact with the road.\n");
}

@end

int main ()
{
    Tire *t;
    t = [Tire new];
    [t description];

    return 0;
}

```

---

