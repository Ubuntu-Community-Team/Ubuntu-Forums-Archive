---
title: "Include time.h in makefile?"
date: 2014-12-15
forum: Programming Talk
---

### Post by jusaca on 2014-12-15
At the moment I'm on learning creating a GUI with GTK+.
To built my Program I use a makefile with this content:
```

CC       = gcc
CFLAGS = `pkg-config --cflags gtk+-3.0`
LIBS     = `pkg-config --libs gtk+-3.0`

Data_logging : Data_logging.o 
   $(CC) $(LIBS) -o Data_logging Data_logging.o 

Data_logging.o : Data_logging.c
   $(CC) $(CFLAGS) -c Data_logging.c

```

This works a treat, but now I have to add the time.h for my application.
If i try to build it just with the #include time.h in the code I get the error, that the file oder path couldn't be found.
What have I to type in my makefile to tell the programm to include the fike corect?

I have to admit, that I still didn't get the way makefiles are working and that I'm copying my parts together... ;/

---

### Post by kpatz on 2014-12-15
Try **#include <time.h>** with the angle brackets.

You may need to also **#include <sys/time.h>**.

---

### Post by jusaca on 2014-12-15
I type this in my makefile? In the code I already have this ;)

// By the way, what is the difference between time.h and sys/time.h?

---

### Post by kpatz on 2014-12-15
If your code already has the #includes they should work.  No special changes to the Makefile is needed.

Unless you're missing time.h in your /usr/include directory.  Do you have the libc6-dev package installed?

What's the exact error message you're getting when you run make?

---

### Post by jusaca on 2014-12-15
Yes, libc6-dev is installed, I just checked. On another program I was already able to include the time.h, the only difference to my current project was the makefile. 
For that other project I used
```

all: SPI_Com

SPI_Com: SPI_Com.o
   gcc SPI_Com.c -lbcm2835 -o SPI_Com

SPI_com.o: SPI_Com.c
   gcc -c SPI_Com.c

clean:
   rm -rf *0 SPI_Com

```

The error I get now with the new Makefile for GTK is:

"Data_Logging.c:2:19: fatal error: timer.h Datei oder Verzeichnis nicht gefunden
compilation terminated.
makefile:10: recipe for target 'Data_Logging.o' failed"

"Datei oder Verzeichnis nicht gefunden" means "File or Path not found".

---

### Post by spjackson on 2014-12-15
> **jusaca said:**
> 
"Data_Logging.c:2:19: fatal error: timer.h Datei oder Verzeichnis nicht gefunden
compilation terminated.
makefile:10: recipe for target 'Data_Logging.o' failed"

"Datei oder Verzeichnis nicht gefunden" means "File or Path not found".

The error message you have posted is for timer.h not time.h. What is timer.h?

---

### Post by Rocket2DMn on 2014-12-15
Agreed that it's complaining about timer.h, not time.h.
In case that's just a copy typo -- on some systems, you need to link with librt at compile time.  Pass -lrt to gcc.

---

### Post by jusaca on 2014-12-16
Oh, thats just embarrasing, a silly typo... Yes, of course I meant time.h, not timer.h ;/
I searched hours for that mistake!

But now the problems go on with another lib: The bcm2835.h
From an older project a already know, that I have to inlcude the library in the makefil with -lbcm2835, so I added this to the LIBS line:
```

LIBS     = `pkg-config --libs gtk+-3.0` -lbcm2835

```

But I still get an error, when I try to use a function from this lib:
"undefined reference to `bcm2835_init'

Maybe somebody can explain to me how I correctly add this lib to my makefile? I want to understand how to write these things!^^

---

### Post by spjackson on 2014-12-16
> 
Maybe somebody can explain to me how I correctly add this lib to my makefile? I want to understand how to write these things!
As far as we can tell, you have correctly added the library to the makefile.
What is the command that is being executed by make for the link? (i.e. show all the output from 'make' not just the error message.)
How did you install the library?
Is it for the right architecture?
Are you building this on a Raspberry Pi?

---

### Post by jusaca on 2014-12-16
Yes, I try to build this on the Raspberry and the library is correct installed - at least I could include it in an other project with the old makefild from above (#5). I just opened this project and testet the making - there it works just fine, I can use every Function from the bcm2835. So it really seems to be an issue with the makefile - or something I'm overlooking this time...

The whole return from make:
```

gcc -lgtk-3 -lgdk-3 -latk-1.0 -lgio-2.0  -lpangocairo-1.0 -lgdk_pixbuf-2.0 -lcairo-gobject -lpango-1.0 -lcairo  -lgobject-2.0 -lglib-2.0 -lbcm2835 -o Data_Logging Data_Logging.o
gcc `pkg-config --libs gtk+-3.0`  -lbcm2835 -o Data_Logging Data_Logging.o
Data_Logging.o: In function `main':
Data_Logging.c:(.text+0x11d4): undefined reference to `bcm2835_init'
Data_Logging.c:(.text+0x11fc): undefined reference to `bcm2835_gpio_fsel'
Data_Logging.c:(.text+0x1208): undefined reference to `bcm2835_gpio_write'
Data_Logging.c:(.text+0x1214): undefined reference to `bcm2835_gpio_write'
collect2: ld returned 1 exit status
makefile:7: recipe for target 'Data_Logging' failed
make: *** [Data_Logging] Error 1

```

I really hope this can help^^

---

### Post by steeldriver on 2014-12-16
Your Makefile in post #5 places the library AFTER the source file
```

   gcc **SPI_Com.c** -lbcm2835 -o SPI_Com

```

whereas your command above places the libraries BEFORE the object file
```

gcc -lgtk-3 -lgdk-3 -latk-1.0 -lgio-2.0  -lpangocairo-1.0 -lgdk_pixbuf-2.0 -lcairo-gobject -lpango-1.0 -lcairo  -lgobject-2.0 -lglib-2.0 -lbcm2835 -o Data_Logging **Data_Logging.o**

```

In general, dependencies are resolved left-to-right so you usually want the order to be something like

```

gcc -o Data_Logging **Data_Logging.o **-lgtk-3 -lgdk-3 -latk-1.0 -lgio-2.0  -lpangocairo-1.0  -lgdk_pixbuf-2.0 -lcairo-gobject -lpango-1.0 -lcairo  -lgobject-2.0  -lglib-2.0 **-lbcm2835 **

```
or
```

gcc -o Data_Logging **Data_Logging.o [B]-lbcm2835 **[/B]-lgtk-3 -lgdk-3 -latk-1.0 -lgio-2.0  -lpangocairo-1.0  -lgdk_pixbuf-2.0 -lcairo-gobject -lpango-1.0 -lcairo  -lgobject-2.0  -lglib-2.0 

```

(the order of linking the gtk/gdk libs relative to the bcm2835 lib is probably a matter of taste, but since it's fairly "low level" functionality I'd tend to put it after the "high-level" GUI libs).

---

### Post by spjackson on 2014-12-16
Ah yes. So you want.
```

   $(CC) -o Data_logging Data_logging.o $(LIBS)

```

---

### Post by jusaca on 2014-12-16
Ha, that was it! It works! Thanks, I never would have guessed that^^

---

