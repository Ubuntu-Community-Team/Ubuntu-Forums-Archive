---
title: "Need help with programming using GTK+"
date: 2010-03-15
forum: Programming Talk
---

### Post by gabe17 on 2010-03-15
Hi there! I am just beginning with GTK+. I am doing a program which should read a number, write it on the screen and I also need the number as "int" to next manipulation.  The other numbers also needs to be kept, the image will show more. 
The screen is included as an attachment.

This is the code that I've written: 
```

//gcc -o bc main.c `pkg-config --libs --cflags gtk+-2.0`
#include <gtk/gtk.h>
#include <stdio.h>
#include <stdlib.h>

static void enter_callback(GtkWidget *widget, GtkWidget *entry)
{
    const gchar *entry_text;
    entry_text = gtk_entry_get_text(GTK_ENTRY(entry));
    printf("Vstup: %s\n", entry_text);
}   

int main(int argc, char *argv[])
{
    char hlavicka1[] = "Nm.";
    char hlavicka2[] = "Inserted nm";
    char hlavicka3[] = "nth";
    
    GtkWidget *window;
    GtkWidget *vbox;
    
    GtkWidget *menubar;
    GtkWidget *filemenu;
    GtkWidget *file;
    GtkWidget *koniec;
    GtkWidget *nova_hra;
    
    GtkWidget *table; 
    GtkWidget *label1;
    GtkWidget *vstup;
    GtkWidget *button;
    
    GtkWidget *tabulka_vystup;
    GtkWidget *labelx, *labely, *labelz;
    GtkWidget *labelxx, *labelxy, *labelxz;    
    gtk_init(&argc, &argv); 
    
    window = gtk_window_new(GTK_WINDOW_TOPLEVEL); 
    gtk_window_set_title(GTK_WINDOW(window), "NTH"); 
    gtk_window_set_default_size(GTK_WINDOW(window), 400, 300);
    gtk_window_set_position(GTK_WINDOW(window), GTK_WIN_POS_CENTER); 
    
    table = gtk_table_new(2, 3, FALSE); 
    
    vbox = gtk_vbox_new(FALSE, 0);
    gtk_container_add(GTK_CONTAINER(window), vbox);
    
    menubar = gtk_menu_bar_new(); 
    filemenu = gtk_menu_new(); 
    
    file = gtk_menu_item_new_with_label("File");
    nova_hra = gtk_menu_item_new_with_label("New");
    koniec = gtk_menu_item_new_with_label("Exit");
    
    
    gtk_menu_item_set_submenu(GTK_MENU_ITEM(file), filemenu);
    gtk_menu_shell_append(GTK_MENU_SHELL(filemenu), nova_hra);
    gtk_menu_shell_append(GTK_MENU_SHELL(filemenu), koniec);
    gtk_menu_shell_append(GTK_MENU_SHELL(menubar), file);
    gtk_box_pack_start(GTK_BOX(vbox), menubar, FALSE, FALSE, 3);
    
    gtk_box_pack_start(GTK_BOX(vbox), table, FALSE, FALSE, 3);
    label1 = gtk_label_new("Enter: "); 
    gtk_table_attach(GTK_TABLE(table), label1, 0, 1, 0, 1, GTK_FILL | GTK_SHRINK, GTK_FILL | GTK_SHRINK, 10, 10);
    vstup = gtk_entry_new(); 
    gtk_table_attach(GTK_TABLE(table), vstup, 1, 2, 0, 1, GTK_FILL | GTK_SHRINK, GTK_FILL | GTK_SHRINK, 10, 10);
    button = gtk_button_new_with_label("Enter"); 
    gtk_table_attach(GTK_TABLE(table), button, 2, 3, 0, 1, GTK_FILL | GTK_SHRINK, GTK_FILL | GTK_SHRINK, 10, 10); 
    gtk_widget_set_size_request(button, 80, 30);    

    tabulka_vystup = gtk_table_new(2, 3, FALSE);
    gtk_box_pack_start(GTK_BOX(vbox), tabulka_vystup, FALSE, FALSE, 3); 
    labelx = gtk_label_new(hlavicka1); //
    gtk_table_attach(GTK_TABLE(tabulka_vystup), labelx, 0, 1, 0, 1, GTK_FILL | GTK_SHRINK, GTK_FILL | GTK_SHRINK, 20, 5);
    
    labely = gtk_label_new(hlavicka2); //
    gtk_table_attach(GTK_TABLE(tabulka_vystup), labely, 1, 2, 0, 1, GTK_FILL | GTK_SHRINK, GTK_FILL | GTK_SHRINK, 40, 5);
    
    labelz = gtk_label_new(hlavicka3); //
    gtk_table_attach(GTK_TABLE(tabulka_vystup), labelz, 2, 3, 0, 1, GTK_FILL | GTK_SHRINK, GTK_FILL | GTK_SHRINK, 40, 5);
    
    labelxx = gtk_label_new("1.\n2.\n3.\n4.\n5.\n6.\n7.\n8."); //
    gtk_table_attach(GTK_TABLE(tabulka_vystup), labelxx, 0, 1, 1, 2, GTK_FILL | GTK_SHRINK, GTK_FILL | GTK_SHRINK, 20, 5);

    g_signal_connect (G_OBJECT (button), "clicked", G_CALLBACK(enter_callback), (gpointer) vstup);
    g_signal_connect_swapped(G_OBJECT(window), "destroy", G_CALLBACK(gtk_main_quit), NULL);
    g_signal_connect(G_OBJECT(koniec), "activate", G_CALLBACK(gtk_main_quit), NULL);
    
     gtk_widget_show_all(window);
    
    gtk_main();
    
    return 0;
}

```//Sorry that I haven't changed some names of variables to english

---

### Post by feuloren on 2010-03-15
What's the problem ?
You should use a gtk_liststore and a gtk_tree_view to display the values instead of a gtk_table with a lot of widgets packed in.

---

