---
title: "MIDI in Ubuntu"
date: 2012-05-03
forum: New to Ubuntu
---

### Post by GuitarHero on 2012-05-03
I can't seem to figure out MIDI in linux.  I just got a usb midi keyboard I want to use for transcribing.  It works in MuseScore for note input but really what I want to use it for is just as a keyboard to check pitches/chords.  

It seems everything revolves around QjackCtl which I don't really understand.  I've downloaded all sorts of synths from the software center and can't figure out how to get the keyboard to play.

What do I need?  The more basic the better.  I dont need a bunch of different sound options, just a general piano sound.

---

### Post by GuitarHero on 2012-05-03
I found a qsynth/jack tutorial but I cant seem to start jack:

21:10:34.471 Patchbay deactivated.
21:10:34.472 Statistics reset.
21:10:34.485 ALSA connection change.
21:10:34.509 D-BUS: Service is available (org.jackaudio.service aka jackdbus).
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
21:10:34.525 ALSA connection graph change.
21:11:13.165 D-BUS: JACK server could not be started. Sorry
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
Thu May  3 21:11:13 2012: Starting jack server...
Thu May  3 21:11:13 2012: JACK server starting in realtime mode with priority 10
Thu May  3 21:11:13 2012: [1m[31mERROR: Cannot lock down 82246176 byte memory area (Cannot allocate memory)[0m
Thu May  3 21:11:13 2012: control device hw:0
Thu May  3 21:11:13 2012: control device hw:0
Thu May  3 21:11:13 2012: Acquired audio card Audio0
Thu May  3 21:11:13 2012: creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
Thu May  3 21:11:13 2012: control device hw:0
Thu May  3 21:11:13 2012: [1m[31mERROR: ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode[0m
Thu May  3 21:11:13 2012: [1m[31mERROR: Cannot initialize driver[0m
Thu May  3 21:11:13 2012: [1m[31mERROR: JackServer::Open() failed with -1[0m
Thu May  3 21:11:13 2012: [1m[31mERROR: Failed to open server[0m
Thu May  3 21:11:14 2012: Saving settings to "/home/ryan/.config/jack/conf.xml" ...
21:11:18.819 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started

---

### Post by llamabr on 2012-05-03
This isn't really an absolute beginner question.  Try moving it to another thread, if you don't get a reply.

What's the brand or model of the keyboard?  What software did it ship with, and what programs did you try?

```
brock@vader:~$ apt-cache search midi keyboard
allegro-examples - example programs and demo tools for the Allegro library
amsynth - two oscillator software synthesizer
bristol-data - vintage synthesizer emulator (data files)
bristol - vintage synthesizer emulator
freej-dbg - realtime video mixer and linear video editor
freej-doc - realtime video mixer and linear video editor
freej - realtime video mixer and linear video editor
libfreej-dev - realtime video mixer and linear video editor
libfreej0-dbg - realtime video mixer and linear video editor
libfreej0 - realtime video mixer and linear video editor
python-freej-dbg - realtime video mixer and linear video editor
python-freej - realtime video mixer and linear video editor
freewheeling - live looping musical instrument
frescobaldi - LilyPond sheet music editor for KDE4
lmms-common - Linux Multimedia Studio - common files
lmms - Linux Multimedia Studio
midish - shell-like MIDI sequencer/filter
musescore-common - Full featured WYSIWYG score editor (common files)
musescore - Full featured WYSIWYG score editor
noteedit - KDE Music Editor
pykaraoke-bin - free CDG/MIDI/MPEG karaoke player
rumor - Realtime MIDI keyboard to Lilypond converter
vkeybd - Virtual MIDI Keyboard
vmpk - Virtual MIDI Piano Keyboard
brock@vader:~$ 

```

---

### Post by GuitarHero on 2012-05-03
It's an Akai professional LPK25.  A tiny USB MIDI controller.  I don't think it came with any software but it should be able to interface with any midi program.

Right now I'm trying to use Qsynth and QJackctl.

Sorry, I didn't know if MIDI qualified as beginner or not.

---

### Post by llamabr on 2012-05-03
Hey, don't apologize -- if you get an answer here, then it all worked out.

If not, did you try ubuntu-studio?  You could try that thread:

[http://ubuntuforums.org/showthread.php?t=1358857&page=3](http://ubuntuforums.org/showthread.php?t=1358857&page=3)

---

