---
title: "midi files"
date: 2012-02-28
forum: New to Ubuntu
---

### Post by thuja.plicata on 2012-02-28
I am trying to open some MIDI sequence .mid files created by my choir director. I have tried installing several software packages from the ubuntu site, but nothing has worked so far. Can anyone assist?  Thanks!

---

### Post by audiomick on 2012-02-28
What have you installed? It will help people help you if you let them know.

According to the description in Synaptic package manager, pykaraoke should be able to play .mid files. Did you try that?

---

### Post by thuja.plicata on 2012-02-28
Yes, I tried that. The file opens and the words come up, but no sound! It's the sound I need, so I can learn the music. I'm sorry I didn't put in all the names of what I tried installing. I am at work and the ubuntu-based computer is at home. I can re-send this request when I get back home and can answer that question. But thanks for answering!

---

### Post by 3rdalbum on 2012-02-28
You need the Timidity package to play MIDIs.

---

### Post by thuja.plicata on 2012-02-28
Hi - Is this the TiMidity++ MIDI sequencer? That's the only Timidity package I see in my ubuntu software center.

---

### Post by thuja.plicata on 2012-02-28
> **audiomick said:**
> What have you installed? It will help people help you if you let them know.

According to the description in Synaptic package manager, pykaraoke should be able to play .mid files. Did you try that?
OK, here's a list of what I tried installing: aqualung,audacious,bangarang,potamus,pykaraoke, seq24.  Rhythmbox and movie player were already installed and they don't work. I mean, they say they are playing the files, but I can't hear anything. Someone else suggested the timidity package. I believe I also tried installing something called timidity++midi sequencer, which did not work.

---

### Post by andrew.46 on 2012-02-28
One of the applications on your list, audacious, is capable of midi playback. However I build my own and I am not sure if the repository audacious has that capability compiled in, I attach a screenshot to show the plugin and preferences, you also need a soundfont...

---

### Post by thuja.plicata on 2012-02-28
Thanks, I will see if I can install all this!

---

### Post by Lalaith on 2012-02-29
1) just a silly thought, only to check it up... have you checked your volume is on, right? And you checked that your pc can play other kind of sounds? :-\" 

2) I had the same issue when I tried to play some partitures on tuxguitar. I installed a package from software center that is named "software sound renderer (MIDI sequencer, MOD player)" [it popped up the first when I searched for "timidity"]. When installed, I had to go to the options of the tuxguitar program and set the MIDI port to a port that worked (for me, #1), otherwise, it would'nt play anything. Maybe the only thing is failing is this port-thing setting. (just a guess).

---

### Post by audiomick on 2012-02-29
> **Lalaith said:**
> ... And you checked that your pc can play other kind of sounds? ....

This is a valid point. You know that a MIDI file doesn't in itself contain any sounds, don't you? It is only control data. There needs to be a sound engine somewhere. I'm afraid I'm not up on things these days enough to know if there should be something like that on a normal PC or not. I studied that stuff about 20 years ago, and haven't had much to do with it since. ;)

---

### Post by thuja.plicata on 2012-02-29
Yes, good question, but my sound is definitely on! I'm at work now, but when I get home this evening I'll look for the software sound renderer. And no, I did not know that the midi file doesn't contain sounds, only control data. That explains a lot! But at work, I can play the files with Windows media player, no problem, and I hear the music. At home, anything I try and open them with just scrolls out the words from the songs.

---

### Post by audiomick on 2012-02-29
> **thuja.plicata said:**
>  But at work, I can play the files with Windows media player, no problem, and I hear the music.

Yes, I know that some (all?) motherboards have midi sound generators on them, and that windows is set up to use them. As I said, I just haven't had anything much to do with this for years, so I'm not up to par with it. 

The way I see it, either your computer has no sound engine at all, which I suspect is unlikely, it is there but not supported, which I think also might be unlikely, or it is there and supported but the programs you are using to try and play the files aren't talking to it. It think the latter is probably the most likely. I hope someones shows up soon who can sort it out for you.

---

### Post by thuja.plicata on 2012-02-29
Yes, I think you're right. The files just aren't communicating.  I may try building onto the Audacious program, as someone suggested. It's beyond my experience to do so, but I'm (slowly) learning!

---

### Post by audiomick on 2012-02-29
That's not a bad idea, if you can work it out. I had a very brief look at Audacious, without having really learnt how to use it. It looks like a very powerful recording and editing program. If you are musically active, it could turn out to be a useful thing to be able to use.

Good luck.

---

### Post by thuja.plicata on 2012-02-29
Thanks, Michael!

---

### Post by winh8r on 2012-02-29
I think you might also have to edit the /etc/modules file

```
sudo gedit /etc/modules
```

and add the following lines to it and save it again:


```
snd-seq-device
snd-seq-midi
snd-seq-oss
snd-seq-midi-event
snd-seq
```

I may be wrong but I am sure someone will tell me if I am mistaken.

Hope this helps

---

### Post by thuja.plicata on 2012-02-29
OK, thanks, but here's a really basic question. Where do I find the terminal on my computer? Because what you're suggesting requires that I open a terminal, right?

---

### Post by audiomick on 2012-02-29
That's easy. If you are using 10.10 or earlier, it is in the applications menu in "accesories" or whatever the section is called where all the bits and pieces are.

If you are using 11.04 or 11.10 with unity on it, just type "terminal" in the search window in the dash.

You would be well advised to copy those commands and paste them into the terminal. The terminal has an oddity: you have to use shift+ctrl+v to paste (likewise shift+ctrl+c to copy) if you want to use the keyboard shortcuts for that.

---

### Post by thuja.plicata on 2012-02-29
Thanks, Michael! As soon as I get home from work I'm going to give this a try. I'll let you know how it goes.

---

### Post by thuja.plicata on 2012-03-01
OK, Andrew, thanks to your screen shot, I have been able to re-install Audacious, find the appropriate plug-in, and configure it. However, I am mystified as to how to acquire a sound font. I don't find one in the ubuntu software list. I assume the filename on your screenshot is the sound font in your system.  

Thanks for your patience with a newbie!

---

### Post by thuja.plicata on 2012-03-01
Thanks, Michael, found the terminal (duh...!). Now I'm waiting to get Andrew's advice on how to acquire a sound font. Even if I never get the durn files to play, I'm learning a lot.

---

### Post by andrew.46 on 2012-03-01
> **thuja.plicata said:**
> OK, Andrew, thanks to your screen shot, I have been able to re-install Audacious, find the appropriate plug-in, and configure it. However, I am mystified as to how to acquire a sound font. I don't find one in the ubuntu software list. I assume the filename on your screenshot is the sound font in your system.

Good to hear you have made some progress :). The 2 soundfonts I use can be downloaded from here:

Soundfonts for Linux 
[http://www.personalcopy.com/linuxfiles.htm](http://www.personalcopy.com/linuxfiles.htm)
  

> Thanks for your patience with a newbie!

We have all been there...

---

### Post by thuja.plicata on 2012-03-01
THANK YOU, Andrew! I will download this later this evening and give it a try.

---

### Post by thuja.plicata on 2012-03-01
[COLOR=Black][B]Woo Hoo! Andrew and Michael, it worked! I can now play my files! Good thing, too, as I have to learn these things before a concert on Sunday.

Thanks to everyone who helped me! I expect you'll hear from me again in the future - hopefully with a new challenge.[/B][/COLOR]

---

### Post by andrew.46 on 2012-03-02
Great news, best wishes for the concert too :).

---

### Post by thuja.plicata on 2012-03-02
Thanks, Andrew!

---

### Post by audiomick on 2012-03-02
Great to hear. My best wishes also for the concert. ;)

---

### Post by thuja.plicata on 2012-03-03
Thank you, Michael! I sing medieval music. Hard to imagine 13th century music amplified by electronic computer software...yet, here it is!

Be well!

---

