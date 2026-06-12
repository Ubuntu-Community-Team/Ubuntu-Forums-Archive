---
title: "gtk+ structure member problem"
date: 2009-10-13
forum: Programming Talk
---

### Post by swappo1 on 2009-10-13
Hello,

I am having trouble with setting gchar *filename to gchar *file_name where gchar *file_name is a member of a structure FileInfo and struct FileInfo is a nested struct of PublicData.  Here is my code:
```

structure from window.h

typedef struct
{
	gboolean FILE_FLAG;
	gchar *file_name;
}FileInfo;

signals.c

void save_file_as(GtkButton *save, MainWin *mw, FileInfo *fi)
{
	GtkWidget *dialog;
	GtkTextIter start, end;
	gchar *filename, *content;
	gint result;
	
	dialog = gtk_file_chooser_dialog_new("Save As...", NULL,
							GTK_FILE_CHOOSER_ACTION_SAVE, GTK_STOCK_OK,
							GTK_RESPONSE_ACCEPT, GTK_STOCK_CANCEL,
							GTK_RESPONSE_CANCEL, NULL);
	
	result = gtk_dialog_run(GTK_DIALOG(dialog));
	
	if(result == GTK_RESPONSE_ACCEPT)
	{
		filename = gtk_file_chooser_get_filename(GTK_FILE_CHOOSER(dialog));
		gtk_text_buffer_get_bounds(mw->buffer, &start, &end);
		content = gtk_text_buffer_get_text(mw->buffer, &start, &end, FALSE);
		g_file_set_contents(filename, content, -1, NULL);
		fi->FILE_FLAG = TRUE;
		fi->file_name = filename;
		g_free(filename);
		g_free(content);
	}
		
	gtk_widget_destroy(dialog);
}

```


Here is the output from when I hit the save as button. 
```
(codepad2:10842): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(codepad2:10842): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(codepad2:10842): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(codepad2:10842): GLib-GObject-CRITICAL **: g_object_get_qdata: assertion `G_IS_OBJECT (object)' failed
Segmentation fault

```

If I print filename to screen, I get the path to the file.  I initially have fi->file_name set to NULL.  When I try to print fi->file_name to screen, I get a segmentation fault.  I am not sure what is going on with fi->file_name.

---

### Post by MadCow108 on 2009-10-13
```

fi->file_name = filename;
g_free(filename);

```
here you copy the filename pointer to fi->file_name pointer and the deleting the content filename (and fi->file_name) points to.
The result is that both pointers are invalid.
the next thing that tries to dereference fi->file_name or filename will produce a segfault

use g_strdup to allocate a copy of filename and assign that to fi->file_name
(or don't free filename in the first place if thats ok in your application)

---

### Post by swappo1 on 2009-10-13
```
fi->file_name = g_strdup(filename);
		g_free(filename);
		g_free(content);
```
fi->file_name is now storing the filename.  However, I am still getting the errors previously.  If I comment out, fi->file_name = g_strdup(filename);, I no longer get the errors, so there is still a problem with this statement.

---

### Post by MadCow108 on 2009-10-13
use a debugger (like gdb) to track the exact cause of the problem
[http://dirac.org/linux/gdb/](http://dirac.org/linux/gdb/)

---

