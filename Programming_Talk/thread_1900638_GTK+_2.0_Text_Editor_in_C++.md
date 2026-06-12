---
title: "GTK+ 2.0 Text Editor in C++"
date: 2011-12-26
forum: Programming Talk
---

### Post by theopfor on 2011-12-26
I am currently making a text editor using GTK+ 2.0. I am programming it in C++. The editor currently has a good start, but is rather bland.

[IMG]http://theopfor.pcriot.com/stuff/TextEditor.png[/IMG]

So, now I need to add something to make it more, visually appealing. It's lacking some items, but, currently, I'm looking more towards quality over quantity. 

How do I add buttons with images on them? I am making the buttons from stock. 

How do I get my file chooser dialog to work? It will pop everything up, but not save anything, or load anything, and I don't understand why.

How do I add more libraries to the code? Whenever I do, I get an error. Since I am making this in C++, I have to compile it in terminal with ```
gcc main.cpp -o compiled `pkg-config --cflags --libs gtk+-2.0`
``` (Code::Blocks will only compile GTK+ programs in C). 

Here is the code: 

```
//Text editor
#include <gtk/gtk.h>

  ////////////////////
 //    GLOBAL    //
///////////////////

static GtkWidget *window, *text, *tabs;


static GtkTextBuffer *buffer;


  /////////////////////////
 //    FUNCTIONS     //
////////////////////////

//When the quit button is pressed
static void quit(GtkWidget *window, gpointer data){
    gtk_main_quit();
}

/*static void newDoc(GtkWidget* widget, gpointer data){
    gtk_notebook_append_page(GTK_NOTEBOOK(notebook), text, defaultTitle);
};*/

static void fileOpen(GtkWidget *load, gpointer window){
    GtkWidget *choose;
    
    choose     =    gtk_file_chooser_dialog_new("Choose a file to open", GTK_WINDOW(window), GTK_FILE_CHOOSER_ACTION_OPEN, GTK_STOCK_OK,
                                        GTK_RESPONSE_OK, GTK_STOCK_CANCEL, GTK_RESPONSE_CANCEL, NULL);    
    if (gtk_dialog_run(GTK_DIALOG(choose)) == GTK_RESPONSE_ACCEPT){
        
        char *path     =    gtk_file_chooser_get_filename(GTK_FILE_CHOOSER(choose));
        gtk_text_buffer_set_text(buffer, path, -1);
    }
    
    gtk_widget_destroy(choose);
}

static void fileSave(GtkWidget *save, gpointer window){
    GtkWidget *saved;
    
    saved     =    gtk_file_chooser_dialog_new("Choose a file to open", GTK_WINDOW(window), GTK_FILE_CHOOSER_ACTION_SAVE, GTK_STOCK_OK,
                                        GTK_RESPONSE_OK, GTK_STOCK_CANCEL, GTK_RESPONSE_CANCEL, NULL);
    gtk_widget_show_all(saved);
    
    gint resp    =     gtk_dialog_run(GTK_DIALOG(saved));
    
    gtk_widget_destroy(saved);
}

/*static void fontSelect(GtkWidget *font, gpointer window){
    GtkWidget *fonts;
    
    fonts    =    gtk_font_selection_dialog_new("Font");
    
    gtk_widget_show_all(fonts);
    
    gint resp    =    gtk_dialog_run(GTK_DIALOG(fonts));
    
    gtk_widget_destroy(fonts);
}*/


  /////////////////////////////
 //    MAIN PROGRAM    //
/////////////////////////////

int main(int argc, char *argv[]){
    
    //Just some setup
    
    //Misc.
    GtkWidget *hbox, *vbox, *defaultTitle;
    
    //Buttons
    GtkWidget *load, *save, *quit;
    
    gtk_init(&argc, &argv);
    
      //////////////////////////////////
     //    INITIALIZATION          //
    //////////////////////////////////
    window     =     gtk_window_new(GTK_WINDOW_TOPLEVEL);
    text        =    gtk_text_view_new();
    load        =    gtk_button_new_from_stock(GTK_STOCK_OPEN);
    save        =    gtk_button_new_from_stock(GTK_STOCK_SAVE);
    quit        =    gtk_button_new_from_stock(GTK_STOCK_CLOSE);
    hbox    =    gtk_hbox_new(0, 5);
    defaultTitle=    gtk_label_new("Untitled");
    tabs        =    gtk_notebook_new();
    buffer    =    gtk_text_view_get_buffer(GTK_TEXT_VIEW(text));
    
    vbox        =    gtk_vbox_new(0, 3);
    buffer    =    gtk_text_view_get_buffer(GTK_TEXT_VIEW(text));
    
    //Window
    gtk_window_set_title(GTK_WINDOW(window), "Text editor");
    gtk_window_set_default_size(GTK_WINDOW(window), 600, 400);
    
    //The notebook
    gtk_notebook_set_tab_pos(GTK_NOTEBOOK(tabs), GTK_POS_TOP);
    
    gtk_notebook_append_page(GTK_NOTEBOOK(tabs), text, defaultTitle);
    
    //Attach st00f to our hbox
    gtk_box_pack_start(GTK_BOX(hbox), load, 0, 1, 0);
    gtk_box_pack_start(GTK_BOX(hbox), save, 0, 1, 0);
    //gtk_box_pack_start(GTK_BOX(hbox), font, 0, 1, 0);
    gtk_box_pack_start(GTK_BOX(hbox), quit, 0, 1, 0);
    
    //Attach st00f to our vbox
    gtk_box_pack_start(GTK_BOX(vbox) , hbox, 0, 1, 0);
    gtk_box_pack_start(GTK_BOX(vbox), tabs,1,1,0);
    
    
    
    
      /////////////////////
     //     EVENTS     //
    /////////////////////
    
    //Window closing
    g_signal_connect(window, "delete-event", G_CALLBACK(gtk_main_quit), NULL);
    
    //Quit
    g_signal_connect(quit, "clicked", G_CALLBACK(quit), window);
    
    //Open
    g_signal_connect(load, "clicked", G_CALLBACK(fileOpen), window);
    
    //Save
    g_signal_connect(save, "clicked", G_CALLBACK(fileSave), window);
    
    //Font
    //g_signal_connect(font, "clicked", G_CALLBACK(fontSelect), window);
    
    
      ///////////////////
     //    OTHER    //
    //////////////////
    gtk_container_add(GTK_CONTAINER(window), vbox);
    gtk_widget_show_all(window);
    gtk_main();
    return 0;
}
```Thanks ahead of time! :D

---

### Post by SledgeHammer_999 on 2011-12-26
1. Install the "build-essential" package.
2. Create an empty C++ project in Code::Blocks
3. Use Gtkmm(these are C++ bindings for Gtk+). DOn't forget to install libgtkmm-dev. [www.gtkmm.org](www.gtkmm.org)
4. Redo your code using Gtkmm
5. Use [Gtk::Button::set_image()](http://developer.gnome.org/gtkmm/unstable/classGtk_1_1Button.html#ac49972018a8ed3392e897cdf9da66391).
6. If you insist on using the C API then use [gtk_button_set_image()](http://developer.gnome.org/gtk3/stable/GtkButton.html#gtk-button-set-image).

(In codeblocks: open your projects settings and insert in the compiler's custom/extra flags " **'pgk-config gtkmm-2.4 --cflags'  **" and in the linker's custom/extra flags "**  'pgk-config gtkmm-2.4 --libs'  **")

---

### Post by theopfor on 2011-12-27
:confused:I'm confused on the part where I change the compiler and linker settings.  I don't see an area to copy and paste anything. In Compiler Flags, I see a bunch of check boxes, but nothing to copy and paste. In the linker settings, I am just 100% confused with. 

Any way you could explain it very throughly? I have never opened that section of the IDE.

---

### Post by SledgeHammer_999 on 2011-12-27
1. Project->Build Options
2. Compiler Settings -> Other options. Paste: 'pgk-config gtkmm-2.4 --cflags'
3. Linker Settings -> Other Linker options. Paste: 'pgk-config gtkmm-2.4 --libs'
4. Don't forget the ' in the above commands.
5. It should compile now.

---

### Post by theopfor on 2011-12-27
g++ fatal error: no input files

I did what you said, but I don't understand that error...

---

