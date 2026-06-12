---
title: "Ubuntu hello.c:1:20: error:  stdio.h: No such file or directory"
date: 2008-06-11
forum: Programming Talk
---

### Post by Black Mage on 2008-06-11
I am trying to compile a simple C program.

I've done this so far:

```

sudo apt-get install build essentail

:~/Desktop/cprogram$ sudo updatedb
:~/Desktop/cprogram$ locate stdio.h
/usr/include/stdio.h
/usr/include/bits/stdio.h
/usr/include/c++/4.2/tr1/stdio.h
/usr/lib/perl/5.8.8/CORE/nostdio.h

```

And when I try to run a simple hello world c program, it says STDIO.H not found.

Can anyone help?

---

### Post by KingTermite on 2008-06-11
What's your code look like?
How are you compiling it?

---

### Post by WW on 2008-06-11
[This thread](http://ubuntuforums.org/showthread.php?t=689635) gives an example of a simple "Hello world" program, and the commands to compile it. See if that example works for you; it may help you find what is wrong with your program or the commands that you are using.

---

### Post by Npl on 2008-06-11
you have a c-library and its development files installed?
try **sudo apt-get install libc6-dev**

---

### Post by dfreer on 2008-06-11
> **Black Mage said:**
> I am trying to compile a simple C program.

I've done this so far:

```

sudo apt-get install build essentail

:~/Desktop/cprogram$ sudo updatedb
:~/Desktop/cprogram$ locate stdio.h
/usr/include/stdio.h
/usr/include/bits/stdio.h
/usr/include/c++/4.2/tr1/stdio.h
/usr/lib/perl/5.8.8/CORE/nostdio.h

```

And when I try to run a simple hello world c program, it says STDIO.H not found.

Can anyone help?

Maybe you just misspelled it in your quote, but the program is called build-essential:
```
sudo apt-get install build-essential
```

---

