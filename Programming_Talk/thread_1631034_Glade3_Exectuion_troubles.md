---
title: "Glade3 Exectuion troubles"
date: 2010-11-26
forum: Programming Talk
---

### Post by HeZ on 2010-11-26
Hi all
I have found a glade tutorial on the net which i am working through 
([http://tadeboro.blogspot.com/2009/09/glade3-tutorial-2-constructing.html](http://tadeboro.blogspot.com/2009/09/glade3-tutorial-2-constructing.html))
I have completed that section of the tutorial and i am just having a small problem at this point. I can compile without any errors but i do not have permission to run it somehow.
I am running Ubuntu 10.10. I have tried the following:

I have tried compiling the .c file as:
```
gcc -o tut tut.c $(pkg-config --cflags --libs gtk+-2.0 gmodule-2.0)
```
and
```
sudo gcc -o tut tut.c $(pkg-config --cflags --libs gtk+-2.0 gmodule-2.0)
```
Both work exactly the same (as would be expected i think)

Now when i try to exectue:
```
./tut gives -- bash: ./tut permission denied
```
```
sudo ./tut gives -- bash: ./tut command not found
```
Exectuing from the file manager gives an error 
> could not display There is no application installed for executable files

I right click on the file and properties>permissions and try to tick the "allow executing.." box but it does not let me.
I have tried 
```
sudo chmod a+x tut
```
No effect

Im a bit stuck here :/
It is a fresh Ubuntu installation i have use update manager to get all the latest updates.
libgtk2.0-dev is installed:
```
pkg-config --modversion gtk+-2.0 glib-2.0 pango cairo
2.22.0
2.26.0
1.28.1
1.10.0
```

but is there something else i have to do to execute files? Some kind of built in security that i haven't found yet?
Please help
Thanks

---

### Post by HeZ on 2010-11-26
problem solved thanks
Turns out i was trying to execute from a different partition. 
How can i make it so i can execute from that partition?

---

### Post by Arndt on 2010-11-26
> **HeZ said:**
> problem solved thanks
Turns out i was trying to execute from a different partition. 
How can i make it so i can execute from that partition?

I'm not sure what you mean by "executing from a different partition", nor how it affects your problem.

But don't do sudo so much. It's for system administrative tasks, not building and executing user programs.

---

