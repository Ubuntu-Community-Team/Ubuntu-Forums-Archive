---
title: "How do I make the speakers louder?"
date: 2012-11-06
forum: New to Ubuntu
---

### Post by minetruly on 2012-11-06
Good day.

VLC media player can make the audio come out twice as loudly as it does with any other application. I'm wondering if there is some command line I can put into Terminal to make the computer capable of playing audio at "200%" no matter what software is making the noise.

(Ubuntu 12.0.4 on an HP Pavilion dv6.)

Posted to Absolute Beginners Section because I really am a beginner, and have only copied command lines for a couple little things like enabling chiral scrolling and changing the screen idle time. I'm expecting something similar to raise my speakers' limit.

Thank you!

---

### Post by josephmills on 2012-11-06
Open Dash (see picture one) 
enter in Settings (or just sound) 
[img]http://ubuntuforums.org/attachment.php?attachmentid=226802&&stc=1&thumb=1&d=1352247030[/img]
then go to **Sound**

then mess around (see screenshot) 
[img]http://ubuntuforums.org/attachment.php?attachmentid=226801&stc=1&thumb=1&d=1352247030[/img]
:) hope this helps

---

### Post by Frogs Hair on 2012-11-06
I thought VLC had an equalizer in tools , but I don't know if it is applicable in the Linux version.

---

### Post by minetruly on 2012-11-06
Crikey! That's exactly what I needed! Thank you!! I especially appreciate the trouble you went to in providing screenshots. How thoughtful of Ubuntu to have a slider all ready for me!

If anyone is planning on posting the command lines for it, I'm still curious to see how that would work.

---

### Post by minetruly on 2012-11-06
How do I give a comment a "tumbs up" or "solved"? Thank you again, josephmills!

---

### Post by minetruly on 2012-11-06
Deepest apologies, but it turns out the previously posted solution does not quite work. My changes to the master volume are not "remembered," and when I check back on the Sound panel, the slider has reset itself to below 100%.

I still REALLY appreciate the time josephmills took to answer, especially, again, taking the trouble with the screenshots. 

How can I enable a higher limit to the volume, and make it stick, even after restarting? What I'm imagining is that somewhere in the OS is a bit of code that says, "do not put any more energy than X through to the speakers," which protects the speakers from playing sound loud enough to damage them. Kind of like putting a circuit breaker between your software and your speakers. This, then, would just be a number you can change in the code to globally raise the limit... at risk to your speakers, of course, but I'd imagine the default limit is cautiously low. 

Isn't this the sort of thing you can do in Terminal?

(If any of my statements seem naiive or lacking in technical terms, please note that I really am a beginner.)

---

### Post by wojox on 2012-11-06
Have you tried [paman]("http://superuser.com/a/146792/112391") (PulseAudio Manager).

---

### Post by josephmills on 2012-11-07
I would ask this question on askubuntu.com. I looked through most the dbus setting and can not find anything to remeber the last state of the volume. 

some things that I think that might help you on finding you way to a answer 

[http://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/User/PulseAudioStoleMyVolumes](http://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/User/PulseAudioStoleMyVolumes)

I would also say look at the file 

/etc/pulse/default.pa
do you see the part that looks like this ?  
```
### Automatically restore the volume of streams and devices
load-module module-device-restore
load-module module-stream-restore
load-module module-card-restore

``` 


Is that the same or is it commented out ?  (comments are just # at start of line )

again sorry that things did not work out but I am sure that there is someone somewhere that is a volume master good luck

---

