---
title: "Midi in Ardour"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by Periswell on 2008-05-06
this must sound like it is coming from a noob from some of you people and this most have been my millionth problem post today but its late at night and a quick google search did not give any logical answer. the simple question is is how do i add a .midi file in ardour. no matter what i do it can only open .wav. all i want to do is to convert midi files to wav so i can add them to my movie i made in blender. please help.

-josh.

---

### Post by Periswell on 2008-05-07
bumped back from 10th page. please answer.

---

### Post by warbread on 2008-05-07
A MIDI file is not audio.  You cannot open a MIDI file using an audio program.  Think of MIDI as the sheet music a musician uses to play music from.  Does that piece of sheet music do anything if you put it into a cd player?  The sheet music (MIDI file) needs a musician to play it in order to make noise. I believe Rosegarden can read .midi files, but you still need to give it an instrument to play.  Something like Zynaddsubfx or Qsynth, if you have some sound fonts, can be controlled by Rosegarden.  Once you have your sheet music in front of some musicians and can get them playing what you want, then you'll need to record them, just like any other band or orchestra.  THAT's where Ardour comes in.

---

### Post by Periswell on 2008-05-07
so i just press record in ardour when rosegarden is playing.

---

### Post by warbread on 2008-05-07
Well, you'll have to send your instrument's outputs to Ardour's inputs, otherwise Ardour won't have anything to read.  For that you'll probably need Jack.  Have you used that before?

---

### Post by Periswell on 2008-05-07
nope, anyway, what is jack?

-josh

---

### Post by warbread on 2008-05-07
Jack takes the output of one audio program and sends it to the input of another.  See [jackaudio.org]("http://jackaudio.org/") for more information.  

You need the realtime kernel enabled, the jackd soundserver running and then jack enabled programs, such as Rosegarden and Ardour.

---

### Post by Periswell on 2008-05-07
so i just stick a wire into the speacker output and the other end in the microphone input?

-josh

---

### Post by warbread on 2008-05-07
Well, that's the basic idea, except it's all done in software.  Imagine that every Jack-enabled program has a cable coming out of it that carries sound out and a plug that other programs can plug into where sound comes in.  You decide where they plug into.

---

### Post by rjmoerland on 2008-05-07
Try this link for a step-by-step explanation:[http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/]("http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/")

---

### Post by Biggy on 2008-05-07
Use [Hydrogen]("http://www.hydrogen-music.org")

---

### Post by Periswell on 2008-05-07
thanks

---

### Post by goodmanbrown on 2008-05-11
The advice you've gotten here seems right.  The best way to get midi into ardour is via a softsynth like ZynAddSubFX hooked up with Jack.  But depending on what you're trying to do, there's a quick and dirty way that doesn't involve Jacking anything together.

1. Install timidity++, a midi player.

```
sudo apt-get install timidity
```

2. Use timidity++ to convert your midi file to wav.

```
timidity -Ow [your_midi_file]
```

(The -Ow switch tells timidity to write a wav file to disc)

3.  From inside Ardour, import existing audio file.  (Maybe it is "import external audio file."  I can't remember, but you get the idea.

---

