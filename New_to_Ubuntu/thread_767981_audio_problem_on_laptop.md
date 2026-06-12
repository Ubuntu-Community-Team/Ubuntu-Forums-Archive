---
title: "audio problem on laptop"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by nirakarsethy on 2008-04-26
My audio icon showes that its workiing fine. I used totem player in Ubuntu with a .spx file. Its playing and the vizualization is also working but the sound is not coming.

PLease help
nirakar sethy

---

### Post by Dr.Gringo on 2008-04-26
Post the Output of lspci in Terminal

I myself need some help With my Alienware laptop this is my output:

```
Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
```

EDIT: [This]("http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/#comment-234") doesn't seem to be working with Hardy Heron anymore!!!

---

### Post by Dr.Gringo on 2008-04-26
It's incredible that my alienware m15x has everything working except the audio. Actually it has been the same problem for all the laptops i have installed ubuntu in; I should be an expert in this.

EDIT: HELP; This is the only thing that is keeping Ubuntu from being a great OS!!!

---

### Post by Dr.Gringo on 2008-04-26
Someone please terminate my misery and Help me with the audio!!!

---

### Post by bcnaat on 2008-04-26
Try going installing gstreamer. It 'fixed' my sound out of the blue. I went to youtube to see if the videos would play, it said I needed some codecs and when it searched it found two gstreamer files and I installed them. I have sound now?

---

### Post by gavinjb on 2008-04-26
Just found this thread that might help you

[http://ubuntuforums.org/showthread.php?t=767094&highlight=sound](http://ubuntuforums.org/showthread.php?t=767094&highlight=sound)

only problem is I have the 

```
Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
```

and there is no similar entry for my card (when I goto System / Prefs/ Sound, there are no devices listed).

---

### Post by nirakarsethy on 2008-04-26
But in XP its having Realtek audio driver. How do I know that its Intel's

---

### Post by Dr.Gringo on 2008-04-26
Thanks guys but none of those options worked for me...

---

### Post by gavinjb on 2008-04-26
I have managed to get one step closer, if you follow the steps in this link

[http://ubuntuforums.org/showthread.php?t=762349&highlight=dell+inspiron+1525](http://ubuntuforums.org/showthread.php?t=762349&highlight=dell+inspiron+1525)

If you have an hsfmodem run sudo depmon -a and sudo update-initramfs -u after removing the modem and renaming the file.

Only problem is I now get the following error when I goto System/Prefs/Sound and click to test sound.

```

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Failed to connect stream: Invalid argument

```

---

### Post by Dr.Gringo on 2008-04-26
Thanks gavinjb, but i believe that specifies in the rev 02 and most likely would not apply to my card all possible solutions i have found from lurking do not work with Hardy Heron for a reason or other.

---

