---
title: "Tuxguitar too slow."
date: 2008-08-14
forum: New to Ubuntu
---

### Post by diwas on 2008-08-14
Well my hardware config is in my signature. I have XP as well as Ubuntu. In XP, I use Guitar Pro 5.2, and here, its Tuxguitar. But I dont know why Tuxguitar is slow here. I mean it plays but it frequently jams for a few milliseconds and then moves on to another note...or chord whatever. While in XP Guitar Pro 5.2 with RSE works without any problem.

What might be the possible reason for it??

---

### Post by diwas on 2008-08-22
bump

---

### Post by diwas on 2009-01-19
This might be old post but i still have the problem...can anyone help me?

---

### Post by The Switch Blade on 2009-05-29
I also have this problem.

---

### Post by Bölvaður on 2009-05-29
difficult to tell with that information.

is it also slow when playing midi files in an audio player?
if so then install another midi library :)
if not then.. like.. um... have a bowl of popcorn :popcorn:

---

### Post by wsonar on 2009-05-29
I didn't even know there was a tuxguitar

---

### Post by diwas on 2009-05-31
> **Bölvaður said:**
> difficult to tell with that information.

is it also slow when playing midi files in an audio player?
if so then install another midi library :)
if not then.. like.. um... have a bowl of popcorn :popcorn:
YEA ITS SOLVED!!! 
I had a bowl of popcorn. *sigh* :(

---

### Post by philinux on 2009-05-31
You probably need ubuntu studio as it uses a low latency or real time kernel.

If you google > ubuntu low latency, you'll get a lot of info to help you decide.
[http://ubuntuforums.org/archive/index.php/t-474670.html](http://ubuntuforums.org/archive/index.php/t-474670.html)

---

### Post by The_Eddster on 2009-08-10
How did you fix it? What MIDI library did you install? 
I have this latency problem too. I don't want to install a low-latency kernel though, I tried installing ubuntu studio and it kept crashing all the time.

---

### Post by limeades on 2011-11-12
Uhm this is probably a late reply but you can fix it by changing its affinity. Basically, Tux Guitar cant handle itself with a cpu that has more than one core, so just go to the the task manager and go to the Processes tab. From there, find tuxguitar.exe, right-click it, set affinity and uncheck everything except for one. Should be working after that,

Cheers:popcorn:

---

### Post by overdrank on 2011-11-12
Back to sleep little thread. Thread closed

---

