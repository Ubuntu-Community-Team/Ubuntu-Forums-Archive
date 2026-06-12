---
title: "gtk2 perl confusion"
date: 2010-09-16
forum: Programming Talk
---

### Post by alexxxm on 2010-09-16
I hope some gtk2/perl guru will be able to lend a hand... I come from the perl/tk world and I'm utterly confused!

THE PROBLEM
I want to embed an X application in my program (an RTF word processor, say kwrite, openoffice...). In Perl/Tk I was able to do it, as long as the X application supported embedding, e.g.:
xterm -into <ID>
mplayer -wid <ID>
dillo -x <ID>
Then somebody suggested me that in Gtk2/Perl you could do it with whatever application, but I'm stuck.
These are 2 solutions I assembled so far - but they dont work!
(I tried to embed gnome-dictionary as a test)

SOLUTION1
```

#!/usr/bin/perl
use warnings;
use Gtk2 '-init';
use Gnome2::Wnck;

my $id;
my $screen = Gnome2::Wnck::Screen -> get_default();
$screen -> force_update();
my @windowslist = $screen -> get_windows();

foreach my $w (@windowslist) {
  my $name = $w -> get_name();
  my $class_name = $w -> get_class_group() -> get_name();
  $id = $w -> get_xid();

  if($name eq "Dictionary")
  {
  print <<"EOS";
$w
  name: $name
  class name: $class_name
  id $id
EOS

  return;
  }


my $window = new Gtk2::Window;
$window->resize (500, 200);
$window->signal_connect (destroy => sub { Gtk2->main_quit; });

my $vbox = Gtk2::VBox->new(FALSE, 6);
$window->add($vbox);

my $entry = Gtk2::Entry->new;
my $socket = new Gtk2::Socket;

$vbox->pack_start($socket, TRUE, TRUE, 0);
$vbox->pack_start($entry, TRUE, TRUE, 0);

$socket->add_id($id);
$window->show_all;

Gtk2->main;

}

```

This approach creates a new window with simply an entry line in it, and doesnt embed gnome-dictionary. No errors, no warnings.


SOLUTION 2

The second one relies on a C program that acquires the xid of the program to be embedded, and passes it to the perl program:
```

#include <stdio.h>
#include <X11/Xlib.h>
#include <X11/Xutil.h>

int main(int argc, char *argv[]) {
    int i;
    unsigned int number_of_children;

    Display *display;
    Window window, root, *children, window_root, window_parent;
    XClassHint class_hint;
    XTextProperty wmname;

    if(argc<=1){printf("Please provide a window name as an argument\n");return 1;}
    if (!(display = XOpenDisplay(":0.0"))) {printf("no display\n");return 1;};
    if (!(root = DefaultRootWindow(display)))  {printf("no default root window\n");return 1;};
    if (!(XQueryTree(display, root, &window_root, &window_parent, &children, &number_of_children)))  {printf("no Xquerytree\n");return 1;};
    if (!(number_of_children > 0))  {printf("no children\n");return 1;};

    for (i=0;i<number_of_children;i++) {
        if (!XGetWMName(display, *(children+i), &wmname)) continue;
        if (!XGetClassHint(display, *(children+i), &class_hint)) continue;

        if (strcmp(argv[1], (char *) wmname.value) == 0)
         {
            window = *(children+i);
            break;
         }
    }
    if (number_of_children > 0) XFree(children);
    if (i == number_of_children) return 1;

   printf("%d", window);

}

```

```

#!/usr/bin/perl -w

use strict;
use Gtk2 '-init';

my $windowname=$ARGV[0];

my $window_id_of_program_to_embed=`getwindowid2 $windowname`;
if($window_id_of_program_to_embed eq '')
{print"no window $windowname found\n"}
else
{print"$windowname is at xid <$window_id_of_program_to_embed>\n"}

my $window = new Gtk2::Window;
my $socket = new Gtk2::Socket;

$window->add($socket);
$socket->add_id($window_id_of_program_to_embed);
$window->show_all;

Gtk2->main;


```

This approach (launch it by "<perlprogramname> Dictionary") after printing the info:
Dictionary is at xid <46137345>,
creates a ver small square window, with nothing in it. No warnings, no errors.

I am so frustrated... hope somebody could at least point me in the right direction!

Thank you for your time!


alessandro

---

