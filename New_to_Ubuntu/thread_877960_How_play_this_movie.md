---
title: "How play this movie"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by jmfa59 on 2008-08-02
when trying to play this clip I got error message I attached a screen shot of that message THANKS

---

### Post by kostkon on 2008-08-02
Hmmmm, I think you need to install the Windows codecs package (called *w32codecs* for 32bit Ubuntu, *w64codecs* for 64bit) that is offered by the [*Medibuntu* repository]("http://www.medibuntu.org/").

Add this repository to your software sources list (instructions on how to do it are on the site) and then go to *Synaptic* and search for the *w32codecs* package if you have a 32bit Ubuntu (or the *w64codecs* if you have a 64bit system) and then install it.

Also make sure that you have the *gstreamer0.10-pitfdll* package installed.

---

### Post by jamesrfla on 2008-08-02
You need to get Sipro ACELP.net. Go to System>administration>system matic pack manager. Then go to the search button and type in Sipro ACELP.net. If anything comes up click the box and install it. Hope this helps.

---

### Post by natirips on 2008-08-02
Sounds like it's encoded with some weird (likely pro-pirate-ry) codec, which may not even exist for Linux, although I might be way wrong.

If possible re-download the video in a diffrent format.

Also, try using VLC media player, it's a bit CPU intesitive but plays almost everything out-of-the-box. So far I haven't encountered a video file it wouldn't at least try playing in some buggy way.

---

