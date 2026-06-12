---
title: "Leafpad system sounds audacity"
date: 2012-11-02
forum: New to Ubuntu
---

### Post by Kevin McCready on 2012-11-02
I was recording off an internet stream with audacity and also using leafpad.

If a search in leafpad finds nothing, then leafpad gives a loud ping.

The ping was recorded. Yuk.

Any help appreciated.

---

### Post by cwsnyder on 2012-11-02
Audacity has the capability to silence the ping, but only by dropping out anything during the duration of the ping.  I don't know of any method to bring back any other sound which was occurring at the time of the ping.

---

### Post by Kevin McCready on 2012-11-02
I don't mind re-recording. Can I turn off system sounds? Can I turn off leafpad sounds.

Does audacity has capacity to do "stitching" like in pictures? Then maybe I could stitch out the old and stitch in the new.

---

### Post by cwsnyder on 2012-11-03
Yes, you can turn off system sounds, but not specific application sounds.  Check your settings menus.

Yes, Audacity can do a cut-and-paste with sound, if you can locate the proper area on your recordings.

---

### Post by Kevin McCready on 2012-11-04
Thanks. In Lubuntu there is no settings menu. There is a preferences menu but I couldn't find system sounds there.

---

### Post by bryncoles on 2012-11-04
Hi Kevin McCready.  

Audacity can do noise removal.  I think what you'd need to do is record the 'ping' on its own (for example, at the end of the stream, when you've finished recording whatever you wanted to record).  Then select effect -> noise removal.  Highlight the ping (on its own) and select / play that sound.  Then highlight the area in the audio stream where the ping crept in and play / remove the sound.  Audacity will do its best to remove teh ping noise, while leaving the rest of the audio stream in place.  

More information on that here:

[http://wiki.audacityteam.org/wiki/Noise_Removal](http://wiki.audacityteam.org/wiki/Noise_Removal)

Also, [a guy on the ask ubuntu](http://askubuntu.com/questions/80384/where-are-the-lxde-sound-preferences) pages recommends installing xfce4-mixer to control system sounds in Lubuntu.  I don't know if you'd want to do that though.

---

### Post by Kevin McCready on 2012-11-04
Thanks but that sounds a bit fiddly. I'd rather learn how to turn off the system sounds if someone knows how in Lubuntu

---

### Post by bryncoles on 2012-11-04
No problem.  Disabling system sounds is definitely the better solution to the problem!

---

### Post by Kevin McCready on 2012-11-04
yes, but how do you do it?

---

### Post by cwsnyder on 2012-11-06
Go to **Preferences** menu entry >> **Customize Look and Feel** >> **Other** tab >> **Sound Effect** selections to turn off system sounds in Lubuntu.

---

### Post by Kevin McCready on 2012-11-08
hmm thanks. who would have guessed???

---

