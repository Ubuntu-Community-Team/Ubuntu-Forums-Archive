---
title: "Gdk.Pixbuf memory leak in Vala"
date: 2010-09-13
forum: Programming Talk
---

### Post by veverica17 on 2010-09-13
Hi folks, here is a simple question. Can you help me find the memory leak in this Vala code ? 
If it helps I can post the generated c code too ^^

```

using GLib;
using Gtk;
using Gee;

void test1 () 
{
    Gee.ArrayList<Gdk.Pixbuf> list = new Gee.ArrayList<Gdk.Pixbuf>();
    
    for( int a = 0; a < 10000; a++)
    {
        string path = "/usr/share/icons/gnome/48x48/stock/data/stock_lock.png";
        
        list.add( new Gdk.Pixbuf.from_file( path ) );
    }
    
    list.clear(); 

    [COLOR="red"]// when the function returns it *should* free all alocated memory, or am I missing something? [/COLOR]            
}

int main (string[] args) 
{
	Gtk.init( ref args);

	[COLOR="Red"]// the memory usage here is ~3mb[/COLOR]
	test1();
	[COLOR="red"]// here it is ~94mb [/COLOR]

	Gtk.main();
	return 0;
}

```

---

