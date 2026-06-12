---
title: "DVD doesn't show up"
date: 2016-01-12
forum: New to Ubuntu
---

### Post by aurinko2 on 2016-01-12
I used to be able to watch DVDs on my Ubuntu, but I haven't done that in a long time (maybe a year or two) so when I tried today, it didn't work.
So I thought I'd try upgrading my 14.04 LTS to 15.04 and to 15.10 in case that would help, but no.

When I insert a CD, I get a pop up that asks what I want to do with the CD. When I insert a DVD, nothing at all happens. When there's a CD in the drive, I can browse to it with the file browser program (I don't know which one I have, it doesn't say the name of it anywhere), but when there's a DVD in the drive, I can't even find it in the file browser program. I've tried with 2 different DVDs, neither of them show up.

I tried the instructions on this page:
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)
And I get "libdvd-pkg is already the newest version."

sudo regionset /dev/sr0
regionset version 0.1 -- reads/sets region code on DVD drives
ERROR: Could not open disc "/dev/sr0"!
Please ensure there is a readable CD or DVD in the drive.

VLC won't open any DVDs either.
"[COLOR=#ff0000]Playback failure:[/COLOR]
[COLOR=#000000]DVDRead could not open the disc "/dev/sr0".[/COLOR]

 [COLOR=#ff0000]Your input can't be opened:[/COLOR]

 [COLOR=#000000]VLC is unable to open the MRL 'dvdsimple:///dev/sr0'. Check the log for details."

I go look at the log:

dvdread error: DVDRead cannot open source: /dev/sr0
core debug: no access_demux modules matched
core debug: creating access 'dvdsimple' location='/dev/sr0', path='/dev/sr0'
core debug: looking for access module matching "dvdsimple": 25 candidates
core debug: no access modules matched
core error: open of `dvdsimple:///dev/sr0' failed
core debug: dead input
core debug: repeating item
core debug: starting playback of the new playlist item
core debug: resyncing on sr0
core debug: sr0 is at 0
core debug: creating new input thread
core debug: Creating an input for 'sr0'
core debug: requesting art for sr0
core debug: using timeshift granularity of 50 MiB, in path '/tmp'
core debug: `dvdsimple:///dev/sr0' gives access `dvdsimple' demux `' path `/dev/sr0'
core debug: specified demux `any'
core debug: creating demux: access='dvdsimple' demux='any' location='/dev/sr0' file='/dev/sr0'
core debug: looking for access_demux module matching "dvdsimple": 20 candidates
lua debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/art/01_googleimage.luac
lua debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/art/02_frenchtv.luac
lua debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/art/03_lastfm.luac
lua debug: Trying Lua scripts in /usr/share/vlc/lua/meta/art
core debug: no art finder modules matched
core debug: art not found for sr0
core debug: looking for meta fetcher module matching "any": 1 candidates
qt4 debug: IM: Setting an input
lua debug: Trying Lua scripts in /home/kaisa/.local/share/vlc/lua/meta/fetcher
lua debug: Trying Lua scripts in /usr/lib/vlc/lua/meta/fetcher
lua debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/fetcher/tvrage.luac
lua debug: skipping script (unmatched scope) /usr/lib/vlc/lua/meta/fetcher/tvrage.luac
lua debug: Trying Lua scripts in /usr/share/vlc/lua/meta/fetcher
core debug: no meta fetcher modules matched
core debug: searching art for sr0
core debug: looking for art finder module matching "any": 2 candidates
lua debug: Trying Lua scripts in /home/kaisa/.local/share/vlc/lua/meta/art
lua debug: Trying Lua scripts in /usr/lib/vlc/lua/meta/art
lua debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/art/00_musicbrainz.luac
lua debug: skipping script (unmatched scope) /usr/lib/vlc/lua/meta/art/00_musicbrainz.luac
lua debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/art/01_googleimage.luac
lua debug: skipping script (unmatched scope) /usr/lib/vlc/lua/meta/art/01_googleimage.luac
lua debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/art/02_frenchtv.luac
lua debug: skipping script (unmatched scope) /usr/lib/vlc/lua/meta/art/02_frenchtv.luac
lua debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/art/03_lastfm.luac
lua debug: skipping script (unmatched scope) /usr/lib/vlc/lua/meta/art/03_lastfm.luac
lua debug: Trying Lua scripts in /usr/share/vlc/lua/meta/art
core debug: no art finder modules matched
core debug: looking for meta fetcher module matching "any": 1 candidates
lua debug: Trying Lua scripts in /home/kaisa/.local/share/vlc/lua/meta/fetcher
lua debug: Trying Lua scripts in /usr/lib/vlc/lua/meta/fetcher
lua debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/fetcher/tvrage.luac
core debug: using meta fetcher module "lua"
core debug: removing module "lua"
core debug: searching art for sr0
core debug: looking for art finder module matching "any": 2 candidates
qt4 debug: IM: Deleting the input
lua debug: Trying Lua scripts in /home/kaisa/.local/share/vlc/lua/meta/art
lua debug: Trying Lua scripts in /usr/lib/vlc/lua/meta/art
lua debug: Trying Lua playlist script /usr/lib/vlc/lua/meta/art/00_musicbrainz.luac
dvdread error: DVDRead cannot open source: /dev/sr0

And then it repeats over and over and over again.
[/COLOR]
I'm out of ideas, what should I do next?

---

### Post by leunam12 on 2016-01-13
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

