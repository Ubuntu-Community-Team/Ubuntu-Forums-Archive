---
title: "FreeBASIC 0.17 is available!"
date: 2007-05-27
forum: Programming Talk
---

### Post by Antoni on 2007-05-27
The official release or FreeBASIC 0.17 is available since May 14

FreeBASIC is an open source Basic compiler doing fast code for Linux, Windows and DOS32

Get it at
[http://www.freebasic.net/forum/viewtopic.php?t=8256](http://www.freebasic.net/forum/viewtopic.php?t=8256)

What's new? Here are the most important additions.

New -lang command line option
-lang qb is designed to compile QB programs, supports GOSUB, ON ERROR, and returns to the default SINGLE variable type. In return it is limited to 4Mb of memory and will not support OOP. Compatibility with QB will be improved.

-lang fb requires the declaration of all variables, switches to passing parameters byval by default, does not support ON ERROR, GOSUB or type suffixes. In exchange it supports OOP features

-lang deprecated is for compatibility with pre 0.17 FB programs and will ve removed in the future


Enhanced TYPE  working as objects:
-method ,properties, constructors and destructors support 
-private and public members and methods
-operator overloading in types
-new and free operators
-Not supported yet: static members and inheritance

Syntax enhancements:
-FOR [var] AS [type] = 0 
-Multi-level EXIT and CONTINUE (now it's legal to write EXIT DO, DO, DO)

New functions in the runtime lib: 
-FRAC, FileCopy, FileAttr, FileLen, FileDateTime.IsDate
-__FB_ARGC__  __FB_ARGV__ allow to manage the command line parameters in C style 
-Rnd relies now in a high resolution  Mersenne Twister algorithm and  no morein C runtime's rand (which gave different results in differnt platforms). A clone QB's RND algorithm is used  witg -lang qb 
-TYPEOF (works at compile time)

New in the gfxlib:
-VESA linear drive in the DOS version 
-Support for fullscreen in Win32-GDI 
-SCREENEVENT to    mouse, keyboard and window focus changes
-SCREENCONTROL allows to set and retrieve gfx system internal states, for example to set the window position
-GFX_NO_FRAME,GFX_SHAPED_WINDOW,GFX_ALWAYS_ON_TOP for frameless, shaped or always on top graphic windows 
-BLOAD and BSAVE manage palettes in 256 bits modes

-#macro #endmacro preprocessor keywords allowing for multiline macros

-lillo's profiler dropped in favor of gprof (gnu's profiler)

-Built in variables holding the state of most of the command line options for use in conditional compilation

-Headers translated for libraries as GDI+, JavaNative Interface, Cairo

And many more...

Enjoy!

---

### Post by samjh on 2007-05-27
Fantastic news.

I had a lot of fun tinkering with FreeBasic recently.  Reminds me of the fun and carefree days of playing around with GW-BASIC and QBasic.

I read they will implement proper object-oriented programming for 0.18.  That should be a very good development. :)

---

