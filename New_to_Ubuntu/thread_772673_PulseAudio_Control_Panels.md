---
title: "PulseAudio Control Panels?"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by brucewagner on 2008-04-28
Is there a Control Panel for PulseAudio in Hardy Heron?

How do I find it?

---

### Post by jespdj on 2008-04-28
You can install the package padevchooser, via Synaptic or in a terminal window:
```
sudo apt-get install adevchooser
```
After installing that, look in Application / Sound & Video, you'll have PulseAudio Device Chooser there. If you click on it, you'll get an extra icon in the top right of the screen which you can click to configure PulseAudio, set volumes etc.

You can make the PulseAudio Device Chooser start automatically when you login by going to System / Preferences / Sessions and clicking on the Add button. Enter the following for the command to run:

/usr/bin/padevchooser

---

### Post by brucewagner on 2008-04-28
> **jespdj said:**
> After installing that, look in Application / Sound & Video, you'll have PulseAudio Device Chooser there.

Why isn't this installed by default on Ubuntu?

Otherwise, how are users supposed to control their audio?

---

### Post by MemoryDump on 2008-04-28
> **brucewagner said:**
> Why isn't this installed by default on Ubuntu?

Otherwise, how are users supposed to control their audio?
I've been asking myself this question too. :-k

also, when I ran "sudo apt-get install adevchooser" I got:
"E: Couldn't find package adevchooser"

I'm assuming I'm missing a repo? I thought I had them all enabled.

edit: hmm.. it seems I have "/usr/bin/padevchooser" installed already.. however I'm not really sure how to use it. I'm having a hard time as I have 2 sound cards. (yes I need both. 1 for my speakers the other for my headset)

---

### Post by kostkon on 2008-04-28
Check this: [http://tombuntu.com/index.php/2008/04/10/adjust-volume-of-individual-applications-with-pulseaudio/]("http://tombuntu.com/index.php/2008/04/10/adjust-volume-of-individual-applications-with-pulseaudio/")

---

### Post by Shachiel on 2008-04-28
> **MemoryDump said:**
> I've been asking myself this question too. :-k

also, when I ran "sudo apt-get install adevchooser" I got:
"E: Couldn't find package adevchooser"

I'm assuming I'm missing a repo? I thought I had them all enabled.

edit: hmm.. it seems I have "/usr/bin/padevchooser" installed already.. however I'm not really sure how to use it. I'm having a hard time as I have 2 sound cards. (yes I need both. 1 for my speakers the other for my headset)

Thats because the package is padevchooser, try

```

sudo apt-get install padevchooser pavumeter pavucontrol paprefs paman

```

Or check the guide at [http://www.pulseaudio.org/wiki/PerfectSetup](http://www.pulseaudio.org/wiki/PerfectSetup)

---

### Post by Tatty on 2008-04-28
I went to Applications->Add/Remove then searced for "pulse".

---

### Post by brucewagner on 2008-04-30
Obviously, the GUI user interface & all controls need to be installed BY DEFAULT. 

What were the Ubuntu developers thinking?

Is there some reason they DIDN'T include them installed by default?

---

### Post by brucewagner on 2008-04-30
> **Tatty said:**
> I went to Applications->Add/Remove then searced for "pulse".

And what happened?

Did that work as well?

---

