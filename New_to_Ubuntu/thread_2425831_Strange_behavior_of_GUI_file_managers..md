---
title: "Strange behavior of GUI file managers."
date: 2019-08-31
forum: New to Ubuntu
---

### Post by hk42 on 2019-08-31
For exemple using nemo in the /usr/bin folder lots of files are marked "unknown" and refuse to be executed.
In a terminal no problem.
In Thunar some are marked as shared library or links.

---

### Post by TheFu on 2019-08-31
What are the permissions for the files?

---

### Post by hk42 on 2019-08-31
In the /usr/bin directory mostly rwx,r_x,r_x
But if for a file I ask "properties"  it takes quite a long time to say that they are not executable.
I tried the 3 users I created they all suffer the problem.
Midnight Commander is not affected.
As I have also XFCE as window manager I have yet to try it.

---

### Post by TheFu on 2019-08-31
In /usr/bin/ are mostly CLI programs, so attempting to run them without the required inputs doesn't make sense.  If you seek a prompt to help fill out the inputs, sorry, no GUI file manager is going to do that.

The required inputs must be provided with the program invocation.

If you try to run the 'cp' program from a file manager, it needs at least 2 inputs.  The source and the target.  If you run nemo from a terminal, each of the programs you try to run through it will output their error or default help when the required options aren't provided.

I used caja to try and run c++. Got this error in the terminal where I started caja.
```
c++: fatal error: no input files
```

Similar output for other programs.

A few of the GUI programs did launch, but not all. I've changed machines and the "recent" directories don't exist on the newer machine.

I don't have a better answer. Sorry.  If you are interested in each of the programs in /usr/bin/, then almost all of them will have a manpage on your machine.  The first paragraph is usually enough, but most commands have some interesting, more advanced, capabilities, than most people know about. Those are documented farther down in the manpage.

There's also many books that group the different sorts of programs into groups and cover each well enough.
[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) is a reasonably good book, sold in book stores, but also with a free, no-hassle, download. I've used it to suppliment my Linux classes.

---

### Post by mc4man on 2019-09-01
Not strange behaviour at all.
These days the majority  of executable binaries are compiled with either -fPIC and/or -fPIE,  meaning position independent code and position independent executable.
So the file manager will see them as type: unknown :  application/x-sharedlib and not allow direct executing.
Such binaries are more secure than if compiled without a position  independent parameter

you can clearly see as most don't get the executable icon in your filemanager

---

### Post by hk42 on 2019-09-01
Thanks mc4man for this answer it correspond exactly to what I experienced.
This plus the fact that symbolic links display the size of the target will encourage me to stick to my trusted Midnight Commander.
It seems that the nice file hierarchy that attracted me to Linux 20 years ago is a thing of the past.

---

