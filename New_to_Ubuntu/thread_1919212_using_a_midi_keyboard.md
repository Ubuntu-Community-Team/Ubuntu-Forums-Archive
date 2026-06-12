---
title: "using a midi keyboard"
date: 2012-02-02
forum: New to Ubuntu
---

### Post by djembeing on 2012-02-02
I'm having some trouble.
 I'm using a Roland D-5, some $5 midi to usb interface cable, Ubuntu 10.10 on a Gateway MT 6728.

I start jack, in the connections tab it say VEIWCON (which I assume is this little interface) in both readable and writable columns(i unplug in, VEIWCON disappears, plug it back in, it reappears. )

So, I open Qsynth (or zynaddsubfx, or rosegarden, or musescore, or reaper [in wine]) Making sure in jack's audio tab that it's connected to the system output. and in the alsa tab, I connect VEIWCON to qsynth(or whatever i'm tinkering with) I get nothin. Also tried connecting VEIWCON to midithru and then midi thru to qsynth. nothin

If i click on zyn's keyboard it makes sound as it should. If i load a midi file in rosegarden it plays fine, and the midi file will trigger notes on the roland keyboard.  
So, checking (for example) rosegarden's midi setup, input enabled, midi device = VEIWCON, "mash" on roland keys, nothin (except sound from the roland's headphones.)

On the interface there are three lights, a power light, illuminated when plugged in.  another light that will blink in tandem with the default click track in rosegarden (no sound from roland phones though) Or blink with a midi file.  and another light that I've never seen illuminated.
Also, if I use LMMS, I'm able to play the roland from the computer, not the other way around which is what I want.
Any ideas?
I'm kinda new to midi, I have gotten my electronic drumset to work as it should through usb with reaper.
Could be the interface/cable, I got that one in particular because a reviewer said it worked fine with ubuntu, plug n play.

---

