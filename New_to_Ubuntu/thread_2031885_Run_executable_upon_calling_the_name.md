---
title: "Run executable upon calling the name"
date: 2012-07-22
forum: New to Ubuntu
---

### Post by KylePhys on 2012-07-22
I am going probably to ask a trivial question. New to Linux, used windows.

I got a small program in the form of executable (not windows exe, linux binary) and i can run it by ./'name',  I just would like to know how i can "install" it so that by calling it in command line (typing the name of the program) it would run. E.g. I installed mathematica 8 and by calling "mathematica" in the command line it opens.

Thanks in advance for answers.:)

---

### Post by papibe on 2012-07-22
Hi KylePhys.

The easiest way is to create a personal ~/bin and copy the binary there (it works with scripts too).

When that directory exists, it is added to the system path on startup.

I hope that helps. Let us know how it goes.
Regards.

---

### Post by KylePhys on 2012-07-30
Thanks, I'll give a try. )

---

### Post by hakermania on 2012-07-30
Just to add that papaibe's solution will not work for other users in your machine. If you want every user to be able to run the program by simply calling its name, you should place it under /usr/bin/, something that requires super user privileges:
```

sudo cp executable /usr/bin/

```

---

### Post by Lars Noodén on 2012-07-30
Putting the script or program in ~/bin/ will be the easiest, but if you just created the directory, you'll have to log out and then log back in again for [font=Courier New].profile[/font] to find it.

---

