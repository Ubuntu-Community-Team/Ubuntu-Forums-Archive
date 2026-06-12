---
title: "Linux Scripts, Audio Playback, Shell Tabs"
date: 2011-02-26
forum: Programming Talk
---

### Post by jmg158 on 2011-02-26
Okay, so, as you can probably tell, this is my first foray into this field, so if I stumble into ignorance, please correct me.

I was just reading about scripting in linux and I had a few questions. As a first serious attempt at writing something I was hoping to write a program that could play an audio file, and then play another audio file over top (like sampling for example) of the first and so on and so forth.

1) I know many command prompt environments can have a multi-tab interface. I was planning on using Sox to play my clips, however this occupies the tab while it is open, so I would need to play it in a side tab to allow further function (ie... playing over top.) Is there a way to say "execute this command in a different tab and then return to this one?"

2) Would anyone experienced with this recommend linux for something like this? I wanted to give it a go as an introduction into intermediate use of the language but I can't honestly say I've played audio using C++ or any other language. 

Again, I'm just toying with ideas at this point so I'm not terribly attached to any of these ideas. Any input would be appreciated.

---

### Post by CaptainMark on 2011-02-27
Bash scripting is the most basic place to start in ubuntu because the terminal is a bash shell and a script will just let you automatically run a series of commands. What your trying to do, do you already know how to do it in a terminal? Remember that programs designed to be used with a gui do not always let you control them fully from a terminal.

Edit: just had a look at sox, i see its terminal based, cool,. if you already know the terminal commands for what you want to do just write a text file ```
#!/bin/bash

command1
command2
command3
etc.
```
make this executable and it will run one command after the next, these will run only one after the other though, ive never really done more than the basics in bash myself, perhaps someone will help by telling us if you can run two commands simultaneously because id like to know too

---

### Post by jmg158 on 2011-02-28
yes, I know the basic functionality from the command prompt and listing them like that does not enable playing more than one song at the same time. I'm wondering now whether using & can allow it to run in the bg or something. 

That may be an idea but I'd really appreciate some more experienced input than my own.

---

### Post by CaptainMark on 2011-03-02
okay i dont a bit of googling, you just add an ampersand (&) to the end of a line and it will run and return immediately, to test i ran ```
#!/bin/bash

aplay desktoplogin.wav
aplay email.wav
```Plays desktoplogin.wav (which is quite slow and long) and when its done plays email.wav which is short and loud. However running ```
#!/bin/bash

aplay desktoplogin.wav &
aplay email.wav
```Plays them at the same time and email.wav finishes waaay before desktoplogin.wav does, so it definately works

Bish bash bosh!

---

### Post by jmg158 on 2011-03-03
I can't test it yet but taking your word for it... that sounds fantastic. 

I'm thrown by 'aplay' though. I'm not familiar with it really, but hopefully it won't be difficult to iron out compatibility or anything like that. It isn't exclusively for wav's is it?

Anyway that's interesting. I found out the other day that you can pipeline them in (play "this.mp3" | play "that.mp3") and it will play them simultaneously, but then I couldn't imagine how to write in any interesting features like muting or volume or deciding to repeat.

I mean, I'm still not positive but I don't see nearly as many issues.

Thanks a bunch!

---

### Post by CaptainMark on 2011-03-03
The pipe command is used to pass results from one command to the next, its more useful for if you wanted to for example find all .wav files and pass them to a sound converter to turn them into .mp3 or something, ive never used it much with media playing honestly more file managing.

aplay is more a sound-bite sampler than a media player, i only use it to play desktop sounds and yes as far as im aware it only uses .wav

---

