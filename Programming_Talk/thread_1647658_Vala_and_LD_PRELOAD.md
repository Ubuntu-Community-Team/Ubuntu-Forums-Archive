---
title: "Vala and LD_PRELOAD"
date: 2010-12-17
forum: Programming Talk
---

### Post by Hornet.ch on 2010-12-17
Hi

I'm new to Vala and doing a small project for myself. What I want to do is overriding the GtkFileChooserDialog with a custom Dialog. I already found some sample code written in C using LD_PRELOAD. I tried to translate the code pieces to Vala and came up with code like this:

```

Widget* gtk_file_chooser_dialog_new (char* title, Window* parent, FileChooserAction action, char* first_button_text, ...) {
	Widget* widget = new MyCustomDialog();
	return widget;
}

```

I did the same for all the other gtk_file_chooser_* functions. The problem now is, that the Vala source compiles, but the generated C code can't be compiled because of the following error:

/usr/include/gtk-2.0/gtk/gtkfilechooserdialog.h:57: note: previous declaration of ‘gtk_file_chooser_dialog_new’ was here

Now my question:
Is it even possible to do something like this in Vala, or do I have to hack something in C? If yes, what did I do wrong?

Greetings
Hornet

---

