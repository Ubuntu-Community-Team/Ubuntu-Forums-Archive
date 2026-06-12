---
title: "MIDI input with Audacity??"
date: 2011-10-10
forum: New to Ubuntu
---

### Post by lpbryan on 2011-10-10
I'm sure this question has already been posted somewhere in these forums but I was unable to find it - at least in language that I could understand. Sorry if it's repetitive!

I recently started downloaded Audacity and wanted to try using a friend's mini-keyboard that plugs into the USB port. I understand that the keyboard is creating MIDI files, not sound, and that Audacity doesn't recognize MIDI? I'm wondering if there is a package for Audacity or something can download that will convert MIDI into something it can use?

I'm using Ubuntu 11.04 on an Acer Aspire One, and the keyboard I want to use is AKAI professional LPK25. The version of Audacity is 1.3.13

Keep in mind that this is posted in beginner talk... :)

---

### Post by marin123 on 2011-10-10
You will need some kind of VST if you want to play the keyboard.

I mean, if you plug the keyboard and play, what will that sound like? You will need an instrument that you will play.

I suggest you download LMMS and read introduction from here [http://lmms.sourceforge.net/wiki/index.php/0.4:Getting_Started](http://lmms.sourceforge.net/wiki/index.php/0.4:Getting_Started)

---

### Post by CatKiller on 2011-10-10
FluidSynth is a pretty good software synth. If it's definitely Audacity you want to use, you can use JACK to connect your MIDI input device to FluidSynth & connect FluidSynth's audio output to Audacity's inputs. Otherwise you could use something like Rosegarden to play with the MIDI as-is before exporting the audio.

---

