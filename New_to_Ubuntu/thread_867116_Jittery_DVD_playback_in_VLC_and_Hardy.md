---
title: "Jittery DVD playback in VLC and Hardy"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by SlappyPappy on 2008-07-22
I have been slowly installing Hardy on a spare drive as I still keep using Gutsy day to day. I tried watching a DVD using VLC in Hardy for the first time and it was quite jittery or choppy. VLC works great in Gutsy but for whatever reason not in Hardy. 

Mplayer plays DVDs smoothly in Hardy so it's not a big problem that VLC is having issues but I'd like to fix it if at all possible. Am I missing a setting somewhere in VLC that can stop the chop?

Thanks for any help you can offer.  :)

---

### Post by Potatoj316 on 2008-07-22
have you installed libdvdcss and libdvdread? (i think they are on version 3 and 2 respectivly)  I doubt they would play without those packages though.

---

### Post by SunnyRabbiera on 2008-07-22
Try other players like totem or xine?

---

### Post by SlappyPappy on 2008-07-22
Everything is installed and those other players aren't what I'm looking for. 

Still curious if there is a setting that I'm missing in VLC.

---

### Post by SlappyPappy on 2008-07-26
Okay, for real, this is ridiculous!

What is wrong with VLC in Hardy? I mean it worked flawlessly in Gutsy and now it's this choppy playing piece of garbage! I mean it will outright stop, freezing on a frame for seconds and then decide to start going again for a few seconds and then el freezo again.

Still looking for a way to fix VLC!

---

### Post by swisscow on 2008-07-26
Try enabling deinterlacing (VLC > Video > Deinterlacing > Blend) if playback is choppy or if you notice artifacts.

(From multimedia how-to sticky)

---

### Post by SlappyPappy on 2008-07-26
Tried that but no change. 

I'm about 2 seconds away from deleting VLC.  :confused:

---

### Post by SlappyPappy on 2008-07-27
Wow, this is remarkably depressing. 

Not sure what my next move is. I've used VLC for years and it's always been great. This is my first truly bad experience with the beast.

Freaking shame really.

Do I stay with Gutsy or complete the move to Hardy?

I'm in a quandary.

---

### Post by luminos77 on 2011-01-24
> **swisscow said:**
> Try enabling deinterlacing (VLC > Video > Deinterlacing > Blend) if playback is choppy or if you notice artifacts.

(From multimedia how-to sticky)

> **SlappyPappy said:**
> Tried that but no change. 

I'm about 2 seconds away from deleting VLC.  :confused:

> **SlappyPappy said:**
> Wow, this is remarkably depressing. 

Not sure what my next move is. I've used VLC for years and it's always been great. This is my first truly bad experience with the beast.

Freaking shame really.

Do I stay with Gutsy or complete the move to Hardy?

I'm in a quandary.

This response may be way too late but if you want to return back to vlc, I found a way.  

Follow the user swisscow's instructions, but also follow this path.  Video/deinterlace/ click "on" , the blend option should automatically be set.  VLC already takes care of the jittering, just make sure you have the mediubuntu repository in your system.  The deinterlacing removed series of small horizontal lines that were there without it enabled.  

My problem is that the video quality in general is not DVD quality.  I noticed it has been two years since this was posted, have you found a way to reclain DVD quality in ubuntu?  Thanks.

---

