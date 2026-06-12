---
title: "Cannot find curses.h"
date: 2006-12-19
forum: Programming Talk
---

### Post by typost81 on 2006-12-19
Hi.

I'm new to these forums, so forgive some of my ignorance.  I've been trying to write a program that uses the <curses.h> header file, but when I compile it it says:

error: curses.h: No such file or directory

I've tried this, as was suggested in another thread:

sudo apt-get install libncurses5-dev

And receive the following output:

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libncurses5-dev

I am completely stumped.  Any help would be greatly appreciated.  Thank you.:D 

](*,)

---

### Post by diepruis on 2006-12-19
What does

```

sudo aptitude search curses

```

return?

Which version of Ubuntu are you using?

---

### Post by typost81 on 2006-12-19
Actually I just had to run the following commands first:

```
sudo apt-get update
sudo apt-get upgrade          

```  

To before I could install the packages.  Now I have a whole new problem.  I'm using 6.06 dapper.

---

### Post by tribaal on 2006-12-19
Try installing the **libncurses-dev** or **ncurses-dev** packages.
Usually header files are contained in the *-dev packages...

Hope this helps.

- trib'

---

### Post by typost81 on 2006-12-19
Problem solved.  Thanks

---

