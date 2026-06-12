---
title: "Oh nuts! Not again."
date: 2008-08-18
forum: New to Ubuntu
---

### Post by ChocolateChip_Wookie on 2008-08-18
Hi all,

I've had this laptop working for a couple of weeks. I had sound (I swear) but now, I have nothing. My speakers do not appear to be working anymore and Skype reports that there is an 'error' with the input device when making a test call although neglects to specify what the error might be. The speakers were on mute because random sounds from the operating system annoy me, but when I tried to view a video on youtube, I cannot hear it. Can anyone help diagnose? Yes, the speakers are 'on', no, it isnt on mute. I have tried a test but nothing. Can anyone help? I'm not sure where to start with this one.

Thanks in advance

Spec : Sony Vaio SZ4
Linux Mint 5 (Ubuntu Hardy Heron)

---

### Post by boblemur on 2008-08-18
you should try, and see if any of the sound drivers work in

system > prefrences > sound

try first alsa and click test, then you can try the others, if none of them work... there is a sound trouble shoot here:

[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)

good luck :) 

ohh and also, try and pick better names for ur posts eg (No Sound on Sony Vaio) you will get better and faster help, and people who may have had ur problem before will overlook Oh nuts! Not again. but if they see something they have had to fix in the past they will come and help :) just some advice if you want to avoid 0 posts

---

### Post by nhasian on 2008-08-18
if you log out, then log back in, does the sound start working again?  my sound occasionally cuts out too.  it has something to do with the flash plugin (youtube)

---

### Post by ChocolateChip_Wookie on 2008-08-20
> **boblemur said:**
> you should try, and see if any of the sound drivers work in

system > prefrences > sound

try first alsa and click test, then you can try the others, if none of them work... there is a sound trouble shoot here:

[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)

good luck :) 



I did the first thing on the link and hey presto! Something had become muted? Argh.

I cannot understand what because the little 'speaker' icon insisted that everything is fine, but hey ho. ALSAMIXER found the problem.

Thanks very much. Bookmarked for future reference.

---

