---
title: "[SOLVED] How to export to mp3 in Audacity?"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by garyed on 2008-05-19
I've been trying to export a wav to mp3 in Audacity.

It prompts me to find libmp3lame.so but it's nowhere on my computer.

I installed Lame throught apt-get & it works from a command line but I can't get Lame to work through Audacity. 
Any ideas?

---

### Post by muted1987 on 2008-05-19
there is a quicker and easy way to do this 

1. in terminal sudo aptitude install mpg123

2. also in terminal navigate to folder .wav is in

3. also in terminal mpg123 -w file.mp3 file.wav 

renaming file to the name if the wav file 

hope this helps

---

### Post by garyed on 2008-05-19
Thanks for the help but I really want to be able to export to an mp3 from an editing program. I guess I'm getting lazy. I can use the command line with Lame & it does the job too but I don't understand why Audacity needs something else from Lame to work.

---

### Post by muted1987 on 2008-05-19
im not sure about that as im only starting out myself


but in synaptic maybe even though you have lame installed maybe you have missed the component audacity is looking for. could always give reinstalling Lame a try

---

### Post by garyed on 2008-05-19
I'll try that but usually apt-get does the same thing as synaptic.
Maybe my versions are not right. I'm running gusty Ubuntu Studio.

---

### Post by muted1987 on 2008-05-19
i wouldnt know anything about different distros as i came in right at the end of gutsys life 4 days before hardy came out.

---

### Post by garyed on 2008-05-19
There was a package in synaptic called "liblame0" that I had to install.
Along with it came "liblame-dev" but that did the trick.
Now I can export to mp3 direct from Audacity.

I was planning on reinstalling Lame completely but searching through synaptic I saw that package that looked similar to the file audacity was looking for so I tried it & it worked. Thanks again for the ideas.

---

