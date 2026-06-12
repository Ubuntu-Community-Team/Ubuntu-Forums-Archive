---
title: "Is there any library for reading/writing/parsing simple config files?"
date: 2010-04-30
forum: Programming Talk
---

### Post by Daniil on 2010-04-30
I need a small library for working with my config file but can't find any. LibXML2 is too big for saving 8 flat parameters, I think :)

But I am too lazy to write own library (bicycle) and it not a unix-way :)

---

### Post by MadCow108 on 2010-04-30
there is boost::program_options which can also read/write configuration files:
[http://www.boost.org/doc/libs/1_42_0/doc/html/program_options.html](http://www.boost.org/doc/libs/1_42_0/doc/html/program_options.html)

---

### Post by Daniil on 2010-04-30
> **MadCow108 said:**
> there is boost::program_options which can also read/write configuration files:
[http://www.boost.org/doc/libs/1_42_0/doc/html/program_options.html](http://www.boost.org/doc/libs/1_42_0/doc/html/program_options.html)

Thanks, but sorry, I forgotten to say, that program is on pure C. And Boost is C++ specific.

---

### Post by loell on 2010-04-30
how about YAML and its respective parsers?

---

### Post by nvteighen on 2010-04-30
Uh... is the file written by you in no specific well-known standard? If so, I don't see any problem in writing your own code for this.

---

### Post by Daniil on 2010-04-30
> **loell said:**
> how about YAML and its respective parsers?

Thanks for open to me this new technology. But, I think, it is similar heavy as XML for my application.

---

### Post by Daniil on 2010-04-30
> **nvteighen said:**
> Uh... is the file written by you in no specific well-known standard? If so, I don't see any problem in writing your own code for this.

No, application should write and read. And I want to use popular format:

# comment
[My_Section]
value1 = "qwe"
  value2= 123

I.e., read/write functions can be written quickly, but I don't want to reinvent the wheel :)

---

### Post by SledgeHammer_999 on 2010-04-30
Then if you're using Gtk you can use the appropriate glib functions. They are perfect for *.ini-like config files.

link->[http://library.gnome.org/devel/glib/stable/glib-Key-value-file-parser.html](http://library.gnome.org/devel/glib/stable/glib-Key-value-file-parser.html)

---

### Post by Daniil on 2010-04-30
> **SledgeHammer_999 said:**
> Then if you're using Gtk you can use the appropriate glib functions. They are perfect for *.ini-like config files.

link->[http://library.gnome.org/devel/glib/stable/glib-Key-value-file-parser.html](http://library.gnome.org/devel/glib/stable/glib-Key-value-file-parser.html)

Yes, I use Gtk.
This is what I was looking for. Thanks a lot!

---

### Post by sheperson on 2010-04-30
> **SledgeHammer_999 said:**
> Then if you're using Gtk you can use the appropriate glib functions. 

Is there anything similar to that in Qt?

---

### Post by the_unforgiven on 2010-04-30
> **sheperson said:**
> Is there anything similar to that in Qt?
Does [QSettings]("http://doc.trolltech.com/3.3/qsettings.html") class help?

---

### Post by phrostbyte on 2010-04-30
There is also libconfuse. It makes UNIX-style config files instead of .ini

---

