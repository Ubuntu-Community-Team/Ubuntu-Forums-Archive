---
title: "audacity static in recording"
date: 2012-07-03
forum: New to Ubuntu
---

### Post by briar rabbit on 2012-07-03
hello

I have audacity which worked fine until today.  There is static in any thing I try to record, even when there should be silence as nothing being input.

The only changes I have made since last using audacity was installing vlc.

I tried to uninstall and then put audacity back but,, no good still have static.

Is anyone else having or had this problem with static in audacity recording.

I really like my audacity.  I think there is something interfering with it somehow.

Any help is appreciated.

---

### Post by Redblade20XX on 2012-07-03
Do you have pulse audio volume control installed? If not you should install it because it will alow you to control what is being inputted and outputted in your system.

Also take a look in Audacity preferences to see what channels input set to (ie. microphone). Take a screenshot of it and post it here.

- Red

---

### Post by briar rabbit on 2012-07-03
Hi thanks for the reply

I have a lot of pulse audio and there are some I do not have which should I have?

[IMG]http:///home/ferg/1%20%20%20Desktop/Audacity%20Preferences.png[/IMG]

[IMG]http:///home/ferg/1%20%20%20Desktop/Microphone.png[/IMG]

hope I did that right   --- how do you add a png screen shot ... duh

Thhe microphone worked before at the present setting.

---

### Post by briar rabbit on 2012-07-07
Hello,

There are a lot of patient helpful people on this forum, I thank them all.

It turns out that I had changed the mic settings in alsamixer in the terminal while working on vlc, which made no difference to vlc.  Days later when I went back to audacity I found the static and did not know where it was coming from.   Sounds dumb I know, but that is what happened.  Changed the mic setting back and static gone.

The thing is there is too much that is not user friendly with pcs.

So for static in audacity it could be the alsamixer settings

---

