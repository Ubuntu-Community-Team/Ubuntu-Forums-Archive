---
title: "vips and pkg-config: problem compiling examples"
date: 2008-07-14
forum: Programming Talk
---

### Post by sickasabat on 2008-07-14
I am trying to write programs that use the graphics libraries provided by the vips image processing system ([www.vips.ecs.soton.ac.uk](www.vips.ecs.soton.ac.uk)). The vips and nip2 package are installed and I can run vips commands and the nip2 gui. What I want to do is to write my own programs that make use of the vips functions. So I tried to run some of the "hello world" programs that are provided on the site. This is the one I have used:
```

#include <stdio.h>
#include <vips/vips.h>

int
main (int argc, char **argv)
{
  IMAGE *im;
  double avg;

  /* Start up VIPS. This will load translations, init the
   * threading system, init any libraries that VIPS uses and load any
   * plugins.
   */
  if (im_init_world (argv[0]))
    error_exit ("unable to start VIPS");

  if (argc != 2)
    error_exit ("usage: %s <filename>", g_get_prgname ());

  if (!(im = im_open (argv[1], "r")))
    error_exit ("unable to open");
  if (im_avg (im, &avg))
    error_exit ("unable to find avg");
  im_close (im);

  printf ("Hello World!\nPixel average of %s is %g\n", argv[1], avg);

  return (0);
}

```

to compile it, I use the following command provided from the website
```

gcc -Wall try5.c `pkg-config vips-7.12 --cflags --libs`

```

I replaced try5.c with the name I called my file and vips-7.12 with vips-7.14 because that is the version that I downloaded.

I made sure that when I typed it in I use the ` character as opposed to the ' character.

The error that I get is:
```

Package vips/vips-7.14 was not found in the pkg-config search path.
Perhaps you should add the directory containing `vips/vips-7.14.pc'
to the PKG_CONFIG_PATH environment variable
No package 'vips/vips-7.14' found

```

I checked the PKG_CONFIG_PATH variable and found that it hadn't been set to anything. So I set it to the directory where the file vips-7.14.pc is.
So now echo $PKG_CONFIG_PATH returns ~/Documents and the file vips-7.14.pc has the path ~/Documents/vips/vips-7.14.pc

I don't think that the problem lies with the vips file because I would assume that the message would complain about an incorrect .pc file. So I can only guess that there is something that I'm failing to set up properly. Any help would be greatly appreciated. 

thanks

---

### Post by hod139 on 2008-07-14
> **sickasabat said:**
> I checked the PKG_CONFIG_PATH variable and found that it hadn't been set to anything. So I set it to the directory where the file vips-7.14.pc is.
So now echo $PKG_CONFIG_PATH returns ~/Documents and the file vips-7.14.pc has the path ~/Documents/vips/vips-7.14.pc

I don't know if you can use the tilde '~' shortcut for home directory in the environment variable.  Also, you wrote that PKG_CONFIG_PATH should contain the directory containing the pc file, but that's not what you did.  Try
```
PKG_CONFIG_PATH="/home/username/Documents/vips"
```

---

### Post by sickasabat on 2008-07-14
Thanks for the quick reply. I made the changes that you recommended but I received this error instead:
```

Failed to open 'vips-7.14.pc': No such file or directory
No package 'vips-7.14.pc' found

```

That package definately exists in that directory. I'm trying to understand what and how the pkg-config thing works. Does it (for this one compilation) add the directory in the variable to the library path? I am thinking this because in the given example code the vips.h file is added the same way that stdio.h is added. Whereas if you write your own header files you add them with #include "myheader.h".

---

### Post by hod139 on 2008-07-14
pkg-config allows for a portable way to distribute libraries.  If the library has external dependencies, they are managed by pkg-config.  For example, if you wanted to use the gdkmm-2.4 library, To get the cflags type
```

pkg-config --cflags gdkmm-2.4

```

and to get the libraries type
```

 pkg-config --libs gdkmm-2.4

```

This is much easier then trying to remember to add 
```

-lgdkmm-2.4 -lpangomm-1.4 -lgdk-x11-2.0 -lcairomm-1.0 -lglibmm-2.4 -lsigc-2.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lpango-1.0 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0 -lcairo

```
to a Makefile.

As for why pkg-config cannout find vips-7.14.pc using the environment variable PKG_CONFIG_PATH, I don't know.  You can try putting  vips-7.14.pc into 
```

 /usr/lib/pkgconfig/

```
which is the default search location.

---

