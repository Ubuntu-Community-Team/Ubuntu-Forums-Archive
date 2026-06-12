---
title: "C: capturing stdout"
date: 2010-01-27
forum: Programming Talk
---

### Post by MadCow108 on 2010-01-27
I want to write a testcase testing the output of a function printing to stderr.
for that I somehow need to get the stderr from within the same process.
I also want to avoid having to execute the testcase from a wrapperscript.

I found you can reopen stderr to a filestream with freopen but it seems impossible to reattach the output to stderr again in a portable way.
Unfortunately I would like to do this too.

is there some way I'm overlooking to capture stderr and resetting it in C, without changing the outputting functions code or using a wrapper program around the testcase?

pseudo code I'm looking for:
```

to_test():
  print "output"

test_function():
  file = freopen("file", stderr)
  to_test();
  assert(compare_with_golden_file(file, golden))
  reset_stderr

```

---

### Post by Can+~ on 2010-01-27
Wait? In C? Why are you using python in the example?

EDIT: Oh... pseudocode, sorry about that.

---

### Post by dwhitney67 on 2010-01-27
If I read your post correctly, you want to direct stderr messages to a file, for a temporary amount of time, and then restore everything to 'normal' so that future stderr-directed messages are displayed on the console, as they normally would.

Well, here's some 'cheesy' code that does this, and it should be portable:
```

#include <stdio.h>

int main(void)
{
   FILE* errFile = fopen("myErrors", "w+");
   FILE* save_stderr = stderr;

   stderr = errFile;

   // this will go to the file
   fprintf(stderr, "This is my first error message.\n");

   fclose(errFile);

   stderr = save_stderr;

   // this will go to the terminal
   fprintf(stderr, "This is my second error message.\n");

   return 0;
}

```

---

### Post by MadCow108 on 2010-01-28
are you sure this is portable?
according this not:
[http://c-faq.com/stdio/undofreopen.html](http://c-faq.com/stdio/undofreopen.html)
and it says it is impossible in the way in want it :(

---

### Post by kzmd on 2010-01-28
Take a look into dup() and dup2(). They will allow you to duplicate a file descriptor. From here you should be able to redirect the output of stderr to somewhere else for testing.

Edit: Apologies, I didn't realise the C-Faq you linked explicitly mentioned dup and dup2.

---

### Post by dwhitney67 on 2010-01-28
> **MadCow108 said:**
> are you sure this is portable?
according this not:
[http://c-faq.com/stdio/undofreopen.html](http://c-faq.com/stdio/undofreopen.html)
and it says it is impossible in the way in want it :(

Works under Linux and Mac OSX.  I'm not sure if I care if it works anywhere else.  As I have mentioned in the past, I hold Windoze in low regard; it is a great multi-media center, but useless for anything else.

---

