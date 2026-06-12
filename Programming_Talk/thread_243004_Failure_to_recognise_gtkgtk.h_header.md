---
title: "Failure to recognise gtk/gtk.h header"
date: 2006-08-24
forum: Programming Talk
---

### Post by theDentist on 2006-08-24
Can anyone help me.  When I write a simple program in C that just displays a gnome window (Just testing to see if my system works), and then compile it using gcc, I get an error message saying that gtk/gtk.h doesn't exist.  I successfully use Glade so I know gtk is installed correctly, so why cannot the gcc compiler recognise the gtk/gtk.h header when I just code the app with the editor.

---

### Post by theDentist on 2006-08-24
Oops! I seem to have answered my own question with a bit of research in the forums.  I've solved it, I typed
   gcc `pkg-config --cflags --libs gtk+-2.0` -o foo foo.c
where foo is my executable name and foo.c is my source file.   :-D

---

### Post by donyfrosman on 2008-01-06
i have same problem with you but i try 
```
gcc `pkg-config --cflags --libs gtk+-2.0` -o foo foo.c

``` and error comment comes  
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable

so what must i do to solve that in detail?

---

### Post by Kadrus on 2008-01-06
> **donyfrosman said:**
> i have same problem with you but i try 
```
gcc `pkg-config --cflags --libs gtk+-2.0` -o foo foo.c

``` and error comment comes  
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable

so what must i do to solve that in detail?

If I am not mistaken..it's the libgtk2.0-dev package
so try:
```

sudo apt-get install libgtk2.0-dev
```
I think that's the package..I forgot though..

---

### Post by daniel6 on 2008-02-09
Thank you, thank you, thank you! This is the silver bullet that has delivered me from dependancy hell. I am forever grateful!

Dan

---

### Post by KB1LQC on 2008-07-02
> sudo apt-get install libgtk2.0-dev

I did that and I still get errors when I use:

#include <gtk/gtk.h>

I searched for the files on my hard drive but cannot find anything "gtk.h"  Any other suggestions?

---

### Post by WW on 2008-07-02
> **KB1LQC said:**
> I did that and I still get errors when I use:

#include <gtk/gtk.h>

I searched for the files on my hard drive but cannot find anything "gtk.h"  Any other suggestions?

If the command **sudo apt-get install libgtk2.0-dev** was successful, you should have the gtk library installed.

Does the directory **/usr/include/gtk-2.0/** exist?

Show the output of this command:
```

pkg-config --cflags --libs gtk+-2.0

```

---

### Post by KB1LQC on 2008-07-02
> -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1  -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lpango-1.0 -lcairo -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0 

is the output of the command

and yes the directory /usr/include/gtk-2.0 does exist

---

### Post by WW on 2008-07-02
> **KB1LQC said:**
> I did that and I still get errors when I use:

#include <gtk/gtk.h>

What is the command you are using to compile your code?

Are you using a command like one of those shown above, or also shown in the [GTK+ 2.0 Tutorial](http://library.gnome.org/devel/gtk-tutorial/stable/)?

What errors are you getting?

---

### Post by KB1LQC on 2008-07-02
cc -o foo foo.c

---

### Post by WW on 2008-07-02
When you read the tutorial, you'll find this example in the section "Compiling Hello World":
```

gcc -Wall -g helloworld.c -o helloworld `pkg-config --cflags gtk+-2.0` `pkg-config --libs gtk+-2.0`

```
which can be simplified a bit to:
```

gcc -Wall -g helloworld.c -o helloworld `pkg-config --cflags --libs gtk+-2.0`

```
Chnage "helloworld" to "foo" and try it with your program.

---

### Post by days_of_ruin on 2008-07-02
> **KB1LQC said:**
> cc -o foo foo.c

Just do what the above posters are doing.

---

### Post by sohaikia1 on 2008-08-14
I think I know what you have been doing wrong. You mistake `(left single quotation) with '(right single quotation). So you should compile using the following command:

   gcc test.c -o test `pkg-config --cflags --libs gtk+-2.0`

instead of using

   gcc simple.c -o simple 'pkg-config --cflags --libs gtk+-2.0'

---

### Post by abiusx on 2011-05-25
The easiest and most elegant way would be to 


[LIST=1]
[*]Right-click project name in Project Explorer, select properties (Alt+Enter)
[*]Navigate to "C/C++ Build" -> "Settings"
[*]Select Miscellaneous under Compiler and Linker (there are C compiler and C++ compiler, select both preferably)
[*]Add **`pkg-config --cflags --libs gtk+-2.0` **with a space character before it to the end of the field.
[/LIST]

Now you should be able to build if you have appropriate libraries and headers.
Keep in mind that ` is backtick and is different from ' which is quote. Backtick means run this command in terminal and replace its output here, And that command lists Include and Lib folders for GTK.

---

