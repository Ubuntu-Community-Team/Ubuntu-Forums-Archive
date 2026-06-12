---
title: "VLC  DVD Problem"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by s.fox on 2008-11-12
Hi,

I have been having trouble with playing a DVD on Intrepid Ibex.   I can play other DVD's just fine.  The one I can't play is a new DVD I bought today.  It does play in my DVD player.   Ubuntu recognizes it but VLC gives me this error:

```
Your input can't be opened:
VLC is unable to open the MRL 'dvd:///dev/scd0'. Check the log for details.
```

I had a look at [this]("http://ubuntuforums.org/showthread.php?t=766683") guide but now I am stuck.  The error message says check the logs except that I don't know how to,  and when I have what to do about it.  If anyone could talk me through resolving this then I would be forever grateful.

Thanks to anyone who can help.

---

### Post by s.fox on 2008-11-20
Nobody?

---

### Post by LowSky on 2008-11-20
have you tried using any other player, like mplayer or xine?

take a look at the VLC forums as well
[http://forum.videolan.org/viewforum.php?f=13](http://forum.videolan.org/viewforum.php?f=13)

---

### Post by gandaran on 2008-11-20
to play encrypted dvd's you need to install **libdvdcss2** from the medibuntu repository
to add the medibuntu repo follow these instructions [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by mc4man on 2008-11-20
You may want to post the title name. There are a handful of titles that have no solution for playback on unlicensed players due to a certain structure protection. The odds are overwhelming that your title isn't one of those.

Though if it is  you'll need to rip and fix for playback.

I would certainly try other players as mentioned.

---

### Post by oldos2er on 2008-11-20
Open VLC, choose Media, Open Disc, and choose your DVD drive under Disc Device. FWIW, mine is /dev/scd0 .

---

### Post by Bablefish on 2008-11-20
In one word Automatrix   It worked for me

---

### Post by oldos2er on 2008-11-20
> **Bablefish said:**
> In one word Automatrix   It worked for me

 Use of Automatix is not supported, since it creates so many "issues."

---

### Post by s.fox on 2008-11-20
Thanks for all the replies people,  I was beginning to think it was unsolvable. :)

I shall try the other players when I next boot into Ubuntu.

The title of the DVD is:  Futurama Benders Game

Once again,  thanks for all the support! :)

-Ash R

---

### Post by LowSky on 2008-11-20
Could it be a region error?
I know the US/Canada is Region 1, and Europe is region 2

---

