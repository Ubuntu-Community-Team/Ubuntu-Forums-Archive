---
title: "[SOLVED] Ubuntu wont find DVD"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by Alnird on 2008-08-03
Hi all!

First of all, I searched the forum for a solution, but I couldn't understand what the frick they where getting at, so I'm making my own thread, sorry..

My problem today is that I want to ripp some of my DVDs into VIDEO-TS/AUDIO-TS folders. But when I inserted the DVD into my drive, it didn't do anything. I tried with 3 different DVDS, tried opening it from file browser, VLC and Totem, but it wouldn't admit that I had placed a DVD in the drive, nothing.

So if someone could come up with an easy or at least understanable solution to this minor setback I would be really glad =)

Thanks in advance, Alnird

---

### Post by northern lights on 2008-08-03
[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by jamesrfla on 2008-08-03
Make sure you have a DVD writer first.

---

### Post by northern lights on 2008-08-03
> **jamesrfla said:**
> Make sure you have a DVD writer first.
And exactly why would a writer be necessary for ripping?

---

### Post by Alnird on 2008-08-03
I did everything I could find, I checked under "Play DVDs" and executed the commands, but it's still the same problem.

---

### Post by northern lights on 2008-08-03
I am assuming you're on i386 Hardy. If that's not the case, do not follow the upcoming instructions.

If you don't know what your on, run ```
lsb_release -a

```to verify.

Navigate to "System > Administration > Software Sources". Enable all repositories but 'proposed' and 'backports'.

Then run ```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```
Update (synchronize index files w/ sources), install public keyring, update again```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```Install the library necessary for DVD playback```
sudo apt-get install libdvdcss2
```Install a player and a ripper```
sudo apt-get install vlc dvdrip
```

As an aside you might also like wma/wmv support, which is now possible with medibuntu enabled```
sudo apt-get install w32codecs
```

Hit Alt+F2 > type "dvdrip" > hit Enter > rip away

---

### Post by Alnird on 2008-08-04
I think that I did everything except the last two steps, but I already have VLC installed (bot not dvdrip as far as I know).

Thanks a lot for sorting it out, I'm done with the codes but when I'm going to choose my DVD unit it wont give me a list to choose from. I press the listbutton, but it just marks it and nothing more. It's like my computer wont acknowledge the DVD :confused:

I tried putting in a CD to see if it reacted, but it didn't! Like it's not hoocked up or something.. I'll just shut down my computer to check it..

---

### Post by jamesrfla on 2008-08-04
> **northern lights said:**
> And exactly why would a writer be necessary for ripping?

Sorry I wasn't paying attention to the question.

---

### Post by Alnird on 2008-08-04
I think I just found the problem.. I had a plug in the DVD så it was set as master. I removed it, turning it into slave and voiala, everything works like a charm.. Sometimes I get amazed at myself, I mean I really should have figuered this out.

Thanks for all the help, and I say it again couse it can't be said enough, I love you guys =)

---

### Post by northern lights on 2008-08-04
> **Alnird said:**
> Sometimes I get amazed at myself, I mean I really should have figuered this out.
Mostly, you miss the simple and "that-was-soooo-obvious" kind of things...

---

