---
title: "[SOLVED] Irssi + audacious.pl some coding help needed..."
date: 2008-11-19
forum: Programming Talk
---

### Post by michande03 on 2008-11-19
well am very happy with the script, but wanted to enhance it a bit for my own pleasure but ran in som troubles.

```
use strict;
use vars qw($VERSION %IRSSI);
# Audacious Irssi Script v1.0.4
#
# Change Log:
# v1.0.4:
#       - Added Repeat on/off capability
#       - Added Shuffle on/off capability
#       - Fixed script output handling for audacious version in case audacious isn't running
#       - If encountered a problem with audacious version, try changing `audacious --version` to `audtool -v`
# v1.0.3:
#       - Added Playlist functionality
#       - Added Song details (Bitrate/Frequency/Length/Volume)
#       - Current song notice with song details (Optional)
# v1.0.2:
#       - The script now handles warning support if you got audacious not running
#       - Added track number, current time elapse and total track time
#       - Added Stop functionality
# v1.0.1:
#       - Added ability to autonotify the channel after skipping a song (optional)
#       - Added Skip/Play/Pause/Resume calls
#
# How To Use?
# Copy your script into ~/.irssi/scripts/ directory
# Load your script with /script load audacious in your Irssi Client
# Type '/audacious help' in any channel for script commands
# For autoload insert your script into ~/.irssi/scripts/autorun/ directory
# Even better would be if you placed them in ~/.irssi/scripts/ and created symlinks in autorun directory
#
use Irssi;
$VERSION = '1.0.4';
%IRSSI = (
   authors      =>   "Dani Soufi",
   contact      =>   "IRC: FreeNode Network, #Ubuntu-LB",
   name         =>   "Audacious Irssi Script",
   description  =>   "Displays Current Song".
                     "Skips/Plays/Pauses/Stops/Resumes/Shuffles/Repeats Songs".
                     "Displays Script/Player's Current Version".
                     "Current Song Details",
   license      =>   "Public Domain",
);

sub cmd_song {
   my ($data, $server, $witem) = @_;
        # Get current song information.
        # If you want song details to be displayed
        # directly with the current song:
        # - Uncomment lines: 50/51/56/57/60
        # -* Comment line 59 (Important)
    if ($witem && ($witem->{type} eq "CHANNEL")) {
    if (`ps -C audacious` =~ /audacious/) {
      my $position = `audtool --playlist-position`;
      my $song = `audtool --current-song`;
      my $current = `audtool --current-song-output-length`;
      my $total = `audtool --current-song-length`;
#      my $bitrate = `audtool --current-song-bitrate-kbps`; #line 50
#      my $frequency = `audtool --current-song-frequency-khz`; #line 51
      chomp($song);
      chomp($position);
      chomp($current);
      chomp($total);
#      chomp($bitrate); #line 56
#      chomp($frequency); #line 57

  $witem->command("/me np: $song"); #line 60
# $witem->command("/me is listening to: #$position | $song ($current/$total) [$bitrate kbps/$frequency khz]"); #line 60
   }
    else {
      $witem->print("Audacious is not currently running.");
    }
   return 1;
  }
}

```

is the part I am interested in and I want to add a line looking kinda like this...

```
my $path = `audtool --current-song-tuple-data file-path | sed -r 's/.*\/(.*)/\1/g'`;
```

to get rid of full path and just show dir file is in.

it does work very well in bash and gives result I want, but how to get it nicely in perl??

Any ideas??

Thx beforehand and a shoutout to this forum, has helped a lot in the past :)

---

### Post by michande03 on 2008-11-22
bump

---

### Post by michande03 on 2008-11-25
Solved

```
my $path = `audtool --current-song-tuple-data file-path`; $path =~ s/.*\/(.*)/\1/g;
```

I tried it a lot but did give it expressions :( example of what I tried before solving was....

```
my $path = `audtool --current-song-tuple-data <file-path>`; my $path =~ s/.*\/(.*)/\1/g;
```

so had to skip the "my" in second expression :P

as allways small **** that is missed :P

---

