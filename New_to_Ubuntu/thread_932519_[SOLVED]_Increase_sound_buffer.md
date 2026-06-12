---
title: "[SOLVED] Increase sound buffer"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by Trzone on 2008-09-28
I have used several media programs, including totem, kaffeine, audacious and banshee.  However i get a couple skips whenever i use firefox or synaptic.  Any suggestions?

I have no problems with windows, any ideas or thoughts?  I've had this problem for a long time with ubuntu, and I have not found out why.  In VLC media player, i am losing some audio buffers, which is why it seems so scrambled.  I know in windows you can adjust specific things for your soundcard to troubleshoot, does ubuntu have anything like that?

---

### Post by markbuntu on 2008-09-28
This is probably more of a cpu usage issue.

---

### Post by Cresho on 2008-09-28
in vlc, you can adjust sound buffers.  VLC is almost independent from the operating system.

prefference, advanced, click on advanced option in lower right, choose real time priority, adjust vlc priority,  in output modules in audio, sometimes alsa makes a difference, in video default is fine volume normalizer in audio has number of audio buffers.

hope this helps.

---

### Post by Cresho on 2008-09-28
> **Trzone said:**
> I have used several media programs, including totem, kaffeine, audacious and banshee.  However i get a couple skips whenever i use firefox or synaptic.  Any suggestions?

I have no problems with windows, any ideas or thoughts?  I've had this problem for a long time with ubuntu, and I have not found out why.  In VLC media player, i am losing some audio buffers, which is why it seems so scrambled.  I know in windows you can adjust specific things for your soundcard to troubleshoot, does ubuntu have anything like that?

and I dont understand what your saying here.  Your telling me your using vlc in firefox..thats what your telling me.

---

### Post by Cresho on 2008-09-28
vlc isnt optimized at the moment.  5.1 is crap, visualization just eats it.

i use xbmc, or amarok or elisa.

---

### Post by Trzone on 2008-09-28
Now, to be exact, it does occur during high cpu usages, i've tried to play around with vlc but it continues to do it hmm...


Edit:  During high cpu usage, i seem to lose buffers...  and sometimes i just hear interrupts with no buffers lost... My computer : Hp pavilion 521N

---

### Post by markbuntu on 2008-09-28
How much ram do you have?

---

### Post by Trzone on 2008-09-29
i have 512 MB of ram, although system monitor reports 495.5 MB

---

### Post by nowshining on 2008-09-29
> **Trzone said:**
> i have 512 MB of ram, although system monitor reports 495.5 MB

that's not good, i also have 512mb but the amount of ram should be more, but less than 512 due to some stuff, incl. the kernel being held in ram?? is the RAM in ur computer good?? 'cause if that's true ur missing a bunch of ram...

---

### Post by markbuntu on 2008-09-29
Relistically, you should have at least 1GB of ram. This will reduce the use of swap. While swap is pretty fast, it is no substitute for ram for time critial applications like sound which is important. Besides, ram is very cheap these days.

---

### Post by Trzone on 2008-09-29
The swap is irrelevant, these sound problems happen no matter how much memory i am using.  I usually just disable the swap on startup, it's just annoying.   But, i will use memtest to check the ram tonight, although i highly doubt that it is ram, since it works PERFECTLY fine in windows.  Meaning that it is a software problem.  It must be an internal setting or something to that effect...

---

### Post by Trzone on 2008-09-29
Well, i stumbled upon this error message when i tried to switch to pulse audio 


audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect: Connection refused


anyone know what is wrong?  Pulse audio seems to work on intrepid ibex alpha 6 (8.10)

I'll try reinstalling some packages...

---

### Post by markbuntu on 2008-09-29
That is a common message you get when your sound is not set up optimally and sound servers are fighting over access to your sound card. You can fix that and many many other sound issues with my guide here:


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by Trzone on 2008-09-29
using the command pulseaudio -D  i was able to start pulseaudio and select it as the preferred sound server.  It's slightly worse than before, now opening almost any application makes it skip...  So, this is indeed a software issue, is there any specific way of changing a sound server to perform better? specifically alsa or pulse audio?

---

### Post by markbuntu on 2008-09-30
Try these, there is a fix for skipping and stuttering audio in the first one:

[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)


[http://pulseaudio.org/wiki/PerfectSetup](http://pulseaudio.org/wiki/PerfectSetup)

---

### Post by Trzone on 2008-10-01
That fixed a lot of the problems, i can only hear it slightly now, i'll try adjusting some of the values, such as the nice heh thanks

---

### Post by Trzone on 2008-10-01
Well, i tried the defaults in the post 

high-priority = yes
nice-level = -11
realtime-scheduling = yes
realtime-priority = 5
default-fragments = 8
default-fragment-size-msec = 5
resample-method = speex-float-0

Edit: sorry, i do want this problem solved

So with the above values, how would i improve them to perform slightly better? i know i can change speex-float-0 to 3 but im not sure about the default fragment values.  I could always change the nice value again, prolly to -15.  and does realtime priority match nice level? or is it a completely different system?

---

### Post by markbuntu on 2008-10-01
So go back to windows, have fun with your Vista.

Look, this is free. Free free free. People are trying very hard to make it work and very few of them get paid for doing so. But you do not think of this. All you think is that you got something and it doesn't work the way you want it to and that gives you some license to just bitch and complain about it?

We do not need complaints, we need help. 

If you want to complain about something

shut the **** up and go back to windows.

---

### Post by Trzone on 2008-10-02
Anyway, so i made firefox 1/4 of my screen and it seems to go away entirely. Since i want to learn why exactly this happens, if there a way i could renice the xorg server every time on startup automatically? it seems to be an issue.   There's prolly some random kernel flag that is causing this problem.

---

### Post by Trzone on 2008-10-04
The problem seems to be associated with onboard video cards... the whole cpu competing with resource intensive applications (firefox, synaptic, xorg)

Solution: Buy a sound card that has it's own mini processor

---

### Post by hatebreed on 2010-05-04
you guys kill me. When someone is asking for help with a sound buffer, don't tell him he needs more ram when 512 is more than enough. tell the guy the answer, being the buffer setting for sound in linux. If you don't know the answer then don't reply.

---

### Post by lidex on 2010-05-05
> **hatebreed said:**
> you guys kill me. When someone is asking for help with a sound buffer, don't tell him he needs more ram when 512 is more than enough. tell the guy the answer, being the buffer setting for sound in linux. If you don't know the answer then don't reply.

Dude, you're killing us. That thread is two years old. Leave it alone.

---

