---
title: "Perl Gtk2 Radio Button assistance"
date: 2007-01-01
forum: Programming Talk
---

### Post by johnnymac on 2007-01-01
Hey all...

I need a quit and dirty how to for setting up the signal_connect, callback, etc when using RadioButtons with Perl-Gtk2.

Something simple enough like selecting apples, oranges, or peaches and then displaying what was selected via the callback method.  I know how to get the radio buttons to show up and work as a group but I'm not sure how to get the signal handling to work.

Here's my example script if anyone would like to just "throw in" the help.

```

#!/usr/bin/perl
use Glib qw/TRUE FALSE/;
use Gtk2 '-init';

#callback method for radio button goes here

#delete callback
sub delete_event
{
	Gtk2->main_quit;
	return FALSE;
}

#do the GUI crud
$window = Gtk2::Window->new('toplevel');
$window->set_title("Table");
$window->signal_connect(delete_event => \&delete_event);
$window->set_border_width(20);

# Create a 6x6 table
$table = Gtk2::Table->new(6, 6, TRUE);
$window->add($table);

#create radio buttons
$radiobutton = Gtk2::RadioButton->new(undef,"Apples");
$table->attach_defaults($radiobutton,0,1,1,2);
$radiobutton->set_active(TRUE);
$radiobutton->show;
@group = $radiobutton->get_group;

$radiobutton = Gtk2::RadioButton->new(@group,"Oranges");
$table->attach_defaults($radiobutton,1,2,1,2);
$radiobutton->show;

$radiobutton = Gtk2::RadioButton->new(@group,"Peaches");
$table->attach_defaults($radiobutton,2,3,1,2);
$radiobutton->show;

$table->show;
$window->show;

Gtk2->main;

0;

```

---

### Post by Snargle on 2007-01-03
Radio buttons inherit from checkbuttons, togglebuttons, etc., so you sometimes have to look there for methods and signals.

```
#!/usr/bin/perl
use Glib qw/TRUE FALSE/;
use Gtk2 '-init';

#callback method for radio button goes here

#delete callback
sub delete_event
{
	Gtk2->main_quit;
	return FALSE;
}

#do the GUI crud
$window = Gtk2::Window->new('toplevel');
$window->set_title("Table");
$window->signal_connect(delete_event => \&delete_event);
$window->set_border_width(20);

# Create a 6x6 table
$table = Gtk2::Table->new(6, 6, TRUE);
$window->add($table);

#create radio buttons
$radiobutton = Gtk2::RadioButton->new(undef,"Apples");
$table->attach_defaults($radiobutton,0,1,1,2);
$radiobutton->set_active(TRUE);
$radiobutton->show;
@group = $radiobutton->get_group;

$radiobutton = Gtk2::RadioButton->new(@group,"Oranges");
$table->attach_defaults($radiobutton,1,2,1,2);
$radiobutton->show;

$radiobutton = Gtk2::RadioButton->new(@group,"Peaches");
$table->attach_defaults($radiobutton,2,3,1,2);
$radiobutton->show;

$radiobutton->signal_connect('toggled'=> sub{print 'being toggled on/off'."\n";
                                print 'active is ' . $radiobutton->get_active . "\n"});
$radiobutton->signal_connect('activate'=>sub{print 'activated'."\n"});
$radiobutton->signal_connect('clicked'=>sub{print 'clicked'."\n"});
$radiobutton->signal_connect('enter'=>sub{print 'enter'."\n"});
$radiobutton->signal_connect('group-changed'=>sub{print 'group-changed'."\n"});

$table->show;
$window->show;

Gtk2->main;

0;
```

---

