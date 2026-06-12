---
title: "Gyachi, incompatible webcams?"
date: 2008-06-10
forum: Philippine Team
---

### Post by halln on 2008-06-10
Any news with Gyachi may bagong package ba tayo dyan still I can't make my webcam to work. Thanks boss.[-o<

---

### Post by Nhatz on 2008-06-10
Gumagana nman yung webcam ko sa dating gyachi sakin. hehehe:)
ASTIG!

---

### Post by halln on 2008-06-10
swerte k pre, dalawa n webcam ko ayaw tlagang gumana s gyachi, k nman s kopete and ekiga.

---

### Post by loell on 2008-06-10
wtf? 

**Gyachi 4 Loell**?  :lolflag:

baka tumaas ang kilay ni developer pag-nakita nya ito ,akalain nya nag-kunkunwari akong developer nang kanyang project :lol: este nung kanilang project pala. :lol:

sorry, i'll be editing the title :popcorn:

---

### Post by loell on 2008-06-10
try to install this already compiled flashcam

[ATTACH]73540[/ATTACH]

you know, by doing..
```
sudo make install
```

assuming that the webcams involve are v4l2 webcams.

---

### Post by halln on 2008-06-12
> **loell said:**
> try to install this already compiled flashcam

[ATTACH]73540[/ATTACH]

you know, by doing..
```
sudo make install
```

assuming that the webcams involve are v4l2 webcams.

Thanks 4 the package, installed it and walaa! my v4l2 (cheap webcam) works,
but not yet.. after closing and opening gyachi the second time my cam refusing to work again with this screenshot:

---

### Post by loell on 2008-06-12
can you try this script? its for loading the driver..

[http://ubuntuforums.org/showthread.php?t=798149&highlight=gyachi+script&page=2]("http://http://ubuntuforums.org/showthread.php?t=798149&highlight=gyachi+script&page=2")

---

### Post by halln on 2008-06-12
could you send me that link again coz I can't open it, but if this is what you meant:

sudo flashcam -L
Scanning devices
------
Found V4L2 Capture device: /dev/video0 (sn9c102/SN9C1xx PC Camera)
------
Executing: 'modprobe vloopback pipes=1'
~$ flashcam -qD
Forwarding frames from /dev/video0 to /dev/video2
-desktop:~$ Unsupported format.
-desktop:~$ flashcamwrap gyachi


What I'm thinking is if It is possible to uninstall gyachi totally including all the remnants and reinstall it cleanly again. I might did something wrong with it and I want it to start over again. Is there a code to do it without reinstalling the OS? Tnx in advance.

---

### Post by loell on 2008-06-12
you can uninstall it via **synaptic**

or through APT's command line

```
sudo apt-get remove gyachi
```

my bad, the previous link was malformed, its OK now.

---

### Post by halln on 2008-06-14
still can't open your link.

---

### Post by loell on 2008-06-14
this one? just follow the discussion,
[http://ubuntuforums.org/showthread.php?t=798149]("http//ubuntuforums.org/showthread.php?t=798149&highlight=gyachi+script&page=2")


or try this script directly 

[ATTACH]74014[/ATTACH]

---

### Post by Script Warlock on 2008-06-14
bro try mo kaya to 
sudo modprobe -r gspca
sudo modprobe -r xxxxxx(mine is zc0301 thru lsusb)
sudo modprobe -r v4l1_compat
sudo modprobe gspca

ok to sa akin kc palipat-lipat ang webcam ko sa mga workstation sa cafe  namin...

---

### Post by halln on 2008-06-14
Mga bossing, Thnx for the help but everything working fine now. I bought a new webcam,again.. and it's Logitec Quickcam messenger and It just work out of the box. It work in kopete, skype, Gyachi and Ekiga. Thnx for Loel with all his might trying to make my webcam work in gyachi (A! mura mag speech). Anyway, I highly recommend this webcam to anybody.:guitar:

---

### Post by loell on 2008-06-14
heheh,  tatlo na pala webcam mo ngayon :D

---

### Post by halln on 2008-06-15
tatlo n nga tnapon ko n yung isa. I still don't know if voice chat is working with this new cam (with built in mic) coz the last time I use it they couldn't hear me. Is there a way to check if voice is working in gyachi just like in yahoo msgr? I already installed medibuntu repo.

---

### Post by halln on 2008-06-17
voice chat still not working, any how to?

---

### Post by wersdaluv on 2008-06-17
For voice chat, use skype :D

If you don't want to install, we have [http://www.mebeam.com](http://www.mebeam.com) :D

---

### Post by halln on 2008-06-17
kamag-anak ko dyn s pinas dial up lng, k b ang skype with dial up connection?

---

### Post by Samhain13 on 2008-06-18
^May oras na choppy, pero "usable" naman kahit sa dial-up.

---

### Post by loell on 2008-06-18
is your webcam mic now working? there seem to be no all in one solution with that problem.

---

### Post by halln on 2008-06-19
> **loell said:**
> is your webcam mic now working? there seem to be no all in one solution with that problem.

My friends still couldn't hear me even inside private chat rooms. Clicked the green button but still mic isn't working but at least skype is.

---

