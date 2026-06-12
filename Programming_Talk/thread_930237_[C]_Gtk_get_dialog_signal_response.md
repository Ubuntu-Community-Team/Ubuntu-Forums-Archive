---
title: "[C] Gtk get dialog signal response"
date: 2008-09-25
forum: Programming Talk
---

### Post by mike_g on 2008-09-25
I have a popup file selection dialog with a signal connected to it. When the signal function is called I need to be able to find out what to do.

There is a set of response type enumerators [here](http://library.gnome.org/devel/gtk/stable/GtkDialog.html#GtkResponseType) but I cant figure out how to get what the response was in my callback function. 

Heres an example that might help show what I am trying to do:
```
void handle_load_response(GtkWidget *dialog)
{
	/* here I want to get the response and do something like: */
	if(response == GTK_RESPONSE_OK)
	{
		//do something		
	}
	gtk_widget_destroy(dialog);
	
}

void load_config()
{
	GtkWidget *dialog = gtk_file_chooser_dialog_new("Open File",
				      GTK_WINDOW(window),
				      GTK_FILE_CHOOSER_ACTION_OPEN,
				      GTK_STOCK_CANCEL, GTK_RESPONSE_CANCEL,
				      GTK_STOCK_OPEN, GTK_RESPONSE_ACCEPT,
				      NULL);
   
	g_signal_connect(dialog,
                     "response", 
                     G_CALLBACK(handle_load_response),
                     dialog);

	gtk_widget_show_all(dialog);
}
```
Anyone know how I should go about getting the signal response?

Cheers.

---

### Post by mike_g on 2008-09-27
bump o_O

---

### Post by slavik on 2008-09-27
you have to look at the widget's value (you ahve to explicitly look it up).

---

### Post by nvteighen on 2008-09-27
I'd do the following:
```
[color=#B00040]void[/color] [color=#0000FF]load_config[/color]([color=#B00040]void[/color])
{
    GtkWidget [color=#666666]*[/color]dialog [color=#666666]=[/color] 
        gtk_file_chooser_dialog_new([color=#BA2121]"Open File"[/color],
                                    GTK_WINDOW(window),
                                    GTK_FILE_CHOOSER_ACTION_OPEN,
                                    GTK_STOCK_CANCEL, GTK_RESPONSE_CANCEL,
                                    GTK_STOCK_OPEN, GTK_RESPONSE_ACCEPT,
                                    [color=#008000]NULL[/color]);
   
    [color=#008000]**if**[/color](gtk_dialog_run(GTK_DIALOG(dialog)) [color=#666666]==[/color] GTK_RESPONSE_OK)
    {
        [color=#408080]*/* do something... call a function if you want to keep things tidy. */*[/color]
    }

    gtk_widget_destroy(dialog);
}

```

---

### Post by mike_g on 2008-09-28
Thanks guys. I decided that doing GUI stuff in C was becoming too tedious, so I'm learning python with pygtk atm; its a lot simpler. But I'll remember this in case I get back to using Gtk w/ C sometime :)

---

