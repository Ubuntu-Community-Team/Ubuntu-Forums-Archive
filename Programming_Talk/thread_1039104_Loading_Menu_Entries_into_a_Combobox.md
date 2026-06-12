---
title: "Loading Menu Entries into a Combobox"
date: 2009-01-14
forum: Programming Talk
---

### Post by mikeym on 2009-01-14
Hi,

I'm trying to load the items from the Sound and Video menu into a combobox so that they can be used as the default video player for DVD/SVCD/HVD etc. 

So far I've loaded the .desktop files and searched for the ones in the AudioVideo category. And filered out the ones with NoDisplay=true but it still loads a bunch of items which are turned off in my menu. 

Does anyone have any good ideas how to approach this?

This is my script so far:

```

#! /usr/bin/perl
use warnings;
use strict;
use Gtk2 '-init';
use Glib qw/TRUE FALSE/;
#use MIME::Base64;
#use Data::Dumper;

our (@apps, @sizes);

my $icontheme = Gtk2::IconTheme->get_default();

#standard window creation, placement, and signal connecting
my $window = Gtk2::Window->new('toplevel');
$window->set_default_icon($icontheme->load_icon("gstreamer-properties", 16, 'no-svg'));
$window->signal_connect('delete_event' => sub { Gtk2->main_quit; });
$window->set_border_width(5);
$window->set_position('center_always');
$window->set_title('multimedia video selector');

#this vbox will return the bulk of the gui
my $vbox = &ret_vbox();

#add and show the vbox
$window->add($vbox);
$window->show();

#our main event-loop
Gtk2->main();
##########################################################################
sub readdesktops($) {
	my ($dir) = @_;
	opendir(APPS, $dir) or die "Can't open $dir: $!";
	while( defined (my $file = readdir APPS) ) {
		if($file =~ /.desktop$/ && -T "$dir/$file") {
			my $video = 0;
			my $nodisplay = 0;
			my $icon = "";
			my $app = "";
			#print "$file\n";
			open(FILE, "$dir/$file") or die "Can't open \"$dir/$file\": $!";
			while(<FILE>) {
				if (/^Icon= *(.+)$/i) {
					$icon = $1;
				} elsif (/^Name= *(.+)$/i) {
					$app = $1;
				} elsif (/^Categories= *(.+)AudioVideo/i) {
					$video = 1;
				} elsif (/^NoDisplay=true$/i) {
					$nodisplay = 1;
				}
			}
			close FILE;
			if($app && $video && !$nodisplay) {
				push(@apps,[$app, $icon, $file]);
			} 
		}
	}
	closedir(APPS);
}

sub ret_vbox {

	my $vbox = Gtk2::VBox->new(FALSE,5);

	&readdesktops("/usr/share/applications");
	&readdesktops("/usr/local/share/applications/");

	# Sort mutlti dimentional array
	@apps = sort { lc($a->[0]) cmp lc($b->[0]) } @apps; 

	my $list_store = Gtk2::ListStore->new ('Gtk2::Gdk::Pixbuf', 'Glib::String');

	for my $i (0..$#apps) {
		my $bunny;
		my $file = $apps[$i][1];
		#print "$file\n";
		if($icontheme->has_icon("$file")) {
			#@sizes = $icontheme->get_icon_sizes ("$file");
			#print @sizes;
			eval{
				### try block
				$bunny = $icontheme->load_icon("$file", 24, 'no-svg');
			};
			if ($@){
				### catch block
				print "Waring: Failed to load icon \"$file\"!\n";
				undef($bunny);
			};
		} else {
			if ( -f "$file" ) { 
				print "Icon:$file\n"; 
				$bunny = Gtk2::Gdk::Pixbuf->new_from_file_at_scale($file, 24, 24, 1);
			} elsif($file =~ /\.(ico|png|xpm)$/i && -f "/usr/share/pixmaps/$file" ) {
				print "Pixmap:$file\n"; 
				$bunny = Gtk2::Gdk::Pixbuf->new_from_file_at_scale("/usr/share/pixmaps/$file", 24, 24, 1);
			} else {
				undef($bunny);
			}
		}
		my $iter = $list_store->append;
		$list_store->set ($iter, 0 =>$bunny );
		$list_store->set ($iter, 1 =>$apps[$i][0]);
	}
	#$width = $image->get_width;
	#$height = $image->get_height;


	# my $combo_box = Gtk2::ComboBox->new_text; #will cause slew of errors with pixbufs
	# $combo_box->set_model($list_store);

	my $combo_box = Gtk2::ComboBox->new($list_store);

	my $renderer = Gtk2::CellRendererPixbuf->new;
	$combo_box->pack_start ($renderer, FALSE);
	$combo_box->add_attribute ($renderer, pixbuf => 0);

	$renderer = Gtk2::CellRendererText->new;
	$combo_box->pack_start ($renderer, TRUE);
	$combo_box->add_attribute ($renderer, text => 1);


	$combo_box->set_wrap_width (1);
	$combo_box->signal_connect('changed' => sub {
		my ($combo_box) = @_;
		my $iter = $combo_box->get_active_iter;
		print 'iter-> ',$combo_box->get_active_iter,"\n";
		print 'index-> ',$combo_box->get_active,"\n";

		#only works easily when text is first in cell
		# print 'text-> ', $combo_box->get_active_text,"\n";

		print "\n";
	});

		$combo_box->set_active(0);

		$vbox->pack_start($combo_box,TRUE,TRUE,0);
		$vbox->show_all();
		return $vbox;
}

__END__ 

```

---

