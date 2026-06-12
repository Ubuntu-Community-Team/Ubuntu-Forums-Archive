---
title: "moving files..."
date: 2008-10-03
forum: Programming Talk
---

### Post by StOoZ on 2008-10-03
I have a program which downloads files to my main program's directory :
> /home/guy/Programming Projects/ImgGrabber
I would like to move all of them , using C\C++ (not shell's mv , etc...) to :
> /home/nathan/Programming Projects/ImgGrabber/tmp

any idea how to do this?

---

### Post by mindoms on 2008-10-03
I know, you said no bash, but maybe you didnt know this:
using system() [1] you can run bash-commands like cp from within c++.

```

#include<iostream>
...
system("cp /path/* /another/path")
...

```
could do the trick



[1] [http://www.cppreference.com/wiki/c/other/system](http://www.cppreference.com/wiki/c/other/system)

---

### Post by dribeas on 2008-10-03
> **StOoZ said:**
> I have a program which downloads files to my main program's directory :

I would like to move all of them , using C\C++ (not shell's mv , etc...) to :


any idea how to do this?

Just a hint: [rename]("http://linux.die.net/man/2/rename"). You will need to get the directory contents so that you know the names of the files (read opendir/readdir manpages).

---

