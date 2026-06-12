---
title: "How do I build Glade? (latest version)"
date: 2010-09-12
forum: Programming Talk
---

### Post by fallenshadow on 2010-09-12
I have attempted to build Glade with the following options:

```

Configuration:

	Source code location:	 .
	Compiler:		 gcc
	GTK+ UNIX Print Widgets: yes
	GNOME UI Widgets:	 no
	PYTHON Widgets support:	 yes

	Build Reference Manual:  no
	Build User Manual:       yes


```

It did build but when I ran the app the widgets were missing! Not very useful. :D

I think I need to have "GNOME UI Widgets" set to yes for it to build. (and have widgets) However I don't know what package to install to get this support. Anybody know?

---

### Post by kamicc on 2010-09-12
Hmmm... Just look here: [http://packages.ubuntu.com/dapper/glade-gnome](http://packages.ubuntu.com/dapper/glade-gnome)

It says:
```

libgnomedb2-dev 
Database UI widget library for GNOME2 -- development files

```

Does it work? :)


/edit/ My fault.  
[http://packages.ubuntu.com/hardy/glade-3](http://packages.ubuntu.com/hardy/glade-3)

```
You can install the glade-gnome package to provide GNOME widgets, for instance.
```

Does it mean that not only libgnomedb2-dev is needed?

---

### Post by fallenshadow on 2010-09-12
Ah finally I found it. It was called gnomeui-dev.

When you installed it installs a ton of other Gnome packages. However now the message from ./configure is:

```
Configuration:

	Source code location:	 .
	Compiler:		 gcc
	GTK+ UNIX Print Widgets: yes
	GNOME UI Widgets:	 yes
	PYTHON Widgets support:	 yes

	Build Reference Manual:  no
	Build User Manual:       yes

```

Still doesn't work though... im not sure why. :confused:

---

### Post by fallenshadow on 2010-09-12
Ok im gonna give up on this... its going no where at all!](*,)

---

### Post by pbrane on 2010-09-12
I downloaded glade-3.7.1 dev source. Then I did a 
```

./configure --prefix=/usr

```
I ended up with this config:
```


Configuration:

	Source code location:	 .
	Compiler:		 gcc
	GTK+ UNIX Print Widgets: yes
	GNOME UI Widgets:	 no
	PYTHON Widgets support:	 yes

	Build Reference Manual:  no
	Build User Manual:       yes

```
gnomeui is not needed, and in fact is headed towards planned deprecation. Most of the widgets have already been ported to GTK+.

Then I did a 
```

make

```

then I **cd**'d to **src/** and ran it like this
```

./glade-3 &

```
and it ran just fine.

If I wanted to install it, I would do a **sudo make install**, which would install glade-3 into **/usr/bin**

There are some dependencies that you may not have installed. I currently have glade 3.6.7 installed from the repos.

This is what you may need if you don't have glade installed from the repos.
[B]python-gobject-dev docbook-xsl python-gtk2-dev python-gtk2-doc python-dev
  libffi-dev libgladeui-1-9 libglade2-dev python2.6-dev docbook-xsl-doc-html
[/B]
I would recommend installing glade from the repos and then remove just glade, leave the *un-needed* dependencies. Then install glade from source. I'm making a lot of assumptions here about what you are doing.

---

### Post by fallenshadow on 2010-09-12
Excellent! I was on the verge of giving up but not anymore! 8-)

This was the important bit.

> --prefix=/usr

It made all the difference! :) Now I just gotta find the Toolpalette in this!

---

