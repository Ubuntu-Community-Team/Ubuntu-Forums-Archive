---
title: "dvd will not play"
date: 2020-10-10
forum: New to Ubuntu
---

### Post by nginmu on 2020-10-10
lubuntu 20.04

brand new dvd out of sealed packet, visually seems ok

dvd drive whirrs, vlc tries to talk to it, then errors 'cannot be opened' 'check log'

can't find the log for vlc though :-(

tried var/log/syslog but couldn't see anything relating to vlc

any help appreciated

```

 [COLOR=#ff0000]Playback failure:[/COLOR]
 [COLOR=#000000]DVDRead could not open the disc "/dev/sr0".[/COLOR]
 [COLOR=#ff0000]Your input can't be opened:[/COLOR]
 [COLOR=#000000]VLC is unable to open the MRL 'dvd:///dev/sr0'. Check the log for details.[/COLOR][COLOR=#000000]
[/COLOR]
```[COLOR=#000000]
[/COLOR][COLOR=#000000]
ah ok I found the log, tools > messages > verbosity 2:

[/COLOR]```

  [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]processing request item: dvd:///dev/sr0, node: Playlist, skip: 0
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]rebuilding array of current - root Playlist
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]rebuild done - 1 items, index 0
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]starting playback of new item
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]resyncing on dvd:///dev/sr0
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]dvd:///dev/sr0 is at 0
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]creating new input thread
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Creating an input for 'dvd:///dev/sr0'
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]requesting art for new input thread
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]using timeshift granularity of 50 MiB
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]using default timeshift path
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]`dvd:///dev/sr0' gives access `dvd' demux `any' path `/dev/sr0'
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]creating demux: access='dvd' demux='any' location='/dev/sr0' file='/dev/sr0'
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]looking for access_demux module matching "dvd": 19 candidates
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]looking for meta fetcher module matching "any": 1 candidates
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua scripts in /home/me/.local/share/vlc/lua/meta/fetcher
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua scripts in /usr/lib/x86_64-linux-gnu/vlc/lua/meta/fetcher
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua scripts in /usr/share/vlc/lua/meta/fetcher
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]no meta fetcher modules matched
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]looking for art finder module matching "any": 2 candidates
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua scripts in /home/me/.local/share/vlc/lua/meta/art
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua scripts in /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua playlist script /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/00_musicbrainz.luac
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]skipping script (unmatched scope) /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/00_musicbrainz.luac
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua playlist script /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/01_googleimage.luac
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]skipping script (unmatched scope) /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/01_googleimage.luac
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua playlist script /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/02_frenchtv.luac
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]skipping script (unmatched scope) /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/02_frenchtv.luac
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua playlist script /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/03_lastfm.luac
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]skipping script (unmatched scope) /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/03_lastfm.luac
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua scripts in /usr/share/vlc/lua/meta/art
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]no art finder modules matched
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]looking for meta fetcher module matching "any": 1 candidates
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua scripts in /home/me/.local/share/vlc/lua/meta/fetcher
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua scripts in /usr/lib/x86_64-linux-gnu/vlc/lua/meta/fetcher
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua scripts in /usr/share/vlc/lua/meta/fetcher
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]no meta fetcher modules matched
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]looking for art finder module matching "any": 2 candidates
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua scripts in /home/me/.local/share/vlc/lua/meta/art
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua scripts in /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua playlist script /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/00_musicbrainz.luac
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua playlist script /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/01_googleimage.luac
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua playlist script /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/02_frenchtv.luac
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua playlist script /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/03_lastfm.luac
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua scripts in /usr/share/vlc/lua/meta/art
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]no art finder modules matched
 [COLOR=#00008b]*qt*[/COLOR][COLOR=#808080]* debug: *[/COLOR]IM: Setting an input
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#008000]* warning: *[/COLOR]cannot open DVD (/dev/sr0)
 [COLOR=#00008b]*dvdread*[/COLOR][COLOR=#ff0000]* error: *[/COLOR]DVDRead cannot open source: /dev/sr0
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]no access_demux modules matched
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]creating access: dvd:///dev/sr0
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR](path: /dev/sr0)
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]looking for access module matching "dvd": 29 candidates
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]no access modules matched
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]dead input
 [COLOR=#00008b]*qt*[/COLOR][COLOR=#808080]* debug: *[/COLOR]IM: Deleting the input
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]changing item without a request (current 0/1)
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]nothing to play
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]processing request item: dvd:///dev/dvd, node: Playlist, skip: 0
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]rebuilding array of current - root Playlist
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]rebuild done - 2 items, index 1
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]starting playback of new item
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]resyncing on dvd:///dev/dvd
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]dvd:///dev/dvd is at 1
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]creating new input thread
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Creating an input for 'dvd:///dev/dvd'
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]requesting art for new input thread
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]using timeshift granularity of 50 MiB
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]using default timeshift path
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]`dvd:///dev/dvd' gives access `dvd' demux `any' path `/dev/dvd'
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]creating demux: access='dvd' demux='any' location='/dev/dvd' file='/dev/dvd'
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]looking for access_demux module matching "dvd": 19 candidates
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]looking for meta fetcher module matching "any": 1 candidates
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua scripts in /home/me/.local/share/vlc/lua/meta/fetcher
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua scripts in /usr/lib/x86_64-linux-gnu/vlc/lua/meta/fetcher
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua scripts in /usr/share/vlc/lua/meta/fetcher
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]no meta fetcher modules matched
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]looking for art finder module matching "any": 2 candidates
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua scripts in /home/me/.local/share/vlc/lua/meta/art
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua scripts in /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua playlist script /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/00_musicbrainz.luac
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]skipping script (unmatched scope) /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/00_musicbrainz.luac
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua playlist script /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/01_googleimage.luac
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]skipping script (unmatched scope) /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/01_googleimage.luac
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua playlist script /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/02_frenchtv.luac
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]skipping script (unmatched scope) /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/02_frenchtv.luac
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua playlist script /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/03_lastfm.luac
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]skipping script (unmatched scope) /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/03_lastfm.luac
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua scripts in /usr/share/vlc/lua/meta/art
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]no art finder modules matched
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]looking for meta fetcher module matching "any": 1 candidates
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua scripts in /home/me/.local/share/vlc/lua/meta/fetcher
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua scripts in /usr/lib/x86_64-linux-gnu/vlc/lua/meta/fetcher
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua scripts in /usr/share/vlc/lua/meta/fetcher
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]no meta fetcher modules matched
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]looking for art finder module matching "any": 2 candidates
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua scripts in /home/me/.local/share/vlc/lua/meta/art
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua scripts in /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua playlist script /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/00_musicbrainz.luac
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua playlist script /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/01_googleimage.luac
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua playlist script /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/02_frenchtv.luac
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua playlist script /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/03_lastfm.luac
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua scripts in /usr/share/vlc/lua/meta/art
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]no art finder modules matched
 [COLOR=#00008b]*qt*[/COLOR][COLOR=#808080]* debug: *[/COLOR]IM: Setting an input
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#008000]* warning: *[/COLOR]cannot open DVD (/dev/dvd)
 [COLOR=#00008b]*dvdread*[/COLOR][COLOR=#ff0000]* error: *[/COLOR]DVDRead cannot open source: /dev/dvd
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]no access_demux modules matched
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]creating access: dvd:///dev/dvd
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR](path: /dev/dvd)
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]looking for access module matching "dvd": 29 candidates
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]no access modules matched
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]dead input
 [COLOR=#00008b]*qt*[/COLOR][COLOR=#808080]* debug: *[/COLOR]IM: Deleting the input
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]changing item without a request (current 1/2)
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]nothing to play
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]processing request item: dvd:///dev/cdrom, node: Playlist, skip: 0
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]rebuilding array of current - root Playlist
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]rebuild done - 3 items, index 2
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]starting playback of new item
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]resyncing on dvd:///dev/cdrom
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]dvd:///dev/cdrom is at 2
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]creating new input thread
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Creating an input for 'dvd:///dev/cdrom'
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]requesting art for new input thread
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]using timeshift granularity of 50 MiB
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]using default timeshift path
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]`dvd:///dev/cdrom' gives access `dvd' demux `any' path `/dev/cdrom'
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]creating demux: access='dvd' demux='any' location='/dev/cdrom' file='/dev/cdrom'
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]looking for access_demux module matching "dvd": 19 candidates
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]looking for meta fetcher module matching "any": 1 candidates
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua scripts in /home/me/.local/share/vlc/lua/meta/fetcher
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua scripts in /usr/lib/x86_64-linux-gnu/vlc/lua/meta/fetcher
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua scripts in /usr/share/vlc/lua/meta/fetcher
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]no meta fetcher modules matched
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]looking for art finder module matching "any": 2 candidates
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua scripts in /home/me/.local/share/vlc/lua/meta/art
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua scripts in /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua playlist script /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/00_musicbrainz.luac
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]skipping script (unmatched scope) /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/00_musicbrainz.luac
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua playlist script /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/01_googleimage.luac
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]skipping script (unmatched scope) /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/01_googleimage.luac
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua playlist script /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/02_frenchtv.luac
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]skipping script (unmatched scope) /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/02_frenchtv.luac
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua playlist script /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/03_lastfm.luac
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]skipping script (unmatched scope) /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/03_lastfm.luac
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua scripts in /usr/share/vlc/lua/meta/art
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]no art finder modules matched
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]looking for meta fetcher module matching "any": 1 candidates
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua scripts in /home/me/.local/share/vlc/lua/meta/fetcher
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua scripts in /usr/lib/x86_64-linux-gnu/vlc/lua/meta/fetcher
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua scripts in /usr/share/vlc/lua/meta/fetcher
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]no meta fetcher modules matched
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]looking for art finder module matching "any": 2 candidates
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua scripts in /home/me/.local/share/vlc/lua/meta/art
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua scripts in /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua playlist script /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/00_musicbrainz.luac
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua playlist script /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/01_googleimage.luac
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua playlist script /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/02_frenchtv.luac
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua playlist script /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/03_lastfm.luac
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua scripts in /usr/share/vlc/lua/meta/art
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]no art finder modules matched
 [COLOR=#00008b]*qt*[/COLOR][COLOR=#808080]* debug: *[/COLOR]IM: Setting an input
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#008000]* warning: *[/COLOR]cannot open DVD (/dev/cdrom)
 [COLOR=#00008b]*dvdread*[/COLOR][COLOR=#ff0000]* error: *[/COLOR]DVDRead cannot open source: /dev/cdrom
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]no access_demux modules matched
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]creating access: dvd:///dev/cdrom
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR](path: /dev/cdrom)
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]looking for access module matching "dvd": 29 candidates
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]no access modules matched
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]dead input
 [COLOR=#00008b]*qt*[/COLOR][COLOR=#808080]* debug: *[/COLOR]IM: Deleting the input
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]changing item without a request (current 2/3)
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]nothing to play
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]processing request item: dvd:///dev/dvdrw, node: Playlist, skip: 0
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]rebuilding array of current - root Playlist
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]rebuild done - 4 items, index 3
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]starting playback of new item
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]resyncing on dvd:///dev/dvdrw
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]dvd:///dev/dvdrw is at 3
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]creating new input thread
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Creating an input for 'dvd:///dev/dvdrw'
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]requesting art for new input thread
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]using timeshift granularity of 50 MiB
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]using default timeshift path
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]`dvd:///dev/dvdrw' gives access `dvd' demux `any' path `/dev/dvdrw'
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]creating demux: access='dvd' demux='any' location='/dev/dvdrw' file='/dev/dvdrw'
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]looking for access_demux module matching "dvd": 19 candidates
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]looking for meta fetcher module matching "any": 1 candidates
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua scripts in /home/me/.local/share/vlc/lua/meta/fetcher
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua scripts in /usr/lib/x86_64-linux-gnu/vlc/lua/meta/fetcher
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua scripts in /usr/share/vlc/lua/meta/fetcher
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]no meta fetcher modules matched
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]looking for art finder module matching "any": 2 candidates
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua scripts in /home/me/.local/share/vlc/lua/meta/art
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua scripts in /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua playlist script /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/00_musicbrainz.luac
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]skipping script (unmatched scope) /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/00_musicbrainz.luac
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua playlist script /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/01_googleimage.luac
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]skipping script (unmatched scope) /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/01_googleimage.luac
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua playlist script /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/02_frenchtv.luac
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]skipping script (unmatched scope) /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/02_frenchtv.luac
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua playlist script /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/03_lastfm.luac
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]skipping script (unmatched scope) /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/03_lastfm.luac
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua scripts in /usr/share/vlc/lua/meta/art
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]no art finder modules matched
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]looking for meta fetcher module matching "any": 1 candidates
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua scripts in /home/me/.local/share/vlc/lua/meta/fetcher
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua scripts in /usr/lib/x86_64-linux-gnu/vlc/lua/meta/fetcher
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua scripts in /usr/share/vlc/lua/meta/fetcher
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]no meta fetcher modules matched
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]looking for art finder module matching "any": 2 candidates
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua scripts in /home/me/.local/share/vlc/lua/meta/art
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua scripts in /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua playlist script /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/00_musicbrainz.luac
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua playlist script /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/01_googleimage.luac
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua playlist script /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/02_frenchtv.luac
 [COLOR=#00008b]*qt*[/COLOR][COLOR=#808080]* debug: *[/COLOR]IM: Setting an input
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua playlist script /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/03_lastfm.luac
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua scripts in /usr/share/vlc/lua/meta/art
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]no art finder modules matched
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#008000]* warning: *[/COLOR]cannot open DVD (/dev/dvdrw)
 [COLOR=#00008b]*dvdread*[/COLOR][COLOR=#ff0000]* error: *[/COLOR]DVDRead cannot open source: /dev/dvdrw
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]no access_demux modules matched
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]creating access: dvd:///dev/dvdrw
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR](path: /dev/dvdrw)
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]looking for access module matching "dvd": 29 candidates
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]no access modules matched
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]dead input
 [COLOR=#00008b]*qt*[/COLOR][COLOR=#808080]* debug: *[/COLOR]IM: Deleting the input
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]changing item without a request (current 3/4)
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]nothing to play

```[COLOR=#000000]
[/COLOR]

---

### Post by T6&amp;sfpER35% on 2020-10-10
have u tried any other players? although VLC is a great player,i have found that sometimes i would get that error where it wouldn't read the media.
i switched to SMplayer ,and never looked back.never had an error again with any media

PS. does ur drive play other disks fine?

EDIT : ok i posted this before u found the logs...does ur VLC play ANY  disks?

---

### Post by nginmu on 2020-10-10
Thanks for the suggestion - SMplayer's having similar troubles to VLC.

Will check a few other DVDs.

[edit] - tried 2 other known good dvd's. same results. drive keeps trying to read them but never gets off first base. lens seems clean, nothing obviously untoward to the naked eye.

same results with both players, neither seems to be able to see anything at all.

its a fairly old laptop now, HP G72, with the original drive in it. Maybe it's just finally gone dead.

---

### Post by T6&amp;sfpER35% on 2020-10-10
that might be the case , sorry

---

### Post by guiverc on 2020-10-10
I can't test this currently, but normally I'd suggest you look at 

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

to play restricted/commercial DVDs on Ubuntu.

It currently tells you to install a package which isn't available for *focal*, however I believe you'll get what you need with

`sudo apt install **ubuntu-restricted-extras**`

I installed a random disc into my Lubuntu system (*groovy*) and it played (Star Trek; one of the recent ones). The picture was warped, but I believe the region of the disc doesn't match whatever I've setup (*or haven't setup*) my machine to play.

I don't currently have a system I can test this on right now, sorry.  In a few hours maybe.

---

### Post by nginmu on 2020-10-10
Thanks. Tried your suggestions but no joy, the more I look at it, the more I'm getting the feeling the drive just isn't playing ball.

Listening to the noise it's making, it's making the same failed attempts to read over and over again even before the main OS loads.

```
sudo lshw -C disk
```

```

  *-cdrom
       description: DVD-RAM writer
       product: CDDVDW TS-L633N
       vendor: hp
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/sr0
       version: 0300
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=open

```

for status it's showing variously 'open', 'busy', 'nodisc'

---

### Post by Yellow Pasque on 2020-10-11
Try a CD in it. 
If the drive is old, cleaning the lens might help.

---

### Post by guiverc on 2020-10-11
I did a QA-test (*groovy*) install on a  dell optiplex 755 & it responded as yours did (`ubuntu-restricted-extras` did nothing helpful), but with that box alone I wouldn't know if the  cd/dvd drive worked as I may not have used it in a long time..

*FYI:  I know you're on focal and not groovy, but I believe the results will be the same and I'm using the install as a QA-test allowing me to do two things at once.*

I next tried using a dell optiplex 780, but it turns out I'd put the box together incorrectly and the tray won't eject (*drive isn't straight*).. skipping that box.

I tried installing Lubuntu (*groovy*) daily on another box hp dc7700, but that failed ..  that box was going to confirm the issue I felt on d755 &  I'd have then explored further, but it alerted me to a more significant issue with *groovy* so that's now taking attention...

I wanted to confirm what I suspected so I could update the wiki page link I gave up (for *focal* and later releases) but I've since been distracted, but I suspect your "**no joy**" result is what you should have got, alas currently I can't help further  (I'm chasing the *groovy* failure)

---

### Post by ActionParsnip on 2020-10-11
If you run VLC as root, does it work OK?

---

### Post by ajgreeny on 2020-10-11
I am using Xubuntu 20.04 and from what I see in synaptic **libdvd-pkg** is still available, in the multiverse repos, and it still installs the necessary **libdvdcss** files needed to get your commercial DVDs playing properly.

I suspect I may have used synaptic to install everything at that time, though I believe that using terminal should also get it for you.

What does ***apt search libdvd-pkg*** show when run in terminal?

After installing the libdvd-pkg package you have to run command ***sudo dpkg-reconfigure libdvd-pkg*** to actually install the **libdvdcss** library files needed for commercial DVD playing.
If you use synaptic to install the package this extra step is offered automatically.
No idea about 20.10 as I have not yet tried it but will do so soon probably as a VM.

---

### Post by nginmu on 2020-10-11
```

me@me-pc:~$ apt search libdvd-pkg
Sorting... Done
Full Text Search... Done
libdvd-pkg/focal,focal,now 1.4.2-1-1 all [installed]
  DVD-Video playing library - installer

me@me-pc:~$ sudo dpkg-reconfigure libdvd-pkg
[sudo] password for me: 
libdvd-pkg: guest package [libdvdcss2/1.4.2-1~local] is already installed.
me@me-pc:~$ sudo vlc
VLC is not supposed to be run as root. Sorry.
If you need to use real-time priorities and/or privileged TCP ports
you can use vlc-wrapper (make sure it is Set-UID root and
cannot be run by non-trusted users first).
me@me-pc:~$ sudo smplayer
QStandardPaths: XDG_RUNTIME_DIR not set, defaulting to '/tmp/runtime-root'
This is SMPlayer v. 19.10.2 (revision 9245) running on Linux
me@me-pc:~$ 

```

SMplayer as root did not play the DVD from the drive when directed to via the GUI, it just sat there

Tried "100% Clubland 90s" plain shop-bought commercial audio CDROM. Both VLC & SMplayer managed to play all tracks on it albeit with a bit of trouble at first, a lot of thrashing around from the drive and delay before it did finally settle down & play tracks more or less reliably. Also the CDROM came up in PCManFM file manager & allowed GUI navigation to the individual .wav files on it.

Still no dvd play :-(

Mrs Nginmu has a lot of DVDs, she's up now so I can ask permission to borrow.

ok tried 5 more dvds, none play, all doing the same repetitive seeking around but never quite getting there.

The drive is one like this, a TS-L633:

[https://www.ebay.co.uk/itm/323585297614](https://www.ebay.co.uk/itm/323585297614)
[https://www.youtube.com/watch?v=KT2u8wi8bDE](https://www.youtube.com/watch?v=KT2u8wi8bDE)

I've ordered another one in case it's a hardware problem, they're next to nothing

---

### Post by Yellow Pasque on 2020-10-11
> **nginmu said:**
> [code]

Tried "100% Clubland 90s" plain shop-bought commercial audio CDROM. Both VLC & SMplayer managed to play all tracks on it albeit with a bit of trouble at first, a lot of thrashing around from the drive and delay before it did finally settle down & play tracks more or less reliably. Also the CDROM came up in PCManFM file manager & allowed GUI navigation to the individual .wav files on it.

It sounds like it could be a dirty lens. If you have some rubbing alcohol (preferably >= 91%) and the inclination, you should try cleaning it.

---

### Post by nginmu on 2020-10-11
Tried cleaning it, haven't got the most ideal cleaning fluid but had a go with a cotton bud and meths.

I think if it wasn't dead already, I've just put the final nail in the coffin LOL

It's not even doing the seeking now.

Just have to wait for the ebay drive to turn up now.

It was certainly worth a try :-)

---

### Post by garvinrick4 on 2020-10-11
Did you install lubuntu-restricted-extras

> sudo apt install lubuntu-restricted-extras

Cannot hurt to try. Did that install lubuntu-restricted-addons?

Never used lubuntu but is a package cant hurt if still not working

---

### Post by ajgreeny on 2020-10-11
It's  libdvdcss2 that is missing and the restricted-extras package does not add that to the system so I don't think it will help with this DVD problem.

---

### Post by nginmu on 2020-10-14
Thanks everyone for your help. The replacement drive came today - everything worked flawlessly as soon as I installed it.

---

