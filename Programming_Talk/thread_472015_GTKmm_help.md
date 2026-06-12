---
title: "GTKmm help"
date: 2007-06-12
forum: Programming Talk
---

### Post by Paul820 on 2007-06-12
Can anyone help me here please. I am trying to get GTKmm running with codeblocks
on ubuntu feisty. I have done a search on the codeblocks forums and found that i
need to put `pkg-config glibmm-2.4 --cflags` under other options for the compiler
and `pkg-config glibmm-2.4 --libs` under other options for the linker. Now i have
done this part and pointed codeblocks to the include files. I get 50 plus errors.
I have looked on the gtkmm.org website and it tells me what i needed to download.
I have downloaded all the files through synaptic: glibmm, gtkmm, libglademm, gconfmm,
libgnomecanvasmm, libgnomeuimm, and the damn thing is still spitting out errors.
Codeblocks keeps opening a file called types.h pointing to a line that says:
#include <gdk/gdk.h> ( obviously it can't find it ).

On the gtkmm website it doesn't say that i need a package called gdk, i can't
find it in the repo's so where do i get it from. I have been trying with
codeblocks for the last two hours to get it to compile. I tried anjuta
before codeblocks but that keeps looking for the gtkmm2.0 files. I prefer to 
use codeblocks anyway because i am familiar with it. Or i thought i was.

I have done a search on this forum aswell and it says the same as codeblocks forum,
maybe it's just me.

Any help will be much appreciated!!

---

### Post by AlexThomson_NZ on 2007-06-12
I think gtkmm is just a c++ wrapper around gtk, so still might need the gtk dev libs.

Try installing the libgtk2.0-dev package which should have the gdk/gdk.h and other dependancies in it

// have not used gtkmm but have a bit of experience with gtk

---

### Post by Paul820 on 2007-06-13
Thanks AlexThomson_NZ, i have found them. But, i am still getting errors, i had to link to loads of other include files aswell, which the documentation on the gtkmm website never explained. I'm getting errors in the include source code now:

```
:: === gtkmm, Debug ===
/usr/include/gtkmm-2.0/pangomm/tabarray.h:35: error: expected constructor, destructor, or type conversion before ‘(’ token
/usr/include/gtkmm-2.0/gdkmm/pixbuf.h:239: error: ISO C++ forbids declaration of ‘Slot1’ with no type
/usr/include/gtkmm-2.0/gdkmm/pixbuf.h:239: error: typedef name may not be a nested-name-specifier
/usr/include/gtkmm-2.0/gdkmm/pixbuf.h:239: error: expected ‘;’ before ‘<’ token
/usr/include/gtkmm-2.0/gdkmm/pixbuf.h:328: error: expected ‘,’ or ‘...’ before ‘&’ token
/usr/include/gtkmm-2.0/gdkmm/pixbuf.h:328: error: ISO C++ forbids declaration of ‘SlotDestroyData’ with no type
/usr/include/gtkmm-2.0/gtkmm/object.h:43: error: ‘SigC::manage’ has not been declared
/usr/include/gtkmm-2.0/gtkmm/clipboard.h:160: error: ISO C++ forbids declaration of ‘Slot2’ with no type
/usr/include/gtkmm-2.0/gtkmm/clipboard.h:160: error: typedef name may not be a nested-name-specifier
/usr/include/gtkmm-2.0/gtkmm/clipboard.h:160: error: expected ‘;’ before ‘<’ token
/usr/include/gtkmm-2.0/gtkmm/clipboard.h:163: error: ISO C++ forbids declaration of ‘Slot0’ with no type
/usr/include/gtkmm-2.0/gtkmm/clipboard.h:163: error: typedef name may not be a nested-name-specifier
/usr/include/gtkmm-2.0/gtkmm/clipboard.h:163: error: expected ‘;’ before ‘<’ token
/usr/include/gtkmm-2.0/gtkmm/clipboard.h:179: error: expected ‘,’ or ‘...’ before ‘&’ token
/usr/include/gtkmm-2.0/gtkmm/clipboard.h:179: error: ISO C++ forbids declaration of ‘SlotGet’ with no type
/usr/include/gtkmm-2.0/gtkmm/clipboard.h:226: error: ISO C++ forbids declaration of ‘Slot1’ with no type
/usr/include/gtkmm-2.0/gtkmm/clipboard.h:226: error: typedef name may not be a nested-name-specifier
/usr/include/gtkmm-2.0/gtkmm/clipboard.h:226: error: expected ‘;’ before ‘<’ token
/usr/include/gtkmm-2.0/gtkmm/clipboard.h:227: error: expected ‘,’ or ‘...’ before ‘&’ token
/usr/include/gtkmm-2.0/gtkmm/clipboard.h:227: error: ISO C++ forbids declaration of ‘SlotReceived’ with no type
/usr/include/gtkmm-2.0/gtkmm/clipboard.h:234: error: expected ‘,’ or ‘...’ before ‘&’ token
/usr/include/gtkmm-2.0/gtkmm/clipboard.h:234: error: ISO C++ forbids declaration of ‘SlotReceived’ with no type
/usr/include/gtkmm-2.0/gtkmm/clipboard.h:237: error: ISO C++ forbids declaration of ‘Slot1’ with no type
/usr/include/gtkmm-2.0/gtkmm/clipboard.h:237: error: typedef name may not be a nested-name-specifier
/usr/include/gtkmm-2.0/gtkmm/clipboard.h:237: error: expected ‘;’ before ‘<’ token
/usr/include/gtkmm-2.0/gtkmm/clipboard.h:238: error: expected ‘,’ or ‘...’ before ‘&’ token
/usr/include/gtkmm-2.0/gtkmm/clipboard.h:238: error: ISO C++ forbids declaration of ‘SlotTextReceived’ with no type
/usr/include/gtkmm-2.0/gtkmm/container.h:192: error: ISO C++ forbids declaration of ‘Slot1’ with no type
/usr/include/gtkmm-2.0/gtkmm/container.h:192: error: typedef name may not be a nested-name-specifier
/usr/include/gtkmm-2.0/gtkmm/container.h:192: error: expected ‘;’ before ‘<’ token
/usr/include/gtkmm-2.0/gtkmm/container.h:203: error: expected ‘,’ or ‘...’ before ‘&’ token
/usr/include/gtkmm-2.0/gtkmm/container.h:203: error: ISO C++ forbids declaration of ‘ForeachSlot’ with no type
/usr/include/gtkmm-2.0/gtkmm/colorselection.h:190: error: ISO C++ forbids declaration of ‘Slot2’ with no type
/usr/include/gtkmm-2.0/gtkmm/colorselection.h:190: error: typedef name may not be a nested-name-specifier
/usr/include/gtkmm-2.0/gtkmm/colorselection.h:190: error: expected ‘;’ before ‘<’ token
/usr/include/gtkmm-2.0/gtkmm/colorselection.h:193: error: ‘SlotChangePaletteHook’ does not name a type
/usr/include/gtkmm-2.0/gtkmm/menu_elems.h:48: error: ISO C++ forbids declaration of ‘Slot0’ with no type
/usr/include/gtkmm-2.0/gtkmm/menu_elems.h:48: error: typedef name may not be a nested-name-specifier
/usr/include/gtkmm-2.0/gtkmm/menu_elems.h:48: error: expected ‘;’ before ‘<’ token
/usr/include/gtkmm-2.0/gtkmm/menu_elems.h:83: error: expected ‘,’ or ‘...’ before ‘&’ token
/usr/include/gtkmm-2.0/gtkmm/menu_elems.h:83: error: ISO C++ forbids declaration of ‘CallSlot’ with no type
/usr/include/gtkmm-2.0/gtkmm/menu_elems.h:91: error: expected ‘,’ or ‘...’ before ‘&’ token
/usr/include/gtkmm-2.0/gtkmm/menu_elems.h:91: error: ISO C++ forbids declaration of ‘CallSlot’ with no type
/usr/include/gtkmm-2.0/gtkmm/menu_elems.h:127: error: expected ‘,’ or ‘...’ before ‘&’ token
/usr/include/gtkmm-2.0/gtkmm/menu_elems.h:127: error: ISO C++ forbids declaration of ‘CallSlot’ with no type
/usr/include/gtkmm-2.0/gtkmm/menu_elems.h:137: error: expected ‘,’ or ‘...’ before ‘&’ token
/usr/include/gtkmm-2.0/gtkmm/menu_elems.h:137: error: ISO C++ forbids declaration of ‘CallSlot’ with no type
/usr/include/gtkmm-2.0/gtkmm/menu_elems.h:166: error: expected ‘,’ or ‘...’ before ‘&’ token
/usr/include/gtkmm-2.0/gtkmm/menu_elems.h:166: error: ISO C++ forbids declaration of ‘CallSlot’ with no type
/usr/include/gtkmm-2.0/gtkmm/menu_elems.h:175: error: expected ‘,’ or ‘...’ before ‘&’ token
:: More errors follow but not being shown.
:: Edit the max errors limit in compiler options...
:: === Build finished: 50 errors, 0 warnings ===
```

I give up with it, it's a damn nightmare. :(

---

### Post by harun on 2007-06-13
Try installing:

```
sudo apt-get install libgtkmm-2.4-dev
```

In addition to the pkg-config you are using you may want to also do "pkg-config --cflags --libs gtk+-2.0". I can't remember if that is needed or not, but worth a shot.

---

### Post by Paul820 on 2007-06-14
SOLVED: It wasn't `pkg-config glibmm-2.4 --cflags` it was pkg-config **pkg-config gtkmm-2.4 --cflags**, works fine now.

---

