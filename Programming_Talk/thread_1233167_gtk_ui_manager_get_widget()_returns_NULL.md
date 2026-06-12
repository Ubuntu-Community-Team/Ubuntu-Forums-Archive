---
title: "gtk_ui_manager_get_widget() returns NULL"
date: 2009-08-06
forum: Programming Talk
---

### Post by swappo1 on 2009-08-06
Here is my function:
```
GtkWidget *create_menu_bar(GtkWidget *window)
{
	GtkActionGroup *actiongroup;	/*construct a group of actions*/
	GtkUIManager *ui_manager;	/*construct menus and toolbars from an XML description*/
	
	actiongroup = gtk_action_group_new("MainwindowActiongroup");	/*create actiongroup object*/
	/*create a number of actions and add them to the actiongroup*/
	gtk_action_group_add_actions(actiongroup, mainwindow_action_entries, G_N_ELEMENTS(mainwindow_action_entries), NULL);
	
	ui_manager = gtk_ui_manager_new();	/*create a new ui_manager object*/
	gtk_ui_manager_insert_action_group(ui_manager, actiongroup, 0);/*inserts an actiongroup into
	*	the list of actiongroups associated with ui_manager*/
	/*parses a string containg a UI Definition and merges it with the current contents of ui_manager*/
	
	gtk_ui_manager_add_ui_from_string(ui_manager,
		"<ui>"
		"  <menubar name='MainMenu'>"
		"    <menu action='FileMenu'>"
		"      <menuitem action='OpenFile'/>"
		"      <separator name='fsep1'/>"
		"      <menuitem action='SaveFile'/>"
		"    </menu>"
		"    <menu action='EditMenu'>"
		"      <menuitem action='Cut'/>"
		"      <separator name='fsep1'/>"
		"      <menuitem action='Copy'/>"
		"      <separator name='fsep1'/>"
		"      <menuitem action='Paste'/>"
		"    </menu>"
		"    <menu action='HelpAbout'>"
		"      <menuitem action='About'>"
		"    </menu>"
		"  </menubar>"
		"</ui>", -1, NULL);
		
	if(gtk_ui_manager_get_widget(ui_manager, "/ui/MainMenu") == NULL)
		printf("returns NULL\n");
	return 0;
}
```
ui_manager returns non NULL so I am thinking it is my path, "/ui/MainMenu" that is the problem.  I need for this to return a widget.  Any ideas?

---

### Post by SledgeHammer_999 on 2009-08-06
i think you should ommit "/ui" in the path:
[php]if(gtk_ui_manager_get_widget(ui_manager, "/MainMenu") == NULL)[/php]

---

### Post by swappo1 on 2009-08-06
I tried that and it doesn't work.

---

### Post by SledgeHammer_999 on 2009-08-06
on top of my previous recommendation, you have forgotten to close a menuitem:
[php]"      <menuitem action='About'/>"[/php]
maybe this causes a parse error. doesn't ui_manager output errors/warnings in the terminal?

---

### Post by swappo1 on 2009-08-06
The problem was the xml error you pointed out.  I didn't realize that an error there would cause the function to return NULL, otherwise I would have looked more closely at that part.

---

