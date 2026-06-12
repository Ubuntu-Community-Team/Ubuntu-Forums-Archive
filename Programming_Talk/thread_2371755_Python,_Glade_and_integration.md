---
title: "Python, Glade and integration"
date: 2017-09-18
forum: Programming Talk
---

### Post by nilssoderman on 2017-09-18
Hi, I am trying to have my Glade file being displayed on the screen. Where can I find a SIMPLE example how to display my Glade effort? Only the GUI I have been trying to develope. ...been trying now for several hours... Please help me...

---

### Post by Claus7 on 2018-05-28
Hello,

if I understand correctly, you have tampered with glade and you want to preview the result. This can happen as follows:
(it is supposed that you have already created a new project and you have added a GtkWindow)

1) go on the left hand side space (object inspector, underneath the Search Widget bar) and select the GtkWindow. Then do a right click and select Preview snapshot. 

2) do a right click on your working space (inside the created window) and select once again Preview snapshot.

3) Create a folder for your project and save it as: test.glade
In the meantime write as ID of the GtkWindow: testwindow (under the General tab of the right hand side space - property editor)
In the same folder create the file: test.py with the following content:
> from gi.repository import Gtk
builder = Gtk.Builder()
builder.add_from_file("test.glade")
window = builder.get_object("testwindow")
window.show_all()
Gtk.main()

All names above are provided as an example.

Open a terminal in that folder and type the command (this makes test.py executable):
```
chmod 755 test.py
```

Finally run the command:
```
python test.py
```

and you will be able to see the result of your project. In order to exit type in terminal Ctrl+z.

Regards!

---

