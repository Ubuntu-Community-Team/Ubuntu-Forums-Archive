---
title: "Reading file from end in C."
date: 2010-08-05
forum: Programming Talk
---

### Post by Abhijit Bose on 2010-08-05
Functionality is like "tail".

I want to read the last "n" lines of a huge file(around a GB) without reading from the very beginning.

Which C **standard** file access function will help?

is it fseek() or fsetpos()?

a simple example will be appreciated. eg - display last 5 lines of file "dictionary"

---

### Post by Arndt on 2010-08-05
> **Abhijit Bose said:**
> Functionality is like "tail".

I want to read the last "n" lines of a huge file(around a GB) without reading from the very beginning.

Which C **standard** file access function will help?

is it fseek() or fsetpos()?

a simple example will be appreciated. eg - display last 5 lines of file "dictionary"

fsetpos takes something you got earlier with fgetpos, so you cannot use that one alone. fseek seems good.

Is this homework?

---

### Post by Simian Man on 2010-08-05
Hmm, the trouble with fseek is that it operates on bytes and not on lines.  How can you possibly know which byte the fifth from the last line begins on?

I'm curious how tail actually does this.

---

### Post by Abhijit Bose on 2010-08-05
Nope I was solving questions for an upcoming technical interview. I stumbled upon this and couldn't figure out.
I looked up ritchie, but there definition of fseek() was vague. Could you give me a clean example for using fseek()?

---

### Post by Abhijit Bose on 2010-08-05
no i can put the bytes in a char array and check for '\n'. but how does fseek work...
lets say i want to get the last 10Mb of the file... how to set the pointer to 10Mb before the end?
and how to know the file size, most importantly, using C? (so that i dun do the above for a file of size less than 10Mb)

---

### Post by dwhitney67 on 2010-08-05
You can determine the file size using the stat() library function.

Surely you don't want to display the last 10Mb, do you?  Perhaps the last 10 percent of the file.  After all, the file may be smaller than 10Mb... perhaps only a few hundred bytes, maybe less.

fseek() will put you in the ballpark of that range.  Don't worry about searching for newlines... just display the data.  'tail' works on non-ASCII files too.

---

