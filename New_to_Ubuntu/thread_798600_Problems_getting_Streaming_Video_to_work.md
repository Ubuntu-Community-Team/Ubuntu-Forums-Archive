---
title: "Problems getting Streaming Video to work"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by adamgram on 2008-05-18
I am completely new to all this, and trying to set up my laptop (IBM T40) with Ubuntu.  I downloaded 8.4 and installed from the CD, then upgraded to Ubuntu Studio.  I'm not sure if that makes me an 8.4 with all the studio software or if I'm now using 7.10.  

The immediate problem I'm having, though, is with streaming video on the internet.  At first no videos would play, so I read what I could find on the Ubuntu website and downloaded the restricted updates and 'medibuntu' following the instructions I found here 
[https://help.ubuntu.com/community/RestrictedFormats/StreamingVideo](https://help.ubuntu.com/community/RestrictedFormats/StreamingVideo)

Now some videos play fine, others have one or two "0"s in the middle of the screen and I can't operate the video controls, and others won't play at all.  Is there some other plugin I need?  Is it a firefox setting of some sort?  

Thanks in advance.

---

### Post by Happy_Man on 2008-05-18
Hm... do flash videos (eg YouTube) play fine? If so, then I guess you're trying to play a Windows Media stream or something similar. Try installing Vlc media player ```
sudo apt-get install vlc
``` It will install a Firefox plugin that pretty much plays anything.

---

### Post by adamgram on 2008-05-18
Thanks for helping!  Some internet videos will play and some will not.  Youtube videos on the youtube website work fine, but a youtube video posted as a bulletin on myspace is just a blank screen (works fine from other computers).  Theonion.com videos will not play and there are 2 "0"'s in the video screen.  

I downloaded VLC and got the same results.  I also have MPlayer and Movie player on here for watching videos, all of which work fine.

---

### Post by Happy_Man on 2008-05-18
The Onion's videos play fine for me, and they are flash videos, so I'm not sure why they won't play for you. I would assume YouTube's videos, whether they are on Myspace or not, will play. Are you using NoScript or something similar to block flash?

---

### Post by adamgram on 2008-05-18
Not that I'm aware of.  How would I check?  Flash videos work on some websites, but not others.

---

### Post by CJ_Hudson on 2008-05-18
Some media/video streams/downloads require a codex which Microsoft may have put a patent/copyright control on.

---

### Post by adamgram on 2008-05-19
SOLVED:  I followed the instructions here
[http://ubuntuforums.org/showthread.php?t=661833&highlight=streaming](http://ubuntuforums.org/showthread.php?t=661833&highlight=streaming)
and it fixed everything

---

