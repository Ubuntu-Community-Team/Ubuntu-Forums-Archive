---
title: "GTK+ problems"
date: 2009-10-28
forum: Programming Talk
---

### Post by Jekshadow on 2009-10-28
I decided to start learning GTK+, and when I compile the first program:

#include <gtk/gtk.h>

int main(int argc, char *argv[]) {
	GtkWidget *window;
	
	gtk_init(&argc, &argv);
	
	window = gtk_window_new(GTK_WINDOW_TOPLEVEL);
	gtk_widget_show(window);
	gtk_main();
	return 0;
	
}

It gives me this:

./main.o: In function `main':
/home/colinwarren/workspace/AutoComp/Debug/../main.c:6: undefined reference to `gtk_init'
/home/colinwarren/workspace/AutoComp/Debug/../main.c:8: undefined reference to `gtk_window_new'
/home/colinwarren/workspace/AutoComp/Debug/../main.c:9: undefined reference to `gtk_widget_show'
/home/colinwarren/workspace/AutoComp/Debug/../main.c:10: undefined reference to `gtk_main'

My GCC flags are:

gcc `pkg-config --cflags gtk+-2.0` -O0 -g3 -Wall -c -fmessage-length=0 -MMD -MP -MF"main.d" -MT"main.d" -o"main.o" "../main.c"

---

### Post by OutOfReach on 2009-10-28
Try adding '--libs' in addition to '--cflags' in the pkg-config part.

---

### Post by Jekshadow on 2009-10-28
> **OutOfReach said:**
> Try adding '--libs' in addition to '--cflags' in the pkg-config part.

It seems like the problem was my IDE (Eclipse) split up the compiling and the linking, so once I had the Linker use the libs too, it solved the problem.

---

