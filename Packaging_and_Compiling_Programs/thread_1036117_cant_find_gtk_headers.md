---
title: "cant find gtk headers"
date: 2009-01-10
forum: Packaging and Compiling Programs
---

### Post by Woody1987 on 2009-01-10
My program cant find the gtk headers. I have #include <gtk/gtk.h> in my program and i compile with 
```
gcc main.c -o main 'pkg-config --cflags --libs gtk-2.0'
```

but i keep getting 

```
gcc: pkg-config --cflags --libs gtk-2.0: No such file or directory
main.c:2:21: error: gtk/gtk.h: No such file or directory
```

i do have build-essential and libgtk2.0-dev installed and /usr/include/gtk-2.0 does exist

This is really annoying as it works fine on my other computer.

---

### Post by WW on 2009-01-10
> **Woody1987 said:**
> My program cant find the gtk headers. I have #include <gtk/gtk.h> in my program and i compile with 
```
gcc main.c -o main 'pkg-config --cflags --libs gtk-2.0'
```

but i keep getting 

```
gcc: pkg-config --cflags --libs gtk-2.0: No such file or directory
main.c:2:21: error: gtk/gtk.h: No such file or directory
```

Change those single quotes (') around the pkg-config command to single *back-quotes* (`).

---

### Post by Woody1987 on 2009-01-10
> Change those single quotes (') around the pkg-config command to single back-quotes (`).

Tried it, no difference. Thanks anyway.

---

### Post by WW on 2009-01-10
> **Woody1987 said:**
> Tried it, no difference. Thanks anyway.

Are you sure?  The error that you showed in your first post is exactly the error that you will get if you put single quotes around the pkg-config command.  The single back-quotes, on the other hand, tell the shell to run the pkg-config command and put its output in place of the command.

Compare the output of the two echo commands in the following:
```

$ cd /tmp
$ echo 'pwd'
pwd
$ echo `pwd`
/tmp
$ 

```
Note that in the second echo command, the shell replaces `pwd` with the output of pwd before running echo.  This is how you are trying to use the pkg-config command in your gcc command.

Hmmm... are you using bash as your shell?  I don't know if the back-quotes work the same in other shells.

---

### Post by Woody1987 on 2009-01-10
```
matthew@Picard:~$ cd /tmp
matthew@Picard:/tmp$ echo 'pwd'
pwd
matthew@Picard:/tmp$ echo `pwd`
/tmp
matthew@Picard:/tmp$ 
```

how do i check if im using bash?

---

### Post by WW on 2009-01-10
> **Woody1987 said:**
> ```
matthew@Picard:~$ cd /tmp
matthew@Picard:/tmp$ echo 'pwd'
pwd
matthew@Picard:/tmp$ echo `pwd`
/tmp
matthew@Picard:/tmp$ 
```

how do i check if im using bash?

The test you just ran makes it moot--whatever you are using (probably bash) handles the back-quotes.

Given that, I don't see how changing the single quotes to back-quotes can make "no difference" in your gcc command.  Can you show the output that you get with this command (run in the same directory where your code is):
```

gcc main.c -o main `pkg-config --cflags --libs gtk-2.0`

```

---

### Post by Woody1987 on 2009-01-10
```
Package gtk-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk-2.0' found

```

I didnt notice it before, there is a difference. Sorry for wasting your time, but how do i fix this?

---

### Post by WW on 2009-01-10
> **Woody1987 said:**
> ```
Package gtk-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk-2.0' found

```

I didnt notice it before, there is a difference. Sorry for wasting your time,

No worries. :)
> **Woody1987 said:**
> 
 but how do i fix this?
The pkg-config name is actually **gtk+-2.0** (go figure).

I found this by looking for the corresponding file with the .pc extension in [the package's list of files](http://packages.ubuntu.com/intrepid/i386/libgtk2.0-dev/filelist) at packages.ubuntu.com.  You could also look in /usr/lib/pkgconfig, or you can see the names of all the packages with the command **pkg-config --list-all**.

---

### Post by Woody1987 on 2009-01-10
im still not entirely sure what to do, could you explain a little further?

---

### Post by WW on 2009-01-10
Try changing gtk-2.0 to gtk+-2.0 in your gcc command:
```

gcc main.c -o main `pkg-config --cflags --libs gtk+-2.0`

```

---

### Post by Woody1987 on 2009-01-10
YAY, thankyou so much

---

