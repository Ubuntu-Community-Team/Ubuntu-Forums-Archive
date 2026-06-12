---
title: "Stringstream outputs weird"
date: 2013-02-19
forum: Programming Talk
---

### Post by tiamatschosen on 2013-02-19
i was told to make a new thread to post this issue:

my sstream is outputting hex addresses instead of text.

details here towards the bottom:
[http://ubuntuforums.org/showthread.php?t=117531]("http://ubuntuforums.org/showthread.php?t=117531")

---

### Post by Tony Flury on 2013-02-20
One question - it may not be relevant.

Why are you passing your argument as a void *, and then in your code immediately recasting it to a sting *.

Surely it would be better/cleaner/more readable to pass a string * if that is what the argument actually is.

---

### Post by dwhitney67 on 2013-02-20
Perhaps you merely intended to display the contents within the stringstream; therefore instead of:
```

cout << out;

```
you should have:
```

cout << **out.str()** << **endl**;

```
The str() method obtains the string representation of the stringstream; the endl is used to flush the output.  You have several similar statements in the function, so fix each of these.

Unrelated, but you are not returning a value (e.g. 0 or NULL) from your thread function.

---

### Post by dwhitney67 on 2013-02-20
> **Tony Flury said:**
> One question - it may not be relevant.

Why are you passing your argument as a void *, and then in your code immediately recasting it to a sting *.

Surely it would be better/cleaner/more readable to pass a string * if that is what the argument actually is.

My sentiments as well, until I realized it must be a function being called via pthread_create().

---

### Post by tiamatschosen on 2013-02-20
I switched  to ```
cout << out.str() << endl;
```  and i also i also changed the call function to```
 (string *city)
```i still have hex address output.

the way the thread works is it loops until the mutex is unlocked.  if its lock it simply yeilds until its turn comes up again.  the thread_exit() is at the end of the unlocked part.  i did have a standard Cout<<   but on every set of " <<" it switches threads and messes up the printing.

---

### Post by dwhitney67 on 2013-02-20
> **tiamatschosen said:**
> I switched  to ```
cout << out.str() << endl;
```  and i also i also changed the call function to```
 (string *city)
```i still have hex address output.

the way the thread works is it loops until the mutex is unlocked.  if its lock it simply yeilds until its turn comes up again.  the thread_exit() is at the end of the unlocked part.  i did have a standard Cout<<   but on every set of " <<" it switches threads and messes up the printing.

Good... you changed the code... but did you recompile it?

As for cout, it is not thread-safe.  Thus if you have multiple threads that are performing cout, expect that the output will be jumbled together, or that the application will freeze/crash.

P.S.  Did you perhaps change the behaviour of cout to output in hex (base 16)?

---

### Post by tiamatschosen on 2013-02-20
yea im using the sstream because of the how the cout behaves.  i tried doing string concatenation but i got a bout 400 errors per line.  i didnt change anything about how the cout behaves.   

> As for cout, it is not thread-safe.  Thus if you have multiple threads  that are performing cout, expect that the output will be jumbled  together, or that the application will freeze/crash.

is there an easier way to make a single string output so it prints correctly?
and is it safe to assume im not deadlocking if i get the hexcode print out

---

### Post by tiamatschosen on 2013-02-20
strings print out properly now.  forgot i changed the file name when i added the sstream and was still compiling the original code that wasnt working

---

