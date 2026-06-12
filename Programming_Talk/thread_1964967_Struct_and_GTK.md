---
title: "Struct and GTK"
date: 2012-04-24
forum: Programming Talk
---

### Post by xtjacob on 2012-04-24
Hello, I am attempting to run a function when a button is pressed, and have that function print something once it's done running in GTK. It compiles fine with no errors, but when I run it GTK gives me this error:
```
(weather:7078): Gtk-CRITICAL **: gtk_label_set_text: assertion `GTK_IS_LABEL (label)' failed

```

Here's my code:
```
#include <gtk/gtk.h>
char buf[5];

struct variables conditions(char *location);

struct variables {
  char *temp;
  char *dpnt;
  char *rhum;
  char *wind;
  char *pressure;
  char *trend;
  char *windir;
  char *metric;
};

struct guicrap {
  GtkWidget *entry1;
  GtkWidget *temperature;
  GtkWidget *dewpoint;
  GtkWidget *humidity;
  GtkWidget *gwind;
  GtkWidget *gpressure;
};


void button_clicked(GtkButton *button, gpointer *entry1)
{
  struct variables gvariables;
  struct guicrap cguicrap;
  const gchar *location;
  location = gtk_entry_get_text(GTK_ENTRY(entry1));
  gvariables = conditions(location);
  
  sprintf(buf, "%s", gvariables.temp);
  gtk_label_set_text(GTK_LABEL(cguicrap.temperature), buf);

}


int main(int argc, char *argv[]) {

  GtkWidget *window;
  GtkWidget *table;
  GtkWidget *label1;
  GtkWidget *button;
  struct guicrap gguicrap;
  
 
  gtk_init(&argc, &argv);

  window = gtk_window_new(GTK_WINDOW_TOPLEVEL);
  gtk_window_set_position(GTK_WINDOW(window), GTK_WIN_POS_CENTER);
  gtk_window_set_title(GTK_WINDOW(window), "Weather");
  gtk_container_set_border_width(GTK_CONTAINER(window), 10);

  table = gtk_table_new(2, 1, FALSE);
  gtk_container_add(GTK_CONTAINER(window), table);

  label1 = gtk_label_new("Zipcode:");
  gguicrap.entry1 = gtk_entry_new();
  button = gtk_button_new_with_label("Enter");
  gguicrap.temperature = gtk_label_new("temp");
  
  gtk_table_attach(GTK_TABLE(table), label1, 0, 1, 0, 1, GTK_FILL | GTK_SHRINK, GTK_FILL | GTK_SHRINK, 5, 5);
  gtk_table_attach(GTK_TABLE(table), gguicrap.entry1, 1, 2, 0, 1, GTK_FILL | GTK_SHRINK, GTK_FILL | GTK_SHRINK, 5, 5);
  gtk_table_attach_defaults(GTK_TABLE(table), button, 2, 3, 0, 1 );
  gtk_table_attach_defaults(GTK_TABLE(table), gguicrap.temperature, 1, 2, 1, 2); 

  gtk_widget_show(table);
  gtk_widget_show(label1);
  gtk_widget_show(gguicrap.entry1);
  gtk_widget_show(gguicrap.temperature);
  gtk_widget_show(button);
  gtk_widget_show(window);

  g_signal_connect(window, "destroy", G_CALLBACK(gtk_main_quit), NULL);
  g_signal_connect(GTK_BUTTON(button), "clicked", G_CALLBACK(button_clicked), gguicrap.entry1);
  
  gtk_main();

  return 0;
}
```

I think it has something to do with this line:
```
gtk_label_set_text(GTK_LABEL(cguicrap.temperature), buf);
```
Any help is appreciated.

---

### Post by Bachstelze on 2012-04-24
You didn't say if the program stil runs fine or not. If it does, you can probably disregard the message, it is common to have messages like that appearing when running a graphical program (especially GTK) form a terminal.

---

### Post by xtjacob on 2012-04-24
Sorry, the program doesn't run right, my label doesn't change.

---

### Post by Bachstelze on 2012-04-24
In your button_clicked function, cguicrap is not initialised.

---

### Post by xtjacob on 2012-04-24
> **Bachstelze said:**
> In your button_clicked function, cguicrap is not initialised.

I thought I initialised it with this line:
```
struct guicrap cguicrap;
```

---

### Post by Bachstelze on 2012-04-24
No, you only declared it. Initialising a variable in C means giving it an initial value, which you don't do.

---

### Post by xtjacob on 2012-04-24
Hmm, I thought I gave it a value when I first created it in the main function...

```
gguicrap.temperature = gtk_label_new("temp");
```

I also thought that this refered to the gtkwidget label:```
GTK_LABEL(cguicrap.temperature)
```

---

### Post by Bachstelze on 2012-04-24
> **xtjacob said:**
> Hmm, I thought I gave it a value when I first created it in the main function...

```
gguicrap.temperature = gtk_label_new("temp");
```

Yes but this is a different function. ;) If you want it available in your button_clicked function, make it global or pass it as a parameter.

> I also thought that this refered to the gtkwidget label:```
GTK_LABEL(cguicrap.temperature)
```

I don't know much about GTK, but since cguicrap is not initialised, cguicrap.temperature is not what you think it is.

---

### Post by xtjacob on 2012-04-24
Ughhh, GTK is confusing... I have tried passing the stucture on as a whole, but then I get problems with the button and the textbox...

```
  g_signal_connect(GTK_BUTTON(button), "clicked", G_CALLBACK(button_clicked), gguicrap);
```

---

