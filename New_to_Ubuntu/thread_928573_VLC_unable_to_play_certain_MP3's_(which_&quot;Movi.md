---
title: "VLC unable to play certain MP3's (which &quot;Movie Player&quot; has no problem playing)"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by diablo75 on 2008-09-24
I usually use VLC to play my media, but on some MP3's, it gives me the following error:

```
Unable to open 'file:///media/disk/MUSIC/pathtofile/file.mp3'

```
As far as I can tell, it doesn't provide any further detail...

---

### Post by bangmalley on 2008-09-26
run VLC from terminal:
```
vlc -vvv --color
```
and then play your songs and post the debug log to vlc [forum]("http://forum.videolan.org")

---

### Post by diablo75 on 2008-10-16
```
zeke@ubuntu:~$ vlc -vvv --color
VLC media player 0.8.6e Janus
[00000001] main private debug: checking builtin modules
[00000001] main private debug: checking plugin modules
[00000001] main private debug: loading plugins cache file /home/zeke/.vlc/cache/plugins-04041e.dat
[00000001] main private debug: recursively browsing `/usr/lib/vlc'
[00000001] main private debug: module bank initialized, found 218 modules
[00000001] main private debug: opening config file /home/zeke/.vlc/vlcrc
[00000001] main private debug: CPU has capabilities 486 586 MMX 3DNow! MMXEXT SSE FPU 
[00000001] main private debug: looking for memcpy module: 1 candidate
[00000001] main private debug: using memcpy module "memcpy"
[00000283] main playlist debug: waiting for thread completion
[00000283] main playlist debug: thread 3079830416 (playlist) created at priority 0 (playlist/playlist.c:184)
[00000284] main private debug: waiting for thread completion
[00000284] main private debug: thread 3071437712 (preparser) created at priority 0 (playlist/playlist.c:210)
[00000285] main interface debug: looking for interface module: 1 candidate
[00000285] main interface debug: using interface module "hotkeys"
[00000285] main interface debug: thread 3063045008 (interface) created at priority 0 (interface/interface.c:231)
[00000287] main interface debug: looking for interface module: 1 candidate
[00000287] main interface debug: using interface module "screensaver"
[00000287] main interface debug: thread 3054652304 (interface) created at priority 0 (interface/interface.c:231)
[00000289] main interface debug: looking for interface module: 5 candidates
[00000289] main interface debug: using interface module "wxwidgets"
[00000289] main interface debug: thread 3028355984 (manager) created at priority 0 (interface/interface.c:216)
[00000289] wxwidgets interface debug: Using last windows config '(-1,0,0,1024,768)(0,59,49,425,86)(6,0,0,-1,150)'
[00000289] wxwidgets interface debug: id=0 p=(59,49) s=(425,86)
[00000289] wxwidgets interface debug: id=6 p=(0,0) s=(-1,150)
[COLOR="Blue"][00000283] main playlist debug: adding playlist item `/media/disk/MUSIC/dvd1 (Simon Posford)/Simon Posford+/Walter Ego - We're High.mp3' ( /media/disk/MUSIC/dvd1 (Simon Posford)/Simon Posford+/Walter Ego - We're High.mp3 )
[00000283] main playlist debug: creating new input thread
[00000292] main input debug: waiting for thread completion
[00000292] main input debug: creating statistics handler
[00000292] main input debug: `/media/disk/MUSIC/dvd1 (Simon Posford)/Simon Posford+/Walter Ego - We're High.mp3' gives access `' demux `' path `/media/disk/MUSIC/dvd1 (Simon Posford)/Simon Posford+/Walter Ego - We're High.mp3'
[00000292] main input debug: creating demux: access='' demux='' path='/media/disk/MUSIC/dvd1 (Simon Posford)/Simon Posford+/Walter Ego - We're High.mp3'
[00000294] main demuxer debug: looking for access_demux module: 2 candidates
[00000292] main input debug: thread 3012049808 (input) created at priority 0 (input/input.c:265)
[00000292] main input debug: creating access '' path='/media/disk/MUSIC/dvd1 (Simon Posford)/Simon Posford+/Walter Ego - We're High.mp3'
[00000297] main access debug: looking for access2 module: 5 candidates
[00000297] vcd access debug: trying .cue file: /media/disk/MUSIC/dvd1 (Simon Posford)/Simon Posford+/Walter Ego - We're High.cue
[00000297] vcd access debug: could not find .cue file
[00000297] access_file access debug: opening file `/media/disk/MUSIC/dvd1 (Simon Posford)/Simon Posford+/Walter Ego - We're High.mp3'
[00000297] main access debug: using access2 module "access_file"
[00000303] main private debug: pre-buffering...
[00000303] main private debug: received first data for our buffer
[00000303] main private debug: pre-buffering done 1408981 bytes in 0s - 11825 kbytes/s
[00000292] main input debug: creating demux: access='' demux='' path='/media/disk/MUSIC/dvd1 (Simon Posford)/Simon Posford+/Walter Ego - We're High.mp3'
[00000304] main demuxer debug: ID3v2.3 revision 0 tag found, skipping 2093 bytes
[00000304] main demuxer debug: looking for demux2 module: 45 candidates
[00000318] main packetizer debug: looking for packetizer module: 17 candidates
[00000318] main packetizer debug: using packetizer module "mpeg_audio"
[00000304] mpga demuxer debug: did not sync on first block
[00000292] main input debug: selecting program id=0
[00000304] main demuxer debug: looking for id3 module: 1 candidate
[00000304] id3tag demuxer debug: checking for ID3 tag
[00000304] id3tag demuxer debug: found ID3v1 tag
[00000304] id3tag demuxer debug: found ID3v2 tag
[00000304] main demuxer debug: using id3 module "id3tag"
[00000304] main demuxer debug: removing module "id3tag"
[00000304] main demuxer debug: using demux2 module "mpga"
[00000292] main input debug: looking for a subtitle file in /media/disk/MUSIC/dvd1 (Simon Posford)/Simon Posford+/
[00000345] main decoder debug: looking for decoder module: 25 candidates
[00000345] main decoder debug: using decoder module "mpeg_audio"
[00000345] main decoder debug: thread 2987989904 (decoder) created at priority 0 (input/decoder.c:159)
[00000292] main input debug: meta information:
[00000292] main input debug:   - 'Title' = 'We're High'
[00000292] main input debug:   - 'Artist' = 'Walter Ego'
[00000292] main input debug:   - 'Album/movie/show title' = 'More Bass Than Space'
[00000292] main input debug:   - 'Date' = '2000'
[00000292] main input debug:   - 'Track number/position in set' = '6'
[00000292] main input debug:   - 'Genre' = 'Psychedelic'
[00000292] main input debug:   - 'Album/movie/show title' = 'More Bass Than Space'
[00000292] main input debug:   - 'Artist' = 'Walter Ego'
[00000292] main input debug:   - 'Part of a set' = '1'
[00000292] main input debug:   - 'Genre' = 'Psychedelic'
[00000292] main input debug:   - 'Title' = 'We're High'
[00000292] main input debug:   - 'Track number/position in set' = '6'
[00000292] main input debug:   - 'Date' = '2000'
[00000292] main input debug: `/media/disk/MUSIC/dvd1 (Simon Posford)/Simon Posford+/Walter Ego - We're High.mp3' successfully opened
[00000318] mpeg_audio packetizer debug: MPGA channels:2 samplerate:44100 bitrate:224
[00000345] mpeg_audio decoder debug: MPGA channels:2 samplerate:44100 bitrate:224
[00000345] main decoder debug: no aout present, spawning one
[00000349] main audio output debug: looking for audio output module: 5 candidates
[00000349] alsa audio output debug: opening ALSA device `default'
[00000349] main audio output debug: thread 2979597200 (aout) created at priority 0 (alsa.c:662)
[00000349] main audio output debug: using audio output module "alsa"
[00000349] main audio output debug: output 'fl32' 44100 Hz Stereo frame=1 samples/8 bytes
[00000349] main audio output debug: mixer 'fl32' 44100 Hz Stereo frame=1 samples/8 bytes
[00000349] main audio output debug: no need for any filter
[00000349] main audio output debug: looking for audio mixer module: 3 candidates
[00000349] main audio output debug: using audio mixer module "float32_mixer"
[00000349] main audio output debug: input 'mpga' 44100 Hz Stereo frame=1152 samples/1053 bytes
[00000349] main audio output debug: filter(s) 'mpga'->'fl32' 44100 Hz->44100 Hz Stereo->Stereo
[00000351] main private debug: looking for audio filter module: 24 candidates
[00000351] main private debug: using audio filter module "mpgatofixed32"
[00000349] main audio output debug: found a filter for the whole conversion
[00000349] main audio output debug: filter(s) 'fl32'->'fl32' 48510 Hz->44100 Hz Stereo->Stereo
[00000356] main private debug: looking for audio filter module: 24 candidates
[00000356] main private debug: using audio filter module "bandlimited_resampler"
[00000349] main audio output debug: found a filter for the whole conversion[/COLOR]

```
The Blue is what appeared after I dragged one MP3 on top of the new instance of vlc -vvv --color.

The song plays, but if I just run VLC as I normally would (through the Applications>Sound>VLC shortcut), it doesn't work.

---

