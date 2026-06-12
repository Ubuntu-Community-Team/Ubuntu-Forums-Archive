---
title: "VLC player doesn't play DVD..."
date: 2023-05-28
forum: New to Ubuntu
---

### Post by yatski on 2023-05-28
(I *know* this isn't VLC player forum, but I couldn't think another place to post my woes, since one topic that posted about same issue was unanswered in VLC forum.. So here goes a try.)

I decided to try if this system(age-old Sony Vaio, Ubuntu 22.04 LTS) could play DVD:s, and no... 
I managed to download some packages so the hurdle of DVD country region encoding error was cleared. (with help of [https://itsfoss.com/play-dvd-ubuntu-1310/](https://itsfoss.com/play-dvd-ubuntu-1310/))

However, VLC gives following error when I try play DVD:

```
main debug: processing request item: dvd:///dev/sr0, node: Playlist, skip: 0
main debug: rebuilding array of current - root Playlist
main debug: rebuild done - 1 items, index 0
main debug: starting playback of new item
main debug: resyncing on dvd:///dev/sr0
main debug: dvd:///dev/sr0 is at 0
main debug: creating new input thread
main debug: Creating an input for 'dvd:///dev/sr0'
main debug: requesting art for new input thread
main debug: using timeshift granularity of 50 MiB
main debug: using default timeshift path
main debug: `dvd:///dev/sr0' gives access `dvd' demux `any' path `/dev/sr0'
main debug: creating demux: access='dvd' demux='any' location='/dev/sr0' file='/dev/sr0'
main debug: looking for access_demux module matching "dvd": 18 candidates
main debug: looking for meta fetcher module matching "any": 1 candidates
lua debug: Trying Lua scripts in /home/heta/.local/share/vlc/lua/meta/fetcher
lua debug: Trying Lua scripts in /usr/lib/x86_64-linux-gnu/vlc/lua/meta/fetcher
lua debug: Trying Lua scripts in /usr/share/vlc/lua/meta/fetcher
main debug: no meta fetcher modules matched
main debug: looking for art finder module matching "any": 2 candidates
lua debug: Trying Lua scripts in /home/heta/.local/share/vlc/lua/meta/art
lua debug: Trying Lua scripts in /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art
lua debug: Trying Lua playlist script /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/00_musicbrainz.luac
lua debug: skipping script (unmatched scope) /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/00_musicbrainz.luac
lua debug: Trying Lua playlist script /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/01_googleimage.luac
lua debug: skipping script (unmatched scope) /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/01_googleimage.luac
lua debug: Trying Lua playlist script /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/02_frenchtv.luac
lua debug: skipping script (unmatched scope) /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/02_frenchtv.luac
lua debug: Trying Lua playlist script /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/03_lastfm.luac
lua debug: skipping script (unmatched scope) /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/03_lastfm.luac
lua debug: Trying Lua scripts in /usr/share/vlc/lua/meta/art
main debug: no art finder modules matched
main debug: looking for meta fetcher module matching "any": 1 candidates
lua debug: Trying Lua scripts in /home/heta/.local/share/vlc/lua/meta/fetcher
lua debug: Trying Lua scripts in /usr/lib/x86_64-linux-gnu/vlc/lua/meta/fetcher
lua debug: Trying Lua scripts in /usr/share/vlc/lua/meta/fetcher
main debug: no meta fetcher modules matched
main debug: looking for art finder module matching "any": 2 candidates
lua debug: Trying Lua scripts in /home/heta/.local/share/vlc/lua/meta/art
lua debug: Trying Lua scripts in /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art
lua debug: Trying Lua playlist script /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/00_musicbrainz.luac
lua debug: Trying Lua playlist script /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/01_googleimage.luac
lua debug: Trying Lua playlist script /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/02_frenchtv.luac
lua debug: Trying Lua playlist script /usr/lib/x86_64-linux-gnu/vlc/lua/meta/art/03_lastfm.luac
lua debug: Trying Lua scripts in /usr/share/vlc/lua/meta/art
main debug: no art finder modules matched
qt debug: IM: Setting an input
dvdnav warning: ifoOpenVMGI(): Invalid main menu IFO (VIDEO_TS.IFO).
dvdnav warning: ifoOpenVMGI(): Invalid main menu IFO (VIDEO_TS.BUP).
dvdnav error: vm: vm: failed to read VIDEO_TS.IFO
dvdnav warning: cannot open DVD (/dev/sr0)
dvdread warning: Invalid IFO for title 0 (VIDEO_TS.IFO).
dvdread warning: Invalid IFO for title 0 (VIDEO_TS.BUP).
dvdread error: DVDISOVolumeInfo, failed to read ISO9660 Primary Volume Descriptor
dvdread warning: cannot open VMG info
main debug: no access_demux modules matched
main debug: creating access: dvd:///dev/sr0
main debug: (path: /dev/sr0)
main debug: looking for access module matching "dvd": 29 candidates
main debug: no access modules matched
main debug: dead input
qt debug: IM: Deleting the input
main debug: changing item without a request (current 0/1)
main debug: nothing to play
```

If someone can read the code... What's wrong with my VLC player? Or.. Are my DVD:s damaged for good? They've been stored in cupboard for last five years or so.

---

### Post by Holger_Gehrke on 2023-05-28
Have you installed libdvd-pkg (sudo apt install libdvd-pkg)? Commercial video DVDs are partially encrypted to force manufacturers of players to pay to the DVD consortium for a decryption key. Open source projects can't get such a key because a) they don't have that kind of money and b) they'd have to sign a non-disclosure agreement for the key and they can't do that - open source means they publish their source code and the key would be clearly visible. So as a workaround there's a library that cracks the encryption. The legality of this approach is highly dependent on where you live. In some places source code is protected as free speech but executable programs aren't. So this package downloads the source code and compiles and installs it for you.

Holger

---

### Post by yatski on 2023-05-29
Yes, I've installed libdvd-pkg.
I tested DVD (that produced code dump above) this morning and it plays well on DVD player.
(Said DVD player sadly isn't mine so I can't use it to watch it.)

---

