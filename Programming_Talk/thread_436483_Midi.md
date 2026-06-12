---
title: "Midi"
date: 2007-05-07
forum: Programming Talk
---

### Post by Auria on 2007-05-07
Okay i'm not sure people here can actually help me but let's try anyway.

I am the author of a midi app for mac OS X and i'm desperately trying to port it to linux on my ubuntu dual-boot. It's wxWidgets so interface is all fine however seems like everything was desinged to make the audio part as hard as possible.

I have gotten midi working in ALSA, so i tried writing my app in Alsa. However, resources are very little. All samples i found were outdated, segfaulted or simply "TODO". I have tried writing following the docs, and come up with something that looks good to me, but it doesn't work. So i suscribed to the ALSA mailing lists and asked there, but no one seemed to care except someone that didn't know any more than me. So stuck here.

So then i thought, Jack has midi support now, so i'll try it. I think it only was added in a recent version, so i thought i'd install from source. Okay it's installed, but there are no instructions of how to run it. The section is marked "TODO". So stuck here too.

What i want to do is to schedule a few events on a queue and then play them. Sounds very simple but cant get it to work. The only samples of that i could find were miniArp (segfaults) and pMidi (i dont get how it works, it looks very cryptic and likes to use unobivous names like md msp el and fp everywhere so thats a pain to try to understand how it works)

So now this is my last call, here perhaps because i know it's a nice community, does anyone know resources, libs, forums, etc. where i could get anything. Any help is aprpeciated

thanks

---

### Post by snoop on 2007-05-08
I am not sure how much this will help, or if you have seen it before but this page has some examples on midi development with ALSA

[http://www.midi-howto.com/midi-howto-9.html](http://www.midi-howto.com/midi-howto-9.html)

---

### Post by Auria on 2007-05-08
The first example does look nice but when i try to adapt it to my needs it sefaults :( it was desinged for use with keyboards (and i dont use any) also for ALSA 0.9 and its post 1.0 now things might have changed

---

### Post by snoop on 2007-05-09
Hmm....not sure if you want to go this route, but maybe you could look at the code of other apps that have midi capability and see which libraries they are using and how they do it? 

Apps such as Muse, rosegarden 4, etc..

Sorry I couldnt be of more help.

---

### Post by Auria on 2007-05-09
Hi,

I think I have finally found what I want : Portmidi. I had originally disregarded it because on OS X it doesn't do playback but on Linux, after checking,  it does.

I haven't yet gotten it to work within my app but I am positive this will be possible. [http://www.cs.cmu.edu/~music/portmusic/portmidi/](http://www.cs.cmu.edu/~music/portmusic/portmidi/)

Thanks for your answer anyway :)

---

