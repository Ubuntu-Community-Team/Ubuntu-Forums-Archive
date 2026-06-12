---
title: "Can't use Gio::File"
date: 2008-03-08
forum: Programming Talk
---

### Post by xlinuks on 2008-03-08
Hi,
does anyone know what I'm doing wrong about using the Gio::File class?
I'm using C++ and at compile time I get the following error for the a header file  "error: ‘Gio’ was not declared in this scope" referring to the line "typedef Glib::RefPtr<Gio::File> HFile;"

Here's the file itself:
```


#ifndef _XTREE_H
#define	_XTREE_H

#include <gtkmm.h>
#include <glibmm.h>

#include <iostream>
#include <sstream>
#include <vector>
#include <string>

using namespace std;
using namespace Gtk;
using namespace Glib;

class XTree : public Gtk::TreeView {
	
public:
	XTree();
	virtual ~XTree();
	typedef Glib::RefPtr<Gio::File> HFile;
	int listFileNames( vector<HFile> *pvHFiles, string sPath );
	template <class T>
	std::string to_string( const T& t );
};


#endif	/* _XTREE_H */

```

Any hint would be appreciated..

---

### Post by RainCT on 2009-07-29
I figure you don't need an answer anymore, but in case someone else with a similar problem find this thread, I guess the problem is that you're missing an "using namespace Gio;" or something along that lines.

---

