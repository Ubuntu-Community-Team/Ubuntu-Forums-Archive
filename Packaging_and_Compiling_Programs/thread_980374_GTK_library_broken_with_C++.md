---
title: "GTK library broken with C++?"
date: 2008-11-12
forum: Packaging and Compiling Programs
---

### Post by blake82 on 2008-11-12
Hi Folks,

I haven't been able to find ANYTHING about this problem online.

So whenever I try to compile a cpp file that includes <gtk/gtk.h>, even something super simple like a hello world example from the gtk tutorials, I get all these errors. It seems to stem from the fact that the comiler can't find the glibconfig.h andgdkconfig.h header files.

I've downloaded the dev packages and even compiled the latest gtk release and it doesn't seem to work.


Here's an example what what geany's compiler says:
/usr/include/glib/gtypes.h:34:24: error: glibconfig.h: No such file or directory

Any ideas?

---

### Post by gmclachl on 2008-11-13
How are you including the headers are you using pkg-config?

George

---

### Post by Antinumeric on 2008-11-14
I am trying to use the gts library and am getting the same problems- it cannot seem to find glib.h at all. I installed both glib-dev and gtk-dev using apt-get. This happens when i just put <gtk/gtk.h> or <glib.h> at the top, or in gts.h.

edit: i'm not using pkg-config

---

### Post by blake82 on 2008-11-15
They're in /usr/include/

I've compiled the source code, but there's still no XXconfig.h files

---

### Post by Antinumeric on 2008-11-16
hmm- i have a fresh install. quite literally the only commands I have entered are:

sudo apt-get install libgts-dev
sudo apt-get install geany
sudo apt-get install g++
sudo apt-get install firefox

the program i am trying to compile: 
#include <gts.h>

int main(int argc, char** argv)
{
	
	return 0;
}

the error is in gts.h where it cannot find glib.h.

if i change my code to 
#include "/usr/include/glib.h"

then it cannot find any of glib.h's includes like galloca.h etc.

---

