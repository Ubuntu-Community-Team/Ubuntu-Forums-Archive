---
title: "Help me with a simple gtkmm problem"
date: 2007-07-15
forum: Programming Talk
---

### Post by AlexThomson_NZ on 2007-07-15
Hi all,

I'm stuck on (hopefully) a simple issue with gtkmm.  Can someone suggest how to connect a signal_response to a function.  Here's the code:

```

#include "my_about.h"

About::About()
{
}

void About::show()
{
	Gtk::Dialog *pDialog;
	refXml->get_widget("aboutdialog1", pDialog);
	
	// Connect widgets on this dialog
	pDialog->signal_response().connect(sigc::slot(*this, &About::hide));
	
	// Show the dialog
	pDialog->run();
}

void About::hide()
{
	// Shut down the dialog
	Gtk::Dialog *pDialog;
	refXml->get_widget("aboutdialog1", pDialog);
	pDialog->hide();
}

```

As it stands, it gives:
my_about.cpp:11: error: missing template arguments before '(' token.

Thanks!

---

