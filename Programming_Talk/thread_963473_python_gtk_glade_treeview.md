---
title: "python gtk glade treeview"
date: 2008-10-30
forum: Programming Talk
---

### Post by sveri on 2008-10-30
hi all,

i am trying to make a little gui for the xmms2 daemon with
python, gtk and glade.
Now i am stuck at making a column in a treeview "clickable"
I mean i want to click on the column to sort that column 
after the strings in there.

I just cannot get it done, no matter what i try.
I found that link on treeviews very helpful:
[http://fabien.seisen.org/python/gtk2/py_treeview_sort.html](http://fabien.seisen.org/python/gtk2/py_treeview_sort.html)
But it doesn't help me either.

This is what i have so far:

```

dic = {...              }
        
self.wTree.signal_autoconnect(dic)

self.tvPlayList = self.wTree.get_widget("tvPlaylist")

column_status = gtk.TreeViewColumn("Status:", gtk.CellRendererText(), text = 0)        
self.tvPlayList.append_column(column_status)
        
column_id = gtk.TreeViewColumn("ID:", gtk.CellRendererText(), text = 1)        
self.tvPlayList.append_column(column_id)
        
column_album = gtk.TreeViewColumn("Album:", gtk.CellRendererText(), text = 2)
column_album.connect("clicked", self.on_album_clicked, 2)        
self.tvPlayList.append_column(column_album)
        
column_title = gtk.TreeViewColumn("Title:", gtk.CellRendererText(), text = 3)
self.tvPlayList.append_column(column_title)
column_title = gtk.TreeViewColumn("Time:", gtk.CellRendererText(), text = 4)
self.tvPlayList.append_column(column_title)
        
self.playList = gtk.ListStore(str, int, str, str, str)
self.playList.set_sort_func(2, self.sort_album, 0)
        
self.tvPlayList.set_model(self.playList)

def on_album_clicked(self, tc, user_data):
        print "column clicked", tc, user_data

```

I think i am missing something like a connection between 
glade and my functions, but i cannot find a signal in glade
which is responsible to handle the click in a column.

---

### Post by sveri on 2008-10-30
Nevermind, just for the logs.
Glade 3.5.2 seems to have a bug i think.
In the general options of the gtktree the
Headers Clickable Option is set to yes.
That doesn't affect the program anyway.

If add manually "self.tvPlayList.set_headers_clickable(True)"
to my program code everything works as expected.

---

