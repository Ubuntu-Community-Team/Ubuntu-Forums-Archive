---
title: "Can anyone please tell me how to compile a gtk program ?"
date: 2012-04-09
forum: Programming Talk
---

### Post by DaviesX on 2012-04-09
I have made a program that uses gtk for GUI interface
It can be successfully compiled in codeblocks before when I was using Ubuntu 11.10. But when I upgrade to 12.04, I have to re-install the gtk dev package. And when I compile the program, it says some headers can't be found, For example, gtkconfig.h, cairo.h.

I have found that some of those lost headers are in another directory that codeblocks doesn't include those when I created the project with default settings for gtk program. I want to change the search directories but it says that I can "use project options only". How can change it, or is there any other solution ?

Thank you ^_^

---

### Post by r-senior on 2012-04-10
Are you able to compile a GTK+ program from the command line?

*hello.c*
```
#include <gtk/gtk.h>

int main( int argc, char **argv)
{
	GtkWidget *window;

	gtk_init(&argc, &argv);

	window = gtk_window_new(GTK_WINDOW_TOPLEVEL);
	gtk_widget_show(window);

	gtk_main();

	return 0;
}

```

Then, to compile:

```
gcc -o hello hello.c `pkg-config --libs --cflags gtk+-2.0`
```

If it doesn't work, the packages you need for GTK2 are:

```
sudo apt-get install build-essential libgtk2.0-dev
```

Obviously if you are working with GTK3, things are slightly different.

If all that works, you can concentrate on the setup of the IDE, or other packages.

---

### Post by DaviesX on 2012-04-10
Thank you :KS

---

