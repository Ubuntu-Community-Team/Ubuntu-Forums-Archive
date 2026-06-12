---
title: "guitar tuner programming for linux"
date: 2011-06-27
forum: Programming Talk
---

### Post by eladriels on 2011-06-27
actually this "guitar tuner programming" project is not a new idea for me but i couldnt spare  time for it until now. i want to write a program for linux that i can tune my guitar. for programming language i am planning python, c++/c or java. so how can i start or where. how can you guys help me. 

any help will be appreciated:)

---

### Post by PaulM1985 on 2011-06-27
This sounds like a great idea.

Somehow you are going to want to 
-record a sound that you play,
-get the frequency of that sound
-lookup where that frequency is

There is some stuff here on audio frequency:
[http://en.wikipedia.org/wiki/Audio_frequency](http://en.wikipedia.org/wiki/Audio_frequency)

Some (hopefully) useful links found while googling, they are a little Java biased because I program in Java:
[http://www.gamedev.net/topic/435287-audio-programming---find-pitch-note-from-sound-file/](http://www.gamedev.net/topic/435287-audio-programming---find-pitch-note-from-sound-file/)
[http://www.jsresources.org/faq_audio.html#detect_frequency](http://www.jsresources.org/faq_audio.html#detect_frequency)
[http://en.wikipedia.org/wiki/Digital_signal_processing](http://en.wikipedia.org/wiki/Digital_signal_processing)
[http://www.ee.ucl.ac.uk/~mflanaga/java/FourierTransform.html](http://www.ee.ucl.ac.uk/~mflanaga/java/FourierTransform.html)

If you do use Java, you are probably going to want to use JMF (Java Media Framework) or something similar.

I imagine the difficulty will come from getting the frequency of the sound, hopefully the links above will help with that.

Good luck, this is something that I am definitely interested in.  I'm sick of buying batteries for my current tuner.

Paul

---

### Post by gmargo on 2011-06-27
It sounds like a great project.  You might get some ideas from the existing guitar tuner packages available in the repositories.  There are at least two that show up through apt-cache:

gtkguitune - Guitar and other instruments tuner
lingot - accurate and easy to use musical instrument tuner

---

### Post by eladriels on 2011-07-04
> **PaulM1985 said:**
> This sounds like a great idea.

Somehow you are going to want to 
-record a sound that you play,
-get the frequency of that sound
-lookup where that frequency is

There is some stuff here on audio frequency:
[http://en.wikipedia.org/wiki/Audio_frequency](http://en.wikipedia.org/wiki/Audio_frequency)

Some (hopefully) useful links found while googling, they are a little Java biased because I program in Java:
[http://www.gamedev.net/topic/435287-audio-programming---find-pitch-note-from-sound-file/](http://www.gamedev.net/topic/435287-audio-programming---find-pitch-note-from-sound-file/)
[http://www.jsresources.org/faq_audio.html#detect_frequency](http://www.jsresources.org/faq_audio.html#detect_frequency)
[http://en.wikipedia.org/wiki/Digital_signal_processing](http://en.wikipedia.org/wiki/Digital_signal_processing)
[http://www.ee.ucl.ac.uk/~mflanaga/java/FourierTransform.html]("http://www.ee.ucl.ac.uk/%7Emflanaga/java/FourierTransform.html")

If you do use Java, you are probably going to want to use JMF (Java Media Framework) or something similar.

I imagine the difficulty will come from getting the frequency of the sound, hopefully the links above will help with that.
Good luck, this is something that I am definitely interested in.  I'm sick of buying batteries for my current tuner.

Paul

thanks for links,  they helped me to find a starting point. actually the fft thing bothers me and of course the gui's design should be understandable. i use aptuner on windows for years and want to do something similar to it(not cheating just take as an example.:))

---

### Post by eladriels on 2011-07-04
> **gmargo said:**
> It sounds like a great project.  You might get some ideas from the existing guitar tuner packages available in the repositories.  There are at least two that show up through apt-cache:

gtkguitune - Guitar and other instruments tuner
lingot - accurate and easy to use musical instrument tuner

thanks, lingot is pretty useful . i checked its source code , its new versions code is a little complex to understand for me:) but older versions helped me:)

---

