---
title: "Resizable Columns gtk+ vala"
date: 2011-06-17
forum: Programming Talk
---

### Post by Gnomy on 2011-06-17
I've been trying to figure out for a couple of days how to get resizable treeview columns in gtk.

This is what I have:

[PHP]using Gtk;

public class TreeViewSample : Window {

    public TreeViewSample () {
        this.title = "Nation List";
        set_default_size (450, 300);
        var view = new TreeView ();
        setup_treeview (view);
        add (view);
        this.destroy.connect (Gtk.main_quit);
    }

    private void setup_treeview (TreeView view) {

        TreeViewColumn tvc_rn = new TreeViewColumn();
        TreeViewColumn tvc_id = new TreeViewColumn();
        TreeViewColumn tvc_ns = new TreeViewColumn();

        tvc_rn.title = "Ruler";
        tvc_rn.resizable = true;

        view.insert_column_with_attributes (-1, tvc_rn.title, new CellRendererText (), "text", 0);

        tvc_id.title = "ID";
        tvc_id.resizable = true;

        view.insert_column_with_attributes (-1, tvc_id.title, new CellRendererText (), "text", 1);

        tvc_ns.title = "Strength";
        tvc_ns.resizable = true;

        view.insert_column_with_attributes (-1, tvc_ns.title, new CellRendererText (), "text", 2);

        var listmodel = new ListStore (4, typeof (string), typeof (string),
                                          typeof (string), typeof (string));
        view.set_model (listmodel);

    }

    public static int main (string[] args) {     
        Gtk.init (ref args);

        var sample = new TreeViewSample ();
        sample.show_all ();
        Gtk.main ();

        return 0;
    }
}[/PHP]

What am I doing wrong :S

---

### Post by cgroza on 2011-06-17
This is what I found in the pygtk documentation:
[http://www.pygtk.org/docs/pygtk/class-gtktreeviewcolumn.html#method-gtktreeviewcolumn--get-fixed-width](http://www.pygtk.org/docs/pygtk/class-gtktreeviewcolumn.html#method-gtktreeviewcolumn--get-fixed-width)

There are a few width getters and setters...

---

