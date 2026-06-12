---
title: "Festival SayText does nothing (almost)"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by sdlyr8 on 2008-05-09
Hey I just installed Festival and festvox-don for a project I'm working on. I open Festival and try 
```
(SayText "Hello")
```
And I hear nothing (yes, the speakers are on and volume is up:p). But I do get the message 
```
#<Utterance 0xb7129c18>
```
which from what I have looked at is normal and nothing to worry about. But the fact is I'm still not getting any sound. I have also tried 
```
echo "Hello" | festival --tts
```
and again I get nothing..

Anyone know what is wrong here and how to fix it?

---

### Post by terry f on 2008-05-09
I am having some problems as well I get Utterance 0x7f54afce9d30 as an error.

---

### Post by sdlyr8 on 2008-05-10
Yeah well getting the message Utterance 0x7f54afce9d30 isn't really an error (from what I read up).
> The (hex) number in the return value may be different for your installation. That is the print form for utterances. Their internal structure can be very large so only a token form is printed.
But it doesn't give any errors as to why no sound is coming out...

---

### Post by spacesearcher on 2008-06-24
I was having similar problems I found this post:
[http://ubuntuforums.org/showthread.php?t=171182&page=2](http://ubuntuforums.org/showthread.php?t=171182&page=2)
and on that post there was this magical command that fixed it:
```
printf ";use ALSA\n(Parameter.set 'Audio_Method 'Audio_Command)\n(Parameter.set 'Audio_Command \"aplay -q -c 1 -t raw -f s16 -r \$SR \$FILE\")\n" > .festivalrc
```

after i did that it worked.

---

### Post by alienexplorers on 2008-06-24
To get festival to read a text file just run this in terminal:
> festival  --tts "hello.txt"
Just make sure you have something in the text file to read!

---

