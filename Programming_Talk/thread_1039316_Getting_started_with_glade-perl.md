---
title: "Getting started with glade-perl"
date: 2009-01-14
forum: Programming Talk
---

### Post by mikeym on 2009-01-14
Hi,

I've just been writing a couple of perl tests and I came across glade. It looks like it should be perfect for building GUI's with perl. Now I can't seem to find out how to get going with my *.glade* file. I've made the following script according to the only tutorial I can find on the web on this but it doesn't display anything at all (not even an error).

```

#! /usr/bin/perl -w

use strict;
use Gtk2 -init;
use Gtk2::GladeXML;

my $gui = Gtk2::GladeXML->new('dialogue.glade');

# Enter the event loop
Gtk2->main;

__END__ 

```

Could someone point me in the right direction please?

---

### Post by mikeym on 2009-01-14
I should als ostate that I'm ideally looking to be able to use Glade-3. 

Any help would be appreciated.

---

### Post by mikeym on 2009-01-14
Perhaps I havn't got the liberaries installed properly. I've installed everything I can see from Synaptic but every example I can find (which is only a couple) wont run for glade 3 files it just stops without an error.

---

### Post by mikeym on 2009-01-14
I got a reply on this topic on the [GTKForums]("http://www.gtkforums.com/viewtopic.php?p=7049#7049"). It is part of the tutorial [here]("http://www.micahcarrick.com/01-01-2008/gtk-glade-tutorial-part-3.html#3"), but converted for perl.

First install Glade-3 and libgtk2-gladexml-perl with

```
sudo apt-get install libgtk2-gladexml-perl glade-3
```

Then using* Applications>Programing>Glade interface Designer* add a window set tis name and save the project.

Conver the .glade file to a xml with 

```
gtk-builder-convert dialogue2.glade dialogue2.xml
```

Then safe the following as a per script 

```
#!/usr/bin/env perl

use strict;
use warnings;
use utf8;
use Glib qw{ TRUE FALSE };
use Gtk2 '-init';

use subs qw{ main on_window_destroy };


main();

exit(0);


# Subroutines/callbacks
sub main {
	my $builder;
	my $window;

	$builder = Gtk2::Builder->new();
	# Load my glade XML file which I converted from my glade project 
	# using 'gtk-builder-convert'
	$builder->add_from_file( 'dialogue2.xml' );

	# Get my top level object as named in my glade project
	$window = $builder->get_object( 'dialog1' );
	$builder->connect_signals( undef );

	$window->show();
	Gtk2->main();
}

sub on_window_destroy {
    Gtk2->main_quit();
} 

```

---

### Post by Friqenstein on 2009-01-28
mike,

Hi there. I know this may be a bit '*johnny come lately*', but I just recently got back into Glade, so I thought I'd inject some text here.

I was using Glade2 pretty extensively a few years back, but it eventually dwindled to the pile of 'no longer using these apps' for various reasons. One main reason was I fell in love with Perl/Tk and so started writing all my apps (*of somewhat small size*) in Perl/Tk.
With Perl/Tk I could design the GUI as I was writing the meat of the app.

However, I've recently taken up some projects that made me decide to go back to glade because I remember how easily and quickly I could generate a GUI with it... source code and all.
So I installed Glade3 thinking "This is going to be awesome! A few years of no Glade, surely they've made some remarkable improvements!"... boy was I wrong.
IMHO, Glade3 blows compared to Glade2. Granted I've only been using Glade3 for a few weeks now, but I'm not very happy with it. The main factor was that in Glade2 when I build my GUI, I could simply click on the '**Write Source Code**' button, and blamo!
With Glade3, you first have to decide if you want C, or Python, or whatever, then you have to use an external script to generate the XML, then another script to generate everything else. What happened to the ease of flow???
At any rate, it seems that Glade3, and most information/tutorials/examples I find on the net, are Python based. And since I'm not a Python coder, that sort of leaves me with a bitter taste in my mouth. Either I go learn Python, or figure out a way to get Glade3 to generate perl code.

At any rate, I just reinstalled Glade2 a few days ago, and came across a few ideas for generating the perl code.
That's when I came across your post here. (because I use Ubunu :) )

I'm going to give your post a try and see what I can come up with. Hopefully I have good luck as you did.
Kudos to figuring out your own problem, and sorry I didn't find this earlier.
At least I know I'm not the only person on this rock that wants to use perl with glade.

---

### Post by hokiegrad on 2010-01-30
I decided to try out Gtk2::GladeXML and found the glade-article that tries to create a timer app, and had the same problem as mikeym, thus finding this article...

Well not wanting to give up trying to get the tutorial to work, I found the problems...

First, the tutorial makes no mention that the project should be saved in the libglade file format and not the GtkBuilder file format.  I suppose this should be obvious since the Gtk2::GladeXML package is a libglade interface.

Second, Glade does not set the "Visible" property to "Yes" for window1 by default.  So
if you followed the directions correctly you would get an invisible window with no way to make it visible. (without adding code to the sample).

Hopefully this helps the fourth person on this rock that wants to use perl with glade.

---

