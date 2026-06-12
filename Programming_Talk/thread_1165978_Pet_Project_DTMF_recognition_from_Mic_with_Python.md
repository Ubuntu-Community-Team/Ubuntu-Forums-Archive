---
title: "Pet Project: DTMF recognition from Mic with Python"
date: 2009-05-21
forum: Programming Talk
---

### Post by UbuKunubi on 2009-05-21
Hello again!

Today Im trying to use my phone to navigate around firefox.
The idea is that the Mic will pick up the DTMF tone made when I press a key on my phone, and move the link focus accordingly. 

I'm confident that I have most of the code to hand, except, as you've guessed, the DTMF recognition.

Is there a module i need to use to do this for python?

Has anyone else done anything similar?

Thanks,
Ubu

---

### Post by iiska on 2009-05-21
With [NumPy]("http://numpy.org") you could do a Fourier transformation of the recorded sample and then look for the [frequencies]("http://en.wikipedia.org/wiki/DTMF#Keypad") used by the DTMF tones.

I don't yet have experience in doing fft stuff with NumPy, so I'm not sure how tedious doing DTMF recognition that way would be.

---

### Post by UbuKunubi on 2009-05-21
iiska,

Thanks for your pointers.
I knew there had to be something out there.

I did find multimon, which is supposed to decode DTMF directly, BUT it appears not to work. The documentation for it seems sparse (By internet is via my mobile so I dont have 'full' range access to all the search engines results :-( )

Cheers,
Ubu

---

### Post by UbuKunubi on 2009-05-21
This is a BIG problem!

scikits.talkbox 0.2.3 is what is needed to be used for the DTMF detection from [http://pypi.python.org/pypi/scikits.talkbox](http://pypi.python.org/pypi/scikits.talkbox).

But I have NO clue how to use it.

Do any of the Python Guru's have any words of wisdom?

Ubu.

---

### Post by Krupski on 2009-05-21
> **UbuKunubi said:**
> Hello again!

Today Im trying to use my phone to navigate around firefox.
The idea is that the Mic will pick up the DTMF tone made when I press a key on my phone, and move the link focus accordingly. 

I'm confident that I have most of the code to hand, except, as you've guessed, the DTMF recognition.

Is there a module i need to use to do this for python?

Has anyone else done anything similar?

Thanks,
Ubu

I did it quite a long time ago. I digitized a 1024 byte sample of audio at 8000 Hz., did an FFT on it and found the two major frequencies of each "touchtone".

It was in Motorola 68xxx assembler though... sorry no C or Python...

---

### Post by UbuKunubi on 2009-05-21
Krupski,

Thanks for your post,
to be honest i did find myself leaning toward the soldering iron and dusting of a Picstart plus.... but the PCB i have to hand does not have RS232 (yet!).

It does now look like it IS possible to use python to do this.

I searched and fell on [http://www.acronymchile.com/](http://www.acronymchile.com/) which leaves me now at the bottom of a steep learning ramp (again....)

Since my first post my friends who also have Ubuntu have asked if I can add a 'program profile', so you can pick the program with the DTMF, and then navigate around the program. (I think this will need a LOT of Xdo work, but ho hum).

So if ANYONE can help me to get to grips with the Numerical Python and FFT modules I'd be very grateful. (YES the full write up will go here for everyone to use)

Cheers,
Ubu

---

### Post by UbuKunubi on 2009-05-25
Bump!

This is an appeal now to the math and Python Gurus, can anyone please just tip a pointer at how I go about using FFT to determine the Frequency of each sample point?

Many thanks,
Ubu

---

### Post by UbuKunubi on 2009-05-25
Sorry!

Please ignore previous posting!

Researching at [http://xoomer.virgilio.it/sam_psy/psych/sound_proc/sound_proc_python.html](http://xoomer.virgilio.it/sam_psy/psych/sound_proc/sound_proc_python.html)

Led me to read:
> 
 Plotting the Frequency Content

Another useful graphical representation is that of the frequency content of the tone. We can obtain the frequency content of the sound using the fft function, that implements a Fast Fourier Transform algorithm. We'll follow closely the following technical document [http://www.mathworks.com/support/tech-notes/1700/1702.html](http://www.mathworks.com/support/tech-notes/1700/1702.html) to obtain the power spectrum of our sound.

 n = len(s1) 
 p = fft(s1) # take the fourier transform 


Now for a coffee!

Ubu (and out!)

---

### Post by soltanis on 2009-05-25
Dunno if you still need help, but a Fast Fourier Transform takes evenly sampled data and runs an optimized Discrete Fourier Transform over it. A FT takes waveform-encoded data (like sound, but also any other measurement) and returns frequencies of the sine waves, which when added together, approximate the data you gave the function.

Basically, DFT operates on the assumption that every wave can be written as the finite sum of sine waves. It decomposes complex waveforms into those sine waves, which you will need to do if you are listening for particular frequencies in a sound tone.

---

### Post by UbuKunubi on 2009-05-26
soltanis,
thanks for your reply.

I hoping to get this wrapped up before the end of the week!

What I'm trying to learn specifically is:

a) how to step through the sample and get each sample frequency
b) how to test the sample for 2 frequencies (DTMF is two tones at the same time!?!)
c) or how to test for the loudest(clearest?) frequencies.

The sample MAY contain the end of one tone, and the start of another, so I need to find a way of getting a list of frequencies, rather than just testing for a single DTMF.

If anyone help help me further my knowledge PLEASE post!

Many thanks,
Ubu

---

### Post by ushimitsudoki on 2009-05-26
Here is C code for a DTMF decoder, it looks like it will go into Python easily:
[http://en.wikipedia.org/wiki/Goertzel_algorithm](http://en.wikipedia.org/wiki/Goertzel_algorithm)

In fact, someone has already implemented it in Python:
[http://johnetherton.com/projects/pys60-dtmf-detector](http://johnetherton.com/projects/pys60-dtmf-detector)

You could probably do the C->Python conversion yourself before looking at the second link.

> b) how to test the sample for 2 frequencies (DTMF is two tones at the same time!?!)
Yes. That is why it is called **Dual Tone** Multi-Frequency! :)

---

### Post by ad_267 on 2009-05-26
You can think of the output from the Fourier transform as a plot of amplitude against frequency, this is the power spectrum. There will be peaks in this plot corresponding to the frequencies present in your key tone. The lowest frequency peak is the fundamental frequency, you only need the fundamental frequency to determine the tone. This is going to be made a bit more difficult by the fact that there are two tones present, each with a fundamental frequency and higher frequency harmonics.

Determining what's happening at the start and end of a signal is going to be more difficult again, I'm not sure how you'd go about that. I'd just try it out and see what kind of frequency response you get.

---

### Post by UbuKunubi on 2009-05-27
ushimitsudoki,

Many thanks for your reply!
Its very appreciated.
I'll be giving it the go over shortly.
Thanks again,
Ubu

---

### Post by UbuKunubi on 2009-05-27
ad_267,

I agree with your line of thinking,
Its more like I'll have to try different approaches and see what works, perhaps lokking for WHAT works rather than WHY it works.

Cheers,
Ubu

---

