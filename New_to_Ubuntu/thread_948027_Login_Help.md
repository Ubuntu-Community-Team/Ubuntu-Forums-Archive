---
title: "Login Help?"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by Blackdragon1400 on 2008-10-14
I'm trying to think of a way to use a .wav or .mp3 from a text to voice program that i can use to play when I log on to Ubuntu. Something like a "Hello ____" would be really cool. I know how to add the sound file to play on start up, but does anyone know of a text to voice program (that will record what you type into it to an .mp3 or .wav) that is free (or attainable) and that doesn't sound "out of place"?

---

### Post by phidia on 2008-10-14
Try [Festival]("https://help.ubuntu.com/community/TextToSpeech"). The link is to the Ubuntu wiki on that application.

---

### Post by pdub on 2008-10-14
open a terminal and type:

```
espeak "Hello There" -w hello.wav
```

If espeak is not installed then:

```
supo apt-get install espeak
```

---

### Post by Blackdragon1400 on 2008-10-14
yes, but is there a way for Festival to let me record what the tts actually says?

---

### Post by Blackdragon1400 on 2008-10-14
ok, so apparently i dont know where you go to change the sound file that is used when you log on. I assume that it is not the "log in screen ready" one in the Login Preference window?

My bad...

---

### Post by Blackdragon1400 on 2008-10-14
ok, i apologize...next time i will take more than 2 seconds to look for somthing befroe asking. Thanks for the help with the tts though, i got it working just like i wanted to.

Thanks!

---

