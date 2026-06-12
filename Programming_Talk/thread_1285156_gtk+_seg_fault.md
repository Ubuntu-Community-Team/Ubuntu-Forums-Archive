---
title: "gtk+ seg fault"
date: 2009-10-07
forum: Programming Talk
---

### Post by swappo1 on 2009-10-07
Hello,

I am getting a segmentation fault from the open_file function and I can't figure out what the problem is.  I put a printf statement in and determined that the seg fault is just above it.  Any ideas?

```
#include "menu.h"
#include <stdio.h>

#define NUM_ENTRIES 11
#define RAD_ENTRIES 3



static GtkActionEntry entries[] =
{
	{"File", NULL, "_File", NULL, NULL, NULL},
	{"New", GTK_STOCK_NEW, NULL, NULL,
	"Create a new file", NULL},
	{"Open", GTK_STOCK_OPEN, NULL, NULL,
	"Open an existing file", G_CALLBACK(open_file)},
	{"Save", GTK_STOCK_SAVE, NULL, NULL,
	"Save the current file", NULL},
	{"Edit", NULL, "_Edit", NULL, NULL, NULL},
	{"Undo", GTK_STOCK_UNDO, NULL, NULL,
	"Undo the last change", NULL},
	{"Cut", GTK_STOCK_CUT, NULL, NULL,
	"Cut the selection to the clipboard", NULL},
	{"Copy", GTK_STOCK_COPY, NULL, NULL,
	"Copy the selection to the clipboard", NULL},
	{"Paste", GTK_STOCK_PASTE, NULL, NULL,
	"Paste from the clipboard", NULL},
	{"View", NULL, "_View", NULL, NULL, NULL},
	{"Highlight Mode", NULL, "_Highlight Mode", NULL, NULL, NULL}
};

/*for radio submenu on highlight mode drop down menu*/
static GtkRadioActionEntry radio_entries[] =
{
	{"Plain Text", NULL, "Plain Text", NULL, NULL, 1},
	{"C Text", NULL, "C", NULL, NULL, 2},
	{"C++ Text", NULL, "C++", NULL, NULL, 3},
};

/*this will create the menu and tool bar*/
void create_menu_bar(MainWin *mw)
{
	GtkActionGroup *group;
	GtkUIManager *ui_manager;
		
	group = gtk_action_group_new("MainActionGroup");
	gtk_action_group_add_actions(group, entries, NUM_ENTRIES, NULL);
	/*add a radio submenu onto Highlight Mode*/
	gtk_action_group_add_radio_actions(group, radio_entries,
													RAD_ENTRIES, 1, NULL, NULL); 
	
	ui_manager = gtk_ui_manager_new();
	gtk_ui_manager_insert_action_group(ui_manager, group, 0);
	
	/*add the menu from the xml file to the ui*/
	gtk_ui_manager_add_ui_from_file(ui_manager, "menu.ui", NULL);
	/*return the widget found by path /MenuBar*/
	mw->menu_bar = gtk_ui_manager_get_widget(ui_manager, "/MenuBar");
	
	gtk_ui_manager_add_ui_from_file(ui_manager, "toolbar.ui", NULL);
	/*	return the widget found by the path /ToolBar*/
	mw->tool_bar = gtk_ui_manager_get_widget(ui_manager, "/ToolBar");
	
	gtk_window_add_accel_group(GTK_WINDOW(mw->window), 
								gtk_ui_manager_get_accel_group(ui_manager));
}

GtkWidget *create_find()
{
	GtkWidget *entry, *hbox, *button;
	
	entry = gtk_entry_new();
	button = gtk_button_new_from_stock(GTK_STOCK_FIND);
	hbox = gtk_hbox_new(FALSE, 0);
	gtk_box_pack_start(GTK_BOX(hbox), button, FALSE, FALSE, 0);
	gtk_box_pack_start(GTK_BOX(hbox), entry, FALSE, FALSE, 0);
	
	return hbox;
}

static void open_file(GtkButton *open, MainWin *mw)
{
	GtkWidget *dialog;
	gchar *filename, *content;
	gint result;
	
	dialog = gtk_file_chooser_dialog_new("Open File", NULL, 
								GTK_FILE_CHOOSER_ACTION_OPEN, GTK_STOCK_OK,
								GTK_RESPONSE_ACCEPT, GTK_STOCK_CANCEL,
								GTK_RESPONSE_CANCEL, NULL);
	
	result = gtk_dialog_run(GTK_DIALOG(dialog));
	
	if(result == GTK_RESPONSE_ACCEPT)
	{
		
		filename = gtk_file_chooser_get_filename(GTK_FILE_CHOOSER(dialog));
		
		if(g_file_get_contents(filename, &content, NULL, NULL))
		{
			
			mw->buffer = gtk_text_view_get_buffer(GTK_TEXT_VIEW(mw->text_view));
			printf("ok\n");
			gtk_text_buffer_set_text(mw->buffer, content, -1);
			
			g_free(filename);
			g_free(content);
		}
	}

	gtk_widget_destroy(dialog);
}

```

---

### Post by dwhitney67 on 2009-10-07
Compile your source code file(s) with the -g option.

Then run your app in the debugger.

---

### Post by swappo1 on 2009-10-07
> Compile your source code file(s) with the -g option.

Then run your app in the debugger.
Can you explain this in more detail?  Where should I put -g option?  I'm assuming this goes in my Makefile.  Sorry for my ignorance, but I've never used the debugger and am not at all familiar with it.

---

### Post by Zugzwang on 2009-10-07
> **swappo1 said:**
> Can you explain this in more detail?  Where should I put -g option?  I'm assuming this goes in my Makefile.  Sorry for my ignorance, but I've never used the debugger and am not at all familiar with it.

Here's a small introduction: [http://www.ibm.com/developerworks/library/l-gdb/]("http://www.ibm.com/developerworks/library/l-gdb/")

There are also alternatives to the command-line debugger "gdb" (i.e., graphical front-ends), but for the time being, that article should tell you a little bit about the basics.

---

### Post by dwhitney67 on 2009-10-07
And if you are into GUIs, you may want to consider installing/using "ddd", which is a front-end to "gdb".

Once you have compiled your code with the -g option, you can launch gdb or ddd in a similar fashion.
```

gdb myprogram

# or

ddd myprogram &

```

---

### Post by swappo1 on 2009-10-08
> Here's a small introduction: [http://www.ibm.com/developerworks/library/l-gdb/](http://www.ibm.com/developerworks/library/l-gdb/)
I am having a problem running the example program in gdb.  Here is my output.

```
hopchewer@hopchewer:~/Programming/C_programs$ gcc -g gdb_ex.c -o gdb_ex
hopchewer@hopchewer:~/Programming/C_programs$ gdb gdb_ex
GNU gdb 6.8-debian
Copyright (C) 2008 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
---Type <return> to continue, or q <return> to quit---
This GDB was configured as "x86_64-linux-gnu"...
(gdb) print no1
No symbol "no1" in current context.
(gdb) 

```

It seems that the program is not being run in gdb when I type gdb gdb_ex.  According to the example, when I type gdb filename I should get the following.
```
Program received signal SIGFPE, Arithmetic exception.
0x80483ea in wib (no1=8, no2=8) at eg1.c:7
7         result = no1 / diff;
(gdb) 

```
Is there anything I need to do to gdb in addition to installing it to set it up?

---

### Post by dwhitney67 on 2009-10-08
I believe your issue occurred because you have yet to run the program.  Simply running gdb is not sufficient.  Do the following after launching gdb...

Set a breakpoint, at main()
```

b main

```
Then run the program:
```

r

```
Then single-step until you find the line of interest:
```

n

```
If you need to traverse into a function:
```

s

```
All this would be much easier if you were to use "ddd", which is a GUI front-end to "gdb".

---

### Post by MadCow108 on 2009-10-08
you still need to run it in gdb
type run into the gdb prompt
it also takes arguments like the command line

a very useful command is: backtrace
it will show you a call stack where you can exactly see where the segfault occurs without having to set breakpoints

---

