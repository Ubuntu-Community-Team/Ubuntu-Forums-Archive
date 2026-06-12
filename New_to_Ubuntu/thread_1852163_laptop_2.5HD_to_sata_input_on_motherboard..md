---
title: "laptop 2.5HD to sata input on motherboard."
date: 2011-09-29
forum: New to Ubuntu
---

### Post by artyone on 2011-09-29
I've got a connector to get from ide to sata and want to connect the laptop hardrive to my PC as a spare harddrive.

What do I set the jumpers to on the 2.5 HD?
Then will Ubuntu recognise it on startup or do I do preliminary work?
If Ubuntu does recognise it is there anything that'll need to be done to ensure it works properly.

Also it'll, the 2.5 HD, have a windows operating system on it which I would like to preview or just ghost as the laptop it came from belongs to a friend. I've never ghosted so what program, or programs, should I get to preview windows and ghost and then how to go about setting up Ubuntu partitions?

Please excuse my spelling of Recognise in English as opposed to US spelling. Hmm.

---

### Post by artyone on 2011-09-29
[http://ubuntuforums.org/showthread.php?t=1841546&highlight=sata+drive](http://ubuntuforums.org/showthread.php?t=1841546&highlight=sata+drive)

Sorry for the above posting as I'd say everything I'd ever need to know is in th above thread and should have done a search before posting.  I'm :( aren't I?

---

### Post by dwasifar on 2011-09-29
I didn't read that whole thread, so I don't know if your answers are in there, but here's how I would answer your original question.

Most IDE to SATA adapters don't care about jumper settings at all, but if you want to be sure of compatibility, set the jumper to the "Cable Select" position.  Then just connect your SATA cable and boot; Ubuntu should recognize the drive immediately, and you will see it in with the available devices.  Double-clicking on it there will mount it and allow you to look at its contents.  

If you want to ghost the complete drive, and you have a spare drive to ghost it to, the quickest way is to use dd, and I'll explain how to do that if that's what you plan on; just ask.  If all you want is the files off it (and not a bootable copy of Windows), just copy them somewhere by ordinary drag and drop.

---

