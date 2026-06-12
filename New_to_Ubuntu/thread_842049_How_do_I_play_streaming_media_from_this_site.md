---
title: "How do I play streaming media from this site?"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by crjackson on 2008-06-27
I installed Ubuntu on a friends machine and now all I'm getting is complaints that he can't play the streaming media from this site [Fox 99.7]("http://www.wrfx.com/main.html")

So I tried on my systems and I can't play it either.  What needs to be installed so that this will work?

---

### Post by Xiong Chiamiov on 2008-06-27
Just to make sure, do you have all of the codecs installed mentioned in [this thread]("http://ubuntuforums.org/showthread.php?t=766683")?

---

### Post by crjackson on 2008-06-27
Yes

Try clicking on the page, then look on the right hand side and try to play on of the Top 20's and see what you get.  I get a pop-up for a media player that never stops loading.

---

### Post by Xiong Chiamiov on 2008-06-27
Yes, I get that same result.  Looking at the source of the page seems to indicate it's a flash player:
```

<div id="flash_media_player" class="media_player_container_ads" style="display:none;">

```
but I'm not sure why it's not playing.  Considering the quality of the web site and Adobe's plugin, though, it's not that surprising.

---

### Post by crjackson on 2008-06-27
> **Xiong Chiamiov said:**
> Yes, I get that same result.  Looking at the source of the page seems to indicate it's a flash player:
```

<div id="flash_media_player" class="media_player_container_ads" style="display:none;">

```
but I'm not sure why it's not playing.  Considering the quality of the web site and Adobe's plugin, though, it's not that surprising.

Okay, so there is no way I can get this going then?

---

### Post by Xiong Chiamiov on 2008-06-27
> **crjackson said:**
> Okay, so there is no way I can get this going then?
There probably is, but I don't know how. :\

I've found that pretty much *anything* is possible in Linux, just some things are dang difficult...

---

### Post by crjackson on 2008-06-27
> **Xiong Chiamiov said:**
> There probably is, but I don't know how. :\

I've found that pretty much *anything* is possible in Linux, just some things are dang difficult...

Same here.  Hopefully this will get the attention of someone who has the magic bullet.

---

### Post by wolfen69 on 2008-06-27
it says on the FAQ that they do not support linux users. [From here]("http://www.wrfx.com/cc-common/ondemand/faq/") "Unfortunately we do not offer more support for Linux at this time."

---

### Post by crjackson on 2008-06-27
> **wolfen69 said:**
> it says on the FAQ that they do not support linux users. [From here]("http://www.wrfx.com/cc-common/ondemand/faq/") "Unfortunately we do not offer more support for Linux at this time."

Yeah I read that too. It also says to use the MPlayer plugin (which I have) for linux.  I was hopeing that there was some way to get Mplayer to work with this.  I'm guessing there is but it's beyond my technical skills.  I was hoping someone else knows how to do this and could point me to the answer.  I sure can't seem to figure it out on my own.

---

### Post by Pjotr123 on 2008-06-27
I suggest trying VLC for this. I can't check it now, as I'm on an openSUSE machine right now, and openSUSE 11 doesn't seem to like VLC. 

Apply this how-to:

Step 1:
[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)

Step 2:
[http://ubuntutip.googlepages.com/multimediaubuntustep2](http://ubuntutip.googlepages.com/multimediaubuntustep2)

This will probably do the job for you.  :-)

---

### Post by Xerp on 2008-06-27
[https://addons.mozilla.org/en-US/firefox/addon/446](https://addons.mozilla.org/en-US/firefox/addon/446)

---

### Post by crjackson on 2008-06-27
> **Pjotr123 said:**
> I suggest trying VLC for this. I can't check it now, as I'm on an openSUSE machine right now, and openSUSE 11 doesn't seem to like VLC. 

Apply this how-to:

Step 1:
[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)

Step 2:
[http://ubuntutip.googlepages.com/multimediaubuntustep2](http://ubuntutip.googlepages.com/multimediaubuntustep2)

This will probably do the job for you.  :-)

Sadly, I already have VLC and it wouldn't play the stream either.  I'll probably be working on this for days it seems.  If you get a chance, could you please try it on your system and let me know if you got it working?

Thanks.

---

### Post by crjackson on 2008-06-27
> **Xerp said:**
> [https://addons.mozilla.org/en-US/firefox/addon/446](https://addons.mozilla.org/en-US/firefox/addon/446)

If you have this installed, does that link work with your system?  I'm at work and I'll try it myself this weekend, but I would like to hear your results too.

---

### Post by markbuntu on 2008-06-27
The streamer page is looking for a windows browser to play through quicktime. At least that's what I think the page source code is telling me. It uses a bunch of java stuff. Maybe someone else could look at that and tell us.

---

### Post by wolfen69 on 2008-06-27
> **Pjotr123 said:**
> I suggest trying VLC for this. I can't check it now, as I'm on an openSUSE machine right now, and openSUSE 11 doesn't seem to like VLC. 

Apply this how-to:

Step 1:
[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)

Step 2:
[http://ubuntutip.googlepages.com/multimediaubuntustep2](http://ubuntutip.googlepages.com/multimediaubuntustep2)

This will probably do the job for you.  :-)

i doubt it will work. they even say they dont support linux. sit happens.

---

### Post by crjackson on 2008-06-28
> **Xerp said:**
> [https://addons.mozilla.org/en-US/firefox/addon/446](https://addons.mozilla.org/en-US/firefox/addon/446)

This didn't work.  Rule that one out...

---

