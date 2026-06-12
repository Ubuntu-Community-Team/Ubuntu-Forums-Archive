---
title: "Sound and mic problems"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by jakupl on 2008-10-03
I have some very annoying problems. Pretty much as "Troll_the_Great" had [here]("http://ubuntuforums.org/showthread.php?t=881920").
My volume bar does not work. [This is what it does]("http://www.youtube.com/watch?v=lYRLYI0tbLI").

Also when I go to sound recorder, I get.

"Your audio capture settings are invalid. Please correct them in the Multimedia settings."

And when I try alsamixer, I get

```
jakup@bobby:~$ alsamixer

alsamixer: function snd_mixer_load failed: No such file or directory
```

I am open for suggestions. Any help would be appreciated.

---

### Post by Pro-reason on 2008-10-03
Maybe have a look at [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by jakupl on 2008-10-03
> **Pro-reason said:**
> Maybe have a look at [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

I have had this problem before I reinstalled ubuntu. I followed that guide back then, and it solved my volume button problem, but it killed my skype. so I really don't want to use pulseaudio.

---

### Post by markbuntu on 2008-10-03
I have just figured out how to get skype working with pulseaudio. I have put a SKYPE section in my guide, just scroll down until you see the skype section. I saw all these people having so may problems with skype and pulseaudio so I had to check it out. So I did, and found the solution. Tested and confirmed by me on my 2 sound cards, usb headset and usb webcam.

I have a similar volume control issue with my usb headset and I could only fix it with pulseaudio. So look in my guide, and consider your other options.

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by jakupl on 2008-10-03
> **markbuntu said:**
> I have just figured out how to get skype working with pulseaudio. I have put a SKYPE section in my guide, just scroll down until you see the skype section. I saw all these people having so may problems with skype and pulseaudio so I had to check it out. So I did, and found the solution. Tested and confirmed by me on my 2 sound cards, usb headset and usb webcam.

I have a similar volume control issue with my usb headset and I could only fix it with pulseaudio. So look in my guide, and consider your other options.

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

Thankyou very much. I will try/test this on an other installation "on the same computer, with the same problems" when I sober up. Cheers. hic!

---

