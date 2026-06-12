---
title: "Commandline music player woes"
date: 2007-01-09
forum: Programming Talk
---

### Post by DigitalAxis on 2007-01-09
I'd like some help from someone who knows more about Bash scripting (in some specific areas) in fixing up my little frontend so it can play my music properly.

To put it briefly, I have a lot of exotic and ancient music on my computer, and players to play them.  I often use the command line on my system, and consequently I find myself playing a lot of music via command-line interfaces (such as right now, as I type this).

The problem was, I have too many players, so I wrote a bash script frontend called 'player' that identifies and sorts by extension.

Unfortunately, many Amiga Soundtracker (and a few MS-DOS soundtracker formats) use the .mod extension, and they're not all compatible.  UADE (the Unix Amiga Delitracker Emulator) sorts through them and plays them faithfully, but it doesn't (and won't, for obvious reasons) support the MS-DOS Fasttracker 1 format.

I rewrote a 'player2', and used **grep** to search through the files for the format indicator strings.  I know what they are; that's not the problem.

The problem is, it doesn't work.  'player2' consistently fails to identify Fasttracker 1 files, even though it works perfectly every time I try running **grep** by hand.

I've pretty much reached the limit of my bash scripting abilities with this one. (yes, I know **grep** is not meant for searching binary files.)

Right now I feel like I have three (four?) options:
*Find and change the extensions for all of the Fasttracker 1 modules (at which point Timidity will refuse to play them entirely, unfortunately)
*Fix a mistake in my code I haven't noticed.
*Search the specific point in the header where the format identifier is- they are always in the same place, and nearly always four characters long.
*Give up and drag files into Audacious whenever I need my exotic music format fix (note that Audacious also misidentifies a few Fasttracker 1 tunes)

The third option seems like the most probable option, but I have no idea how to search location 0x438 to 0x43b specifically.

Any help?


Attached to this is my code for 'player2'.  My apologies for all the other formats I also identified by name but... I'm curious about such things.

(While we're at it, is there any way I can deal more intelligently with filenames with spaces in them?  Not that I have many; every once and a while I go through and convert spaces to underscores.)

---

### Post by DigitalAxis on 2007-01-14
I finally solved my problem in a flash of inspiration, when I changed the single quotes to double quotes.  For some reason I think it was searching for a literal backslash.

Anyway, the relevant code is now:
```
                "mod")
                        # detect Fasttracker I
                        if (grep -a '[0-9]CHN' "$i" 1>/dev/null); then
                                echo "Fasttracker I"
                                timidity "$i"
                        else
                                        # detect Protracker
                                        if (grep -a "M\.K\." "$i" 1>/dev/null ); then
                                                echo "Protracker"
                                                uade123 --buffer-time=40000 "$i"
                                        else
                                               echo "Ultimate Soundtracker"
                                               uade123 --buffer-time=40000 "$i"
                                        fi
                                fi
                        fi ;;

```

I also realized my code is basically unreadable (cluster of **if** statements notwithstanding), so I sorted all the extensions in alphabetical order- it's not organized by type, but it's easier to find something.

---

