---
title: "C89 with Geany"
date: 2012-07-10
forum: Programming Talk
---

### Post by scorpious on 2012-07-10
I wasn't sure if I should put this post here or in the absolute beginner forum.

Anyway, I'm taking a uni paper learning C89 and using geany as the IDE. I downloaded geany...

```

sudo apt-get install geany
```and now I don't know how to continue. 
I need to download C89 then connect it up with geany somehow.

Any help?

cheers

---

### Post by dwhitney67 on 2012-07-10
> **scorpious said:**
>  
I need to download C89 then connect it up with geany somehow.

Any help?


Try
```

sudo apt-get install build-essential

```
After completing the step above, your system will have the GCC tools, of which 'gcc' is used for compiling C programs.  The default version of the gcc compiler supports C89.  You can switch to later versions of C (e.g. C99) using the -std=c99 or -std=gnu99 compiler options.

As for Geany, I don't anything about it.  If you are learning to program for the first time, IMHO, you should avoid using an IDE.

---

### Post by Bachstelze on 2012-07-10
Also, the default gcc settings are to compile gnu89, which is basically C89 with some GNU extensions. If you want a more pure C89, compile with -ansi.

And I agree with dwhitney67 about not using an IDE if you're just beginning. Or even at all actually, an IDE is not really needed in C IMO. It's not Java.

---

### Post by scorpious on 2012-07-10
Thanks for the replies. 

Turns out all I needed to do was save the files as .c and geany did the rest.

I'll stick with using geany for now as that's what we're being lectured with. But I'll probably stop using it after the course is finished.

---

