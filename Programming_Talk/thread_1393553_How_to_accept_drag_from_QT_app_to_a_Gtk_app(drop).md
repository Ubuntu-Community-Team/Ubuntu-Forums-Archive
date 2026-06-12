---
title: "How to accept drag from QT app to a Gtk app(drop)?"
date: 2010-01-29
forum: Programming Talk
---

### Post by SledgeHammer_999 on 2010-01-29
I am trying to make a program in Gtk(gtkmm) that opens files through drag'n'drop. The program works fine if I drag a file from a Gtk app like Nautilus or Thunar(file managers). But when I try the same thing from Dolphin(KDE's file manager) the cursor's icon DOESN'T even change to indicate that my program can accept a drop. I used the same procedure with Dolphin+Totem and it worked. I tried viewing totem's source and I think I do the same thing with my program.

Anyway, here is an example program:
[php]
#include <gtkmm.h>


class main_window: public Gtk::Window
{

public:
  main_window();
  virtual ~main_window();

protected:
  void handle_dnd_file(const Glib::RefPtr<Gdk::DragContext>& context, int x, int y, const Gtk::SelectionData& selection_data, guint info, guint time);

  Gtk::Label label;
};


main_window::main_window()
{
  add(label);
  show_all();

  std::list<Gtk::TargetEntry> listTargets;
  listTargets.push_back(Gtk::TargetEntry("text/uri-list"));
  drag_dest_set(listTargets, Gtk::DEST_DEFAULT_MOTION | Gtk::DEST_DEFAULT_DROP);
  signal_drag_data_received().connect(sigc::mem_fun(*this, &main_window::handle_dnd_file));

  resize(350,350);
}

main_window::~main_window()
{
}

void main_window::handle_dnd_file(const Glib::RefPtr<Gdk::DragContext>& context, int x, int y, const Gtk::SelectionData& selection_data, guint info, guint time)
{
  if ((selection_data.get_length() >= 0) && (selection_data.get_format() == 8))
    {
      std::vector<Glib::ustring> file_list;

      file_list = selection_data.get_uris();

      if (file_list.size() > 0)
        {
          label.set_label(Glib::filename_from_uri(file_list[0]));
          context->drag_finish(true, false, time);
          return;
        }
    }

  context->drag_finish(false, false, time);
}

int main(int argc, char *argv[])
{
  Gtk::Main main_loop(argc, argv);

  main_window window;

  main_loop.run(window);

  return 0;
}
[/php]

Compile with:
```
g++ main.cpp -o test `pkg-config gtkmm-2.4 --libs --cflags`
```

Drag and drop a file on the window. The window contains a Gtk::Label, which will change to reflect the path to the file you dropped. As you will see nothing happens if you drop a file from Dolphin.

Did I forget something in my code? Plz share any ideas, even if they don't help directly with my problem.

---

### Post by SledgeHammer_999 on 2010-01-30
bump

---

### Post by bmcage on 2010-02-28
Did you find a solution?
I am trying to make this work in Gramps media view.
I discovered that drag and drop from amarok folder view works, but not from konqueror/dolphin.
So my conclusion is that it is a dolphin error, specifically in their drop code.

---

### Post by bmcage on 2010-02-28
I opened a bug on the tracker for this, let's see what they reply: 
[https://bugs.kde.org/show_bug.cgi?id=228891](https://bugs.kde.org/show_bug.cgi?id=228891)

---

### Post by SledgeHammer_999 on 2010-02-28
You better close that bug. I had filed a bug with gtk until I found yesterday(what a coincidence) the solution.

I have posted an entire blog post [here](http://hammered999.wordpress.com/2010/02/28/how-to-accept-a-drag-and-drop-ped-file-in-your-gtkmm-application/). I made that blog in order to post similar problem/solutions in the future, so if you want keep an eye on it.

The bottom line is that you need to use "Gdk::ACTION_COPY | Gdk::ACTION_MOVE" in the third parameter of drag_dest_set(). (*MOVE being the missing part of the puzzle)

---

### Post by bmcage on 2010-03-01
Ok, I'm trying it now. I'll let you know if I can make it work on python (pygtk here). 
Note that the old code works fine on windows with explorer

---

### Post by bmcage on 2010-03-01
Ok, it works also for me with the MOVE, but icon does not update a lot of the time if I use the DEST_DEFAULT_ALL, so I removed the HIGHLIGHT from that, and all wors fine. So I end up with:

```
self.list.drag_dest_set(gtk.DEST_DEFAULT_MOTION|gtk.DEST_DEFAULT_DROP, 
                        dnd_types, 
                        gtk.gdk.ACTION_MOVE|gtk.gdk.ACTION_COPY)
```


I updated the bug entry on KDE dolphin with this info. I'll leave it up to them to decide if ACTION_COPY should not suffice

---

