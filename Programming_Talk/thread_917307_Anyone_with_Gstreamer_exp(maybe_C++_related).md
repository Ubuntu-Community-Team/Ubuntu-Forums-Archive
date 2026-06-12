---
title: "Anyone with Gstreamer exp?(maybe C++ related)"
date: 2008-09-11
forum: Programming Talk
---

### Post by SledgeHammer_999 on 2008-09-11
I am experimenting with gstreamer and gtkmm, thus I am mixing C and C++. I have a particular problem. These are the code snippets:

main_window.h
[php]
#include <gst/gst.h>
class main_window: public Gtk::Window
{ 
...
   protected:
         void play_file();
         static bool feature_filter(GstPlugin *plugin, main_window *data);
...
};[/php]

main_window.cpp
[php]
#include "main_window.h"

void main_window::play_file()
{
    GList* lst;
    lst = gst_registry_plugin_filter(gst_registry_get_default(), (GstPluginFilter) feature_filter, false, this);
    gst_plugin_list_free(lst);
}

bool main_window::feature_filter(GstPlugin *plugin, main_window *data)
{
    const gchar* name = gst_plugin_get_name(plugin);
    GstElementFactory* factory = gst_element_factory_find(name);
    g_print("i found something");
    const gchar* klass = gst_element_factory_get_klass(factory);
    gst_object_unref (GST_OBJECT(factory));
    if (g_strrstr(klass, "Demuxer") != NULL) return true;
    return false;
}[/php]

The function gst_registry_plugin_filter() calls main_window::feature_filter() and builds a GList*. The problem lies within main_window::feature_filter(). The program hangs forever trying to execute this line **GstElementFactory* factory = gst_element_factory_find(name);**. I know because the "g_print" never gets called. During this hanging time there is no cpu activity it just sits there. If I put the almost same line **GstElementFactory* factory = gst_element_factory_find("avidemux");** in main_window::play_file() the function is called without problems.

PS. even if I change name to "avidemux" the command hungs in main_window::feature_filter()

Is this a problem with mixing C and C++? Is this a problem of Gstreamer? Did I forget something? (and yes I am noob).

---

### Post by SledgeHammer_999 on 2008-09-12
Bump

---

### Post by SledgeHammer_999 on 2008-09-12
I got the answer from irc (#gstreamer)--->__tim: you can't use gst_element_factory_find() from within a feature filter, it probably tries to take the default registry's lock again (which is already taken when your callback is called)

---

