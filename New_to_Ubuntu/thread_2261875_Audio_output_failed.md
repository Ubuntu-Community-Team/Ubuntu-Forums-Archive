---
title: "Audio output failed"
date: 2015-01-21
forum: New to Ubuntu
---

### Post by flex567 on 2015-01-21
When I try to play a .mkv file with VLC in lubuntu 14.04 I get this error:
```

 [COLOR=#ff0000]Audio output failed:[/COLOR]

 [COLOR=#000000]The audio device "default" could not be used:[/COLOR]

 [COLOR=#000000]No such file or directory.[/COLOR]


```

is there a way to solve this problem?

---

### Post by ajgreeny on 2015-01-22
Try installing the **linux-image-3.16.0-29-generic** from the repos along with the two **linux-headers** packages of the same version to see if that helps.  You can ignore the **lowlatency** versions for the moment.

What sound hardware do you have? If you're not sure let's see the output of **aplay -l** in terminal.

I am assuming you have already installed** lubuntu-restricted-extras** package to get all the codecs you might need.

---

### Post by flex567 on 2015-01-22
they are both already installed. 

> 
What sound hardware do you have? If you're not sure let's see the output of **aplay -l** in terminal.

It seems I cannot copy paste the terminal's output. So here is the pic.

[IMG]http://i60.tinypic.com/n3x0xu.png[/IMG]

---

### Post by ajgreeny on 2015-01-22
Intel hardware usually presents no problem, so what I see surprises me, if it **really is** a hardware problem.  I suspect codecs or some other software problem rather than just the Intel hardware.

Is it just **.mkv** files that will not play audio or can you get no sound from any other audio or video file-types?

---

### Post by flex567 on 2015-01-22
I get the same error from VLC if I try to play mp3 files

I I try to play it with gnome player, the player plays the file but there is no sound from the speakers.

---

