---
title: "Compilation error"
date: 2007-03-15
forum: Programming Talk
---

### Post by bluezapper on 2007-03-15
Hi,

I am new to GUI development with gnome. I am using Ubuntu Dapper Drake Linux. I have written the following program

```
#include<gnome.h>

int main(int argc,char *argv[])

{

GTKWidget *topLevelWindow;

gnome_init("suc","1.0",argc,argv);

topLevelWindow=gnome_app_new(("suc","Gnome Window");

gtk_widget_show(topLevelWindow);

gtk_main();

exit(0);

}

```
When I compile the above program using the following command:

gcc -o suc suc.c `gnome-config --cflags --libs gnomeui`

I am getting the following errors

suc.c: In function ‘main’:
suc.c:7: error: ‘GTKWidget’ undeclared (first use in this function)
suc.c:7: error: (Each undeclared identifier is reported only once
suc.c:7: error: for each function it appears in.)
suc.c:7: error: ‘topLevelWindow’ undeclared (first use in this function)
suc.c:11: error: syntax error before ‘;’ token

what should be done ??

thanks

bluezapper

---

### Post by SniDa on 2007-03-15
I believe the object type is GtkWidget (note the capitalization), not GTKWidget.

---

