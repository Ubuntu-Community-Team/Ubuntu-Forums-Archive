---
title: "Clipboard: detect cut or copy"
date: 2013-04-15
forum: Programming Talk
---

### Post by bird1500 on 2013-04-15
Hi,
I'm using Gtk's Clipboard class (Gtk::Clipboard::get()), I can get the list of URI's in the clipboard (clipboard->wait_for_uris()) but can't figure out **how to detect if the file URIs have been "cut" or "copied" (in a foreign app e.g. nautilus)** - to know how to treat the URIs on "Paste" in my GUI app: should I delete the original files (cut), or leave them (copy).

---

### Post by bird1500 on 2013-04-15
Well it looks like it's a mess, the Thunar source code uses a "special gnome copied files" atom and a slew of hooks, gee, I hoped for an easy solution.

thunar-clipboard-manager.c:
```

struct _ThunarClipboardManager
{
  GObject __parent__;

  GtkClipboard *clipboard;
  gboolean      can_paste;
  GdkAtom       x_special_gnome_copied_files;

  gboolean      files_cutted;
  GList        *files;
};

typedef struct
{
  ThunarClipboardManager *manager;
  GFile                  *target_file;
  GtkWidget              *widget;
  GClosure               *new_files_closure;
} ThunarClipboardPasteRequest;



static const GtkTargetEntry clipboard_targets[] =
{
  { "text/uri-list", 0, TARGET_TEXT_URI_LIST },
  { "x-special/gnome-copied-files", 0, TARGET_GNOME_COPIED_FILES },
  { "UTF8_STRING", 0, TARGET_UTF8_STRING }
};

```

And more info found [here]("http://qt-project.org/doc/qt-4.8/qclipboard.html"):
> Since there is no standard way to copy and paste files between  applications on X11, various MIME types and conventions are currently in  use. For instance, Nautilus expects files to be supplied with a x-special/gnome-copied-files MIME type with data beginning with the cut/copy action, a newline character, and the URL of the file.

I guess it's because they never dared fixing X11, only working around it, but that's another story.

---

