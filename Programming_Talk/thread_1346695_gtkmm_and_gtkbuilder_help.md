---
title: "gtkmm and gtk::builder help"
date: 2009-12-05
forum: Programming Talk
---

### Post by nickbird on 2009-12-05
I have created my UI using Glade Designer and saved it as "volume.glade"
I am trying to use the gtkmm.org documentation's example ([http://library.gnome.org/devel/gtkmm-tutorial/unstable/sec-builder-accessing-widgets.html.en]("http://library.gnome.org/devel/gtkmm-tutorial/unstable/sec-builder-accessing-widgets.html.en")), but they call their glade file from the driver.  I want to call mine in a class.

I have the following code:

**MainWindow.h**
```
#include <gtkmm.h>
#include <gtkmm/button.h>
#include <gtkmm/window.h>

class MainWindow : public Gtk::Window
{
	public:
		MainWindow();
		virtual ~MainWindow();
	protected:	// Signal Handlers

		void onExitClicked();
	protected:
		Gtk::Button *m_exitButton;
		Gtk::Window *main;
};


```

**MainWindow.cpp**
```

#include "MainWindow.h" 

MainWindow::MainWindow()
{
	Glib::RefPtr<Gtk::Builder> refBuilder = Gtk::Builder::create_from_file("volume.glade");

	refBuilder->get_widget("window1", main);
	main->show();
}

MainWindow::~MainWindow()
{
}

```

**main.cpp**
```

#include "MainWindow.h"
#include <gtkmm.h>

int main(int argc, char* argv[])
{
	Gtk::Main kit(argc, argv);

	MainWindow window;

	Gtk::Main::run(window);

	return 0;
}

```

The problem I run into is that since MainWindow is a Window Type of its own, I end up with a blank window AND the window from the .glade file.

Whats the best way to do this?  Do I suck it up and call it from main, or do I write my own class that is not derived from Gtk::Window?

---

### Post by SledgeHammer_999 on 2009-12-05
Obviously you want ONE app-window, right?
Then why the hell do you create a gtkwindow(MainWindow) and then create another one?(window1)

It's not a bad idea to do it from main...

---

