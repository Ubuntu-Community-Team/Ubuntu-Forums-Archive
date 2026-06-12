---
title: "Audio note detection/ spectrum analysis from mic"
date: 2009-01-18
forum: Programming Talk
---

### Post by h12 on 2009-01-18
I'm looking for a way to get the a note or a list of frequencies from a microphone in real time. Is there any way to do this with a command line utility or, if not, is there any documentation on writing a program that does this?

---

### Post by Zugzwang on 2009-01-19
Getting a list of frequencies is a hard task. Also, interpreting a note is far from being trivial. To give you a start, have a look at the FFT representation of a wave file in Audacity (does it help you? The frequency corresponding to your note should *normally* have the highest color value at a point in time) and look at the following page:

[http://en.wikipedia.org/wiki/Fast_Fourier_transform](http://en.wikipedia.org/wiki/Fast_Fourier_transform)

"Note detection" from wave files is an ongoing research subject, even if done off-line.

---

### Post by teledyn on 2010-04-10
> **h12 said:**
> I'm looking for a way to get the a note or a list of frequencies from a microphone in real time. Is there any way to do this with a command line utility or, if not, is there any documentation on writing a program that does this?

not having the greatest ear (being self-taught) I'd been asking myself this question for a long time, and just this winter I found the answer and more in a little low-cost ($50) program called [Transcribe!]("http://blog.teledyn.com/transcribe-serious-affordable-software-for-tr") (follow link for screenshots and my review) -- and I know what you're  thinking, $50 is a lot for Linux software, but fear not the 30-day free trial is full featured and the very best part is the way this program is offered for Mac DOS and a real O/S, but the Linux version is *native* gtk, with an intelligent install program and everything; that alone is something very rare in the world of semi-commercial and especially 'portable' software.

I used the thing for a month, got addicted, had to buy it.  That makes now three programs I've bought in the past ... hmmm ... in the past 20 years :)

keep in mind, as the other commenter said, obtaining a note from a fourier is non-trivial *for a machine*, but it is not impossible for the human musician: Transcribe shows you the spectral chart *aligned to a keyboard* so you can see where the peaks are and make a pretty educated guess (based on the key signature and the instrument being played) and then *test* your guess with the keyboard sine-tones.

and as they say, *Wait!  There's more! ....* :guitar:

Up to that point i was very intrigued, but then I discovered two features that make transcription super easy for lead-ears like mine: there is a speed control (does not alter pitch) so you can slow the passage down (the way we used to play vinyl LP 33's at 16rpm) and a filter pack that can isolate only those frequencies in the range of the instrument of interest.  Very, very nice.

---

