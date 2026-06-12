---
title: "Hey guys"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by JUDOHAWK on 2008-11-24
I just installed ubuntu tonight lol, first time using linux ever.  Gotta say it's been easier than alot of people make it out to be. I guess you need alil computer know how :/   anyway I was gonna ask a question, Now I didn't need to download any drivers for my video it autodetected and for the most part it's fine, I just can't help but feel that stuff like youtube and whatnot could run alittle better.  Is that something that has to do with needing video drivers?  My computer has onboard video and it's an intel chip, I think the 945G, but I wouldn't know if there are any good drivers for it out there.  

Anyway,  it's not a deal breaker or anything, and I have to admit I'm loving linux so far.

---

### Post by jimreynold2nd on 2008-11-25
The Intel card should have the best driver available installed by default.
Flash is acting weird, because what actually happening behind-the-scene is that Ubuntu uses a wrapper to load the Windows version of Flash (the guys at Adobe don't have true flash binary fo linux yet (correct me if I'm wrong, and I would be delightful to have a compiled native binary flash package). 

But if you have Flash up and running, congrats! I remember struggling with that one for a while. Even so, flash crashes occasionally on my computer, esp. when running 2 flash videos at a time.

My observation is that the less you know about Windows, the easier you are to use Ubuntu.

---

### Post by JUDOHAWK on 2008-11-25
Well I just installed Flash 10 and it's running better now

and I do know quite abit about windows, but Im open minded and don't mind reading up on how to use something.  I just can't believe I havn't tried linux until now, Im really liking it.

---

### Post by Circus-Killer on 2008-11-25
just a side note, please use descriptive topics like "problem with intel gfx card" or something rather than one like "hey guys".

welcome to the free world. ;)

---

### Post by jimreynold2nd on 2008-11-25
Nice to meet you :). I'm used to be a Windows-power-user and that hurts me a lot trying to convert. But now I have been dual booting Ubuntu and openSuSE for nearly 3 months now without any problem.

I haven't tried Flash 10 yet. It's still beta right? I'ma wait till final release :D

---

### Post by JUDOHAWK on 2008-11-25
Oops my bad, sorry XD

---

### Post by JUDOHAWK on 2008-11-25
Right now Im just trying to get to a point where I know what I'm doing here lol

---

### Post by JUDOHAWK on 2008-11-25
Hey JimReynold, that link in your sig was a good read btw.

---

### Post by SuperSonic4 on 2008-11-25
It's also good courtesy to edit your post instead of double or triple posting ;)

How are you getting on anyway?

---

### Post by JUDOHAWK on 2008-11-25
Yea I peruse alot of msg boards so I try to edit posts, just this time it got away from me, sorry.

Anyway, Im getting on fine, better than I thought.  I'm fine with learning as I fly, I figured aslong as I can get ubuntu installed and have a working web browser, if I needed help then I could look it up atleast.  But it's been relatively painless thus far, just need to read directions.  Also another question.  in apps, and add remove, I tried updating the restricted stuff or something, whatever gives you java and mp3 playback all in one and the download speed for that was horrible. Yet when Im using firefox my internet is fast, just a case of slow server?  I do have video and mp3 codecs now by updating the video player though.

---

### Post by nhasian on 2008-11-25
welcome to Ubuntu.  for a great video player try VLC.  if you have a lot of mp3s, you should look at Songbird.

---

### Post by JUDOHAWK on 2008-11-25
I think I'll give VLC a try, I know I've used it on windows before.


Any chance of just running Age of Empires 2 on linux? I've heard of Wine before, I don't play too many games so it's no big deal if I can't play it.

---

### Post by jimreynold2nd on 2008-11-25
Uhhh... never tried. I tried Freelancer and Starcraft broodwar on my computer and it runs great tho. Try the WineHQ appDB ([http://appdb.winehq.org/](http://appdb.winehq.org/)) to see if one particular program is compatible or not.

About mp3s and proprietary stuffs, try adding the Medibuntu repo: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
and then do ```
sudo apt-get install libdvdcss2 w32codecs
```
(replace w32codecs with w64codecs if you are runnung 64bit version)

to make everything a one-liner (on hardy 32bit, for intrepid replace "hardy" with "intrepid", for 64bit use "w64codecs"):
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list && sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update && sudo apt-get install libdvdcss2 w32codecs
```

---

### Post by JUDOHAWK on 2008-11-25
I don't even see it listed :/  I guess I can try it tomorrow or something, it's getting late lol.

Actually I searched for it and it appears to run fine, but like I said, ill work on that tomorrow or something.

Well fine is an overstatement, it doesn't appear to run that well.

---

### Post by vwvr9 on 2008-11-25
welcome to Linux

---

### Post by jimreynold2nd on 2008-11-25
> **JUDOHAWK said:**
> Well fine is an overstatement, it doesn't appear to run that well.

Lol too bad then

---

