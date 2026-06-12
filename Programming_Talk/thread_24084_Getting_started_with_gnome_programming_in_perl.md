---
title: "Getting started with gnome programming in perl"
date: 2005-04-05
forum: Programming Talk
---

### Post by jnoreiko on 2005-04-05
I'm a reasonably confident perl programmer. On Windows I've used Tk to create GUI apps.
I've done some searching about perl and gnome, and it looks like the wya to go is GTK, but I'm a bit confused about what I've read so far. There's various glade packages listed in synaptic, there's things called gnome on CPAN... basically, what do I need to install to get started? (I've already got bluefish :)

---

### Post by ow50 on 2005-04-05
You'll probably get started with:
```
$ sudo apt-get install gazpacho glade-gnome2 libgtk2-perl libglib-perl libgnome2-perl libgtk2-gladexml-perl
```

No need for CPAN, just apt-get.

Glade and gazpacho are gui design apps. Gazpacho appers to be newer and better, but I haven't tried it yet. Those apps will generate a .glade xml file of the gui. Then import it in your perl code with something like:
```
$self->{glade_xml} = Gtk2::GladeXML->new('foo.glade');
```
and load widgets from it with something like:
```
$self->{window} = $self->{glade_xml}->get_widget('window');
```

I'm not sure if I covered all required libs in that list.

---

### Post by jnoreiko on 2005-04-05
[QUOTE=ow50]I'm not sure if I covered all required libs in that list.[/QUOTE]

Either that, or this hello world tutorial I found is REALLY out of date! [http://www.perl.com/pub/a/2000/10/gnome.html](http://www.perl.com/pub/a/2000/10/gnome.html)

---

### Post by jnoreiko on 2005-04-06
I've just managed to run the script at [http://gtk2-perl.sourceforge.net/doc/examples/colorbutton-full.pl](http://gtk2-perl.sourceforge.net/doc/examples/colorbutton-full.pl) , so it must be working! Yay!

Thanks :)

---

