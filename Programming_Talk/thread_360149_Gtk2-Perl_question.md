---
title: "Gtk2-Perl question"
date: 2007-02-12
forum: Programming Talk
---

### Post by geek_Man on 2007-02-12
A'right, all you Perl Hackers, give a fellow hacker a hand.
I'm trying to make a graphical megabyte converter. Basically you type in a number of standard megabytes, click 'convert', and it spits out the megabytes in binary form. Here's the script I have right now:

```
#!/usr/bin/perl

use warnings;
use Glib qw/TRUE FALSE/;
use Gtk2 '-init';

sub convert() {
    $binary = $data * 1.024;
    print "$data standard megabytes converts to $binary binary megabytes\n";
}

sub delete_event {
    Gtk2->main_quit;
    return TRUE;
}

$window = Gtk2::Window->new('toplevel');
$window->signal_connect(delete_event => \&delete_event);
$window->set_title("Type in a number of megabytes to convert");
$window->set_border_width(20);

$box1 = Gtk2::HBox->new(FALSE, 0);
$window->add($box1);

$entry = Gtk2::Entry->new;
$data = $entry->get_text;    # This is where I'm stuck...

$button = Gtk2::Button->new("Convert");
$button->signal_connect(clicked => \&convert, 'convert');

$box1->pack_start($entry, TRUE, TRUE, 0);
$box1->pack_start($button, TRUE, TRUE, 0);

$entry->show;
$button->show;
$box1->show;
$window->show;

Gtk2->main;

0;

```

It's my first Gtk script, so it might look amatuerish (lots of cutting and pasting). BUT! My question is: how can I get the from text in the $entry widget into a scalar? I looked at the man page for Gtk2::Entry and saw the get_text function, but I don't think it works the way it sounds. Help is much appreciated!

---

### Post by wdk on 2007-02-13
Gtk is event driven, which means that you will have to move the call to get_text into your callback function, otherwise your program will have no idea when to actually read out the data from the entry widget.

For example:
```
sub convert {
     my ($widget, $data) = @_;
     my $text = $data->get_text();
     $text = $text * 1.024;
     print "$text\n";
}
```

Then you need to pass the actual entry widget as an argument to your callback function, so:

```
$button->signal_connect(clicked => \&convert, 'convert');
```

becomes

```
$button->signal_connect(clicked => \&convert, $entry);
```

and you can delete the $data = $entry->get_text line you were having trouble with.

Worked on my system that way... (Ubuntu Edgy)

---

### Post by geek_Man on 2007-02-14
Thanks for your help, wdk. But I gotta say that I'm a little confused. Can you post the completed script? I've tried it a bunch of different ways, but I keep getting exceptions. Thanks again!

---

### Post by geek_Man on 2007-02-14
Nevermind... I got it to work and just like you said, too! Thanks! BTW, welcome to the forums.

---

### Post by wdk on 2007-02-14
I'm glad you got it to work. Just remember that any updates to program data (including changing button and label text) should probably be handled by your callback functions, because that is the only way to break out of the gtk main loop. I'm actually working on a GTK project that requires constant processing outside the main loop and simultaneously checking for and processing events... just haven't had much time to get it to work right

You may find this gtk-perl tutorial useful (lots of sample code):
[http://personal.riverusers.com/~swilhelm/gtkperl-tutorial/]("http://personal.riverusers.com/~swilhelm/gtkperl-tutorial/")

happy hacking!

---

### Post by geek_Man on 2007-02-14
Cool beans, thanks man!

---

### Post by wezzul on 2007-05-14
I have been working with gtk2-perl for a while, and find the lack of documentation somewhat of a problem when working with this.  These are some links that have helped me out:

[http://forgeftp.novell.com//gtk2-perl-study/documentation/html/index.html](http://forgeftp.novell.com//gtk2-perl-study/documentation/html/index.html) (fantastic)
[http://live.gnome.org/GTK2-Perl/Recipes](http://live.gnome.org/GTK2-Perl/Recipes)
[http://gtk2-perl.sourceforge.net/doc/pod/](http://gtk2-perl.sourceforge.net/doc/pod/) (the POD, very useful)

WEZ

---

