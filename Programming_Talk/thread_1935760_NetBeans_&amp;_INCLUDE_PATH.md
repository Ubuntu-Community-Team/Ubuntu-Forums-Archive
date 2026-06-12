---
title: "NetBeans &amp; INCLUDE_PATH"
date: 2012-03-04
forum: Programming Talk
---

### Post by areeda on 2012-03-04
I'm starting my first real netBeans C++ project and I'm running into very basic include files not being found like stddef.h or <string> having includes like stdarg.h not found.

While I can track these things down and add places like /usr/include/linux (that one is reasonable) and /usr/include/c++/4.5.2/tr1 and others it seems that there has to be a better way.

So what are people putting in their .profile is there a clean and easy way to deal with this.

thanks
Joe

---

### Post by Zugzwang on 2012-03-05
Have you installed the "build-essential" package? For standard headers, you shouldn't need to change any setting, so check that you have installed everything you need.

Are you sure that it's really header files like stddef.h or <string> that cannot be found? The example directory names you provide indicate otherwise.

The include directory "/usr/include/linux" is only necessary if you compile kernel-level drivers

You shall never need to include "/usr/include/c++/4.5.2/tr1" as directory, as rather, the "tr1" is part of the filename you refer to, e.g.:
```

#include <tr1/unordered_set>

```

---

### Post by areeda on 2012-03-05
Thank you Z
I think you're right, that there is something I've not installed (or set up properly)

sudo apt-get install build-essential

says already installed

As far as am I sure it's really stddef.h, well I get compiler errors like size_t is not defined and the IDE marks files like that as not found.  It has to be something basic and easy.

I'll keep poking around.  I think it should work the way you said but I don't see what I'm doing wrong.

Joe

---

### Post by areeda on 2012-03-06
I have a bit more information.  I'm just starting this project so I installed Eclipse and got it to compile and run.

I then copied the list of include directory and still get the same errors.

Next I guess I'll try reinstaling NetBeans.

---

### Post by Zugzwang on 2012-03-06
Perhaps you can try copying and pasting your error messages here. Then we can check if the header files that are being referred to are not included in some package that has to be installed separately. Make sure to start from the very first error message.

Another very importing thing to try is always to compile&link your program from the command line (or terminal, if you prefer this term) and check if the same problem occurs. This will tell you if it is really a problem with your IDE or your compiler installation.

---

### Post by areeda on 2012-03-06
Thanks.  I'm still confused but making progress.

I reinstalled NetBeans, deleted the NB project, made a new one and copied the sources from the Eclipse project and now I can at least compile and run.

I'm still having some issues with the debugger.  I can set breakpoints and step over but can't step into???

It may have something to do with Qt.  I decided to work on the lower level functions, put them into a library and then do the GUI.

I appreciate your help.

Joe

---

