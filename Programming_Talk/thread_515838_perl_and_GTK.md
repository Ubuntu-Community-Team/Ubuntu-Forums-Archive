---
title: "perl and GTK"
date: 2007-08-02
forum: Programming Talk
---

### Post by diverdale on 2007-08-02
I'm a noob when it comes to GTK so forgive me.  I'm trying to play with a perl / gtk tutorial and when I run it I get:

Can't locate object method "init" via package "Gnome" (perhaps you forgot to load "Gnome"?) at ./test.pl line 8.

Here's the listing....

#!/usr/bin/perl -w
   
    use strict;
    use Gnome;
    
    my $NAME = 'Hello World';
   
    init Gnome $NAME;
   
   my $w = new Gtk::Window -toplevel;
  
   my $label = new Gtk::Label "Hello, world";
   $w->add($label);
  
   show_all $w;
   
   main Gtk;


Tell me I'm missing something simple.

Thanks!

---

### Post by geek_Man on 2007-08-02
This might be a stupid question, but did you download the Gnome package from CPAN? I tried to "use Gnome;", but it's not part of the release.

---

