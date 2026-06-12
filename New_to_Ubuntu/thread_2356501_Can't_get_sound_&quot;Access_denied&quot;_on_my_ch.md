---
title: "Can't get sound &quot;Access denied&quot; on my chromebook"
date: 2017-03-23
forum: New to Ubuntu
---

### Post by metadax on 2017-03-23
Hi everyone,

I'm pretty new to Ubuntu (maybe 2 days maybe 3). I installed it on my chromebook and it's a blast. The big problem is that I can't have sound.
I go on settings>Sound and it can't figure out my sound pilot.

Anyway, I don't remember what command line i did but it gave me my sound pilot (so it recognize it) but it said that the access was denied. I changed the os from ChromeOS to SeaBios to have ubuntu, so it may be the reason why the sound doesn't work. 

And I would like it to work! ^^

So, please, can someone help?

Thank you in advance.

---

### Post by aokurami on 2017-03-25
Hello, Metadax!

Do you have little audio icon on the right-top corner of your screen? 
- if you do, click it and go to "Sound settings...". There you'll see your audio devices in "Output" tab. Click one of them, check out your sound. :)
- If you do, but you don't have anything "Output" section, try installing audio drivers corresponding to your audio-card. Maybe that could help.
- If you don't, well, refer to the second line of answer, maybe that could help.
- Try looking for problems in alsamixer. Launch your terminal and type "alsamixer" in it (without quotes). Maybe you'll find something in here.

Please Reply if you still have problems!

---

### Post by Geoffrey_Arndt on 2017-03-26
Or the Alsamixer settings are off . . . check out this tutorial:   

note the video references Kali Linux, but process is the same in Ubuntu _but you should start at the step of typing in "alsamixer" in the terminal window_ (step 4) (no need to install other apps, libs, etc.).

note2:  the tutorial says to type "m" if the channel is muted - - you can also just hit the up arrow key to unmute the channel.

[https://www.youtube.com/watch?v=JPTzVcBYVE8](https://www.youtube.com/watch?v=JPTzVcBYVE8)

---

