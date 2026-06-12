---
title: "Gtk+"
date: 2009-05-18
forum: Programming Talk
---

### Post by TKC747 on 2009-05-18
I tried compiling the following program and I used the correct command as given in a tutorial but the compiler gcc complained that gtk/gtk.h no such file or directory.  I thought I had installed GTK through the synaptic package manager as I am a novice, what did I do wrong?

#include <gtk/gtk.h>

int main( int argc, char *argv[])
{
  GtkWidget *window;

  gtk_init(&argc, &argv);

  window = gtk_window_new(GTK_WINDOW_TOPLEVEL);
  gtk_widget_show(window);

  gtk_main();

  return 0;
}


Thanks

---

### Post by JupiterV2 on 2009-05-18
What command line did you use to compile this source?

Remember, you need to use pkg-config to properly link and compile gtk projects.

---

### Post by TKC747 on 2009-05-19
> **JupiterV2 said:**
> What command line did you use to compile this source?

Remember, you need to use pkg-config to properly link and compile gtk projects.

I used :

gcc -o simple simple.c `pkg-config --libs --cflags gtk+-2.0`

I cursorily looked for the gtk directory, I tried installing from the command line and  gtk seems to be installed ( no update)-same result from:

sudo apt-get install libgtk2.0-0

result was " not upgraded"

tommy@tommy-desktop:~$ sudo apt-get install libgtk2.0-0
[sudo] password for tommy: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgtk2.0-0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
tommy@tommy-desktop:~$ 
tommy@tommy-desktop:~$ gcc -o testprog test.c 'pkg-config --libs --cflags gtk+-2.0'
gcc: test.c: No such file or directory
gcc: pkg-config --libs --cflags gtk+-2.0: No such file or directory
gcc: no input files
tommy@tommy-desktop:~$ cd Desktop
tommy@tommy-desktop:~/Desktop$ gcc -o testprog test.c 'pkg-config --libs --cflags gtk+-2.0'
gcc: pkg-config --libs --cflags gtk+-2.0: No such file or directory
test.c:1:21: error: gtk/gtk.h: No such file or directory
test.c: In function &#8216;main&#8217;:
test.c:5: error: &#8216;GtkWidget&#8217; undeclared (first use in this function)
test.c:5: error: (Each undeclared identifier is reported only once
test.c:5: error: for each function it appears in.)
test.c:5: error: &#8216;window&#8217; undeclared (first use in this function)
test.c:9: error: &#8216;GTK_WINDOW_TOPLEVEL&#8217; undeclared (first use in this function)
tommy@tommy-desktop:~/Desktop$

---

### Post by PmDematagoda on 2009-05-19
Did you use the single quote or the backward quote that gives the output of a command in place of it? From the commands you posted through the terminal, it would seem that you're using the wrong quote.

---

### Post by Zugzwang on 2009-05-19
@OP: In Ubuntu, you also need to install the "-dev" packages of the libraries you want to use for development. So for gtk2, this would be the package "libgtk2.0-dev".

---

### Post by TKC747 on 2009-05-19
Thank you Zugzwang.  It worked.  It seems I need to learn alot more about the unix shell commands.  Thanks a bunch:D

---

