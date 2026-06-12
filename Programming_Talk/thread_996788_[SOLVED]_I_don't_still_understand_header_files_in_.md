---
title: "[SOLVED] I don't still understand header files in C"
date: 2008-11-29
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-11-29
I have graphics.h and graphics.c. And main.c, which includes graphics.h.

But do I have to compile graphics.c/.h to get it working? main.c doesn't find the header functions. 

It keeps saying a thousand times "undefined reference to ..." when trying to compile main.c.

---

### Post by WitchCraft on 2008-11-29
> **crazyfuturamanoob said:**
> I have graphics.h and graphics.c. And main.c, which includes graphics.h.

But do I have to compile graphics.c/.h to get it working? main.c doesn't find the header functions. 

It keeps saying a thousand times "undefined reference to ..." when trying to compile main.c.

If you have your two files, the gcc directive is:

```

gcc -Wall graphics.c main.c -o YOUR_PROGRAMS_NAME

```

:lolflag:

Main finds the function's declaration (graphics.h), but not it's implementation (graphics.c).
Thus when linking --> undefined reference
which is true, because you didn't reference the implementation if you only compile main.c...

---

### Post by davidbilla on 2008-11-29
As long as either main.c or graphics.h doesn't use graphics.c you don't have to touch graphics.c.

If graphics.h is not in the regular path where your other header files are, then use

$ gcc -I <path-to-graphics.h> main.c

Hey, you seem to be a 'C guy'! Am I not getting your problemor don't I know enough (very likely!)?

---

### Post by WitchCraft on 2008-11-29
> **davidbilla said:**
> As long as either main.c or graphics.h doesn't use graphics.c you don't have to touch graphics.c.

If graphics.h is not in the regular path where your other header files are, then use

$ gcc -I <path-to-graphics.h> main.c

Hey, you seem to be a 'C guy'! Am I not getting your problemor don't I know enough (very likely!)?

What's the point in creating a file you don't use? :confused:

---

### Post by davidbilla on 2008-11-29
> **WitchCraft said:**
> What's the point in creating a file you don't use? :confused:

!!! You have to compile graphics.c if main.c uses it. But what I meant was you don't have to compile graphics.c to run main.c if graphics.c is the one that uses graphics.h and not the other way around and if grahpics.c had nothing to do with main.c!

:confused:

---

### Post by dwhitney67 on 2008-11-29
> **davidbilla said:**
> !!! You have to compile graphics.c if main.c uses it. But what I meant was you don't have to compile graphics.c to run main.c if graphics.c is the one that uses graphics.h and not the other way around and if grahpics.c had nothing to do with main.c!

:confused:

graphics.h should *never* use graphics.c

If main.c does not use graphics.c, then there is no point including graphic.c into the project.

The advice given by WitchCraft in his first post of this thread is correct.  I provided the same advice to the OP the other day, but apparently he does not like to read or just doesn't get/accept it.

---

### Post by nvteighen on 2008-11-29
> **crazyfuturamanoob said:**
> I have graphics.h and graphics.c. And main.c, which includes graphics.h.

But do I have to compile graphics.c/.h to get it working? main.c doesn't find the header functions. 

It keeps saying a thousand times "undefined reference to ..." when trying to compile main.c.

That's because #include <...> searches in the system default directories + those specified using -I when compiling. Just use #include "..." for your headers instead.

---

### Post by davidbilla on 2008-11-29
> **dwhitney67 said:**
> graphics.h should *never* use graphics.c

Some people have the habit of naming whatever file they 'include', with the extension '.h'. That's why I brought up that point. Thanks for that!

> 
If main.c does not use graphics.c, then there is no point including graphic.c into the project.

Oh, but I thought it was the thread starter who had replied to my previous post. Sorry for that! Now I see Witchcraft's edit of the previous post. Thanks.

---

### Post by dwhitney67 on 2008-11-29
> **nvteighen said:**
> That's because #include <...> searches in the system default directories + those specified using -I when compiling. Just use #include "..." for your headers instead.

You are correct with your statement above, however note that if GCC is unable to find a header file, a compiler error is generated, not a link error.

The OP wrote about "undefined references", which implies he successfully compiled his project, but was unable to link.

---

### Post by crazyfuturamanoob on 2008-11-29
When compiling with **gcc main.c graphics.c -o program** or similar, it works :)

So why should I use **-Igraphics.h** there?

---

### Post by dwhitney67 on 2008-11-29
> **crazyfuturamanoob said:**
> When compiling with **gcc main.c graphics.c -o program** or similar, it works :)

So why should I use **-Igraphics.h** there?
Who told you to use the -l option?

graphics.h is *not* a library!!!  It is a header file, that includes function prototypes (definitions).

---

### Post by crazyfuturamanoob on 2008-11-29
> **dwhitney67 said:**
> Who told you to use the -l option?

graphics.h is *not* a library!!!  It is a header file, that includes function prototypes (definitions).

I just read this from some post:
```
$ gcc -I <path-to-graphics.h> main.c
```

Congrats you just got your 2000th post :D lol

---

### Post by dwhitney67 on 2008-11-29
The -I (dash-eye) option is useful when you need to specify the paths to header files you wish to include.  GCC knows about a few standard places to look (e.g. the current working directory, /usr/include).

When including header files from the current working directory, you can use the double-quotes to surround the header file, although you can use the <> brackets if you specify -I./ (which tells GCC to examine the current directory).

It is good practice to include all necessary header files that are necessary to make a file compilable.  So if you create a header file that requires use of SDL structs, then you should include the appropriate SDL header files in your header file.

It is also good practice to also include locally defined header files *before* you include those provided by 3rd-party packages or the OS.

P.S.  Now I have 2001 posts!  :-)

---

### Post by WitchCraft on 2008-11-29
> **crazyfuturamanoob said:**
> When compiling with **gcc main.c graphics.c -o program** or similar, it works :)

So why should I use **-Igraphics.h** there?

Simple, you shouldn't.

You only need to -Idirectory if you link against a library, and need to include the libraries header files directory, for example when you link against boost or wxwidgets. But you don't. And -Igraphics.h is plain unnecessary/wrong.

The poster before was wrongly assuming graphics.c is a library. It is not, it's only another source file.

But glad to hear your problem is solved. Mark the thread as solved.

---

### Post by WitchCraft on 2008-11-29
> **dwhitney67 said:**
> 
P.S.  Now I have 2001 posts!  :-)


:lolflag:

AND: Most of them are useful! Keep it up!

---

### Post by davidbilla on 2008-11-29
> The poster before was wrongly assuming graphics.c is a library. It is not, it's only another source file.

Yes, I was. Sorry about that. Actually what I had thought was that graphics.h was one of *his*-the user's-personal header files. But I didn't suggest '-I graphics.h'. I'd said ```
'-I </path-to-header-file/>'
```

---

