---
title: "[SOLVED] Ubuntu wont play audio from websites"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by GumpTron on 2008-10-14
Hello,

I am starting to get the hang of Ubuntu but I am having one issue. I can hear the start up and shutdown sounds that Ubuntu makes, but for some reason I can't hear the music on this website ([www.rkuprising.com](www.rkuprising.com)) or any other websites. I clicked all the sound test buttons and I am able to hear the chimes but I still cant hear anything really. Help!

p.s. the sounds that i can hear, and they are few, are extremely faint and hard to hear. Thank you for any help.

---

### Post by bangmalley on 2008-10-14
what about switching to ALSA.
System->Preferences->Sound.

---

### Post by hyper_ch on 2008-10-14
you need to install flash

Google for "medibuntu", add the medibuntu repo according to their homepage, update the package list and the install the flash package (can't recall the name right now but you can then find it through synaptic)

---

### Post by GumpTron on 2008-10-14
> **hyper_ch said:**
> you need to install flash

Google for "medibuntu", add the medibuntu repo according to their homepage, update the package list and the install the flash package (can't recall the name right now but you can then find it through synaptic)

i installed the flash through firefox, but i still cant hear the music. Can you elaborate on "medibuntu"? thank you

---

### Post by hyper_ch on 2008-10-14
can you watch videos on youtube??

As for "medibuntu" --> just do as I said ;)

---

### Post by starcannon on 2008-10-14
You'll need some codecs, and to get those you'll need some additional software repositories; so:
[INDENT]
[LIST=1]
[*][https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories](https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories)
[*]System>Administration>Synaptic Package Manager
[LIST]
[*]Search: ubuntu-restricted-extras
[LIST]
[*]tick the box for install
[/LIST]
[*]Search: lame
[LIST]
[*]tick the box for install (I use lame not twolame)
[/LIST]
[*]Search: w32codecs
[LIST]
[*]tick the box for install
[/LIST]
[*]Click Apply
[LIST]
[*]click apply again
[*]consent to the licensing windows that pop up
[/LIST]
[/LIST]
[*]System>Preferences>Sound
[LIST]
[*]Sound Events
[LIST]
[*]Sound playback: Alsa-Advanced Linux Sound Achitecture (test to make sure it works)
[/LIST]
[*]Music and Movies
[LIST]
[*]Sound playback: Alsa-Advanced Linux Sound Achitecture (test to make sure it works)
[/LIST]
[*]Audio Conferencing
[LIST]
[*]Sound playback: Alsa-Advanced Linux Sound Achitecture (test to make sure it works)
[*]Sound capture: Alsa-Advanced Linux Sound Achitecture
[/LIST]
[*]Defaulto Mixer Tracks
[LIST]
[*]Device
[LIST]
[*]Your Actual Sound Card from the drop down list.
[LIST]
[*]Choose the mixer component to control it(Front, PCM, or Master are common choices, mess around find what works best for you).
[/LIST]
[/LIST]
[/LIST]
[/LIST]
[*]Unless I left something out, or something else is wrong, that should get you going.
[/LIST]
Enjoy,
Starcannon
[/INDENT]

---

