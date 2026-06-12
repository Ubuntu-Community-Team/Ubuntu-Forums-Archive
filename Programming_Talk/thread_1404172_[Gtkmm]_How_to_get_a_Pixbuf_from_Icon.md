---
title: "[Gtkmm] How to get a Pixbuf from Icon?"
date: 2010-02-11
forum: Programming Talk
---

### Post by kahumba on 2010-02-11
Hi,
I'm trying to paint the icon of a file in a table (treeview).
The Gtk::TreeView needs a Glib::RefPtr<Gdk:: Pixbuf> to render an icon.
But I get a Glib::RefPtr<Gio::Icon> instead when querying the a file for its icon, this is where I'm stuck:

```

Glib::RefPtr<Gio::File> gioFile = Gio::File::create_for_path(sPath);
Glib::RefPtr<FileInfo> info = gioFile->query_info();
Glib::RefPtr<Gio::Icon> icon = info->get_icon();

```..Now what? How do I get a Pixbuf from this icon?

A snippet would be greatly appreciated.

---

### Post by SledgeHammer_999 on 2010-02-11
As far as I can tell from the gtk docs a GIcon is not used to load and display an icon. It is used for other things. I would recommentd to use one of these:

[static Glib::RefPtr<Pixbuf> create_from_file (const std::string&  filename)](http://library.gnome.org/devel/gtkmm/unstable/classGdk_1_1Pixbuf.html#a20d7a2a52dab246e4bb758ecba38e4ca)
[static Glib::RefPtr<Pixbuf> create_from_file (const std::string&  filename, int width, int height, bool preserve_aspect_ratio=true)](http://library.gnome.org/devel/gtkmm/unstable/classGdk_1_1Pixbuf.html#a5000775e43142f3e764ba64236c95d47)

---

### Post by kahumba on 2010-02-11
My code is about getting the icon/image associated with a given file, i.e. those icons/images you see in the file browser next to each file name. As you can see from my sample code it's what I'm trying to achieve, but I'm stuck figuring out how to make the icon into a Pixbuf cause that's what the TreeView class requires to display an image.

---

### Post by SledgeHammer_999 on 2010-02-11
And the docs are saying that the thing that you are trying to achieve is out of the scope of Gio::Icon. Directly from the Gtk+ docs
> GIcon is a very minimal interface for icons. It provides functions for checking the equality of two icons, hashing of icons and serializing an icon to and from strings.

GIcon **does not provide the actual pixmap** for the icon as this is out of GIO's scope, however implementations of GIcon may contain the name of an icon (see GThemedIcon), or the path to an icon (see GLoadableIcon). 

link-->[http://library.gnome.org/devel/gio/stable/GIcon.html](http://library.gnome.org/devel/gio/stable/GIcon.html)

The links I gave to you, provide you with a Gdk::Pixbuf that you can use it with the Treeview(maybe it automatically resizes the pixbuf).

---

### Post by kahumba on 2010-02-11
There must be some "bridge" (whatever solution that may be) to get the icon (mimetype-icon) associated with a given file/folder in the filesystem. See screenshot, those are the icons I mean and Pixbuf has no means to grab them. And Gtk+ specifies that one can access them (only) by querying the FileInfo class of a Gio::File, that's what I'm doing, but, after I grab those icons I need to transform them into a Pixbuf to be able to display them in my GUI. That's my problem.
Do you know how to do that or do you know any other way to achieve this?

(again, it's not the typical case of loading an image file)

---

### Post by SledgeHammer_999 on 2010-02-11
Hmmm now I understand you. I thought that the file that you access is an actual image. Instead, you want the icon that is associated with the file type. I currently have no solution. I will give it some thought and I will report back I find something.

---

### Post by SledgeHammer_999 on 2010-02-11
I think I found a solution for you. For the column that displays the icons use a CellRenderer. Specifically a Gtk::CellRendererPixbuf. Then use it's [Gtk::CellRendererPixbuf::property_gicon](http://library.gnome.org/devel/gtkmm/unstable/classGtk_1_1CellRendererPixbuf.html#a78c7ab185e9c5c4cb636ff052fe56ffe) to set a gicon for each row.

On how to specify a specific property's value of a CellRenderer for each row dynamically read here:[http://library.gnome.org/devel/gtkmm-tutorial/unstable/sec-treeview.html.en](http://library.gnome.org/devel/gtkmm-tutorial/unstable/sec-treeview.html.en) If you have questions on that feel free to ask.

---

### Post by kahumba on 2010-02-15
Thanks, but I couldn't create a working solution so I came up with this one:
```

Glib::RefPtr<Gdk::Pixbuf> Info::getPixbuf(File *f) {
    //File is a custom class
    static Glib::RefPtr<Gtk::IconTheme> iconTheme = Gtk::IconTheme::get_default();
    Glib::ustring sPath = Glib::build_filename(f->getDirPath(), f->getName());
    Glib::RefPtr<Gio::File> gioFile = Gio::File::create_for_path(sPath);
    Glib::RefPtr<Gio::FileInfo> info = gioFile->query_info();
    Glib::RefPtr<Gio::Icon> icon = info->get_icon();
    //getIconSize() a custom function returning the desired size
    Gtk::IconInfo iconInfo = iconTheme->lookup_icon(icon, getIconSize(), Gtk::ICON_LOOKUP_USE_BUILTIN);
    return iconInfo.load_icon();
}

```

---

