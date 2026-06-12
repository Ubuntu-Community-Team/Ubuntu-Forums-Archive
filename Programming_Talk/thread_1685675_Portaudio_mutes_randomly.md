---
title: "Portaudio mutes randomly"
date: 2011-02-11
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2011-02-11
I haven't used portaudio before. I though I would make a program, which makes procedural motorbike sound.

And I made the program. I use a joystick as throttle, and its just awesome. :cool: Lovely throbbing.


But unfortunately the program froze (deadlocked?) often randomly, and always at exit. :(

The RPM, pitch, volume etc... are altered in real-time by 2 threads, so I thought that might be the problem.


I added mutexes, and that fixed the deadlocks. 

(but portaudio documentation says I shouldn't use mutexes in the callback that produces samples).


Now, it just mutes instead of freezing. What might be the problem and how to fix it?

It prints this at start, and then mutes 2-10 seconds later:
> 
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)


edit:
Reopening the stream unmutes it.
edit2:
Pa_CloseStream() causes a deadlock, while Pa_AbortStream() works fine.

Thanks for your time and replies.

---

