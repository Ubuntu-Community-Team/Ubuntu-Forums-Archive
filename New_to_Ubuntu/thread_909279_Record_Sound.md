---
title: "Record Sound"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by mackattack22 on 2008-09-03
Hello everyone,
      I have an HP Pavilion dv6700 which comes with microphones built in at the top of the screen. I am dual booting Ubuntu 8.04 and Win xp. Here is my problem:
   
I want to use the microphones to record lectures in school, but I am either not using the sound recorder properly, or it is not working. Is there some way I can use the built in microphones to record? 

I know to solve the problem you will probably need to know what soundcard(driver?) I am using, but I don't know how to find that either. 

If you can't tell by now, I am a TOTAL noob, so any info or directions would have to be extremely dumbed down. 
                              
Thanks, 
                              Mack

---

### Post by nothingspecial on 2008-09-06
Well, I don`t know how to fix your mic (I haven`t got one) but you can find your soundcard by typing,

```
lspci -v
```

Look in the output for something that says audio controller and use your favourite search engine if no one can help here.

---

### Post by pyromanic123boom on 2008-09-06
Use audacity, or just plain old sound recorder. To find out which microphone it is, open a terminal and open alsamixer

alsamixer

Then move to the right/left with the keys, and find which is your monitor microphone. It might say things like front panel, back, etc, or screen mic, something along those lines.

Just find out which one it is, and try recording with it using one of the sound recrders I mentioned.

---

