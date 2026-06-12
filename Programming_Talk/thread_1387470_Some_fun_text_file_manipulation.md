---
title: "Some fun text file manipulation"
date: 2010-01-21
forum: Programming Talk
---

### Post by gfunkdave on 2010-01-21
Hey all,

I have an interesting little conundrum I'm hoping to find some advice on. I use Ubuntu on my laptop but run a Windows XP virtual box on it. I basically use XP for iTunes and the Blackberry iTunes sync, which are available only for Windows (Rhythmbox doesn't recognize my Blackberry for some reason.).

I think I reverted XP to a previous saved image, because suddenly my iTunes playlists are many songs smaller than they used to be. I sync my Blackberry to one monster playlist in iTunes. It should have about 1965 songs on it, but instead it now has 1930.

Rather than go through to figure out what the missing 35 songs are, I'd like to write a script to do it. I have pulled the playlist off of my Blackberry - each line looks something like this:

```

file:///SDCard/BlackBerry/music/Media%20Sync/The%20Beatles/Sgt.%20Pepper's%20Lonely%20Hearts%20Club%20Band/02%20With%20A%20Little%20Help%20From%20My%20Friend.m4a
```

Each line from iTunes's playlist export is tab delimited for each tag, something like this:

```
With A Little Help From My Friends	The Beatles	Lennon, John/McCartney, Paul	Sgt. Pepper's Lonely Hearts Club Band		Rock	2677735	163	1	1	2	13	1967	11/24/2004 8:11 PM	12/1/2009 7:41 PM	128	44100		AAC audio file			
```

I suppose the algorithm would be to search for album/artist/song combinations but I'm uncertain quite how to go about it. Any ideas?

---

### Post by Can+~ on 2010-01-21
I think I would:

[LIST=1]
[*]Split-parse the information from one of the files
[*]Build a hash with said information
[*]When parsing the second, do a hash check.
[*]Any entry that doesn't have a key in the hash is a candidate for being the missing file (or a parse error)
[/LIST]

Do the files in your blackberry obey a rigid order? As in "author/album/songn.mp3"?

I would use python, of course. It's a one-shot script. Dictionaries are natural in python and dealing with file and string manipulation is easy-peasy.

---

### Post by myrtle1908 on 2010-01-21
I may have this totally back to front or just plain wrong.  I had a hard time understanding which you wanted.  I can't remember how to reset $/ in Perl.  Too lazy to look it up as its bedtime.  Use at your own peril :)  It should tell you which blackberry songs are not on itunes.  Oh ... and I figured artist and song name was enough to check for.

Hope this helps somewhat :)

```
use strict;
use warnings;
use URI::Escape;

my $berry = 'c:\temp\berry.txt';
my $itunes = 'c:\temp\itunes.txt';
my $itunes_data = '';

my $o = $/;
undef $/;
open(ITUNES, $itunes) or die $!;
$itunes_data = <ITUNES>;
close(ITUNES);

$/ = $o;
open(BERRY, $berry) or die $!;
while (<BERRY>) {
  uri_unescape($_) =~ m/media sync\/(.*?)\/.*?\/(.*)$/gi;
  if (($1 && $2) && ($itunes_data !~ m/$1/gmi) && ($itunes_data !~ m/$2/gmi)) {
    print "$1 $2 --- NOT FOUND ON ITUNES\n";
  }
}
close(BERRY);
```

---

