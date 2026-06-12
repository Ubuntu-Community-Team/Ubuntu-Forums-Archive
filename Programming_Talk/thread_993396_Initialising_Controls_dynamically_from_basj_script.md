---
title: "Initialising Controls dynamically from basj script in GTK+ Dialog"
date: 2008-11-25
forum: Programming Talk
---

### Post by stefanadelbert on 2008-11-25
Hi

I've created a GTK+ dialog using glade-3 which has some GtkComboBoxEntry controls on it.

I'm wrapping the dialog with a bash script and using autoglade to "run" the dialog from within the script. I can then grab the values of the controls and use them in the script and it works really well. It's more flexible than Zenity, but obviously takes a little more work (the classic trade-off).

The issue is that I would like to initialise or pre-populate the GtkComboBoxEntry's with dynamic items, e.g. entries from previous runs of the script, but can't find info on how to do it. I see that autoglade has an --autoinit option, but I'm not sure that this can be used to populate lists.

Has anyone done something like this before?

Stef

---

### Post by MicahCarrick on 2008-11-26
I'm sorry, I do not have an answer to your question as I've never used autoglade. But, if it gets to the point that you need more flexibility, you may want to give PyGTK a try as it's simple like shell scripting is yet you have full access to the glade file to do what you need.

Good luck.

---

### Post by stefanadelbert on 2008-11-26
Thanks for the reply.

I would ideally like to keep the script in bash as it is essentially just a collection of shell commands (subversion admin commands) that I would normally just have in a bash script anyway.

But you're right - it is more flexibility that I'm after, so I might need to change my approach slightly.

If you have to look back at this thread and feel like putting in a link or two to your favourite PyGTK references and resources, it would be much appreciated.

Stef

---

### Post by dtmilano on 2008-12-22
Quick & dirty:

1) In your glade file use something like this for the GtkComboBox:
```
<property name="items" translatable="yes">${ITEMS}</property>
```

2) Set ITEMS in your env
```
ITEMS="Item 1
Item 2"
```

3) Replace ITEMS
```
perl -pe 's/\${ITEMS}/$ENV{ITEMS}/' < my.glade > /tmp/$$.glade
```

4) Autoglade
```
autoglade /tmp/$$.glade
```


And yes, autoglade should do it automatically.

---

### Post by stefanadelbert on 2008-12-23
Thanks for the help on this. You're right about it being quick and dirty, but it could definitely be made to work.

Since I posted this, I have gone the route of PyGtk and I'm relatively happy with that as a solution. It does add a fair amount of additional complexity to what was otherwise a simple task, but also lends an OO solution which immediately makes for a more feature rich, robust and flexible solution, IMO anyway.

So, in summary:
Zenity is great for notifications and quick and easy (and pretty) user input for scripts, but if you're in need of something more complex, then you'll need to create a custom interface and glade-3 is great for that. Autoglade does really well at rendering your glade interface if the interface is relatively simple, but if the interface requires some underlying intelligence (like dynamic control population in my case or maybe some clever input validation) then PyGtk is a good option (there are bindings into Gtk for other languages, like Ruby [see Ruby-GNOME2] and Perl [see gtk2-perl]).

When designing your glade interfaces, take a look here for some tips and guidelines re. Gnome GUI conformity and considerations: [http://developer.gnome.org/projects/gup/hig/1.0/]("http://developer.gnome.org/projects/gup/hig/1.0/")

---

### Post by dtmilano on 2008-12-24
There's still another case that's worth mentioning. autoglade can be used as a module imported in your PyGtk script to provide the basic plumbing and you do other things as it's usually done.

---

