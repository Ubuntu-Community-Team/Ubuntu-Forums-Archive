---
title: "C++ const and memory management quandary"
date: 2010-09-27
forum: Programming Talk
---

### Post by worksofcraft on 2010-09-27
I have a class that I derive lots of other classes from and an important part of it is a **virtual** operator that converts it to a constant char *.

Lately I'm using it to wrap some Gtk widgets and one of them is the combobox from which said operator retrieves the currently active text like so:
```

operator cs_combo::charptr() const {
	gchar *Text = gtk_combo_box_get_active_text(Widget);
	return (charptr) Text;
}

```
Seems easy enough except the text string retrieved from gtk must be freed by a call to g_free(Text) :shock: and as we all know, C/C++ do not have automatic garbage collection.

So my first impulse was to make Text a member of my cs_combo structure and simply dispose of it when a a new call for active text is made, and also in the destructor of course.

However, then I will be modifying the cs_combo structure and so the operator will not be on a read only structure and hence not an override for the virtual method of the base class.

I can think of three options:
[LIST=1]
[*]remove "const" from the base class and all other classes that derive from it.
[*]get rid of the old charptr operator and make one that returns a C++ string or even a glib ustring.
[*]Create an independent list of items to submit to g_free effectively making a primitive sort of garbage collector.
[/LIST]

I think option 2 would be easiest to work with, but I am concerned about the overhead it will produce: unnecessarily allocating and copying strings in countless places.

I wonder if any other C++ programmers have views or alternative solutions: How would you do it?

---

### Post by gzarkadas on 2010-09-27
An option equivalent to #3 (which IMO is the best solution, retaining both the initial design and efficiency), would be to make the Text member `mutable' and not a gchar, but a stack of gchars (ie a custom class). Then, each time your operator is called it will return the top of the stack, while each time the combo text is modified, the old value will be pushed down the stack and the new would become the top one.

Since your const char* returning operator assumes that the caller will not use the raw pointer after the combo instance is destroyed, this scheme is appropriate: all raw pointers last for the lifetime of the generating object. And in your Text member's destructor you can call g_free for all the stack items, without the need to maintain a global list.

---

### Post by spjackson on 2010-09-27
I would strongly favor option 2 unless there is a measurable performance hit.

If performance rules out option 2, I'd cache the value as a **mutable** member of the (base?) class, as per your first impulse. The cast operator would remain const.

I don't much care for option 3.

---

### Post by worksofcraft on 2010-09-27
> **gzarkadas said:**
> An option equivalent to #3 (which IMO is the best solution, retaining both the initial design and efficiency), would be to make the Text member `mutable' and not a gchar, but a stack of gchars (ie a custom class). Then, each time your operator is called it will return the top of the stack, while each time the combo text is modified, the old value will be pushed down the stack and the new would become the top one.

Since your const char* returning operator assumes that the caller will not use the raw pointer after the combo instance is destroyed, this scheme is appropriate: all raw pointers last for the lifetime of the generating object. And in your Text member's destructor you can call g_free for all the stack items, without the need to maintain a global list.

Awesome, and I just tested it too: It works perfectly!
I hadn't even heard of the C++ **mutable** keyword, so your input was exactly what I needed, thank you ever so much :)

---

### Post by worksofcraft on 2010-09-27
> **spjackson said:**
> I would strongly favor option 2 unless there is a measurable performance hit.

If performance rules out option 2, I'd cache the value as a **mutable** member of the (base?) class, as per your first impulse. The cast operator would remain const.

I don't much care for option 3.

Yes I am in two minds about this: In theory the user could sit there all day changing the combo box text e.g. trying something else and eventually there would be a huge stack of old useless entries. Yet conceptually that combo box only ever holds one.

OTOH the user might be entering new successive values that will all get saved when a "save" button is clicked and then the program might need to access them all again. Clearly returning strings would help the calling program, but in most of the code of other derived classes this operator simply points to some often static text held in the object and only used transiently.

Thus I have adopted the philosophy that the calling program needs to make it's own long term copies on the very rare occasions where they could be used beyond the scope of the object they are obtained from.

Your suggestion is however also very good because it convinces me to make another method that returns a proper string. In fact it can simply be a method of the base class by calling the virtual charptr operator and stringifying that :)

I think it might be most flexible to pass said string by reference as a parameter from the caller and append the new text to the given string instead of creating and returning new strings all the time.

---

