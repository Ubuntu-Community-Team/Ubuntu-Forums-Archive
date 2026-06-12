---
title: "[C/Gtk] Setting an Icon for a GtkWidget"
date: 2012-05-11
forum: Programming Talk
---

### Post by dodle on 2012-05-11
I'm trying to create a plugin for lxpanel but I know nothing about Gtk development. I've read over [how to write plugins for lxpanel](http://wiki.lxde.org/en/How_to_write_plugins_for_LXPanel) and am trying to add on to the code. In place of showing text on the widget, I want to display an icon.

[php]trash_constructor(Plugin * p, char ** fp)
{
 /* fp is a pointer to the configuration file stream
     since we don't use it, we'll make sure it doesn't
     give us an error at compilation time */
 (void)fp;

 // allocate our private structure instance
 Trash *pTrash = g_new0(Trash, 1);

 // put it where it belongs
 p->priv = pTrash;

 // update the instance count
 pTrash->iMyId = ++iInstanceCount;

 // make a label out of the ID
 //char cIdBuf[10] = {'\0'};

 //sprintf(cIdBuf, "TP-%d", pTrash->iMyId);

 //GtkWidget *pLabel = gtk_label_new("Trash");
 
 // !!! Here I am trying to create an icon
 GdkPixmap *pIcon = gdk_image_new("test.png");

 // need to create a widget to show
 p->pwid = gtk_event_box_new();

 // set border width
 gtk_container_set_border_width(GTK_CONTAINER(p->pwid), 1);

 // add the label to the container
 //gtk_container_add(GTK_CONTAINER(p->pwid), GTK_WIDGET(pLabel));
 
 // !!! Add an icon to the container
 // How can I do this?
 gtk_container_add(GTK_CONTAINER(p->pwid), ?????));

 // set the size we want
 gtk_widget_set_size_request(p->pwid, 40, 25);

 // our widget doesn't have a window...
 gtk_widget_set_has_window(p->pwid, FALSE);

 // show our widget
 gtk_widget_show_all(p->pwid);

 // success!!!
 return 1;
}[/php]

---

