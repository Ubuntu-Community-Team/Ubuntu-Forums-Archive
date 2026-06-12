---
title: "GTk :adding menu tray to pidgin"
date: 2008-03-22
forum: Programming Talk
---

### Post by ELiz on 2008-03-22
Hi...

I used the following functions to try creating a menu tray....But it seems i am not gettin any output... I dnt get any errors anyways...

static void new_menu_cb()
{
 

GtkWidget *menuitem; 
 PidginBuddyList *blist ;
 menuitem=gtk_menu_item_new_with_label("Start Class");
      pidgin_menu_tray_append(PIDGIN_MENU_TRAY(blist->menutray->parent),menuite                m,NULL);
}

GtkWidget *
pidgin_menu_tray_new() {
	return g_object_new(PIDGIN_TYPE_MENU_TRAY, NULL);
}

GtkWidget *
pidgin_menu_tray_get_box(PidginMenuTray *menu_tray) {
	g_return_val_if_fail(PIDGIN_IS_MENU_TRAY(menu_tray), NULL);
	return menu_tray->tray;
}


static void
pidgin_menu_tray_add(PidginMenuTray *menu_tray, GtkWidget *widget,
					   const char *tooltip, gboolean prepend)
{
	g_return_if_fail(PIDGIN_IS_MENU_TRAY(menu_tray));
	g_return_if_fail(GTK_IS_WIDGET(widget));

	if (GTK_WIDGET_NO_WINDOW(widget))
	{
		GtkWidget *event;

		event = gtk_event_box_new();
		gtk_container_add(GTK_CONTAINER(event), widget);
		gtk_widget_show(event);
		widget = event;
	}

	

		gtk_box_pack_end(GTK_BOX(menu_tray->tray), widget, FALSE, FALSE, 0);
}

static gboolean
plugin_load(PurplePlugin *plugin) {
   
   purple_signal_connect(purple_plugins_get_handle(), "plugin-load", plugin, PURPLE_CALLBACK(new_menu_cb), NULL);
    return TRUE;
}

what modifications should i make in my program???? Any idea???
Eliz

---

