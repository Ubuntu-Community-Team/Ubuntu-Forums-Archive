---
title: "[HowTo]Quick MIDI start-up guide"
date: 2010-01-18
forum: Outdated Tutorials &amp; Tips
---

### Post by frt975 on 2010-01-18
[COLOR=Red]*[SIZE=2]_**Notice: this involves installing non-free (the freedom kind) software**_[/SIZE]*[/COLOR]
This How to shows you how to play midi sound files.

[LIST=1]
[*] ```
sudo aptitude  --with-recommends  install timidity-interfaces-extra fluid-soundfont-g?
``` installs the instruments and gui.
[*]I'm not sure of this last step (It looks like it should be automatic, but it was required for me), but type in ```
sudo nano /etc/timidity/timidity.cfg
``` and remove the # in front of ```
#source /etc/timidity/fluidr3_gs.cfg
#source /etc/timidity/fluidr3_gm.cfg
``` so that the bottom looks like this ```

# By default, try to use the instrument patches from freepats:
source /etc/timidity/freepats.cfg

# alternatively, you can use the fluid-soundfont:
source /etc/timidity/fluidr3_gm.cfg
source /etc/timidity/fluidr3_gs.cfg
```
[/LIST]

---

### Post by andrew.46 on 2010-01-22
Hi frt975,

Thanks for making the effort with this guide :). You may be interested to know that vlc can also play midi files but only if it is compiled against libfluidsynth which I suspect is not the case with the repository vlc. Below is the cvlc output or playing such a file in an appropriately configured vlc:

```

**[COLOR="Red"][0x81166c0] smf demux debug: detected Standard MIDI File (type 1) with 13 track(s)[/COLOR]**
[0x81166c0] smf demux debug:  120 pulses per quarter note
[0xb7a005f0] main input debug: selecting program id=0
[0x81166c0] main demux debug: using demux module "smf"
[0x81166c0] main demux debug: TIMER module_need() : 2.055 ms - Total 2.055 ms / 1 intvls (Avg 2.055 ms)
[0xb7a005f0] main input debug: looking for a subtitle file in /home/andrew/Desktop/
[0x8116f80] main decoder debug: looking for decoder module: 32 candidates
fluidsynth: warning: Failed to pin the sample data to RAM; swapping is possible.
fluidsynth: warning: Ignoring sample *KPianoB5: can't use ROM samples
**[COLOR="Red"][0x8116f80] main decoder debug: using decoder module "fluidsynth"[/COLOR]**
[0x8116f80] main decoder debug: TIMER module_need() : 1148.764 ms - Total 1148.764 ms / 1 intvls (Avg 1148.764 ms)
[0x8116f80] main decoder debug: thread started
[0x8116f80] main decoder debug: thread (decoder) created at priority 5 (input/decoder.c:302)
[0x8118810] main demux meta debug: looking for meta reader module: 2 candidates
[0x8118810] lua demux meta debug: Trying Lua scripts in /home/andrew/.local/share/vlc/lua/meta/reader
[0x8118810] lua demux meta debug: Trying Lua scripts in /usr/share/vlc/lua/meta/reader
[0x8118810] lua demux meta debug: Trying Lua playlist script /usr/share/vlc/lua/meta/reader/filename.lua
[0x8118810] main demux meta debug: TIMER module_need() : 1.925 ms - Total 1.925 ms / 1 intvls (Avg 1.925 ms)
**[COLOR="Red"][0xb7a005f0] main input debug: `file:///home/andrew/Desktop/FourHorsemen.mid' successfully opened
```[/COLOR]**

But I suspect your guide will be a little more straightforward than the complex process of compiling vlc :).

All the best,

Andrew

---

### Post by frt975 on 2010-01-23
You're welcome. :)

---

