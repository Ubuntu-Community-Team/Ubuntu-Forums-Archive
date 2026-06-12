---
title: "[problem] Using GDL"
date: 2009-11-02
forum: Programming Talk
---

### Post by Tomato-kun on 2009-11-02
Hello.

I have a little trouble using GDL.
When i try to unbind item from dock using gdl_dock_item_unbind() i have a couple of warnings:
```

(name:22467): GLib-GObject-WARNING **: invalid uninstantiatable type `-g-type-private--GTypeFlags' in cast to `GtkContainer'
(name:22467): Gtk-CRITICAL **: _gtk_container_queue_resize: assertion `GTK_IS_CONTAINER (container)' failed
(name:22467): GLib-GObject-WARNING **: invalid uninstantiatable type `-g-type-private--GTypeFlags' in cast to `GObject'
(name:22467): GLib-GObject-CRITICAL **: g_object_get_qdata: assertion `G_IS_OBJECT (object)' failed
(name:22467): GLib-GObject-WARNING **: invalid uninstantiatable type `-g-type-private--GTypeFlags' in cast to `GtkObject'
(name:22467): GLib-GObject-WARNING **: invalid uninstantiatable type `-g-type-private--GTypeFlags' in cast to `GtkObject'

```Does it normally? Or it's my fault? Examples coming with gdl sources also provide such warnings on execution.

Thanks.

---

### Post by Tomato-kun on 2009-11-03
hm... steel no ideas...

---

### Post by Tomato-kun on 2009-11-03
i've just change some code and it works... but it seems another warning %)
```

GtkWidget *item = gdl_dock_item_new("name", "human_name", GDL_DOCK_ITEM_BEH_NORMAL);

```
i've added
```

g_object_ref(item);

```
because, as i look throught gdl library code, it unrefs dock object.
q: have i ref/unref GdlDock creation? like
```

GtkWidget *dock = gdl_dock_new();
g_object_ref(dock);

```

upd: warning message
```

(name:19662): Gdl-CRITICAL **: gdl_dock_master_get_controller: assertion `master != NULL' failed

```

---

### Post by Tomato-kun on 2009-11-05
hm. have no problems any more.
i've just add
```

g_object_ref(master);

```
after.
```

GdlDockMaster *master = GDL_DOCK_OBJECT_GET_MASTER(widgets.dock);

```

---

