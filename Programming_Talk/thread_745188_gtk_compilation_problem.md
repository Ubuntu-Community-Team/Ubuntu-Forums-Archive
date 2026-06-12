---
title: "gtk compilation problem"
date: 2008-04-04
forum: Programming Talk
---

### Post by QwUo173Hy on 2008-04-04
I'm trying to compile a helloworld gtk example from a book using the command:

gcc -Wall -g helloworld.c -o helloworld `pkg-config --cflags gtk+-2.0` \ `pkg-config --libs gtk+-2.0`

I get the output:

gcc:  -lgtk-x11-2.0: No such file or directory

But I did find:

jarlath@jarlath-laptop:~$ sudo locate gtk-x11
[sudo] password for jarlath: 
/usr/lib/libgtk-x11-2.0.so.0
/usr/lib/libgtk-x11-2.0.so.0.1200.9

also, running the first pkg-config argument alone results in:

jarlath@jarlath-laptop:~$ `pkg-config --cflags gtk+-2.0`
bash: -I/usr/include/gtk-2.0: No such file or directory

Yet I found this folder:

jarlath@jarlath-laptop:~$ cd /usr/include/gtk-2.0/
jarlath@jarlath-laptop:/usr/include/gtk-2.0$ ls
gdk  gdk-pixbuf  gdk-pixbuf-xlib  gtk


I'm completely stumped. Can anyone help me out?

Regards,
Jarlath

---

### Post by WW on 2008-04-04
I'm not sure what the problem is; I just have a quick tip for you.  To see what pkg-config is doing, don't do this:
> **jarlath said:**
> 
jarlath@jarlath-laptop:~$ `pkg-config --cflags gtk+-2.0`

Instead, run the command without the back quotes:
> 
$ pkg-config --cflags gtk+-2.0


---

### Post by WW on 2008-04-04
> **jarlath said:**
> I'm trying to compile a helloworld gtk example from a book using the command:

gcc -Wall -g helloworld.c -o helloworld `pkg-config --cflags gtk+-2.0` \ `pkg-config --libs gtk+-2.0`

I suspect the backslash in that command is in the book to let you know that it should really be one long command, but the text splits it into two lines to fit the command on the page.  Also, the two uses of pkg-config can be combined into one.  Try this command:
> 
gcc -Wall -g helloworld.c -o helloworld `pkg-config --cflags --libs gtk+-2.0`


---

### Post by QwUo173Hy on 2008-04-04
God, I feel so stupid! Thanks guys, you're both correct. The backslash wasn't a part of the command at all.

Thanks again for your time,
Jarlath

---

