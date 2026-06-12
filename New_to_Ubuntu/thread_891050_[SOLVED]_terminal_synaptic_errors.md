---
title: "[SOLVED] terminal synaptic errors"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by intimatewipe on 2008-08-15
Hello peeps,was trying to download the various codecs etc following the multimedia tutorials,all was well till I got to part 2/5 audio video streaming,when i tried to execute the command "sudo apt-get remove kaffeine-mozilla mozilla-helix-player mozilla-mplayer mozilla-plugin-vlc totem-mozilla xine-plugin" and "sudo apt-get install gnome-mplayer gecko-mediaplayer " I got the following errors in the terminal and then in the synaptic package manager when I tried to use that,I am a relative newbie so please be as clear as possible,this is a fresh install of hardy(putting it on 3 pcs and hopefully my  laptop next),need the codecs/players and acess to synaptic,:confused:
thanks for any input

---

### Post by intimatewipe on 2008-08-15
forgot to say,Both synaptic and terminal give me this error,

---

### Post by dje on 2008-08-15
do what it says, in the terminal run:
```
sudo dpkg --configure -a
```
please search before posting, there are many threads on this topic ;)

dje

---

### Post by intimatewipe on 2008-08-15
sorry dje,seems obvious now you pointed it out,I'm not the sharpest tool in the box,:(

I'll try that mate ,

---

### Post by dje on 2008-08-15
> **intimatewipe said:**
> sorry dje,seems obvious now you pointed it out,I'm not the sharpest tool in the box,:(

I'll try that mate ,

don't apologise !! :D it doesn't actually tell to run it as root so you would have been stuck running it without the sudo ;)
Please mark the thread as solved (Thread tools (top right) >> Mark thread as solved)

dje

---

### Post by nickgaydos on 2008-08-15
Yep, running the command in Sudo. I made a mistake of not running it in sudo and it gave me an error :P

---

### Post by t0p on 2008-08-15
> **dje said:**
> it doesn't actually tell to run it as root so you would have been stuck running it without the sudo


This is actually quite a big issue.  I often see posts on this, so it's something that effects a lot of users.  So why oh why doesn't apt-get *tell* us to run ```
sudo dpkg --configure -a
```

The developers should take heed.  (Any developers here?  Take heed!! ;))

---

### Post by intimatewipe on 2008-08-15
Because I don't know what I'm doing  dje It makes me nervous,years of having windows vomit a blue screen at me every time I got cheeky has left me very cautious:(
I resolved that by using hyperos which makes installs quicker than I can break them(you need at least 6 xps/vistas to equal one decent OS)

---

