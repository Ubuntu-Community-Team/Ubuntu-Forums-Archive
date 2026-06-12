---
title: "Python GUI"
date: 2012-04-22
forum: Programming Talk
---

### Post by xtjacob on 2012-04-22
Hello, I've been looking all over the place, but I cannot figure out how to take a variable and output it through QT4 in Phython. For example, take text that is inputted in the console, and output in a graphical widget. Does anyone know how to do this?

---

### Post by memilanuk on 2012-04-23
Have you looked at the [tutorials]("http://zetcode.com/tutorials/pyqt4/") over on zetcode.com?

Alternately... I've been working my way thru this book:
[URL="http://www.amazon.com/gp/product/B006WB28Q0/ref=docs-os-doi_0"]
Introduction to Python Programming and Developing GUI Applications with PyQT[/URL].  It addresses the use of QT Designer - free GUI designer that generates xml layout files that can then be converted to python modules so you can import all the gui layout.  Very slick.

---

### Post by overcast on 2012-04-23
Pyside (QT framework open source) can do this but i am not so sure if you can find tutorial for this. Most likely you have to do this by reading someone else code. Take a look at sakis3g library for test, that takes input from console and then opens GTK/TK widgets for further operations.

---

### Post by xtjacob on 2012-04-23
hmm, I'm trying to write a GUI for a weather program I wrote in C. What I have is a program that downloads and parses a .json file, but I cannot figure out how to take the information that has een parsed and pass it to the GUI...

---

### Post by memilanuk on 2012-04-23
Unfortunately I'm not really at the level to where I can provide working code of my own that might useful...  but this series of tutorials seems like it should cover the sort of things that you're looking for - taking data that is in list form and presenting it in a GUI dialog using various widgets.

HTH,

Monte

---

### Post by lykwydchykyn on 2012-04-23
Well, there are a lot of ways to do it, but the simplest code I can think of is:
```

app= QApplication(sys.argv)
widget = QLabel(my_text_I_want_to_display)
widget.show()
app.exec_()

```

Of course, if you want to build an actual application or plasma widget or something, there's a lot more to it, but that will get you a simple widget with text on it.

---

### Post by oldfred on 2012-04-23
this site has examples with qt, gtk & tkinter, you have to scroll thru to find examples that are qt, but can copy & use in your editor to test and see how they work. With one example, I just copied & pasted into geany, saved & it worked.

[http://www.daniweb.com/software-development/python/threads/191210/python-gui-programming/7](http://www.daniweb.com/software-development/python/threads/191210/python-gui-programming/7)

---

### Post by xtjacob on 2012-04-23
I've decided to write the gui in GTK with C since I already had a little experience... I'm trying to get it to take text that is inputted into the box, and store it in a variable when the button is pressed. This is what I have: ```
#include <gtk/gtk.h>

void button_clicked(GtkWidget *widget, GtkEntry *entry1)
{
  g_print("clicked\n");
  const gchar *entry_content;
  entry_content = gtk_entry_get_text(GTK_ENTRY(entry1));

}



int main(int argc, char *argv[]) {

  GtkWidget *window;
  GtkWidget *table;
  GtkWidget *label1;
  GtkWidget *entry1;
  GtkWidget *button;
  
 
  gtk_init(&argc, &argv);

  window = gtk_window_new(GTK_WINDOW_TOPLEVEL);
  gtk_window_set_position(GTK_WINDOW(window), GTK_WIN_POS_CENTER);
  gtk_window_set_title(GTK_WINDOW(window), "GtkEntry");
  gtk_container_set_border_width(GTK_CONTAINER(window), 10);

  table = gtk_table_new(2, 1, FALSE);
  gtk_container_add(GTK_CONTAINER(window), table);

  label1 = gtk_label_new("Zipcode:");
  
  gtk_table_attach(GTK_TABLE(table), label1, 0, 1, 0, 1, GTK_FILL | GTK_SHRINK, GTK_FILL | GTK_SHRINK, 5, 5);
  
  entry1 = gtk_entry_new();
  
  gtk_table_attach(GTK_TABLE(table), entry1, 1, 2, 0, 1, GTK_FILL | GTK_SHRINK, GTK_FILL | GTK_SHRINK, 5, 5);

  button = gtk_button_new_with_label("Enter");
  gtk_table_attach_defaults(GTK_TABLE(table), button, 2, 3, 0, 1 );
 
  gtk_widget_show(table);

  gtk_widget_show(label1);
  
  gtk_widget_show(entry1);
  
  gtk_widget_show(button);
  
  gtk_widget_show(window);

  g_signal_connect(window, "destroy", G_CALLBACK(gtk_main_quit), NULL);

  g_signal_connect(G_OBJECT(button), "clicked", G_CALLBACK(button_clicked), &entry1);
  
  gtk_main();

  return 0;
}
```

However when I run it, and press the button the console says:```
(main:8353): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GtkEntry'

(main:8353): Gtk-CRITICAL **: gtk_entry_get_text: assertion `GTK_IS_ENTRY (entry)' failed

```

Do you guys know what's wrong?

---

