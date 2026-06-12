---
title: "fprintf(stderr, ...) prints on top of the fprintf(stdout, ...)"
date: 2011-01-19
forum: Programming Talk
---

### Post by cybo on 2011-01-19
i'm studying for an interview and in preparation for it decided work on some puzzles in c:

here is the one i bumped into:

The following program doesn't "seem" to print "hello-out". (Try executing it) 
```
  #include <stdio.h>
  #include <unistd.h>
  int main()
  {
          while(1)
          {
                  fprintf(stdout,"hello-out");
                  fprintf(stderr,"hello-err");
                  sleep(1);
          }
          return 0;
  }

```What could be the reason?

the result i get after the compilation looks like this:
> hello-errhello-errhello-errhello-errhello-errhello-errhello-errhello-errhello-errhello-errhello-err.......

however if modify the code to the following: 
```
          while(1)
          {
                  fprintf(stdout,"hello-out**_\n_**");
                  fprintf(stderr,"hello-err**_\n_**");
                  sleep(1);
          }

```

everything works. so it seems to me that i don't completely understand how the output works and it seems it has something to do with the '\n' character. i would appreciate any help and explanations. 
thanks.

---

### Post by Arndt on 2011-01-20
> **cybo said:**
> i'm studying for an interview and in preparation for it decided work on some puzzles in c:

here is the one i bumped into:

The following program doesn't "seem" to print "hello-out". (Try executing it) 
```
  #include <stdio.h>
  #include <unistd.h>
  int main()
  {
          while(1)
          {
                  fprintf(stdout,"hello-out");
                  fprintf(stderr,"hello-err");
                  sleep(1);
          }
          return 0;
  }

```What could be the reason?

the result i get after the compilation looks like this:


however if modify the code to the following: 
```
          while(1)
          {
                  fprintf(stdout,"hello-out**_\n_**");
                  fprintf(stderr,"hello-err**_\n_**");
                  sleep(1);
          }

```

everything works. so it seems to me that i don't completely understand how the output works and it seems it has something to do with the '\n' character. i would appreciate any help and explanations. 
thanks.

stderr is usually unbuffered, so every small piece of text sent to it gets printed immediately. stdout is usually buffered, so that output to it is collected in a large block which is only output when filled, or when a '\n' appears, because this is much faster.

If there is material in the buffer and the program exits, I think it is not flushed automatically.

You can use fflush to force the output, and you can change the buffering, using setbuf.

The above is a simplification, but all you need to know is in the manual page for 'setbuf'.

---

### Post by gmargo on 2011-01-20
To expand on Arndt's explanation a bit: 

What's going on is that things printed to **stderr** come out immediately - they are completely unbuffered.

Things printed to **stdout** are appended to a character array buffer, which is BUFSIZ in length.  When the output buffer fills, it is flushed out, and then starts filling again.

When a program exits normally, the output is flushed during program cleanup - no output is lost.  However, since you put a "sleep(1)" in your program, you must have hit a Control-C to stop it, which sends an interrupt signal to the program, causing the program to exit immediately without flushing the output buffer.  If you had waited long enough, you would eventually see the "hello-out" strings come out.  "hello-out" is 9 characters, and BUFSIZ is 8192 characters, so you would have to wait 8192/9 = 910 seconds, or over 15 minutes!

Now try this modified program and compare:
```

#include <stdio.h>
#include <unistd.h>
int main()
{
        int i;
        for (i=0; i < BUFSIZ; i++)
        {
                fprintf(stdout,"hello-out\n");
                fprintf(stderr,"hello-err\n");
        }
        return 0;
}

```Now you'll see a whole bunch of "hello-err" followed by a whole bunch of "hello-out" when the buffer flushes.  There's an interesting transition after the first "hello-out" block:
```

hello-out
hello-hello-err
hello-err

```The "out\n" part of the "hello-out" was not flushed - it's now sitting at the start of the output buffer.

---

### Post by cybo on 2011-01-20
@gmargo,

thanks for clarifying it. i think i get it now.

---

