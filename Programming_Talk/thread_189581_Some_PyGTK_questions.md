---
title: "Some PyGTK questions"
date: 2006-06-05
forum: Programming Talk
---

### Post by Wallakoala on 2006-06-05
I am making an RSS feed aggregator with my friend in PyGTK. This is our first "big" program. One major question we have is that some of the feed descriptions have html tags (i.e. embedded images, text formatting). We are looking for a way we can render that html in the program, just as a program like Liferea does. If anybody knows a way we can do this, it would be greatly appreciated.

Another question I have is less related to pygtk. We want to make this so that it will remember your settings and all of your feeds when you restart the program. What is the best way to do this?

Thanks,
Walla

---

### Post by FryerFox on 2006-06-05
[QUOTE=Wallakoala]We want to make this so that it will remember your settings and all of your feeds when you restart the program. What is the best way to do this?[/QUOTE]

If you're using GNOME, you should probably use GConf
```
import gconf

path = "/apps/myapp"
gconf_client = gconf.client_get_default()
gconf_client.set_string(path, var)
var = gconf_client.get_string(path)
```

Remember, you can turn anything into a string by using the pickle module, so you can use this to store dictionaries and lists too.

---

### Post by vasdee on 2006-06-06
i think what you are after is the gtk-html rendering library libgtkhtml
you can find it with synaptic / apt. 

I think that's exactly what lifrea uses as well, not sure if there is a python binding for it tho

---

### Post by simplyw00x on 2006-06-06
Liferea either uses an embedded mozilla gecko renderer or gtkhtml (you can install either). There are python bindings for both, although AFAIK the gtkhtml bindings are fairly featureless and generally undercomplete.
[http://freshmeat.net/projects/python-gtkhtml/](http://freshmeat.net/projects/python-gtkhtml/)
[http://sourceforge.net/projects/pygtkmoz](http://sourceforge.net/projects/pygtkmoz)

Or, use Gtk-webcore:
[http://gtk-webcore.sourceforge.net/](http://gtk-webcore.sourceforge.net/)

---

### Post by Wallakoala on 2006-06-20
sorry to bring this thread back, but I am having some troubles with the gtkmozembed.

This is the same library as the pygtkmoz.

I have found my way here: [http://www.pygtk.org/pygtkmozembed/class-gtkmozembed.html](http://www.pygtk.org/pygtkmozembed/class-gtkmozembed.html)

There is a nice little explanation of this library, and it seems simple enough. So I decided to test out the example script on that page. The script is the following:
```
import gtk
import gtkmozembed

class TinyGecko:
    def __init__(self):
        self.moz = gtkmozembed.MozEmbed()
                
        win = gtk.Window()
        win.add(self.moz)
        win.show_all()
        # self.moz.load_url('http://www.pygtk.org')
        data = '<html><head><title>Hello</title></head><body>pygtk dev</body></html>'
        self.moz.render_data(data, long(len(data)), 'file:///', 'text/html')

if __name__ == '__main__':
  TinyGecko()
  gtk.main()
```
So I run the script, and the script does not succesfully run. Instead, the words
```
Segmentation fault
``` are displayed in the terminal.

Now I am at a loss.

Any suggestions?

---

### Post by simplyw00x on 2006-06-21
I'd suggest adding 'print foo' every 2 lines where foo is a different word or number each time so you can see where it's crashing.

---

### Post by dpm on 2006-06-21
[quote=Wallakoala]sorry to bring this thread back, but I am having some troubles with the gtkmozembed.

This is the same library as the pygtkmoz.

I have found my way here: [http://www.pygtk.org/pygtkmozembed/class-gtkmozembed.html]("http://www.pygtk.org/pygtkmozembed/class-gtkmozembed.html")

There is a nice little explanation of this library, and it seems simple enough. So I decided to test out the example script on that page. The script is the following:
```
import gtk
import gtkmozembed

class TinyGecko:
    def __init__(self):
        self.moz = gtkmozembed.MozEmbed()
                
        win = gtk.Window()
        win.add(self.moz)
        win.show_all()
        # self.moz.load_url('http://www.pygtk.org')
        data = '<html><head><title>Hello</title></head><body>pygtk dev</body></html>'
        self.moz.render_data(data, long(len(data)), 'file:///', 'text/html')

if __name__ == '__main__':
  TinyGecko()
  gtk.main()
``` So I run the script, and the script does not succesfully run. Instead, the words
```
Segmentation fault
``` are displayed in the terminal.

Now I am at a loss.

Any suggestions?[/quote]

What you are describing is a known (and extremely annoying) gtkmozembed bug specific to Ubuntu:

[https://launchpad.net/products/firefox/+bug/26436](https://launchpad.net/products/firefox/+bug/26436)

To make a long story short: you won't be able to use the gtkmozembed widget in Ubuntu until this bug is fixed (which we won't be seeing any time soon, IMHO).

Some pointers: GtkHtml has already been mentioned on this thread. Apart from not having documentation and being rather dull featurewise in comparison to gtkmozembed, you can also give it a go. 

AFAIK there are Python bindings for gtkhtml2 (which is a dead project) and you can also use gtkhtml3 (which is basically the port of gtkhtml1 to GNOME2, nothing to do with gtkhtml2), which at least is a live project, although the way to invoke it and use it in Python is rather ugly.

Cheers.

---

### Post by Wallakoala on 2006-06-21
[QUOTE=desp]What you are describing is a known (and extremely annoying) gtkmozembed bug specific to Ubuntu:

[https://launchpad.net/products/firefox/+bug/26436](https://launchpad.net/products/firefox/+bug/26436)

To make a long story short: you won't be able to use the gtkmozembed widget in Ubuntu until this bug is fixed (which we won't be seeing any time soon, IMHO).

Some pointers: GtkHtml has already been mentioned on this thread. Apart from not having documentation and being rather dull featurewise in comparison to gtkmozembed, you can also give it a go. 

AFAIK there are Python bindings for gtkhtml2 (which is a dead project) and you can also use gtkhtml3 (which is basically the port of gtkhtml1 to GNOME2, nothing to do with gtkhtml2), which at least is a live project, although the way to invoke it and use it in Python is rather ugly.

Cheers.[/QUOTE]

You have mentioned many things, but can you reccommend one that is easy to use? All I want to do is render the basic html that would be in feed descriptions. Like bold, underline, images, links, etc.

Also a link to the documentation would be helpful as well.

---

### Post by dpm on 2006-06-21
>  Also a link to the documentation would be helpful as well. 
I explicitly mentioned on my last post that there is **no** documentation for gtkhtml AFAIK. Of course, you can always have a look directly at the source code.

Ok, from my brief experiences with PyGtk web content rendering development I can tell you the following:

1. If it worked in Ubuntu, I'd use **gtkmozembed** widget. Advantages: a) it is more or less documented, b) it uses the gecko rendering engine c) it is a live project and is the option with more features and programming ease. 

2. Since it doesn't work, I would recommend you to use **gtkhtml2.** It is not documented, but easy to use through Python bindings. It can do CSS, load images and so on, but you cannot use it for editing HTML (as in what an HTML composer of an email client does, for example). But since you only want it for rendering and not for editing, it should be ok for your application. Disadvantages: a) it is a dead project b) did I mention there is no documentation? c) it is not so trivial to get it to load images, but it works.

3. Alternatively, you could use **gtkhtml3**. As I said, it is not the next version of gtkhtml2, but a ported version of gtkhtml1 to the GNOME2 platform. It is apparently a live project, but again a) there is no documentation b) there are no direct PyGTK bindings, but the widget can be instantiated through Bonobo monikers and functions (it is not nice, but doable). In the past it didn't seem to support CSS, but this may have changed now. IIRC Evolution uses gtkhtml3 in C, but there have been talks of moving to gtkmozembed.

4. I've got no experience with **gtk-webcore**.

To sum up, if the features of gtkhtml2 work for your application, I'd use that. Otherwise, if you can develop on a machine with a different OS (Debian, Fedora or FreeBSD, for example), I'd use gtkmozembed.

Since I'm feeleing particularly nice tonight, here are some links.

* Someone was nice enough to generate some Epydoc documentation for the gtkhtml2 PyGTK bindings:
[http://download.gna.org/advene/epydoc/public/gtkhtml2-module.html]("http://download.gna.org/advene/epydoc/public/gtkhtml2-module.html")

* Using gtkhtml2 in C:
[http://www.ubiobio.cl/~gpoo/weblog/archives/000174.html]("http://www.ubiobio.cl/%7Egpoo/weblog/archives/000174.html")

* gtkhtml2 python binding "documentation"
/usr/share/pygtk/2.0/defs/gtkhtml2.defs

* gtkhtml tutorial in C (old, but some parts still apply to gtkhtml2). The "Inlined Images" section is especially interesting.
[http://primates.ximian.com/~rodo/programing_with_gtkhtml_tutorial/guadec.html]("http://primates.ximian.com/%7Erodo/programing_with_gtkhtml_tutorial/guadec.html")

* gtkhtml C API documentation
[http://www.fifi.org/doc/libgtkhtml-dev/html/gtkhtml.html]("http://www.fifi.org/doc/libgtkhtml-dev/html/gtkhtml.html")

* Very nice tutorial on how to create a web browser in Python under GNOME:
[http://patrick.wagstrom.net/tutorials/pygtkmozembed/pygtkmozembed.html]("http://patrick.wagstrom.net/tutorials/pygtkmozembed/pygtkmozembed.html") 

* Some random gtkmozembed links:
[http://ruby-gnome2.sourceforge.jp/hiki.cgi?Gtk%3A%3AMozEmbed=#Gtk%3A%3AMozEmbed.set_profile_path]("http://ruby-gnome2.sourceforge.jp/hiki.cgi?Gtk%3A%3AMozEmbed=#Gtk%3A%3AMozEmbed.set_profile_path")
[http://www.async.com.br/faq/pygtk/index.py?req=edit&file=faq19.018.htp]("http://www.async.com.br/faq/pygtk/index.py?req=edit&file=faq19.018.htp")
[http://www.mozilla.org/unix/gtk-embedding.html]("http://www.mozilla.org/unix/gtk-embedding.html")
[http://www.pygtk.org//pygtkmozembed/class-gtkmozembed.html]("http://www.pygtk.org//pygtkmozembed/class-gtkmozembed.html")

* And last but not least, I've attached a few files that I either created myself or got  from the net. They are examples in Python of the gtkhtml2 and gtkhtml3 widgets.

Anyway, I hope it helps. 

Keep me posted on how you are getting on with your code.

---

### Post by Wallakoala on 2006-06-21
Wow, thanks desp. I am definetly going to use gtkhtml2, and you have given me some very nice resources. 

I can now get back to work on this thing, so thank you again for all of your help. I will keep you posted on the progress.

---

### Post by Daverz on 2006-06-22
[QUOTE=Wallakoala]
Another question I have is less related to pygtk. We want to make this so that it will remember your settings and all of your feeds when you restart the program. What is the best way to do this?
[/QUOTE]

I recommend [ConfigObj](http://www.voidspace.org.uk/python/configobj.html).  It's easy to use, and it's just a single pure python file you can drop into your module's directory. 

Using GConf would add a non-portable dependency to your project.

---

### Post by Fredo on 2007-10-14
Hi!

The bug with gtkmozembed segfaulting can easily be worked around: Just export LD_LIBRARY_PATH=/usr/lib/firefox before starting your pygtk application.

Nevertheless, it's annoying and I'd be glad if it would get fixed.

Cheers,
Fredo

---

