---
title: "Objective C programing"
date: 2009-08-30
forum: Programming Talk
---

### Post by unbuntubrock on 2009-08-30
I'm trying to learn Objective C, with a book by Stephen Kochan, Programing in Objective C 2.0. I'd like to be able to do alot of the learning away from my mac. So i've been playing for the last two days with GNUstep for windows and then also with Ubuntu. I'm not looking for anything special, the book takes you from writing your first program output - "programing is fun" through a good portion of objective c. 

My problem seems to be the libraries (i think). I could get the following to work under GNUstep with windows (compile and run)

```
//First Example
#import <Foundation/Foundation.h>

int main (int argc, const char * argv[])
{        
          
  NSAutoreleasePool * pool = [[NSAutoreleasePool alloc] init];
  NSLog (@"Programming is fun!");

  [pool release];
  return 0;
}
    
~                                                                               
~                                                                               
~          
```except i had to change and specify the actual directory where the foundation file resides. 

I can't get this to compile on ubuntu. i've installed most of the packages that i think i needed based upon reading alot of posts. 

thoughts.?

Compiling the code on Ubuntu gives me these errors:

monica@Dell-Laptop:~/Progs$ gcc prog1.m -o prog1 -lobjc
prog1.m:2:34: error: Foundation/Foundation.h: No such file or directory
prog1.m: In function ‘main’:
prog1.m:7: error: ‘NSAutoreleasePool’ undeclared (first use in this function)
prog1.m:7: error: (Each undeclared identifier is reported only once
prog1.m:7: error: for each function it appears in.)
prog1.m:7: error: ‘pool’ undeclared (first use in this function)
prog1.m:8: error: cannot find interface declaration for ‘NXConstantString’
                                 
However the code from this [post]("http://ubuntuforums.org/showthread.php?t=1064045") would compile but i couldn't get the program to run.

---

### Post by nvteighen on 2009-08-30
You have to also link the GNUStep base library and tell the compiler where the headers are.

```

gcc -o whatever whatever.m -I/usr/include/GNUStep -lobjc -L/usr/lib/GNUStep -lgnustep-base

```

Usually, one uses GNUStep's Makefiles to compile, actually. Look at [http://www.gnustep.org/resources/documentation/Developer/Base/ProgrammingManual/manual_toc.html](http://www.gnustep.org/resources/documentation/Developer/Base/ProgrammingManual/manual_toc.html)

The status of what OpenStep is is rather confusing. It obviously isn't the "Objective-C Standard Library" like the C or C++ Std. Libs. are, but it finally turns out that to do anything productive in Objective-C, you need OpenStep...

The code in my How-To is without GNUStep... I may post an appendix to it :)

---

### Post by unbuntubrock on 2009-09-03
Thanks, but that didn't seem to do it either. I'm still getting the same errors. The thing that is driving me crazy is that i was able to do all of this and get farther under GNUstep for windows. 

Someone suggested downloading cent os as it would contain all of the libraries for obj c. I ask this because i've been going through all of the packages in synaptic package manager and downloading all of the ones that i thought might be relevant.

The error messages though seem to be the same and revolve around 
prog1.m:7: error: ‘pool’ undeclared (first use in this function)
prog1.m:8: error: cannot find interface declaration for ‘NXConstantString’

Thoughts?

---

### Post by j7%&lt;RmUg on 2009-09-03
You have undeclared variables, i dont even know objective-C and i could see that.

Currently the following variables need to be declared:

pool
NSAutoreleasePool

Hope iv helped.

---

### Post by JordyD on 2009-09-03
> **nisshh said:**
> You have undeclared variables, i dont even know objective-C and i could see that.

Currently the following variables need to be declared:

pool
NSAutoreleasePool

Hope iv helped.

NSAutoreleasePool isn't a variable.

---

### Post by nvteighen on 2009-09-03
> **nisshh said:**
> You have undeclared variables, i dont even know objective-C and i could see that.

Currently the following variables need to be declared:

pool
NSAutoreleasePool

Hope iv helped.

Those are declared in Foundation/Foundation.h

Just an advice... Never talk about anything you don't know about. Sorry if I sound too hard... but it's the very truth and I tell you this so you can improve yourself and know this weakness of yours; I myself have done that same mistake and I know exactly how you feel by reading this post, but it's part of the learning process.

If interested in Objective-C, look at the stickies... It's a great language, a wonderful and senseful OOP low level language.

---

### Post by unbuntubrock on 2009-09-03
Thanks, but back to "me." Any thoughts on what i might try, besides just going back to my mac and xcode.:o

---

