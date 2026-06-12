---
title: "PyGTK Glade, insert text into TextView"
date: 2007-04-28
forum: Programming Talk
---

### Post by Naatan on 2007-04-28
Hi, I have an app with a textview and I'm trying to insert text into it,

By now I've figured out that your supposed to use a buffer, but I can't figure out how it works exactly.

I've googled a lot, but I can't find anything, sadly there's hardly any glade documentation / reference or tutorials out there.

So, anyone got an idea?

Thanks in advance!

---

### Post by seamless on 2007-04-28
You should have something like the following to load the widget fromt the glade file
```
self.wTree = gtk.glade.XML(gladeFile)
self.entryForText = self.wTree.get_widget("name_of_text_widget_in_glade_file")
```

To put text into the glade file you need to get the buffer then use set_text(). You can do it all in one command like this:
```
self.entryForText.get_buffer().set_text("blah")
```

---

### Post by Naatan on 2007-04-29
Cool, that worked :) Only now every time I use that command it replaces the text that's currently in there, but I need to add it underneath the current text.

Any clue?

---

### Post by seamless on 2007-04-29
The insert function is the one you want to use.
```
self.entryForText.get_buffer().insert(self.entryForText.get_buffer().get_end_iter(),  "\n" + your_text)
```

Take a look at [http://www.pygtk.org/docs/pygtk/index.html]("http://www.pygtk.org/docs/pygtk/index.html") it has all the information about working with GTK widgets in python. Also take a look at /usr/lib/pygtk/2.0/demos/ and [http://www.pygtk.org/tutorial.html]("http://www.pygtk.org/tutorial.html").

---

### Post by Naatan on 2007-04-30
awesome, thank you :)

---

### Post by Nekiruhs on 2007-08-05
Sorry to hijack threads but, I have a list from 
```
variable2 = os.popen('find / -name' + variable)
variable3 = variable2.readlines()
```
And I want to display it in a text view, but it says requires a string not a list, so I did
```
variable2 = os.popen('find / -name' + variable)
variable3 = str(variable2.readlines())
```
But that produces results like```
['/usr/bin/firefox\n', '/usr/bin/exaile\n']
```There all on the same line, with brackets and single quotes around it, and with the newline symbols showing. 

Ideally, I want to have the results display on one per line, with single quotes, but no new line symbol and no brackets. Any way to do this in Python + PyGTK + Glade?

---

### Post by errepunto on 2008-10-14
Hello

The built-in function str() only converts a type into a representable string, but it isn't that you are looking for.

The most simple thing you cand do is read all as an string instead of reading separated lines and joining them using the read method with a negative parameter:
```

variable2 = os.popen('find / -name' + variable)
variable3 = variable2.read(-1)
```

But if you want to build an string from a array of strings you can use the join() method of str objects. Documentation about this method that all (ALL!) strings have is documented in [http://docs.python.org/library/stdtypes.html#string-methods](http://docs.python.org/library/stdtypes.html#string-methods), but you only need to know that it uses an string to concatenate elements of an array.

For example, if you want to join all lines with UNIX end line characters (\n), you can do this:
```

variable2 = os.popen('find / -name' + variable)
variable3 = '\n'.join(variable2.readlines())
``` 

Note that you must call method of the string used to join elements, in this example is the UNIX end line character.

The complete snippet example, including GTK part will be:

```

variable2 = os.popen('find / -name' + variable)
variable3 = variable2.read(-1)
#gtk
self.wTree = gtk.glade.XML(gladeFile)
self.entryForText = self.wTree.get_widget("name_of_text_widget_in_glade_file")
self.entryForText.get_buffer().insert(self.entryForText.get_buffer().get_end_iter(),  variable3)
```

Or this if you want to use the "expensive" form of reading the text:
```

variable2 = os.popen('find / -name' + variable)
variable3 = '\n'.join(variable2.readlines())
#gtk
self.wTree = gtk.glade.XML(gladeFile)
self.entryForText = self.wTree.get_widget("name_of_text_widget_in_glade_file")
self.entryForText.get_buffer().insert(self.entryForText.get_buffer().get_end_iter(),  variable3)
```


Regards.

---

