---
title: "Sound problems on my laptop"
date: 2012-07-22
forum: New to Ubuntu
---

### Post by bottaw on 2012-07-22
Hi there, I am fairly new to ubuntu 12.04, and I have recently begun to get sound problems from my speakers. I use google chrome as an internet browser, and every once in a while the sound from videos or music will all of a sudden become fuzzy and crackly, affecting all of the tabs and any new tabs I open up. The only way I have found that fixes it is by closing chrome and reopening it. However, sometimes it will affect the entire computer as well, making me have to restart in order to get sound quality back. I don't know if it is the operating system or the speakers, but I never had this sort of problem when I was using windows on it. Its becoming an ever increasing hassle. Is there anything I can do?

---

### Post by jmfal on 2012-07-22
Welcome to  Ubuntu Forums

Try installing  ubuntu-restricted-extras, it's in the sofrware center, synaptic or usig the terminal:
```
 sudo apt-get install ubuntu-restricted-extras
```

Also if you can try another player in the browser.

---

### Post by bottaw on 2012-07-22
I'm afraid that didn't fix the problem. Its not a specific player in the browser, its the entire browser. Flash games, video streaming, all are affected, and the sound of other programs as well sometimes.

---

### Post by NikTh on 2012-07-22
> **bottaw said:**
> I'm afraid that didn't fix the problem. Its not a specific player in the browser, its the entire browser. Flash games, video streaming, all are affected, and the sound of other programs as well sometimes.

Hi , 
is this a problem with a specific browser ? did you try with another browser ? 

Thanks

---

### Post by bottaw on 2012-07-22
I did not, but its happened to the computer itself without the browser being activated. It just seems to happen more often with the browser loaded.

---

### Post by NikTh on 2012-07-23
> **bottaw said:**
>  I use google chrome as an internet browser, and every once in a while the sound from videos or music will all of a sudden become fuzzy and crackly, affecting all of the tabs and any new tabs I open up. The only way I have found that fixes it is by closing chrome and reopening it. However, sometimes it will affect the entire computer as well, making me have to restart in order to get sound quality back. I don't know if it is the operating system or the speakers, but I never had this sort of problem when I was using windows on it. Its becoming an ever increasing hassle. Is there anything I can do?

Hi , 

I believe is Google Chrome which affects entire system . Nor Ubuntu or your speakers. 

Try to use another browser (e.g Firefox) to see whether the conclusions are.

THanks.

---

### Post by upsla on 2012-07-23
> **bottaw said:**
> I did not, but its happened to the computer itself without the browser being activated. It just seems to happen more often with the browser loaded.
As NikTH suggested please install some other browser and check for problems.

---

### Post by bottaw on 2012-07-23
Its happened when I use puzzle pirates though, which runs on it's own without a browser. Maybe its just when I connect to the internet? Because it doesn't happen when I watch dvds. Trying with mozilla now though. In case it is chrome, is there anything I can do?

---

### Post by jmfal on 2012-07-23
Open alsamixer and decrease the pcm control if there is one

---

### Post by bottaw on 2012-08-28
Ok, I tried it, but now it is doing it with Mozilla Firefox, and the alsamixer didn't help.

---

