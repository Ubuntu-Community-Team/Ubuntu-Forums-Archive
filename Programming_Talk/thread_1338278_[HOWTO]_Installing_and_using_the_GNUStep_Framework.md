---
title: "[HOWTO] Installing and using the GNUStep Framework"
date: 2009-11-26
forum: Programming Talk
---

### Post by nvteighen on 2009-11-26
Hi again!

Some people know my How-to guide to compile Objective-C code using gcc ([http://ubuntuforums.org/showthread.php?t=1064045](http://ubuntuforums.org/showthread.php?t=1064045)). In that How-to I showed how to create an executable **without GNUStep**. The only requirement was the GNU Objective-C Runtime, which is something completely different.

But for sure Objective-C is usually used with the OpenStep libraries or aka. "Framework". There are several implementations of the OpenStep framework; the most used and most stable one is Apple NeXTStep, derived from NeXT NeXTStep. In the Free Software world, we've got two ones: GNU GNUStep and SideStep (a GNUStep fork). Both Free ones are outdated with respect to the current OpenStep specifications; the reasons are many, specially lack of interest in the GNU/Linux community and the outdated GNU Objective-C Runtime (still doesn't support Objective-C 2.0... this means no automatic Garbage Collection, for example).

There's also another issue with GNUStep. You may have read that NeXT/GNUStep is an "object-oriented framework" and seen a picture of NeXT's desktop environment or its GNU clone called Window Maker. Sometimes people call these Desktop Environments as NeXT/GNUStep, which is as false as to say GTK+ is a DE. But don't think this is because people are just plain idiots that don't do their research... No, the situation is a bit comparable to GTK+: GTK+ was initially just a part of GIMP but it grew up into a different project. So, the OpenStep libraries were initially just part of NeXT's NeXTStep OS, then became the OS's API, the OS got extincted but the libraries proved to be useful independently... and the name wasn't changed. Nowadays OpenStep is a bunch of libraries, a framework, that includes lots of things: a general programming library, a GUI toolkit, etc.

If you hear about Apple Cocoa, you should know it is how the Apple GUI toolkit from Apple is known and is NeXTStep based. Nothing else. Don't confuse it with Apple Carbon (the Mac OS Classic compatibility layer)! (yeah... Apple should use more descriptive names).

Actually, much of my intention on writing this How-to is about giving a clearer image of what OpenStep, GNUStep, NeXTStep really are. Having these concepts clear, the steps to follow will be really much easier to follow.

**1. Installing (and how to install what)**
The best thing you can do is to install **gnustep-devel**. That package also includes the development documentation.

```

sudo aptitude install gnustep-devel

```

You can, though, install GNUStep partially. For example, if you're not interested on the GUI toolkit, you could install libgnustep-base-dev... but that might be uncomfortable for someone making his first steps with GNUStep.

**2. An example source code**
You'll have to learn how to use the GNUStep API, of course. The most important thing is probably, that you use NSObject as your root class instead of Object (declared at objc/Object.h). The NSObject class has a lot of advantages over the minimal Object one.

Here's a little example of an Objective-C/GNUStep application (taken from 
```

/* 
 * Copyright c 2001-2004 Free Software Foundation 
 *
 * Permission is granted to make and distribute verbatim copies of this manual
 * provided the copyright notice and this permission notice are preserved on all
 * copies.
 *
 * Permission is granted to copy and distribute modified versions of this manual
 * under the conditions for verbatim copying, provided also that the entire
 * resulting derived work is distributed under the terms of a permission notice
 * identical to this one.
 *
 * Permission is granted to copy and distribute translations of this manual into
 * another language, under the above conditions for modified versions.
 */


#include <stdio.h>
/*
 * The next #include line is generally present in all Objective-C
 * source files that use GNUstep. The Foundation.h header file
 * includes all the other standard header files you need.
 */
#include <Foundation/Foundation.h>

/*
 * Declare the Test class that implements the class method (classStringValue).
 */
@interface Test
+ (const char *) classStringValue;
@end

/*
 * Define the Test class and the class method (classStringValue).
 */
@implementation Test
+ (const char *) classStringValue;
{
    return "This is the string value of the Test class";
}
@end

/*
 * The main() function: pass a message to the Test class
 * and print the returned string.
 */
int main(void)
{
    printf("%s\n", [Test classStringValue]);
    return 0;
}

```

**3. Compiling**
Ok, there are two ways of compiling a GNUStep program. One is using GNUStep Makefiles, which are usually a hassle to use with small projects as they have to be customized in order to avoid having the whole GNUStep Framework linked to your program. The other one is to do this, which will just link the GNUStep base library:

```

gcc -o test test.m -I/usr/include/GNUstep -L/usr/lib/GNUstep -lobjc -lgnustep-base -Wall

```

First, "GNUstep" is the correct name of the directory, as annoying it can be. Second, you still have to link to libobjc.so, which is the Objective-C Runtime!

For GNUStep Makefiles, refer to the Manual. For GUI applications and big stuff, they may be much more useful than the command I've given above. But for someone that just wants to learn about GNUStep, this is all what's needed.

@end :D

---

### Post by stylx on 2010-06-19
> **nvteighen said:**
> Hi again!

Some people know my How-to guide to compile Objective-C code using gcc ([http://ubuntuforums.org/showthread.php?t=1064045](http://ubuntuforums.org/showthread.php?t=1064045)). In that How-to I showed how to create an executable **without GNUStep**. The only requirement was the GNU Objective-C Runtime, which is something completely different.

But for sure Objective-C is usually used with the OpenStep libraries or aka. "Framework". There are several implementations of the OpenStep framework; the most used and most stable one is Apple NeXTStep, derived from NeXT NeXTStep. In the Free Software world, we've got two ones: GNU GNUStep and SideStep (a GNUStep fork). Both Free ones are outdated with respect to the current OpenStep specifications; the reasons are many, specially lack of interest in the GNU/Linux community and the outdated GNU Objective-C Runtime (still doesn't support Objective-C 2.0... this means no automatic Garbage Collection, for example).

There's also another issue with GNUStep. You may have read that NeXT/GNUStep is an "object-oriented framework" and seen a picture of NeXT's desktop environment or its GNU clone called Window Maker. Sometimes people call these Desktop Environments as NeXT/GNUStep, which is as false as to say GTK+ is a DE. But don't think this is because people are just plain idiots that don't do their research... No, the situation is a bit comparable to GTK+: GTK+ was initially just a part of GIMP but it grew up into a different project. So, the OpenStep libraries were initially just part of NeXT's NeXTStep OS, then became the OS's API, the OS got extincted but the libraries proved to be useful independently... and the name wasn't changed. Nowadays OpenStep is a bunch of libraries, a framework, that includes lots of things: a general programming library, a GUI toolkit, etc.

If you hear about Apple Cocoa, you should know it is how the Apple GUI toolkit from Apple is known and is NeXTStep based. Nothing else. Don't confuse it with Apple Carbon (the Mac OS Classic compatibility layer)! (yeah... Apple should use more descriptive names).

Actually, much of my intention on writing this How-to is about giving a clearer image of what OpenStep, GNUStep, NeXTStep really are. Having these concepts clear, the steps to follow will be really much easier to follow.

**1. Installing (and how to install what)**
The best thing you can do is to install **gnustep-devel**. That package also includes the development documentation.

```

sudo aptitude install gnustep-devel

```

You can, though, install GNUStep partially. For example, if you're not interested on the GUI toolkit, you could install libgnustep-base-dev... but that might be uncomfortable for someone making his first steps with GNUStep.

**2. An example source code**
You'll have to learn how to use the GNUStep API, of course. The most important thing is probably, that you use NSObject as your root class instead of Object (declared at objc/Object.h). The NSObject class has a lot of advantages over the minimal Object one.

Here's a little example of an Objective-C/GNUStep application (taken from 
```

/* 
 * Copyright c 2001-2004 Free Software Foundation 
 *
 * Permission is granted to make and distribute verbatim copies of this manual
 * provided the copyright notice and this permission notice are preserved on all
 * copies.
 *
 * Permission is granted to copy and distribute modified versions of this manual
 * under the conditions for verbatim copying, provided also that the entire
 * resulting derived work is distributed under the terms of a permission notice
 * identical to this one.
 *
 * Permission is granted to copy and distribute translations of this manual into
 * another language, under the above conditions for modified versions.
 */


#include <stdio.h>
/*
 * The next #include line is generally present in all Objective-C
 * source files that use GNUstep. The Foundation.h header file
 * includes all the other standard header files you need.
 */
#include <Foundation/Foundation.h>

/*
 * Declare the Test class that implements the class method (classStringValue).
 */
@interface Test
+ (const char *) classStringValue;
@end

/*
 * Define the Test class and the class method (classStringValue).
 */
@implementation Test
+ (const char *) classStringValue;
{
    return "This is the string value of the Test class";
}
@end

/*
 * The main() function: pass a message to the Test class
 * and print the returned string.
 */
int main(void)
{
    printf("%s\n", [Test classStringValue]);
    return 0;
}

```

**3. Compiling**
Ok, there are two ways of compiling a GNUStep program. One is using GNUStep Makefiles, which are usually a hassle to use with small projects as they have to be customized in order to avoid having the whole GNUStep Framework linked to your program. The other one is to do this, which will just link the GNUStep base library:

```

gcc -o test test.m -I/usr/include/GNUstep -L/usr/lib/GNUstep -lobjc -lgnustep-base -Wall

```

First, "GNUstep" is the correct name of the directory, as annoying it can be. Second, you still have to link to libobjc.so, which is the Objective-C Runtime!

For GNUStep Makefiles, refer to the Manual. For GUI applications and big stuff, they may be much more useful than the command I've given above. But for someone that just wants to learn about GNUStep, this is all what's needed.

@end :D

Sorry this doesn't work with ubuntu 10.4 gnustep-devel is a broken package

---

### Post by nvteighen on 2010-06-19
> **stylx said:**
> Sorry this doesn't work with ubuntu 10.4 gnustep-devel is a broken package

Hm... I don't know. Ask the package mantainers; I'm no longer using Ubuntu and gnustep-devel was the way to make it work... and is still the way in Debian.

---

### Post by r-senior on 2010-07-24
I've been playing around with Objective-C and GNUstep and I've got as far as getting simple command-line tools to work, both using vanilla gcc and GNUmakefiles.

So a program like this works:

```
#import <Foundation/Foundation.h>

int main (void) { 
  NSLog (@"Executing");
  return 0;
}
```

with a GNUmakefile like this:

```
include $(GNUSTEP_MAKEFILES)/common.make

TOOL_NAME = LogTest
LogTest_OBJC_FILES = source.m

include $(GNUSTEP_MAKEFILES)/tool.make
```

It works :) 

$ ./obj/LogTest
2010-07-24 12:57:30.356 LogTest[29863] Executing

Just a pity the Objective-C 2.0 features aren't supported. :(

But when I try to create a GUI application:

```
#import <Foundation/Foundation.h>
#import <AppKit/AppKit.h>

int main (void) {
	NSAutoreleasePool *pool;
	pool = [NSAutoreleasePool new];
	[NSApplication sharedApplication];
	[COLOR="Red"]NSRunAlertPanel (@"Test", @"Hello from the GNUstep AppKit", nil, nil, nil);[/COLOR]
	return 0;
}
```

with the appropriate GNUmakefile (I found these examples in a GNUstep tutorial):

```
include $(GNUSTEP_MAKEFILES)/common.make

APP_NAME = AppTest
AppTest_OBJC_FILES = source.m

include $(GNUSTEP_MAKEFILES)/application.make

```

That doesn't work :(

$ openapp ./AppTest.app
Segmentation fault

EDIT: The segmentation fault occurs on the line in red where it tries to show the alert.

Any ideas? I'm running 10.04, all up to date, 64-bit.

I also get segmentation faults when I try to run any of the GNUstep tools, such as Project Center. I did find a post that suggested installing Gorm, which I think may be what makes gnustep-devel "broken", but that doesn't help?

---

### Post by nvteighen on 2010-07-24
> **r-senior said:**
> I've been playing around with Objective-C and GNUstep and I've got as far as getting simple command-line tools to work, both using vanilla gcc and GNUmakefiles.

So a program like this works:

```
#import <Foundation/Foundation.h>

int main (void) { 
  NSLog (@"Executing");
  return 0;
}
```

with a GNUmakefile like this:

```
include $(GNUSTEP_MAKEFILES)/common.make

TOOL_NAME = LogTest
LogTest_OBJC_FILES = source.m

include $(GNUSTEP_MAKEFILES)/tool.make
```

It works :) 

$ ./obj/LogTest
2010-07-24 12:57:30.356 LogTest[29863] Executing

Just a pity the Objective-C 2.0 features aren't supported. :(

But when I try to create a GUI application:

```
#import <Foundation/Foundation.h>
#import <AppKit/AppKit.h>

int main (void) {
	NSAutoreleasePool *pool;
	pool = [NSAutoreleasePool new];
	[NSApplication sharedApplication];
	[COLOR="Red"]NSRunAlertPanel (@"Test", @"Hello from the GNUstep AppKit", nil, nil, nil);[/COLOR]
	return 0;
}
```

with the appropriate GNUmakefile (I found these examples in a GNUstep tutorial):

```
include $(GNUSTEP_MAKEFILES)/common.make

APP_NAME = AppTest
AppTest_OBJC_FILES = source.m

include $(GNUSTEP_MAKEFILES)/application.make

```

That doesn't work :(

$ openapp ./AppTest.app
Segmentation fault

EDIT: The segmentation fault occurs on the line in red where it tries to show the alert.

Any ideas? I'm running 10.04, all up to date, 64-bit.

I also get segmentation faults when I try to run any of the GNUstep tools, such as Project Center. I did find a post that suggested installing Gorm, which I think may be what makes gnustep-devel "broken", but that doesn't help?

Hum... I'm experiencing something similar on Debian Squeeze... but it's not segfaulting... Let me check.

---

### Post by Mark76 on 2010-07-24
I get a whole list of errors to do with loading /var/lib/defoma/gnustep -nfont.d/Font/name of font whenever I try to run any GS app.

---

### Post by nvteighen on 2010-07-24
> **Mark76 said:**
> I get a whole list of errors to do with loading /var/lib/defoma/gnustep -nfont.d/Font/name of font whenever I try to run any GS app.

There's a really bad major bug ([http://bugs.debian.org/568307](http://bugs.debian.org/568307)) that's preventing GNUStep working on Ubuntu **and** Debian (testing, which Ubuntu always syncs with)... Just look at Google, it seems to be defoma's fault or something.

Moreover, the gnustep-back-common package at Debian Squeeze's repos cannot purge the fonts when uninstalled... you have to manually remove /var/lib/defoma/gnustep-nfont.d and then run defoma-reconfigure (everything as root).

It seems gnustep-back-common version 0.18.0 fixes this, but that's on Debian unstable...

---

### Post by Mark76 on 2010-07-24
Okay. I removed the gnustep-nfont.d folder, ran defoma-reconfigure and then tried running GWorkspace from the terminal and got

> 2010-07-24 16:13:04.517 GWorkspace[16096] No fonts found!

---

### Post by r-senior on 2010-07-24
Well it's good to see I'm not the only one ;)

I'm not seeing font problems. I tried running the GUI application with debug set and I get this:

```
(gdb) run
Starting program: /home/richard/GNUstep/Projects/AppTest/AppTest.app/AppTest 
[Thread debugging using libthread_db enabled]

Program received signal SIGSEGV, Segmentation fault.
0x00007ffff70eb75e in ?? () from /usr/lib/libgnustep-base.so.1.19
```

---

### Post by Mark76 on 2010-07-24
That's because you have no fonts installed.

Either that or you hate anti-aliasing.

---

### Post by nvteighen on 2010-07-24
> **Mark76 said:**
> Okay. I removed the gnustep-nfont.d folder, ran defoma-reconfigure and then tried running GWorkspace from the terminal and got

Er... those instructions were if you wanted to remove GNUStep... I think I phrased it clearly, but if I wasn't, I apologize. Reinstall gnustep-back-common.

---

### Post by r-senior on 2010-07-26
OK, I've made progress.

I decided to try removing all the Ubuntu GNUstep packages and building GNUstep from source. I had a few dependencies to sort out with Synaptic, in particular gobjc and xorg-dev, plus anything marked as required or recommended in [this list]("http://www.gnustep.org/resources/documentation/User/GNUstep/gnustep-howto_2.html#SEC2").

Then (after a brief foray into building each component manually, which I don't think is necessary), I used the [gnustep-startup]("http://wwwmain.gnustep.org/resources/downloads.php?site=ftp%3A%2F%2Fftp.gnustep.org%2Fpub%2Fgnustep%2F#core") script.

It needs to be run sudo of course and the GNUstep.sh file needs to be sourced to get anything to compile under GNUstep.

So I'm in a position now where I can compile and run the command line tool examples that I had working with the Ubuntu GNUstep packages. I can also compile and run things like Gorm, ProjectCenter and example GUI applications.

But I can only run them successfully as root. :( If I try to run as a normal user I get a window pop up (example attached) and then a log message like this:

$ openapp Gorm.app
/usr/GNUstep/Local/Applications/Gorm.app/Gorm: Uncaught exception NSInvalidArgumentException, reason: cifframe_do_call types (v64@0:8Q16@24@32@40Q48@56 / v60@0:8Q16@24@32@40I48@52) missmatch for addObserver:selector:name:object:suspensionBehavior:for:

Any bright ideas?

---

### Post by r-senior on 2010-07-26
OK, cancel that question. I added the following to /etc/rc.local and rebooted and it's working OK now:

```
if [ -f /usr/GNUstep/System/Tools/gdomap ]; then
  /usr/GNUstep/System/Tools/gdomap
fi
```

---

### Post by isthisfree on 2012-01-05
> **nvteighen said:**
> Hi again!

Some people know my How-to guide to compile Objective-C code using gcc ([http://ubuntuforums.org/showthread.php?t=1064045](http://ubuntuforums.org/showthread.php?t=1064045)). In that How-to I showed how to create an executable **without GNUStep**. The only requirement was the GNU Objective-C Runtime, which is something completely different.

But for sure Objective-C is usually used with the OpenStep libraries or aka. "Framework". There are several implementations of the OpenStep framework; the most used and most stable one is Apple NeXTStep, derived from NeXT NeXTStep. In the Free Software world, we've got two ones: GNU GNUStep and SideStep (a GNUStep fork). Both Free ones are outdated with respect to the current OpenStep specifications; the reasons are many, specially lack of interest in the GNU/Linux community and the outdated GNU Objective-C Runtime (still doesn't support Objective-C 2.0... this means no automatic Garbage Collection, for example).

There's also another issue with GNUStep. You may have read that NeXT/GNUStep is an "object-oriented framework" and seen a picture of NeXT's desktop environment or its GNU clone called Window Maker. Sometimes people call these Desktop Environments as NeXT/GNUStep, which is as false as to say GTK+ is a DE. But don't think this is because people are just plain idiots that don't do their research... No, the situation is a bit comparable to GTK+: GTK+ was initially just a part of GIMP but it grew up into a different project. So, the OpenStep libraries were initially just part of NeXT's NeXTStep OS, then became the OS's API, the OS got extincted but the libraries proved to be useful independently... and the name wasn't changed. Nowadays OpenStep is a bunch of libraries, a framework, that includes lots of things: a general programming library, a GUI toolkit, etc.

If you hear about Apple Cocoa, you should know it is how the Apple GUI toolkit from Apple is known and is NeXTStep based. Nothing else. Don't confuse it with Apple Carbon (the Mac OS Classic compatibility layer)! (yeah... Apple should use more descriptive names).

Actually, much of my intention on writing this How-to is about giving a clearer image of what OpenStep, GNUStep, NeXTStep really are. Having these concepts clear, the steps to follow will be really much easier to follow.

**1. Installing (and how to install what)**
The best thing you can do is to install **gnustep-devel**. That package also includes the development documentation.

```

sudo aptitude install gnustep-devel

```

You can, though, install GNUStep partially. For example, if you're not interested on the GUI toolkit, you could install libgnustep-base-dev... but that might be uncomfortable for someone making his first steps with GNUStep.

**2. An example source code**
You'll have to learn how to use the GNUStep API, of course. The most important thing is probably, that you use NSObject as your root class instead of Object (declared at objc/Object.h). The NSObject class has a lot of advantages over the minimal Object one.

Here's a little example of an Objective-C/GNUStep application (taken from 
```

/* 
 * Copyright c 2001-2004 Free Software Foundation 
 *
 * Permission is granted to make and distribute verbatim copies of this manual
 * provided the copyright notice and this permission notice are preserved on all
 * copies.
 *
 * Permission is granted to copy and distribute modified versions of this manual
 * under the conditions for verbatim copying, provided also that the entire
 * resulting derived work is distributed under the terms of a permission notice
 * identical to this one.
 *
 * Permission is granted to copy and distribute translations of this manual into
 * another language, under the above conditions for modified versions.
 */


#include <stdio.h>
/*
 * The next #include line is generally present in all Objective-C
 * source files that use GNUstep. The Foundation.h header file
 * includes all the other standard header files you need.
 */
#include <Foundation/Foundation.h>

/*
 * Declare the Test class that implements the class method (classStringValue).
 */
@interface Test
+ (const char *) classStringValue;
@end

/*
 * Define the Test class and the class method (classStringValue).
 */
@implementation Test
+ (const char *) classStringValue;
{
    return "This is the string value of the Test class";
}
@end

/*
 * The main() function: pass a message to the Test class
 * and print the returned string.
 */
int main(void)
{
    printf("%s\n", [Test classStringValue]);
    return 0;
}

```

**3. Compiling**
Ok, there are two ways of compiling a GNUStep program. One is using GNUStep Makefiles, which are usually a hassle to use with small projects as they have to be customized in order to avoid having the whole GNUStep Framework linked to your program. The other one is to do this, which will just link the GNUStep base library:

```

gcc -o test test.m -I/usr/include/GNUstep -L/usr/lib/GNUstep -lobjc -lgnustep-base -Wall

```

First, "GNUstep" is the correct name of the directory, as annoying it can be. Second, you still have to link to libobjc.so, which is the Objective-C Runtime!

For GNUStep Makefiles, refer to the Manual. For GUI applications and big stuff, they may be much more useful than the command I've given above. But for someone that just wants to learn about GNUStep, this is all what's needed.

@end :D
Thanks for posting the above.  I'm a complete newbie to this.  I have some programming experience although that was on Windows and with existing libraries.  I get the following error when trying your suggestion:

> In file included from /usr/include/GNUstep/Foundation/NSClassDescription.h:30:0,
                 from /usr/include/GNUstep/Foundation/Foundation.h:50,
                 from test.m:24:
/usr/include/GNUstep/Foundation/NSException.h:42:2: error: #error The current setting for native-objc-exceptions does not match that of gnustep-base ... please correct this.

I'm afraid I really am a complete newbie at this but I'm keen to learn.

edit - change code tags to quote tags to display

---

