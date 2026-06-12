---
title: "no sound on youtube anymore, causes firefox to freeze and cant re-open"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by WinterMadness on 2008-08-13
audio on firefox used to work fine, until now.
the video will freeze (but keep downloading) and i have to force quit firefox and then when i try to reload firefox it says its still running

---

### Post by tuxxy on 2008-08-14
Did you recently edit or update any plugins or flash settings, what version of flash are you using

---

### Post by wilbbe01 on 2008-08-14
I had a problem like this a while back.  I doubt you are in the same situation as me, but here is what my problem was just in case you may be in a similar situation.

Whenever I had wine running under my 64 bit ubuntu box, youtube or any other similar internet video site would play a couple of seconds, then the video and audio would both freeze and everything would go to crap.  Closing wine and reopening firefox and *boom* all would be well.

You don't happen to have anything open that is somehow locking your audio or something?  Have you reinstalled flash and such since you first started experiencing the problems?

As for the reopening of firefox, there should be a lock of some kind in a firefox directory somewhere.  It would likely be called [something].lock but I don't remember off the top of my head.  I'd look but I've only got Vista at my disposal right now.  Tell me if any of that helps, or if it doesn't in which case I'll look a bit harder.  Good luck.

---

### Post by sydbat on 2008-08-14
I have/had a similar problem with Amarok running. Just turn off the other stuff that may be taking audio-type resources and reboot Firefox. Should work fine.

---

### Post by lian1238 on 2008-08-14
To restart firefox, first really quit first:
```

killall firefox

```or firefox-bin or firefox-something. Type "killall firef" then press TAB. Now you can restart firefox.
As for the sound, do you know what you did before this happened? I have a feeling it has something to do with the flash plugin. Type "about<colon>plugins" (replace <colon> with ":") in the address bar of firefox, and tell us what is under Flash. For example, mine looks like this:

Shockwave Flash
 File name:  libflashplayer.so
Shockwave Flash 9.0 r124

---

### Post by WinterMadness on 2008-08-14
> **tuxxy said:**
> Did you recently edit or update any plugins or flash settings, what version of flash are you using

nope. this is really weird because now its working. but i know a little bit later it wont.

---

### Post by tuxxy on 2008-08-14
Is it workign now because you have closed a conflicting app maybe?

---

### Post by MOHCTP on 2009-12-15
> **WinterMadness said:**
> nope. this is really weird because now its working. but i know a little bit later it wont.

I have the same problem: initially, the sound works, but the next day it's dead silent **until you restart FireFox** And you can't just quit FireFox and start it again, it will say that FireFox is already running, so you will have to kill or end the process before you can run it again.  Once you restart FireFox though, the sound will work just fine... until some time later when the same thing happens again.
Any ideas?

---

### Post by supermelon928 on 2009-12-15
I had a similar problem with ubuntu 8.04. My computer would lean back and forth between being able to play the sound for files on my computer and play the sound for things on firefox involving flash. It would go back and forth seemingly whenever it felt like it.

Unfortunately, I was never able to find out why it did this, and the problem went away when I got 9.04.

What version are you currently using?

---

### Post by MOHCTP on 2009-12-15
> **supermelon928 said:**
> I had a similar problem with ubuntu 8.04. My computer would lean back and forth between being able to play the sound for files on my computer and play the sound for things on firefox involving flash. It would go back and forth seemingly whenever it felt like it.

Unfortunately, I was never able to find out why it did this, and the problem went away when I got 9.04.

What version are you currently using?

9.10
I updated everything I could: the plugin first, then FireFox, then, finally, Ubuntu itself -- none of it helped.

Had enough, switching to Chrome.  I wish they had IE on Linux -- best, most stable and compliant browser ever.

---

### Post by jamieleshaw on 2009-12-15
> **MOHCTP said:**
> 9.10
I updated everything I could: the plugin first, then FireFox, then, finally, Ubuntu itself -- none of it helped.

Had enough, switching to Chrome.  I wish they had IE on Linux -- best, most stable and compliant browser ever.
Hahhah that's hilarious *you are joking right?*

---

### Post by pedja_portugalac on 2009-12-15
> **MOHCTP said:**
> 9.10
I updated everything I could: the plugin first, then FireFox, then, finally, Ubuntu itself -- none of it helped.

Had enough, switching to Chrome.  I wish they had IE on Linux -- best, most stable and compliant browser ever.

Did you tried to download flash plugin .tar.gz for linux from adobe [http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_(.tar.gz](http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_(.tar.gz)) and put libflashplayer.so into /usr/lib/mozilla/plugins/ ?
I had problem few days ago and resolved it like this. Now it plays like a charm.

---

### Post by MOHCTP on 2009-12-16
> **jamieleshaw said:**
> Hahhah that's hilarious *you are joking right?*

Joking?  Not at all.  Google for "no sound in Firefox" and then do the same for "no sound in Internet Explorer".  With more than twice the marketshare and its reputation, you'd think IE would have ten times the number of hits.  The results, however, are the opposite of what you'd expect.

I like FireFox because of its many plugins and because it's not Microsoft, but objectively IE is a much more stable browser, and correctly renders a much higher percentage of Web pages than FF.

I mean come on, I can't even restart FireFox without going into a process manager and killing it.  If they can't handle a simple Quit function, what is there to talk about?

---

### Post by jamieleshaw on 2009-12-16
> **MOHCTP said:**
> Joking?  Not at all.  Google for "no sound in Firefox" and then do the same for "no sound in Internet Explorer".  With more than twice the marketshare and its reputation, you'd think IE would have ten times the number of hits.  The results, however, are the opposite of what you'd expect.

I like FireFox because of its many plugins and because it's not Microsoft, but objectively IE is a much more stable browser, and correctly renders a much higher percentage of Web pages than FF.

I mean come on, I can't even restart FireFox without going into a process manager and killing it.  If they can't handle a simple Quit function, what is there to talk about?
Actually Firefox has the largest Market Share now..........
I've never had any probs with Firefox.
Fiefox is standards compliant and for me way more things work in it.

---

### Post by MOHCTP on 2009-12-16
> **pedja_portugalac said:**
> Did you tried to download flash plugin .tar.gz for linux from adobe [http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_(.tar.gz](http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_(.tar.gz)) and put libflashplayer.so into /usr/lib/mozilla/plugins/ ?
I had problem few days ago and resolved it like this. Now it plays like a charm.

Thank you pedja,

I haven't tried that, but since I do have sound after I kill and re-run FireFox, I didn't think my problem was config related, or that I was missing any files.  If that were the case, I wouldn't have any sound period.

Nevertheless, I did copy libflashplayer.so into /usr/lib/mozilla/plugins/
I don't know what it does, but I will report back here with the results...

---

### Post by MOHCTP on 2009-12-16
> **jamieleshaw said:**
> Actually Firefox has the largest Market Share now..........
I've never had any probs with Firefox.
Fiefox is standards compliant and for me way more things work in it.

Jamie,

Your perspective and objective reality are two different things.  You can't just spew nonsense like this without any data to back it up.

Now, I gave you the query to prove that FireFox has more problems with sound than IE, and here's a marketshare link: [http://marketshare.hitslink.com/report.aspx?qprid=0](http://marketshare.hitslink.com/report.aspx?qprid=0)

It works for you? Great! It doesn't work for me, and, as you can see, we are in a thread of quite a few people for whom it doesn't work either. You will also note that many of them clearly state: "sound works in IE, but not in FF", which means when FF fails, IE is what people go to. 

I don't want to start an off-topic flame war, just giving you something to think about.

---

### Post by Temposs on 2009-12-16
Oy.

1) Flash is **not a standard** to be complied with. It's a closed-source proprietary plugin that no one except Adobe can change.

2) If a flash app works better on Windows and IE, that's because the Adobe developers for Flash and the developers of the particular flash app you're using tested/optimized/bug-fixed more on IE than Firefox and more on Windows than Linux.

3) Firefox devs can do very little to improve flash performance. They don't have the source code and they can only guess at what causes issues.

EDIT: In fact, just a few years ago, Flash on Linux was wayyy behind Flash on Windows. It sucked. But Adobe has improved their Linux plugin a lot, although it's still a little inferior. Linux folks have been petitioning Adobe to open-source the Flash plugin for Linux for a long time. But they refuse. We just can't do much about the state of the Linux Flash player without the source code. It's all on Adobe's shoulders, and we must wait with baited breath for the next version and the hoped-for improvements it may bring.

---

### Post by MOHCTP on 2009-12-16
> **Temposs said:**
> Oy.

1) Flash is **not a standard** to be complied with. It's a closed-source proprietary plugin that no one except Adobe can change.


Excellent post, Temposs, right on.

The only counter-argument I have, being a developer myself, is that no matter what kind of cr@p Adobe puts into their plugin, FF should not hang because of it.  

As for flash in general, if Adobe does not improve their plugin significantly and/or does not release the source, an open source alternative will eventually emerge.  I hear this already happened with PDF and Java, so maybe flash is not far behind.

---

### Post by VastOne on 2009-12-16
> **MOHCTP said:**
> Excellent post, Temposs, right on.

The only counter-argument I have, being a developer myself, is that no matter what kind of cr@p Adobe puts into their plugin, FF should not hang because of it.  

As for flash in general, if Adobe does not improve their plugin significantly and/or does not release the source, an open source alternative will eventually emerge.  I hear this already happened with PDF and Java, so maybe flash is not far behind.

Inevitably this will happen and I for one will stand and sing when it does....:)

---

### Post by Temposs on 2009-12-16
> **MOHCTP said:**
> Excellent post, Temposs, right on.

The only counter-argument I have, being a developer myself, is that no matter what kind of cr@p Adobe puts into their plugin, FF should not hang because of it.  

If the Flash plugin itself hooks into the Firefox process in the right ways, I think it could easily hang Firefox were Flash to go down. 

> 
As for flash in general, if Adobe does not improve their plugin significantly and/or does not release the source, an open source alternative will eventually emerge.  I hear this already happened with PDF and Java, so maybe flash is not far behind.

There are in fact two open source flash players, Gnash and Swfdec. You can try them in Ubuntu, but you should uninstall the Adobe flash player before you try them. They do not have every feature that the Adobe Flash plugin has, but supposedly for the features they have, they are a LOT better in terms of performance and stability. Because they are behind in features, most people will choose not to use the open source plugins because they won't work on some sites.

---

### Post by jamieleshaw on 2009-12-16
actually nevermind

---

### Post by VastOne on 2009-12-17
> **jamieleshaw said:**
> actually nevermind

Why?

Please expand on your solution as it may in fact help someone else with the same or similar issues.

Thanks!

8-)

---

### Post by supermelon928 on 2009-12-17
> **VastOne said:**
> Why?

Please expand on your solution as it may in fact help someone else with the same or similar issues.

Thanks!

8-)

love your icon.

---

### Post by VastOne on 2009-12-17
> **supermelon928 said:**
> love your icon.

Thanks!

:guitar::biggrin::-D

---

