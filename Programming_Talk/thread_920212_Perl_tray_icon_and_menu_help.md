---
title: "Perl tray icon and menu help"
date: 2008-09-15
forum: Programming Talk
---

### Post by scragar on 2008-09-15
OK, so I took I'm learning Gtk2 with perl, and I've managed to be able to create windows and icons etc, but the one thing I can't get working is to make a window associated with a tray icon like most programs have.

I've been looking over the checkmail source, since I know this is written in perl and uses the tray icon.

From the checkgmail source to make the menu appear they call this function:
[php]sub pack_menu {
	# This code (and the relevant menu display routine) is based 
	# on code from yarrsr (Yet Another RSS Reader) (http://yarrsr.sf.net)

	$menu = Gtk2::Menu->new;
	
	my $menu_check = Gtk2::ImageMenuItem->new($trans{menu_check});
	$menu_check->set_image(Gtk2::Image->new_from_stock('gtk-refresh','menu'));
	$menu_check->signal_connect('activate',sub {
		queue_check();
		foreach my $label (keys(%label_delay)) {
			queue_check($label);
		}
	});
#
#        ... create a few more items in the same way
#

	my $menu_quit = Gtk2::ImageMenuItem->new_from_stock('gtk-quit');
	$menu_quit->signal_connect('activate',sub {
			Gtk2->main_quit;
	});
	
	# Pack menu ...
	$menu->append($menu_check);
	$menu->append($menu_undo) if $cookies;
	$menu->append($menu_compose);
	$menu->append(Gtk2::SeparatorMenuItem->new);
	$menu->append($menu_prefs);
	$menu->append($menu_about);
	$menu->append(Gtk2::SeparatorMenuItem->new);
	$menu->append($menu_restart);
	$menu->append($menu_quit);
	
	$menu->show_all;
}[/php]

I tried duplicating this code(both in an edited, and an edited version), but nothing appears to make it appear, any help finding what I'm missing?

---

### Post by forger on 2008-09-15
Since you're not showing your code I can't think anything else except:
1) installed dependencies?
```
sudo apt-get install libgtk2-perl libgtk2-gladexml-perl
```
2) did you define dependencies in perl script?
3) You didn't execute Gtk2->main ?
4) You have errors you didn't post? :)

[http://gtk2-perl.sourceforge.net/doc/gtk2-perl-tut/ch-GettingStarted.html#sec-HelloWorld](http://gtk2-perl.sourceforge.net/doc/gtk2-perl-tut/ch-GettingStarted.html#sec-HelloWorld)

I would also suggest on using [glade]("apt://glade") to create your window:
[http://search.cpan.org/dist/Gtk2-GladeXML/GladeXML.pm](http://search.cpan.org/dist/Gtk2-GladeXML/GladeXML.pm)

---

### Post by scragar on 2008-09-15
I didn't post my code because much of it is unrelated, all I really did was copy and paste that function (other than using my to declare the $menu) into my code:
[php]BEGIN{
  sub showMenu{
## tried with and without this:
#  Gtk2->main_quit;
    my $menu = Gtk2::Menu->new;
    my $menu_quit = Gtk2::ImageMenuItem->new_from_stock('gtk-quit');
    $menu_quit->signal_connect('activate',sub {
      Gtk2->main_quit;
      CleanUp();
      exit;
    });
    $menu->append($menu_quit);
    $menu->show_all;
## tried with and without this line:
#  Gtk2->main;
  }
}[/php]
Then I called this when I click a button(I'm susspecting that's the problem, but the checkgmail code doesn't appear to set the menu's location anywhere(from the related code anyway), so I don't think this is related):
[php]
my $button2 = Gtk2::Button->new("Show Menu");
$button2->signal_connect( "clicked", \&showMenu );
[/php]
I don't get any errors when I run the code(and using **print $menu** shows that $menu is being set right)

---

### Post by scragar on 2008-09-15
Bah, forget it, after a bit of searching I found the function I needed(**$menu->popup**)

---

