---
title: "Python VTE emulation on Ubuntu,   v = vte.Terminal() AttributeError: 'module' object"
date: 2010-12-07
forum: Programming Talk
---

### Post by Steveuntu on 2010-12-07
Hi,

I try to run a terminal emulation using Python+Gtk+Vte. Before develop
my own sources, i'm testing some examples like this ;
[http://www.eurion.net/python-snippets/snippet/Embed%20a%20VTE%20termi](http://www.eurion.net/python-snippets/snippet/Embed%20a%20VTE%20termi)...

```
if __name__ == '__main__':
    # create the terminal
    v = vte.Terminal()
    v.connect ("child-exited", lambda term: gtk.main_quit())

    # fork_command() will run a command, in this case it shows a prompt
    v.fork_command()

    # create a window and add the VTE
    window = gtk.Window()
    window.add(v)
    window.connect('delete-event', lambda window, event: gtk.main_quit())

    # you need to show the VTE
    window.show_all()

    # Finally, run the application
    gtk.main()

```

But when i try to run, i get this message error;

    v = vte.Terminal()
AttributeError: 'module' object has no attribute 'Terminal'

I'm using ubuntu 9.10 karmic. I've installed (apt-get) python-gtk, /2,
-dev, libvte...

Anyone know if there's a bug on this using karmic, or i must to
download and compile gtk/vte from sources?

thanks,

Steve,

---

### Post by MeanEYE on 2011-02-13
Did you import **vte** module?

For any additional help you can use python console command. Just start it by typing 'python' in your terminal and once there do this:

```
import vte
help(vte)
```

It will list everything within vte module.

---

