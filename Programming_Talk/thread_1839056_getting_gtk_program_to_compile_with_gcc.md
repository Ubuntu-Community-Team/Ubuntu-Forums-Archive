---
title: "getting gtk program to compile with gcc"
date: 2011-09-04
forum: Programming Talk
---

### Post by LinuxSavedMyComputer on 2011-09-04
I have a pdf tutorial for gtk 2.0 (google "gtk tutorial pdf"). I have a machine that dual boot 64-bit ubuntu without internet and 32-bit vista with internet. i tried the first example but it could not locate the options related to gtk used in pckconfig. It says at the begging to install gtk but ubuntu already has it (i think). How do i get gtk to compile? I can't use anything like the software center or synaptic or apt-get because i don't have internet. (I can download it on Vista.)

---

### Post by Smart Viking on 2011-09-04
Post the code in CODE tags, and if the tutorial said how to compile it, include that.
By telling us to google for your tutorial you're just making things unnecessary hard, we might not even find the right one, so don't expect us to.

---

### Post by LinuxSavedMyComputer on 2011-09-04
```

#include &#1048576; gtk/gtk.h

int main( int argc,
char *argv[] )
{
GtkWidget *window;
gtk_init (&argc, &argv);
window = gtk_window_new (GTK_WINDOW_TOPLEVEL);
gtk_widget_show (window);
gtk_main ();
return 0;
}

```
compiled with
```
gcc base.c -o base ‘pkg-config --cflags --libs gtk+-2.0‘
```

note that it is the FIRST result when you google gtk tutorial pdf

---

### Post by gardnan on 2011-09-05
Could you please be more specific about the error that you are getting when you are compiling? It can mean the difference between us suggesting downloading a file and rebooting a system.

Anyway, what I believe you want is the GTK development libraries, which you can either download on your Ubuntu install once you get internet on it, or download the .deb files on your Windows machine from here 
(for 2.0)
[http://packages.ubuntu.com/natty/libgtk2.0-dev](http://packages.ubuntu.com/natty/libgtk2.0-dev)
(for 3.0)
[http://packages.ubuntu.com/natty/libgtk-3-dev](http://packages.ubuntu.com/natty/libgtk-3-dev)
Then move the files to your Ubuntu machine and install them using dpkg --install name-of-deb-file.deb

Also, when you want someone to reference an online document, such as a tutorial, it is usually appropriate to give a link, just to ensure that everyone is looking at the same document.

---

