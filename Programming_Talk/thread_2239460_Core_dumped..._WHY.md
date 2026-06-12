---
title: "Core dumped... WHY?"
date: 2014-08-14
forum: Programming Talk
---

### Post by fahedsl on 2014-08-14
Hello, I am  teaching myself some programming, and Im working on a small program, on Geany with GTK+ 3, Mariadb and mysql++. I'm sure all of them are working fine. 
I'm experimenting a bit with functions, because i'm new to the language, soo i did this(supossed to show an empty window, with an invisible grid):

```

// Cabeceras#include <mysql++/mysql++.h>
#include <iostream>
#include <iomanip>
#include <gtk/gtk.h>


// Nombres (evita ::)
using namespace std;
using namespace mysqlpp;


//Globales
GtkWidget *wventana;


//DEFINICIONES


int ventana(string titulo, int margen)
{
    const char * tituloc = titulo.c_str();


    wventana = gtk_window_new (GTK_WINDOW_TOPLEVEL);
    gtk_window_set_position (GTK_WINDOW (wventana), GTK_WIN_POS_CENTER);
    gtk_window_set_title (GTK_WINDOW (wventana), tituloc);
    gtk_container_set_border_width(GTK_CONTAINER(wventana), margen);
    return 0;
}


int grid()
{
GtkWidget *grid;


    grid = gtk_grid_new();
    gtk_container_add(GTK_CONTAINER(ventana), grid);
    return 0;
}


//INICIO
int main(int argc, char *argv[])
{
    //INICIO GTK
    gtk_init (&argc, &argv);


    //Widgets
    ventana("ventana",10);
    grid();


    //mostrar todo gtk
    gtk_widget_show_all (wventana);
    gtk_main ();


    return 0;
}

```

It compiles successfully with this instructions :

```
g++ -Wall -I/usr/include/mysql -I/usr/local/include/mysql++  -o "%e" "%f" `pkg-config --cflags --libs gtk+-3.0`
```

(%e and %f are file names completed automatically by Geany), but when I try to run the program, it shows:

```
Segmentation fault (core dumped)
```

Please, someone tell me why that is happening and/or how to fix it.
Thanks in advance.

---

### Post by lisati on 2014-08-14
Duplicate of [http://ubuntuforums.org/showthread.php?t=2239459](http://ubuntuforums.org/showthread.php?t=2239459) closed in the interests of not diluting the community's ability to help.

---

