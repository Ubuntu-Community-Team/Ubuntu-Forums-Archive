---
title: "[Objective-C] HOWTO: Compiling Objective-C with gcc"
date: 2009-02-08
forum: Programming Talk
---

### Post by nvteighen on 2009-02-08
Hi there!
I'm here looking a bit into Objective-C and I'm impressed. It's a really nice language (just "C with Classes" not C++ bloat) but I won't go into that here.

But I had real troubles to get the sources compiled with gcc under Debian (so Ubuntu is surely the same) and after a lot of research, I could. Here's a little how-to for anyone interested.

1. Install the GNU Objective-C Runtime.
```

sudo apt-get install gobjc

```

Despite what some webpages imply, you **don't need** GNUStep (the GNU clone of Apple NeXTStep).

2. Write some source. Here's a very small example.
```

// hello.m
#import <objc/Object.h>
#import <stdio.h>

@interface Number: Object
{
@public
    int number;
    
}

- (void)printNum;

@end

@implementation Number: Object


- (void)printNum
{
    printf("%d\n", number);
}

@end

int main(void)
{
    Number *myNumber = [Number new]; // equal to [[Number alloc] init]

    myNumber->number = 6;

    [myNumber printNum];

    return 0;
}

```

As you see, there are some differences with Apple Objective-C. The base object class is called Object, not NSObject. The Object class's interface is at objc/Object.h, as you see it #import'ed.

3. Compile:
```

gcc -o hello hello.m -Wall -lobjc

```

-o and -Wall are optional, as you surely know if you have used gcc or g++ before for C or C++, respectively. The key argument is -lobjc. For some weird reason, you have to manually link to the GNU Objective-C Runtime, otherwise, you're lost.

If you happen to be using gcc in Mac OS X, then you have to also pass -fgnu-runtime to avoid the Apple NeXTStep Runtime.

@end ;)

---

### Post by CptPicard on 2009-02-08
I have been thinking of investigating objc too.. what are you using to learn from? :)

---

### Post by nvteighen on 2009-02-08
> **CptPicard said:**
> I have been thinking of investigating objc too.. what are you using to learn from? :)
Objective-C is just a couple of Smalltalk-like extensions over C, so you just learn those extensions and the rest is pure old C. It's a really nice OOP low-level language.

I use Apple's official documentation. But take in account the #import <objc/Object.h> and the Object vs. NSObject issues I described above.

[http://developer.apple.com/documentation/Cocoa/Conceptual/ObjectiveC/Introduction/chapter_1_section_1.html#//apple_ref/doc/uid/TP30001163-CH1-SW2](http://developer.apple.com/documentation/Cocoa/Conceptual/ObjectiveC/Introduction/chapter_1_section_1.html#//apple_ref/doc/uid/TP30001163-CH1-SW2)

This is also very good:
[http://objc.toodarkpark.net/](http://objc.toodarkpark.net/)

---

### Post by CptPicard on 2009-02-08
Too bad that at least according to the "computer language benchmarks game" ObjC is about comparable to Java in speed, and at least for me the only reason to move down the ladder in the C-direction is an increase of speed. Having some higher-level features thrown in on top of C would be really nice though (especially so that it does not turn into C++ ;) )

---

### Post by escapee on 2009-02-08
It really is a nice language, but unfortunately it needs so much work to really be useful outside of OSX (in terms of libraries).  I think the GTK binding project has halted as well.  Not sure what other libraries are out there at the moment, it's been a while since I've looked.

---

### Post by cb951303 on 2009-02-08
It would be really great to see someone compare objc to vala :KS

---

### Post by cpatton90 on 2009-03-14
I'm a CS student in my last week of an intro C class... my first marked exploration in programming was in Python, Ruby, etc. and a little C++. I'm addicted to OOP, but I love how close C is to the hardware, and indeed, how much more real it feels. The  solution might be C++, but I find the code to be quite ugly and too complicated. I've found objc to be the natural solution... I really hope to see more support for it, especially on the GNU/Linux platform.

---

### Post by cpatton90 on 2009-03-14
thanks for the HOWTO, by the way!

---

### Post by nvteighen on 2009-03-14
> **cpatton90 said:**
> I'm a CS student in my last week of an intro C class... my first marked exploration in programming was in Python, Ruby, etc. and a little C++. I'm addicted to OOP, but I love how close C is to the hardware, and indeed, how much more real it feels. The  solution might be C++, but I find the code to be quite ugly and too complicated. I've found objc to be the natural solution... I really hope to see more support for it, especially on the GNU/Linux platform.

The support is there, the issue are the libraries. We're stuck on a NeXTStep/GNUStep (or its fork SideStep) mindset where Objective-C development means to necessarily use those frameworks, which is totally untrue.

That's why some people (including me) are working on a joint effort to create non-Step Free Software libraries for basic core classes. Look at COList at my sig. Look at the sister projects by the Core Objectives team too.

---

### Post by bechir62 on 2009-11-26
After compilation you get a hello file of type exec

to launch it type :
/.hello

thanks for the HOW TO nvteighen

---

### Post by smasadat on 2010-05-26
it works fine just executing the exec file like-
./hello

---

### Post by yilin on 2010-06-02
Does any one managed to build gnustep from source via svn on ubuntu 10.04?
I have trouble make it work

---

### Post by forestgump2012 on 2012-03-22
Thanks ,I have been trying compiling objective-c with gcc on linux,not installing gnustep.
I have done it.  thank you very much!

---

### Post by hoboy on 2012-03-23
Do you use any ide for your Objective-C coding  ?

---

