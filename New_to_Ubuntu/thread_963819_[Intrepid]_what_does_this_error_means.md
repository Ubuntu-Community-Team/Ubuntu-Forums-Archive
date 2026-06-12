---
title: "[Intrepid] what does this error means??"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by _sphinx_ on 2008-10-30
Whenever I start restart "pulseaudio" I get the following error message. Please explain why there is no real time and high-priority as stated by the following line--
D: main.c: Can realtime: no, can high-priority: no
Is this because of this that whenever I play a video it hangs. It never runs smoothly.

```

$ pulseaudio --start -vvv
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root priviliges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
D: main.c: Started as real root: no, suid root: yes
I: main.c: We're in the group 'pulse-rt', allowing high-priority scheduling.
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
I: core-util.c: Successfully gained nice level -11.
I: main.c: Giving up CAP_NICE
D: main.c: Can realtime: no, can high-priority: no
W: ltdl-bind-now.c: Failed to find original dlopen loader.
I: main.c: Daemon startup successful.

```

---

### Post by Choad on 2008-10-30
i think real time audio is something ubuntu studio does... it involves some kernel patches that aren't in the main branch 

this is what i've heard

edit: i don't think that is what is causing your video to hang however.

---

### Post by _sphinx_ on 2008-10-30
Also vlc media player does not give audio at all. Although all the other players give the audio like, rhythmbox, mplayer, movie player, smplayer, etc. I have checked all the setting of the vlc media player but no help.
One more  thing,  as soon as I try to play a audio file through vlc player all the other players hangs. I have to restart them in order to play the file.
Any help guys.........plzzzz.......

---

