---
title: "Gtk::AboutDialog and close"
date: 2008-09-07
forum: Programming Talk
---

### Post by Emill on 2008-09-07
Hello, I have set up an AboutDialog in Glade and I use c++ and glademm-2.4, gtkmm-2.4.

I can show the dialog with the code:

Gtk::AboutDialog *dialog = 0;
refXml->get_widget("aboutdialog1", dialog);
dialog->show();

But I have no idea how to connect the close button on it to close the dialog.

/Emil

---

### Post by mssever on 2008-09-07
I use the response signal, and call the_dialog.hide() from the signal handler.

---

### Post by nvteighen on 2008-09-07
> **Emill said:**
> 
But I have no idea how to connect the close button on it to close the dialog.


"Prebuilt" GtkDialogs do that automatically. Don't worry: as mssever said, the return value will be defined by the clicked button.

---

### Post by mssever on 2008-09-07
> **nvteighen said:**
> GtkDialogs do that automatically.
They don't in my program, and I've seen several other GTK programs where the close button on the GtkDialog doesn't work. That's why you have to explicitly handle the response signal.

---

### Post by Emill on 2008-09-07
Ok. I don't know exactly how to do it, but when I test with:
Gtk::Dialog *dialog = 0;
refXml->get_widget("aboutdialog1", dialog);
dialog->signal_response().connect(sigc::ptr_fun(dialog->hide));
dialog->show();

I get a compile error. When I test:

Gtk::Dialog *dialog = 0;
refXml->get_widget("aboutdialog1", dialog);
dialog->signal_response().connect(sigc::ptr_fun(dialog_close));
dialog->show();

and then

viod dialog_close(){
 //nothing here
}

I get a compile error in the adaptor_trait.h include file (some sigc lib).

---

### Post by kknd on 2008-09-07
Example:

void your_show_about_callback()
{
    int res = about->run();
    about->hide();
}

You can handle the response code if you want. dialog->run() is blocking, so about->hide() will be called only when the dialog is closed (this is handled automatically, but not hide automatically).

---

### Post by Emill on 2008-09-07
Ok, now it works :)

My final code is:
Gtk::AboutDialog *aboutdialog1 = 0;
refXml->get_widget("aboutdialog1", aboutdialog1);
aboutdialog1->run();
aboutdialog1->hide();

---

### Post by Emill on 2008-09-07
Hmm... When I use that code, the rest of the application locks until I close the AboutDialog. I don't want that.

---

### Post by tseliot on 2008-09-07
Instead of doing aboutdialog1->run() (which locks the application until a response is given) you can connect the response signal emitted by the dialog to a function so that when a user clicks on the button, the dialog is destroyed or hidden. In the following example the dialog is destroyed:

```

g_signal_connect_swapped (dialog, "response",
                           G_CALLBACK (gtk_widget_destroy),
                           dialog);

```

This is how I would do it in C. I *guess* it's the same in C++.

---

### Post by Emill on 2008-09-08
I've tried with:
aboutdialog->signal_response().connect(sigc::ptr_fun(gtk_widget_destroy));

and some other functions instead of gtk_widget_destroy, however, I get a compile error in some adaptor_trait.h header file.

---

### Post by mssever on 2008-09-08
> **Emill said:**
> I've tried with:
aboutdialog->signal_response().connect(sigc::ptr_fun(gtk_widget_destroy));

and some other functions instead of gtk_widget_destroy, however, I get a compile error in some adaptor_trait.h header file.
Please disable smilies in your posts, since they're making your code unreadable. Also, you can use [noparse]```

```[/noparse] tags to improve the legibility of your code.

---

### Post by Emill on 2008-09-08
Is this a bug in the sigc++ header files or is it meant that one can get a compile error in those files?

---

### Post by viciouslime on 2008-09-09
Anybody know how to do this in Ruby?

---

### Post by MeduZa on 2008-11-24
umm I have the same problem, gtkmm don't have the autoconnect C stuff and for that reason (I think) the close button don't work.
There is any way to connect on_click event on the close button?
How we can made the close button to work on c++?

---

### Post by MeduZa on 2008-11-24
> **kknd said:**
> Example:

void your_show_about_callback()
{
    int res = about->run();
    about->hide();
}

You can handle the response code if you want. dialog->run() is blocking, so about->hide() will be called only when the dialog is closed (this is handled automatically, but not hide automatically).

this solution works like charm xD

---

### Post by placidrage on 2009-01-14
First add a new member function to the gtk view object you wrote (let's call it on_about_close), then connect with the following code:

```

aboutdialog->signal_response().connect(sigc::mem_fun(on_about_close));

```

Then write your callback like so:

```

void on_about_close(int response) {
aboutdialog->hide();
}
```

your code didn't work and gave you a compile error because the signal_response sends out an integer value of the response received to the callback, which is gtk_widget_destroy in your code, and that doesn't take any values as it's a method. Hence the need to code a callback that takes that integer as an entry variable. That being said, the AboutDialog widget sends out only the Gtk::RESPONSE_CLOSE response which is in reality nothing but an -7 integer, so no need to analyse the integer you get from the signal. It's only useful for other more complex dialogs with more then one response ID being sent back.

Hope this helps,

Joe R. Nassimian

> **Emill said:**
> I've tried with:
aboutdialog->signal_response().connect(sigc::ptr_fun(gtk_widget_destroy));

and some other functions instead of gtk_widget_destroy, however, I get a compile error in some adaptor_trait.h header file.

---

### Post by placidrage on 2009-01-14
Oops, my bad, I forgot to mention a few stuff, and did a big mistake in the signal connection.

if you're programming in object-oriented, then the previous code means that the callback function is part of the object, but the syntax I gave was wrong, as I forgot to pass the object as an additional argument in the slot.

here is how it's suppose to be written:
```

aboutdialog->signal_response().connect(sigc::mem_fun(*this, on_about_close));

```

And if you're not programming in object-oriented, then you'll have to write a callback still (on_about_close), and use it the same way with the following code:

```

aboutdialog->signal_response().connect(sigc::ptr_fun(on_about_close));

```

Voila, that should be it.

Sorry for the confusing previous post.

Joe R. Nassimian

---

### Post by djtarki on 2010-04-15
> **tseliot said:**
> Instead of doing aboutdialog1->run() (which locks the application until a response is given) you can connect the response signal emitted by the dialog to a function so that when a user clicks on the button, the dialog is destroyed or hidden. In the following example the dialog is destroyed:

```

g_signal_connect_swapped (dialog, "response",
                           G_CALLBACK (gtk_widget_destroy),
                           dialog);

```This is how I would do it in C. I *guess* it's the same in C++.


That worked for me. Thanks very much!

:guitar:

---

