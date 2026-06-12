---
title: "Run a Program"
date: 2010-03-31
forum: Packaging and Compiling Programs
---

### Post by KdotJ on 2010-03-31
Hey all,

Say for example that I have a program named "testprog" and its written and compiled in java. It there a way that I can write a script and add to my /sbin directory that will allow me to run the "testprog" program simply by opening a terminal and typing "testprog"?

Could I write a file that is like a shell script containing:
```
java /home/kris/testprog
```

?? I'm guessing this is not the answer at all. Any help is greatly appreciated

---

### Post by deer dance on 2010-04-01
You're not even close.

```
#!/bin/bash

java /home/kris/testprog

```

That's much closer.

---

### Post by Compyx on 2010-04-01
Don't put stuff in the /sbin directory, that's reserved for binaries and scripts run by root. My preferred way is to create a bin directory in your home directory: /home/kris/bin and make sure it's in your PATH. Or, if you want other users to use your program as well, put it in /usr/local/bin.

One way to add your personal bin directory to the PATH is by putting the next line in ~/.bashrc:
```

export PATH=$PATH:/home/kris/bin

```

---

### Post by KdotJ on 2010-04-01
Thanks for the replies guys,

> **deer dance said:**
> You're not even close.

```
#!/bin/bash

java /home/kris/testprog

```

That's much closer.

I noticed that line in the files already in the directory as I was snooping around. But I just thought that is was a comment. What language are they in?
 
(compyx, thanks for the tip, I shall set that up)

---

### Post by deer dance on 2010-04-01
It's in bash.

And the first time that specific line of code is introduced in a program, it tells the program to use the bash shell

---

