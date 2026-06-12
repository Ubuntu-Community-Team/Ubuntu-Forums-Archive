---
title: "mystery segmentation fault"
date: 2010-12-20
forum: Programming Talk
---

### Post by worksofcraft on 2010-12-20
I had a go at making shared library and linked it with an application that works fine with the static library, but with the shared library it crashes with a segmentation fault when the program is trying to exit.

gdb reports it as being in a function called "g_slice_free_chain_with_offset" from /lib/libglib-2.0.so.0


gdb claims that it was called by a destructor of one of my objects so I looked in said destructor only to see that it is a completely empty method:
```

cs_glade::~cs_glade() {}

```

Not only that but the object doesn't even have any data members :confused:

[php]
// wrap graphical user interface from GtkBuilder as an indexable container (by widget name)
struct cs_glade: cs_map_item {
	cs_glade(charptr pGladeFileName, charptr pWindowName);

	const cs_gtkitem &widget(charptr pName) const {
		return dynamic_cast<const cs_gtkitem &> (operator[](pName));
	}
// ~cs_glade(); // crashes on exit
};
[/php]

So I deleted the pointless destructor... and the program now exits fine... problem solved... or is it?

My next might involve adding a destructor to said class or one of it's descendants... how can I find out why it is calling that glib function if it isn't in my code?

---

### Post by worksofcraft on 2010-12-20
Problem solved... Trying to use autotools was making it all to complicated for me :(
I think I'll stick with a nice straight forward  bash script from now on :P

---

