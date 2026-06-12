---
title: "GTK and Eclipse?"
date: 2008-05-26
forum: Programming Talk
---

### Post by Nuvious on 2008-05-26
I've set up the eclipse cdt and it successfully compiled the hello world program.  I'm not trying to run this simple GTK program:

```
/*
 *File name: window.c
 */

#include <gtk/gtk.h>
#include <glib.h>

int main (int argc, char *argv[])
{
  /*-- Declare the GTK Widgets used in the program --*/
  GtkWidget *window;

  /*--  Initialize GTK --*/
  gtk_init (&argc, &argv);

  /*-- Create the new window --*/
  window = gtk_window_new(GTK_WINDOW_TOPLEVEL);

  /*-- Display the window --*/
  gtk_widget_show(window);

  /*-- Start the GTK event loop --*/
  gtk_main();

  /*-- Return 0 if exit is successful --*/
  return 0;
}

```

I get the No such file or directory errors on gtk/gtk.h and glib.h includes and I'm sure it's because I don't have my Project build setting set up right.  I've tried appending several extended commands to the g++ build string with no success.  Anyone know how to set up the Eclipse CDT to be able to compile GTK programs?  Thanks in advanced for any serious replies!

David Cheeseman

---

### Post by xlinuks on 2008-05-26
I managed to configure NetBeans to compile GTK apps by simply guessing how to do that, doing the same with Eclipse - I failed, even after googling a bit. So I decided to stick with NetBeans and I'm very happy, if no one answers your question I suggest trying what I did.

---

### Post by mike_g on 2008-05-26
Are you sure that you have installed the GTK development libraries? Not having installed it would produce an error like that.

---

### Post by Nuvious on 2008-05-26
> **mike_g said:**
> Are you sure that you have installed the GTK development libraries? Not having installed it would produce an error like that.

I had not installed it (thought it was pre-installed with ubuntu).  However, now I have the libraries included via the Directories part of the Project Build Configurations in Project Properties but am now getting this error:

```
Severity and Description	Path	Resource	Location	Creation Time	Id
/usr/include/glib-2.0/glib/garray.h error: ‘array’ was not declared in this scope		Test	line 94	1211840857378	1133
```

And my includes are set up as follows:

```

/usr/include/gtk-2.0
/usr/include/glib-2.0/glib
/usr/include/c++/4.2.3
/usr/include/glib-2.0

```

I figured 'array' should've been covered by the second include.  Is this the correct way to include items?  Should I be using a different method?  If not, why doesn't it recognize 'array' (which I believe is included via glibconfig.h).

Thanks for your replies!

---

### Post by jtrindle on 2008-05-31
I'm having the same problem... I have gtk2.0-dev, glib2.0-dev packages installed, but I still get a cascading series of errors when compiling a simplified version of this program in Eclipse.

Help?
 
Thanks.

---

### Post by jtrindle on 2008-05-31
I did get it to compile, but I had to explicitly add all the following to my project:

/usr/include/gtk-2.0
/usr/lib/gtk-2.0/include
/usr/include/glib-2.0
/usr/lib/glib-2.0/include
/usr/include/cairo
/usr/include/atk-1.0
/usr/include/pango-1.0

which got rid of the errors.  I had to add /usr/lib to my lib search path and gtk to my lib list (no surprise there).

I thought there was supposed to be an environment variable that defined the INCLUDE path, or C_INCLUDE_PATH, or CPLUS_INCLUDE_PATH.  It's not set on my system.  Where should I set it, and will Eclipse respect it when it's there?

Thanks!

---

### Post by cro on 2008-07-12
Combining information from a number of sources, as long as you have the GTK source libraries installed (check in /usr/include/ for gtk-2.0), you can set up Eclipse to work with GTK files like this. This is a workaround, and I'm sure there's a better way :)

* Create a new 'C Project', Project type 'Executable', toolchain 'Linux GCC', selecting defaults for all pages
* Once the project is created, right-click on the project name and choose 'properties' (Alt-Enter)
* Expand the C/C++ Build menu and select 'Settings'
* In "GCC C Compiler", change the 'Command line pattern', add
```
`pkg-config --cflags --libs gtk+-2.0`
```
after ```
${COMMAND}
```

Example:
```
${COMMAND} `pkg-config --cflags --libs gtk+-2.0` ${FLAGS} ${OUTPUT_FLAG}${OUTPUT_PREFIX}${OUTPUT} ${INPUTS}
```

* Do the same in GCC C linker

You should now be able to build and run GTK source files from Eclipse.

I have successfully compiled and run both tutorial files from [http://library.gnome.org/devel/gtk-tutorial/stable/c39.html](http://library.gnome.org/devel/gtk-tutorial/stable/c39.html) using the above settings.

---

### Post by jbrackett on 2008-12-27
In case anyone else stumbles onto this post like I did...
Those are backticks (key above tab) not single quotes.  Explanation of the compilation options here - [http://library.gnome.org/devel/gtk-tutorial/stable/x111.html](http://library.gnome.org/devel/gtk-tutorial/stable/x111.html)

---

### Post by sms0611 on 2009-04-02
Here's a way to do what cro (above) has done but a little more elegantly and easier to use and remember.

In eclipse

window->preferences

expand c/c++ then select Managed Build

click on new (define a variable)

Name: gtkc
Value: `pkg-config --cflags --libs gtk+-2.0`  
   (note backwards single quotes are important)

click OK

Repeat if you want to set up one for c++ as well using the c++ variables.

click apply
click Ok

Now you have one or two compiler variables you can apply to any c or c++ project as shown below.

select your project (in this case a c project) then

project->properties

select c/c++ Build

under GCC C Compiler-> Miscellaneous

in Other Flags add ${gtkc} at the end

select GCC C Linker->Miscellaneous

in Linker Flags add ${gtkc}

click apply

click OK.

Have fun.

---

### Post by Cripton on 2009-07-19
thanks sms0611, it works perfectly!

---

### Post by detrix42 on 2009-08-11
Thanks for the help.  But now I am getting the following:

```
./gtkmain.o: In function `_start':
/build/buildd/glibc-2.9/csu/../sysdeps/i386/elf/start.S:65: multiple definition of `_start'
/usr/lib/gcc/i486-linux-gnu/4.3.3/../../../../lib/crt1.o:/build/buildd/glibc-2.9/csu/../sysdeps/i386/elf/start.S:65: first defined here
./gtkmain.o:(.rodata+0x0): multiple definition of `_fp_hw'
/usr/lib/gcc/i486-linux-gnu/4.3.3/../../../../lib/crt1.o:(.rodata+0x0): first defined here
./gtkmain.o: In function `_fini':
/build/buildd/glibc-2.9/csu/../sysdeps/generic/initfini.c:109: multiple definition of `_fini'
/usr/lib/gcc/i486-linux-gnu/4.3.3/../../../../lib/crti.o:/build/buildd/glibc-2.9/csu/../sysdeps/generic/initfini.c:109: first defined here
./gtkmain.o:(.rodata+0x4): multiple definition of `_IO_stdin_used'
/usr/lib/gcc/i486-linux-gnu/4.3.3/../../../../lib/crt1.o:(.rodata.cst4+0x0): first defined here
./gtkmain.o: In function `__data_start':
(.data+0x0): multiple definition of `__data_start'
/usr/lib/gcc/i486-linux-gnu/4.3.3/../../../../lib/crt1.o:(.data+0x0): first defined here
./gtkmain.o: In function `__data_start':
(.data+0x4): multiple definition of `__dso_handle'
/usr/lib/gcc/i486-linux-gnu/4.3.3/crtbegin.o:(.data+0x0): first defined here
./gtkmain.o: In function `_edata':
(*ABS*+0x804a044): multiple definition of `__bss_start'
./gtkmain.o: In function `_end':
(*ABS*+0x804a04c): multiple definition of `_end'
./gtkmain.o: In function `_edata':
(*ABS*+0x804a044): multiple definition of `_edata'
./gtkmain.o: In function `_init':
/build/buildd/glibc-2.9/build-tree/i386-libc/csu/crti.S:15: multiple definition of `_init'
/usr/lib/gcc/i486-linux-gnu/4.3.3/../../../../lib/crti.o:/build/buildd/glibc-2.9/build-tree/i386-libc/csu/crti.S:15: first defined here
/usr/lib/gcc/i486-linux-gnu/4.3.3/crtend.o:(.dtors+0x0): multiple definition of `__DTOR_END__'
./gtkmain.o:(.dtors+0x4): first defined here
collect2: ld returned 1 exit status
make: *** [gtktutorial] Error 1

```

I am not sure why there is multiple definitions. Argh.

---

### Post by npmeyer on 2009-08-27
I'm not sure if this is the cause of your multiple definition problems, but I would hazard a guess that maybe it's because both --cflags and --libs are being passed to pkg-config for both compiling and linking steps.

Perhaps try defining two variables under Window > Preferences > C/C++ > Managed Build

GTK_CFLAGS = `pkg-config --cflags gtk+-2.0`
GTK_LIBS = `pkg-config --libs gtk+2.0`

Add ${GTK_CFLAGS} to the compiler flags only and ${GTK_LIBS} to the linker flags only.

---

### Post by cybrid on 2009-09-16
The way sms0611 has put it is quite elegant but it has a drawback. Putting the directory listing as an environment variable only available to the IDE when you build/run the project makes the intellisense useless.

---

### Post by bd@cb8be8510 on 2010-02-15
thanks sms0611 ... after 2 days of googling, I finally found your solution!

---

### Post by tuonp on 2011-06-02
Things are going to be far better at least in the end of August 2011.

Pkg-config support is under development and will provide an easy to use user interface to select the required packages.

This feature will be integrated to CDT.

You can follow the project here:
[http://code.google.com/p/pkg-config-support-for-eclipse-cdt/](http://code.google.com/p/pkg-config-support-for-eclipse-cdt/)

---

