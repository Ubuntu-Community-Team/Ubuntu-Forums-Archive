---
title: "Help with GTK+-3.0"
date: 2012-01-06
forum: Programming Talk
---

### Post by madhater on 2012-01-06
Hi All. 

I am currently writing a basic text editor using gtk+-3.0 and C language for my Duke of Edinburgh's Silver award. 

I have set up eclipse IDE so that it will compile gtk+-3.0 applications. However I get the following error when I compile the code: 


Building target: james-edit
Invoking: GCC C Linker
gcc  -o"james-edit(eclipse-only)"  ./src/main.o    `pkg-config --libs --cflags gtk+-3.0`
./src/main.o: In function `func_open_dialog':
/home/james/workspace/james-edit (eclipse-only)/Debug/../src/main.c:151: undefined reference to `open_file'
collect2: ld returned 1 exit status
make: *** [james-edit(eclipse-only)] Error 1

The error is to do with the following function: 


```
void func_open_dialog(void)
{
	GtkWidget *open_dialog;
	 open_dialog = gtk_recent_chooser_dialog_new  ("Open",
													 NULL,
	                GTK_STOCK_CANCEL, GTK_RESPONSE_CANCEL,
	                  GTK_STOCK_OPEN, GTK_RESPONSE_ACCEPT,
													NULL);

	  if (gtk_dialog_run (GTK_DIALOG (open_dialog)) == GTK_RESPONSE_ACCEPT)
	  {
	    GtkRecentInfo *info;

	    info = gtk_recent_chooser_get_current_item (GTK_RECENT_CHOOSER (open_dialog));
	    open_file (gtk_recent_info_get_uri (info));
	    gtk_recent_info_unref (info);
	  }

	gtk_widget_destroy (open_dialog);

}

```

Any help would be appreciated. :D At a guess I would say something to do with the linker, am I not including a header file that should be there?


James

---

### Post by Brandon Williams on 2012-01-06
The linker doesn't care about header files. If you didn't include the right header file, then compile should fail before you get to the linker. I suppose it's possible that the compiler used a bad default function prototype in the absence of the header file, but that is not the most likely problem.

The linker can't find the open_file function. Is it the correct function name? And if so, where is the function defined?

---

### Post by madhater on 2012-01-06
I "borrowed" the code of the gnome developer website. I am afraid I don't know where open_file is defined. As far as I know it was not dropped when gtk+ 3 was released. 

James

---

### Post by Brandon Williams on 2012-01-07
I see now that you used the example from the GtkFileChooserDialog documentation. I don't think that's meant to be a working example. I think it's only meant to show you how the dialog works and that you are meant to provide the open_file function yourself.

---

