---
title: "Wierd bug in all media players?"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by Google Spider on 2008-06-10
Hi,
I'm having problems with all media players I've tried so far -- kaffeine, totem, Mplayer and VLC. 

Whenever I try to skip a bit forward or backward in a video(by dragging the slider), it takes me back to **t=0** and starts playing from the beginning of the file. ](*,)

Today I reported this bug to Totem launchpad but the dev marked it invalid saying :"This bug has already been reported". Now I'm surprised by the fact that *all* my players are having the same problem. Makes me wonder if there something wrong with *my* installation  :confused:

Are your media players working as expected? If it really is a bug in all media players, what can I do while they fix it? Please suggest some other players I can use in the meantime..or any fix to my problem if you can ;)

Thanks for your time!

---

### Post by drs305 on 2008-06-10
The same is true trying to listen to archived online internet audio broadcasts. I've yet to find a linux media player which can consistently move forward or backward the way windows media player can. It's really frustrating.

---

### Post by ukripper on 2008-06-10
I only find this problem using firefox for bbc radio only iplayer and other flash player plugins works fine, offline everything works as expected in audacious, XMMS, VLC or mplayer.

---

### Post by DrMega on 2008-06-10
I'm guessing, because I don't know much about the inner workings of media players on Linux, but do all the affected media players use the gstreamer or xine multimedia engines? I.e. is the problem not with the media players, but the underlying infrastructure I wonder.

---

### Post by Google Spider on 2008-06-10
I was wondering the same thing. Probably all players share some common code.

---

### Post by sonicb00m on 2008-06-10
think its a gstreamer problem.

---

### Post by acidsolution on 2008-06-10
I dont have problem while working offline in either 
VLC or mplayer or totem or Rythmmusic box all are working fine for me 
the only problem is when i want to play live media through firefox. Firefox plugins has the problem but offline mode works well for me 
:)

---

### Post by DrMega on 2008-06-10
I think you can choose between gstreamer and xine for the multimedia engine, if I'm not mistaken. I know in Totem you can. Maybe xine is good, but gstreamer has the bug perhaps?

---

### Post by SunnyRabbiera on 2008-06-10
gstreamer is still new, thats why I use the win32 codecs... it works for me.

---

### Post by Google Spider on 2008-06-10
> **SunnyRabbiera said:**
> gstreamer is still new, thats why I use the win32 codecs... it works for me.

I will really appreciate step by step instructions to do this!:)

Or this:
> **DrMega said:**
> I think you can choose between gstreamer and xine for the multimedia engine, if I'm not mistaken.

I just want to get these things working :D

---

### Post by Google Spider on 2008-06-11
yeah I guess.

---

