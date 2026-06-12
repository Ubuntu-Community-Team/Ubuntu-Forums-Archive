---
title: "Spotify not playing anything"
date: 2014-04-23
forum: New to Ubuntu
---

### Post by Karolina.K on 2014-04-23
Hello I just installed spotify native client , and it is not playing any files at all.
I tried to install the ffmpeg which some people said was the cause of the problem, but this did not solve the 
problem, 

Please help me :(  I have no idea what it can be :( (its not muted or anything like that)

---

### Post by Karolina.K on 2014-04-23
when I try to play a file spotify gives me this output:

13:30:33.531 E [ap_handler_impl.cpp:1693        ] ChannelError(0, 1, get_wallet)
13:30:34.445 I [audio_driver_linux.cpp:18       ] Using PulseAudio
13:30:34.466 I [index.html:1                    ] Uncaught SyntaxError: Unexpected number

---

### Post by Karolina.K on 2014-04-23
Solved , downgrade ffmpeg to scaucy version , and it will work

---

### Post by chello2 on 2014-05-06
How did you downgrade ?

---

