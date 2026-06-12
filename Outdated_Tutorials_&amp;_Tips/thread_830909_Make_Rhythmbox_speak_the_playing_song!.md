---
title: "Make Rhythmbox speak the playing song!"
date: 2008-06-16
forum: Outdated Tutorials &amp; Tips
---

### Post by aaargh486 on 2008-06-16
Sometimes I listen to music with my screen turned off while doing something else. But sometimes when it goes to the next song I can't remember it and I have to turn on the screen for a while, look at the song and turn it back off.
As this is a bit irritating so I found a solution. I made my computer speak.

You'll need to install these packages in Synaptic to make it work:
```

libnet-dbus-perl
espeak
```

Goto "Applications" -> "Accessories" -> "Text Editor".

In this file paste: 

```

#!/usr/bin/perl -w

use Net::DBus;
use Net::DBus::Reactor;
use strict;

my $prevsong = "none";

my $bus = Net::DBus->find;
my $rhythm = $bus->get_service("org.gnome.Rhythmbox");
my $shell = $rhythm->get_object("/org/gnome/Rhythmbox/Shell", "org.gnome.Rhythmbox.Shell");
my $player = $rhythm->get_object("/org/gnome/Rhythmbox/Player", "org.gnome.Rhythmbox.Player");

sub SayPlaying()
{
	my $uri = $player->getPlayingUri;
	my %props = %{$shell->getSongProperties( $uri )};
	my $title = $props{'title'};
	my @tmp = split('\(', $title);
	$title = $tmp[0];
	$title =~ tr/'/ / ;
	
	if ($title =~ m/$prevsong/)
		{return;}
	
	$prevsong = $title;
	
	print $title, "\n";
	system "padsp espeak -a500 '$title' &>/dev/null";
}

$player->connect_to_signal("playingUriChanged", \&SayPlaying );

my $reactor = Net::DBus::Reactor->main();
$reactor->run();

```

Save it in your preferred location. 

Afterwards locate it in the File Explorer. Right-click on it, go to the tab "Permissions" and tap on "Allow executing the file as a program".

Finally, when Rhythmbox is playing. Just double-click on the file and press "Run".

It'll say the next playing song every time the song ends.

PS: Yes, I know that Perl code can be shorter, but I hate obfuscating code.

---

