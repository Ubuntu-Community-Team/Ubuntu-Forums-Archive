---
title: "Get Me Started on Voice Recognition"
date: 2009-12-06
forum: Programming Talk
---

### Post by Jefferythewind on 2009-12-06
Hi all,
  I understand that the scope of this question is not limited to just Ubuntu, so i apologize a little for posting here, however love using ubuntu and over the years have received a lot of good advice at the UbuntuForums so I will ask the gracious community:

  I am getting into a little bit programming, although I am still pretty new to it, I have done some C and some BASIC.  Anyway, i would like to get started with my own speech recognition program.  I was wondering if anyone knows anything about which language would be best to get me started.  I have just visited the Sphinx website,[http://cmusphinx.sourceforge.net/html/cmusphinx.php]("http://cmusphinx.sourceforge.net/html/cmusphinx.php") and I think that it may be a little to advanced for me to dive right into their code, so I really want to start very slowly myself.

 Basically i want to know what language/compiler could i use on ubuntu/Linux that would allow me to monitor a microphone input in real-time and hopefully trigger some responses.  I know that the hard part is to get the program to recognize your voice, but I will worry about that later, i don't even know where to start.

Thanks a lot everybody

---

### Post by CptPicard on 2009-12-06
Well, yes, the entire problem is essentially totally non-language-dependent and the hard parts are math (I believe bayesian belief networks have shown good success at voice recognition at least at Microsoft's research labs).

I guess this is a case of learning to program first... learn Python and play with some audio library; I am sure there are those around.

---

### Post by Jefferythewind on 2009-12-06
Thanks Captain, I have a few interesting scripts i python, i will take a look and try to learn a little.  A follow up question:  I am working with the Arduino ([http://en.wikipedia.org/wiki/Arduino]("http://en.wikipedia.org/wiki/Arduino")) and part of real-time audio processing the sound has to go through analog-to-digital conversion (ADC).  I imagine that isn't required on python, it must be part of the basic OS, is that correct?

---

### Post by CptPicard on 2009-12-06
Oh, you have some special hardware involved in this. That probably changes the situation quite a bit... I honestly know nothing of this interface, you're much better off referring to the manual :)

---

### Post by grayrainbow on 2009-12-06
> **Jefferythewind said:**
> Thanks Captain, I have a few interesting scripts i python, i will take a look and try to learn a little.  A follow up question:  I am working with the Arduino ([http://en.wikipedia.org/wiki/Arduino]("http://en.wikipedia.org/wiki/Arduino")) and part of real-time audio processing the sound has to go through analog-to-digital conversion (ADC).  I imagine that isn't required on python, it must be part of the basic OS, is that correct?
No, ADC, just like a DAC, is part of your soundcard.
Btw [http://ubuntuforums.org/showthread.php?t=671190]("http://ubuntuforums.org/showthread.php?t=671190")

---

### Post by Jefferythewind on 2009-12-06
Thanks grayrainbow,
  I had seen that post and actually tried using sphynx, which compiled alright but i started getting fatal errors when starting the training, which is part of the tutorial.  That seems very complex and is a large combined effort, i hope i get it going on Ubuntu.  What I am trying to do is much simpler.  No speech to text, just speech commands that can execute other things...

---

### Post by phrostbyte on 2009-12-07
If you want to write your own engine you need some kind of ML algorithm. An algorithm based on the concept of Hidden Markov Models works often for speech. I think Sphinx's algorithm uses HMMs.

---

### Post by phrostbyte on 2009-12-07
If it's a small set of commands try this algorithm:

[LIST=1]
[*]From each command, generate a 256 bucket histogram from the frequency PCM data. Store this somewhere.
[*]When the user speaks something, likewise generate a 256 histogram from their waveform.
[*]Do vector distance measure (Euclid, chi-square, etc.) on the user's histogram and each of the command's histogram
[*] The histogram which has the closest distance to the user's histogram is the right answer. 
[/LIST]

This algorithm involves very little math, which some would argue is always a plus. :) I have another, possibly stronger algorithm in mind which uses eigenvectors and eigenvalues but I will not get into that. :P

---

### Post by TheStatsMan on 2009-12-07
> **phrostbyte said:**
> If you want to write your own engine you need some kind of ML algorithm. An algorithm based on the concept of Hidden Markov Models works often for speech. I think Sphinx's algorithm uses HMMs.

If ML refers to maximum likelihood, then this statement is a bit miss-leading. I estimate HMMs all the time without ML so whilst you could possibly use it, you certainly don't need it.

---

### Post by meastp on 2009-12-07
I just took a course in AI-programming where the third (and last) project was speech recognition. The course website is here ( [http://www.idi.ntnu.no/emner/it3105/](http://www.idi.ntnu.no/emner/it3105/) ).

---

### Post by Jefferythewind on 2009-12-07
> **phrostbyte said:**
> If it's a small set of commands try this algorithm:

[LIST=1]
[*]From each command, generate a 256 bucket histogram from the frequency PCM data. Store this somewhere.
[*]When the user speaks something, likewise generate a 256 histogram from their waveform.
[*]Do vector distance measure (Euclid, chi-square, etc.) on the user's histogram and each of the command's histogram
[*] The histogram which has the closest distance to the user's histogram is the right answer. 
[/LIST]

This algorithm involves very little math, which some would argue is always a plus. :) I have another, possibly stronger algorithm in mind which uses eigenvectors and eigenvalues but I will not get into that. :P

Phrostbyte.  I think for the first kind of program that I am doing this will be enough.  There will be only a small number of commands.  Also this light way of programming will be good for the stand-alone device i have.  I will try to get something like this going before i venture into Eigenspace.

---

