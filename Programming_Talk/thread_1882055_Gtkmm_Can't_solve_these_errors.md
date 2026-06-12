---
title: "Gtkmm: Can't solve these errors"
date: 2011-11-16
forum: Programming Talk
---

### Post by fallenshadow on 2011-11-16
> 
gtkmm-CRITICAL **: gtkmm: widget `help_about' (in GtkBuilder file) is of type `gtkmm__GtkMenuItem' but `GtkButton' was expected

CRITICAL **: Gtk::Builder::get_widget(): dynamic_cast<> failed. Segmentation fault


As usualy Gtkmm is causing me much pain and suffering. I am trying to get a menu item to link to a dialog but its not working at all. Any ideas?

---

### Post by cgroza on 2011-11-16
Well, with the current information, it looks like a cast/type issue.

Can you isolate the problem to a specific piece of code?

---

### Post by fallenshadow on 2011-11-16
I don't really know the cause of it... maybe the problem is with the .glade file. You can download a folder of this new alpha version and try and help if you like. 

[Link to code]("http://www.photofiltre-lx.org/projects/xwii/downloads/Xwii-GUI-code-0.5-ALPHA.tar.gz")

The files you would want to look at would be:

GUI.cpp about.cpp

The "GUI-compile" script compiles these 2 files. The code will compile at the moment but it displays these errors when the binary is run from the terminal.

---

### Post by crdlb on 2011-11-16
On line 129 of GUI.cpp: ```

	refBuilder->get_widget("help_about", button);
```

button is a Gtk::Button*, but the UI file defines "help_about" as a GtkImageMenuItem.

---

### Post by fallenshadow on 2011-11-17
Yes I know that but I need a solution... what should I replace button with?

---

### Post by PaulM1985 on 2011-11-17
So why not change the button to be a GtkImageMenuItem?

---

### Post by fallenshadow on 2011-11-17
Yes that is the obvious solution but I tried that and it doesn't work.

---

### Post by pbrane on 2011-11-17
When connecting menu items use the **connect_clicked** function I provided in  GUI.cpp
```

//	refBuilder->get_widget("help_about", button);
//	button->signal_clicked().connect((sigc::mem_fun(*this, &mainWindow::show_about_dialog)));
	connect_clicked("help_about", sigc::mem_fun(*this, &mainWindow::show_about_dialog));

```

This works for buttons as well. Have a look at that function.

---

### Post by fallenshadow on 2011-11-17
I tried that already but the resulting binary still didn't work. I launched the binary through the terminal this time to try and find an error.

I now get the following:

> 
Segmentation fault


I presume its a problem with the glade file. I will investigate the glade file just in case.

---

### Post by fallenshadow on 2011-11-17
Woohoo! All fixed! Just had to revert some changes in the way it was loading the Glade file. :D

Thanks pbrane! ;) Without your suggestion I would not have investigated that connect method again.

---

