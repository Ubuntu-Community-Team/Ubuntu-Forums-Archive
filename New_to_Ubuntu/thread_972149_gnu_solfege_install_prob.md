---
title: "gnu solfege install prob"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by nnjond on 2008-11-05
Hi, have tried to fire up an ear trainer but something is wrong and i don't know what my next move should be. Can anyone help?

"/usr/lib/solfege/_solfege_c_midi.so: undefined symbol: awe_set_channel_mode

You should configure sound from the preferences window, and try to use an external midi player. Or try to recompile the program and check for error messages to see why the module is not built."




thanks

---

### Post by adamgram on 2008-11-25
I'm getting the same error message on my laptop.  Did you ever get this resolved?  It's weird cause under GNU Solfege Preferences each of the individual tests (midi, wav, mp3) work fine, but the one at the bottom, 'Apply changes and play test sound' gives the same error message you got, and there is just no sound when I try to use the program.  I don't have any other audio issues with this computer.  Any help would be appreciated, thanks in advance.

---

### Post by allaf on 2008-12-22
UP, Same pb here.

---

### Post by gkforcare on 2009-01-03
Please see [this issue]("http://code.google.com/p/solfege/issues/detail?id=77") as an explanation. Try to upgrade or use the AutoPackage download. It should be solved in version 3.11 onwards. I'm trying it right now.

---

### Post by gkforcare on 2009-01-03
I tried it and it works ;-) Have fun!

---

### Post by spiderbatdad on 2009-04-26
working fine for me on jaunty. perhaps because i have other audio tool installed...like avidemux...which probably included timidity...search synaptic package manager.

---

### Post by spiderbatdad on 2009-04-26
hmm. not entirely sure of your solution, as I am running the program and do not have the package solfege-oss installed. So i think it may have more to do with your sound card or sound preferences. Generally I avoid add/remove and use synaptic package manager for all programs in the repos.

---

### Post by sodden on 2009-12-03
Hi guys.
Have same problem, but can't fix it.
installed solfege oss through sinaptic, checked and I do have timidity installed, i've changed audio setting to use external midi player, but still nothing...
please help ...
thanks

---

### Post by waspbr on 2010-01-04
go to File> preferences > Sound setup tab and select external midi player

---

