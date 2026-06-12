---
title: "[Python] Short beep Long beep wait"
date: 2011-03-25
forum: Programming Talk
---

### Post by ki4jgt on 2011-03-25
Wanting to write a program for Morse Code. Would like to emit a short beep and a long beep and be able to wait in silence for about a second between words and letters. Originally I thought of making MP3 files of all the letters and then playing them like that, but I was wondering if I could make a system beep to accomplish this.

---

### Post by cgroza on 2011-03-25
Hmmm, if I remember, there is a special character ("\a") that did make the mother board speaker beep. But I do not think that it is suitable for you. Maybe if you register the long beep and the short beep on some file that you can play, you could create 2 functions that will beep.

---

### Post by ki4jgt on 2011-03-25
What's the best way to play a sound file? I've tried wx.Sound(path) but the sound part isn't defined (according to error I keep getting)

---

### Post by cgroza on 2011-03-25
Take a look on gstreamer, although it may be too much for a simple sound.

---

### Post by ki4jgt on 2011-03-26
> **cgroza said:**
> Take a look on gstreamer, although it may be too much for a simple sound.

Anything which would be usable on all OSs?

---

### Post by cgroza on 2011-03-26
Why do you need beeps anyway? Are you planning to stream it over a microphone or a file? For me, output in a text format is more useful.

---

### Post by ki4jgt on 2011-03-26
I'm planning on allowing them to learn by ear. I want to capture what they type (in any window), add it to a list, and then keep playing the list's first letter (Removing letters which are played) making it easier to learn. Most people get really slow when they study by ... --- However, if they study by ear, they associate it with rhythm and are able to keep up with it at speeds way faster than most people who use the ... --- method. I'm still Google surfing, but all I can find that doesn't require installing something (Which means, all my users would also have to install it) is wx.Sound(), which doesn't seem to be defined. I've looked into generating tones, found a great script which dealt with frequency and time, but ultimately required me to install another module.
It's fine for me to do that, but I'd say (Guessing) a good 30 percent of my users, have barely learned to check their emails, much less install a module into Python.

---

### Post by cgroza on 2011-03-26
You can bundle the modules with your installer, or make a script that will install it automatically. The wx.Sound is not installed by default either. You need to get the wxPython library for it.

---

