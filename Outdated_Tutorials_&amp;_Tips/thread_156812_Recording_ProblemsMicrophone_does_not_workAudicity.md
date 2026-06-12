---
title: "Recording Problems/Microphone does not work/Audicity recording failiure"
date: 2006-04-07
forum: Outdated Tutorials &amp; Tips
---

### Post by SkimWear on 2006-04-07
Not really a HOW-TO. but more of a HOW-I-FREAKING-SOLVED-THE-PROBLEM-AFTER-COUNTLESS-HOURS-AND-BASICALLY-ON-TRIAL-AND-ERROR.

ill just post what I did and check if it works for anyone that is having these same issues as well. afterall, the reason i write this is because when i searched under microphone not working, audicity microphone problems, and recording failiure, i got so many hits and all unawnsered questions.

FYI: my PC has an internal sound card and SB Live! 5.1 card which I use for music recording and teamspeak and skype.

here goes:
1. Make sure you have all your soundcard drivers installed and working. That means first have sound before attempting on recording.
2. hopefully by now you have heard of ALSA, OSS and ESD.
3. open up the wonderful alsamixer in terminal.
4. if you have multiple soundcards (like me), the command to open/use the card would be alsamixer -c 1 << (0 opens your default, 1 is your secondary, and so forth...)
5. PRESS f4. to switch to recording view.
6. make sure under MIC or LINE (whichever input you are using to record) MM is not showing. IF you see MM under the input you are recording from, highlight the input and press 'm' on your keyboard. that switches it from MUTE to ON.
7. Move the slider up.
8. Open up Volume Control. this can be done numerous of ways, my personal fave: dbl click on the speaker icon on your taskbar.
9. make sure on FILE>>change device its set to the right device.
10. click edit>>>preferences. and enable all the preferences you might think are important. ie: line-in, microphone, capture, aux.
11. In case its STILL muted, unmute the microphone and the line input jack, then make sure whichever input you are using is selected. by that i mean click the little microphone icon next to the mute button.
12. might want to run terminal and 'killall esd' it works for some people
13. if it didnt work dont worry, just run the command 'esd' and everything is peachy
14. open up audicity...click file>>>preferences. make sure where the recording is set to matches to what card/device you are using. I have two, so i chose the second one :) my SB LIVE.
15. make sure on output its the same. if you want to output from there too.
16. attempt to make recordings.

personal notes: as for skype and ts2. most likely the killall esd thing works without you having to reboot your pc everytime you want to use it.
this is mainly for those who wish to use their sound card for productive things, or just to eat crap with sound recorder.

btw: havent gotten soundrec to work yet. just audacity. its working great.

---

### Post by ax-ax on 2007-10-20
I love you :)

---

### Post by akwatve on 2008-01-27
I tried as per your suggestion.......But I cannot record anything... :-(
When I used arecord -f cd test.wav, all I get is a 44 byte test.wav file which contains nothing. Alsa is really pathetic when it comes to recording. I even tried OSS4. It was able to record sound but unfortunately it wasnt playing anything

---

