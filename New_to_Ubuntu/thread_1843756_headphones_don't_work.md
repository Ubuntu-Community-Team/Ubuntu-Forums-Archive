---
title: "headphones don't work"
date: 2011-09-14
forum: New to Ubuntu
---

### Post by arabookworm on 2011-09-14
to start off I just need to let you all know that I am basically computer illiterate. This whole Ubuntu thing is me trying to keep my 7 year old brother out of my computer. He's already figured out how to get onto windows, even password protected (I have no idea, there's no way he figured out my password) and has figured out how to disable parental controls. He then proceeds to destroy computers with viruses by clicking on anything that looks interesting, usually involving pokemon. So this is basically a move made out of desperation. Use small words please? kthx. 

Whenever I play something, the speakers work, but if I put in headphones they either make no sound, or the headphones work but the speakers continue playing. I trying fiddling with the sound options, but nothing really changes that.

remember: small words

---

### Post by psrdotcom on 2011-09-14
This might be a problem with your audio drivers .. Please try to find the proper audio driver and install it .. :)

---

### Post by arabookworm on 2011-09-14
um, could you explain drivers a bit please? I'm *really* computer illiterate, but I'm sort of at the end of my rope.

---

### Post by Denver Dave on 2011-09-14
Do you have sound with speakers instead of headphones?

I'm chasing a similar issue with no sound, at least not with flash, not sure about other sound - I have speakers.   Running DVD trial.

---

### Post by dfarrell07 on 2011-09-14
What method are you using to check if you have sound? For example, are you playing a YouTube video or some song from you computer? If a YouTube video, the error might be that you don't have Flash installed correctly. But, we will leave that for now.

Under Sound Preferences -> Hardware (tab), try picking another device, like some HD Audio Controller vs Internal Audo, or the other way around. Each time you make a change, try clicking the 'test speakers' button on the same page. Also on the Hardware tab, try picking different profiles from the drop-down list and clicking 'test speakers.' 

Obviously make sure your sound is turned up, which you can see by the slider on the Sound Preferences window.  

The next thing I would check is the Output tab of Sound Preferences. Try choosing another sound device, if you have one, and testing your speakers.

In my experience, the error is normally one of those things. Perhaps someone else has other ideas.

---

### Post by dfarrell07 on 2011-09-14
> **Denver Dave said:**
> I'm chasing a similar issue with no sound, at least not with flash, not sure about other sound - I have speakers.   Running DVD trial.

Go to the Ubuntu Software Center (using the bar on the left, or the windows-key search feature), and search for 'Adobe Flash Plugin.' Install that, and flash should work well. You may need to restart your browser or computer, not sure. 

@ the original poster - if you are playing videos to check the sound, you could try this fix as well.

---

### Post by jtarin on 2011-09-14
Try Alasamixer. At the commandline (Terminal)type ```
alsamixer
```

```
alsamixer recognizes the following keyboard commands.
General Controls

The Left and right arrow keys are used to select the channel (or

device, depending on your preferred terminology). You can also use 'n'

("next") and 'p' ("previous").

The Up and Down Arrows control the volume for the currently selected

device. You can also use '+' or '-' for the same purpose. Both the left and

right signals are affected. For independent left and right control, see

below.

The 'B' or '=' key adjusts the balance of volumes on left and right chan-

nels.

'M' toggles muting for the current channel (both left and right). You can

mute left and right independently by using ',' (or '<') and '.' (or '>')

respectively.

SPACE toggles recording: the current channel will be added or removed

from the sources used for recording. This only works for valid input

channels, of course. You can toggle left and right independently by

using Insert (or ';') and Delete (or ') respectively.

'L' re-draws the screen.

Quick Volume Changes

Page Up increases volume by 5.

Page Down decreases volume by 5.

End sets volume to 0.

You can also control left & right levels for the current channel inde-

pendently, as follows:

[Q | W | E ] -- turn UP [ left | both | right ]

[Z | X | C ] -- turn DOWN [ left | both | right ]

If the currently selected mixer channel is not a stereo channel, then

all UP keys will work like 'W', and all DOWN keys will work like 'X'.

Exiting

Quit the program with ALT-Q, or by hitting ESC. Please note that you

might need to hit ESC twice on some terminals since it's regarded as a

prefix key
```

---

### Post by arabookworm on 2011-09-14
I tried to do what a previous poster suggested with alsamixer but there's nothing to control whether the sound comes from the speakers or the headphones. the headphones are working for the most part, but the speakers on the computer are still going even when headphones are in.

---

### Post by jtarin on 2011-09-14
Can you plug your headphones into an alternate location on you computer?

---

### Post by lidex on 2011-09-21
> **arabookworm said:**
> to start off I just need to let you all know that I am basically computer illiterate. This whole Ubuntu thing is me trying to keep my 7 year old brother out of my computer. He's already figured out how to get onto windows, even password protected (I have no idea, there's no way he figured out my password) and has figured out how to disable parental controls. He then proceeds to destroy computers with viruses by clicking on anything that looks interesting, usually involving pokemon. So this is basically a move made out of desperation. Use small words please? kthx. 

Whenever I play something, the speakers work, but if I put in headphones they either make no sound, or the headphones work but the speakers continue playing. I trying fiddling with the sound options, but nothing really changes that.

remember: small words
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

