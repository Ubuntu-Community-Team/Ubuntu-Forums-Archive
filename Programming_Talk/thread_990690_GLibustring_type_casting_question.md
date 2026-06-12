---
title: "GLib::ustring type casting question"
date: 2008-11-23
forum: Programming Talk
---

### Post by samjh on 2008-11-23
I'm trying to convert a numerical input into a floating-point value.  Specifically it is a gtkmm application, the input is of type GLib::ustring, and it needs to be converted into a standard double.

Is there a clean/simple way to do this?  I've tried the usual set of C++ type casts (ie. static_cast, et al.), but alas, it is not possible.

---

### Post by dexter on 2008-11-23
You cannot just use casting to convert from a string to a float. I'm not that familiar with glib, but check out this website: [http://www.gtkmm.org/docs/glibmm-2.4/docs/reference/html/classGlib_1_1ustring-members.html](http://www.gtkmm.org/docs/glibmm-2.4/docs/reference/html/classGlib_1_1ustring-members.html). You can get a standard char* array by using c_str(). Next you can use atof ([http://www.cplusplus.com/reference/clibrary/cstdlib/atof.html](http://www.cplusplus.com/reference/clibrary/cstdlib/atof.html)) to get a floating point number out of the string.

```

Glib::ustring testUString("1.23456789");
char * UStringToCharArray = testUString.c_str();
double floatingPoint = atof(UStringToCharArray);

```
(not tested)

---

### Post by samjh on 2008-11-23
Ah well, I was hoping there would be a cleaner way to do it.

Back to the hack...

---

