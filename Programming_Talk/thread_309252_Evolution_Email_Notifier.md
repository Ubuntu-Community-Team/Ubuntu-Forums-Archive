---
title: "Evolution Email Notifier"
date: 2006-11-29
forum: Programming Talk
---

### Post by bradleyd on 2006-11-29
Hello all,
I am a network admin for the county where I live. I am the only person in the county that has any Linux or Unix knowledge. When I got here it was a windwos world, all MSCE's. Now there is one LPIC. Since my arrival I have switched some of the machines over to Linux. Our DNS and FTP servers are now running Ubuntu.(Have been a Debian fan, gave Ubuntu a try and very pleased)I am now converting some of the desktops to Ubuntu. All is going well. I am going through the usual growing pains, "I can't find anything?", "where is Internet Explorer?", "Where is Word?", etc...One real request that I got was there was no email notify? I pointed out there is one, you can add it to the panel. They didn't like that much. We use exchange 2003 as our email server, so I have the "guinea pigs" use Evolution. The users seem to be somewhat comfortable with it. I searched for a email notify script or something similar to Outlooks notify message window. I have found a few, but still no love from the new users. They wanted to see the subject and who it was from, so they could decide wheter to stop working or read email later. I decided to give them what they want and write my own. I wrote it in perl, I know Ubuntu loves there Python, but I am still currently learning Python and more versed in perl. 
     The app shows the subject and who it is from in a message box and puts an icon in the tray. Not anything fancy, but new users seem to like it. I thought I would post the code and how to if anyone is interested. Like I said it is simple but effective. Please feel free to change it in anyway. Ok enough blabber and heres the code and how to.

*****use must have perl installed and and perl gtk2, you can get it from CPAN **[http://search.cpan.org/~tsch/Gtk2-1.141/Gtk2.pm]("http://search.cpan.org/%7Etsch/Gtk2-1.141/Gtk2.pm")****

[B]***The Code
#!/usr/bin/perl -w
#bsmith 11/02/2006
use Gtk2 '-init';
use Gtk2::TrayIcon;



my @email=grep /^(subject|from):/i,<STDIN>;
my $window = Gtk2::Window->new;
$window->set_title ("New Mail");
$window->signal_connect (delete_event => sub {Gtk2->main_quit; TRUE});
$window->set_icon_from_file('/path to icon/some-email-icon.gif');
my $tview= Gtk2::TextView->new();

my $content = "@email";
my $buffer = $tview->get_buffer();
$buffer->set_text($content);
$tview->set_cursor_visible (0);
$tview->set_editable(0);
my $pic = Gtk2::Image->new_from_file('/path to icon/some-email-icon.gif');
my $icon= Gtk2::TrayIcon->new('trayicon');
my $button = Gtk2::ToolButton->new($pic,'NULL');

$icon->add($button);
$button->signal_connect (clicked => sub {system($ARGV[0]);Gtk2->main_quit; 1});

$icon->show_all;
$window->add($tview);
$window->show_all;
Gtk2->main;[/B]

*****make sure you place the right path to the icon you choose, I chose a simple envelope icon. You will have to adjust icon size so it fits in notification tray area. I had to use 35x35, it will depend on your resolution.*******

Next place your new script and icon in a folder called EvoTray(you can change it to whatever you want)chmod a+x whatever you named your perl script, I called it evotray.pl. I also made sure the path icon reflected the new folder it resides in.

Fire up evolution and goto Edit-->Message Filters.
Then click add. In the filter search name field type EvoTray. Leave the default rule as is, just add your email address to text box right of contains. Now go down to second panel under Then, and change move to folder to "Pipe To Program". Then hit browse and navigate to EvoTray folder or what ever you called it, and select EvoTray.pl  I have included a screenshot of what it looks like under the filter setup.

Now the final truth, with evolution open highligth an email sent to you and hit ctr-y, this should pop up a window with subject and from. There also should be your icon in the notification tray. I include a screenshot of what it should look like.

That's pretty much it. Not much to it. just though I would share it. Like I said feel free to change it in anyway. Any questions or comments are welcome. I am going to port this to Python and add a few changes, will post back with that when I am finished.
Thanks,
bradleyd

---

### Post by kaamos on 2006-11-29
Very nice! Althought the focus stealing window is a usability nightmare, this is a feature that evo is lacking. Just started to explore how to pipe the data to libnotify. :)

---

### Post by bradleyd on 2006-11-29
yeagh I want to fix that in the next one. I am playing with wxPython right now and using tray icon and ballon tip to display email info instead of popup window.

---

### Post by tjk on 2006-12-01
Wow - just what I've been wanting...  can this be made into an official plugin? (as I know nothing about programming and wouldn't be able to set this up)

---

### Post by bradleyd on 2006-12-01
I don't know about plugin, but you can install it easy. If my instructions are easy to follow let me know I can walk you through it.

---

### Post by zadig on 2007-12-08
I would really like this, if I could actually make it run. I dont see any errors when i run it. I dont see any tray icons either, I dont see any popups when new email arrives and so on. I just dont what's wrong as i dont get any errors

---

### Post by bradleyd on 2007-12-09
Zadig,
so from the command line if you run:
  ```
perl mail.pl 
```
nothing happens? Does the cursor jump down to a new line?
Try typing 
```
Subject:
```
then press:
```
ctr-l d
```
There should be a icon in the tray and a window frame in the left hand corner of the desktop.

If this still does not work, post back a screen shot.

---

### Post by zadig on 2008-04-03
I've switched to thunderbird :S 
I even uninstalled evolution.

---

