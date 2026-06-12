---
title: "Keyval to Unicode and back in PyGTK"
date: 2008-05-13
forum: Programming Talk
---

### Post by MicahCarrick on 2008-05-13
I have a little utility half-written in C that I'm dinking around with porting to Python because a) I want to learn more Python and b) it will be easier to maintain. I'm relatively new to Python so I might be missing something fundamental...

With this application, I need to run characters from a GtkTextView and from the "key-press-event" through a common function. The function uses the GDK keyval form to make a comparison and pass a boolean value back.

Here is a simplified example which returns true for the escape character:

```
def is_char_valid(ch):
    return is_keyval_valid(gtk.gdk.unicode_to_keyval(ch))

def is_keyval_valid(keyval):
    if keyval == 0xff1b: return True
    return False
```

If I pass a keyval to is_keyval_valid() from the "key_press_event" it works fine. However, when I pass a character to is_char_valid() obtained from GtkTextIter.get_char() I get this error:

```
 unicode_to_keyval() argument 1 must be integer<k>, not unicode
```

I don't understand... gtk.TextIter.get_char() returns a unicode character and gtk.gdk.unicode_to_keyval() takes a unicode character as it's argument. What am I missing?

---

### Post by MicahCarrick on 2008-05-13
I figured out...

return is_keyval_valid(gtk.gdk.unicode_to_keyval(**_ord_**(ch)))

---

