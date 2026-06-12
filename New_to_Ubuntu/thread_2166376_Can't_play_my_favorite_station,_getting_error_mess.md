---
title: "Can't play my favorite station, getting error messages with player"
date: 2013-08-09
forum: New to Ubuntu
---

### Post by User_1 on 2013-08-09
Hello all,

I have a new 13.04 Lubuntu installation and I'm having trouble getting my fav station to play.  The station is SomaFM btw.  I can play stuff on Pandora but I'm more interested in the former.  When I click a link on SomaFM to play a channel, I get this message, "Could not load mplayerplug-in is now gecko mediaplayer 1.0.8."  I'm pretty sure I have VLC installed.  I might have gecko installed too.  I really don't know. 

Any help on this would be greatly appreciated.

---

### Post by monkeybrain20122 on 2013-08-09
Well it works in Firefox. Are you using Chrome? gecko-mediaplayer doesn't load in Chrome and it has been like that for sometimes. So I always use Firefox for online multimedia.

The easiest way is to just use Firefox. If you insist on using Chrome try the totem plugin and see if it works. type about://plugins in Chrome's address bar, then click the "detailed" tab and disable all entries of gecko-mediaplayer and make sure that totem's plugins are enabled (that includes something called the "vlc media plugin (compatible Video..)" though I think it is actually totem. Now see if this works (chances are it won't cos Totem is not very good for that kind of streams). Failing that you may try to download the .asx file and play it in VLC.

EDITED: Ok, I see you are on  Lubuntu so you are using Chromium. gecko-mediaplayer doesn't work in Chromium either (it is just a crippled, alpha version of Chrome)  and the solution is the same except that in lubuntu totem is not installed by default. so instead of installing a whole bunch of stuffs the easiest way is to install Firefox from synaptic. Yes, gecko-mediaplayer is installed by default or you won't see the error message in Chromium. 
Finally make sure you have installed lubuntu-restricted-extras for codecs.

P.S. Someone should have filed a bug against lubuntu, It doesn't make sense that they bundle chromium as the default browser and gecko-mediaplayer as the default web mediaplugin while it is known that gecko-mediaplayer has been broken in Chrome/Chromium for ages. Maybe I will do that.

---

### Post by howefield on 2013-08-09
> **User_1 said:**
> I have a new 13.04 Lubuntu installation and I'm having trouble getting my fav station to play.  The station is SomaFM btw.

Working fine with Chromium here whether clicking links for external player or using the pop up player. Although I'm using Ubuntu not Lubuntu, I''ll come back to this later when less busy if you haven't gotten it to work.

---

### Post by monkeybrain20122 on 2013-08-09
> **howefield said:**
> Working fine with Chromium here whether clicking links for external player or using the pop up player. Although I'm using Ubuntu not Lubuntu, I''ll come back to this later when less busy if you haven't gotten it to work.

Which version of lubuntu and which version gecko-mediaplayer? I don't think gecko-mediaplayer works on Chrome/Chromium since version 1.4 or something. It might work in Ubuntu(lubuntu) 12.04

---

### Post by howefield on 2013-08-11
> **User_1 said:**
> I'm pretty sure I have VLC installed.

Did you install the vlc browser plugin ?

---

