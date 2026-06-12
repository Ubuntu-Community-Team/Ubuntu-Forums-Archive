---
title: "HOW-TO Glade with Perl-Gtk2"
date: 2010-07-02
forum: Programming Talk
---

### Post by Unterseeboot_234 on 2010-07-02
I spent some time discovering how Gtk2 binds with perl, but then again I was also learning perl. One of the problems is perl / glade / Gtk2 are moving targets when we speak of current tutorials. I hope you can use this.

1. Glade is a front-end to select widgets from a pallet, to make up components to include with your software. The final result is an <xml> file. Other Linux libs (such as Glib) can read that information to compose your component onto the screen. Get the latest Glade from Ubuntu repositories. There are many antiquated tutorials about Glade on the internet.

2. Gtk2 is a library, written in C. You probably already have it. Gnome Toolkit is the widgets.

3. Perl is a scripting language with a large community of authors. A reusable block of perl code is called a module.pm. We write our own code to provide the logic. Otherwise, Glade's <xml> file, and perl-gtk2.pm will magically bind buttons to functions.

I mentioned the many Glade Tuts on the web are rather dated. Furthermore, they all spend the first 15 pages doing an unnecessary walk-thru of Glade's features. You do need some of that walk-thru. Get this pdf down load...

[**http://live.gnome.org/GTK2-Perl/GladeXML/Tutorial**]("http://live.gnome.org/GTK2-Perl/GladeXML/Tutorial")

The recent Glade changes a couple of things. Used to be, you declared what TYPE of output for Glade to make. Today, we can also SaveAs.. to [] GtkBuilder or [x] Libglade from the File Navigator dialog. GtkBuilder is the default, you want libglade for this How-To. The difference is the schema-structure of <xml> that Glade will write.

Perl-gtk (ubuntu repositories) is the bindings. Used to be: we had to run a separate program to translate <xml> for use with this lib. No more. This library now takes the <xml> from Glade as it is.

If you downloaded the pdf I mention above, it is from Grant McLean of New Zealand. He does a wonderful job as a demonstration but doesn't give us his code listing. Here it is, two files...

```
#!/usr/bin/perl -w
# starttime.pl

use strict;

use FindBin;
use lib $FindBin::Bin;

use TalkTimer;

TalkTimer->run;

```

```
package TalkTimer;

use strict;
use warnings;

use Gtk2 -init;
use Gtk2::GladeXML;

use Glib qw(TRUE FALSE);

use base 'Class::Accessor::Fast';

__PACKAGE__->mk_accessors(qw(
	label progress start_stop start_time running warned times_up) );

use constant TIMER_MAXIMUM => 5 * 60;
use constant TIMER_WARNING => 4 * 60;

sub run { my $self = shift->new; Gtk2->main; }

sub new { return bless({}, shift)->_init; }

sub _init {
	my $self = shift;

	my $glade_file = __FILE__;

	$glade_file =~ s/TalkTimer.pm/talk-timer.glade/;
	my $gui = Gtk2::GladeXML->new('talk-timer.glade');
	$gui->signal_autoconnect_from_package($self);
	
	$self->label		($gui->get_widget('timer_label') );
	$self->start_stop	($gui->get_widget('start_stop')  );
	$self->progress		($gui->get_widget('progress_bar'));

	$self->label->modify_font(
	Gtk2::Pango::FontDescription->from_string("Sans 36") );

	$gui->get_widget("appwin")->show();


	return $self;
}

sub on_start_stop_clicked {

	my $self = shift;

	if($self->running) {
		$self->stop_timer;
	}
	else {
		$self->start_timer;
	}
}

sub start_timer {
	my $self = shift;

	$self->start_time(time);
	$self->running( TRUE );
	$self->warned( FALSE );
	$self->times_up( FALSE );
	$self->start_stop->set_label('Stop');
	Glib::Timeout->add(1000, sub{ $self->tick });
}

sub stop_timer {
	my $self = shift;

	$self->running( FALSE );
	$self->label->set_text('0:50');
	$self->progress->set_fraction(0 );
	$self->start_stop->set_label('Start');
}

sub tick {
	my $self = shift;
	
	return FALSE unless $self->running;

	my $secs = time - $self->start_time;
	$self->label->set_text(
		sprintf('%d:%02d', int($secs/60), $secs % 60)
	);

	my $frac = $secs > TIMER_MAXIMUM ? 1 : $secs/TIMER_MAXIMUM;
	$self->progress->set_fraction($frac);

	if($secs >= TIMER_MAXIMUM and !$self->warned) { 
		$self->times_up(TRUE);
		# play tune
	}
	elsif($secs >= TIMER_WARNING and !$self->warned) {
		$self->warned(TRUE);
		# play tune
	}
	return TRUE;
}


sub on_appwin_destroy {
	Gtk2->main_quit();
}

1;
```

---

