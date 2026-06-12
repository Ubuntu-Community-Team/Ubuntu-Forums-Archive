---
title: "Problems with Flash video"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by zorblek on 2008-09-24
I'm having intermittent difficulties watching Flash embedded videos in Ubuntu Hardy. I have several different problems, which I suspect are related. All of them have occurred in both Firefox and Opera and with videos from multiple sites, which leads me to conclude that the problem is with Flash, and not with the browsers or sites themselves. Also, the problems occur regardless of network or CPU load, or how much of the video has been loaded. Also, non-video Flash content, i.e. games and such, don't seem to be affected.

* Sometimes when a Flash video is loading or playing the browser crashes. It doesn't hang or slow down or anything, it just exits without any warning.

* More frequently, the video will stop playing as if it were buffering. The embed will then disappear, leaving a white or gray rectangle in its place. (Sometimes there will be a smaller gray rectangle inside a white rectangle.) Once this has happened once, it will happen with all videos until the browser is restarted.

* Video playback will often be very choppy for no apparent reason, even when the whole video has already loaded.

I tried reinstalling all Flash-related packages using Synaptic, but it didn't seem to have any effect.

Does anybody have an idea of what might be causing this? A Google search hasn't turned up anything useful.

---

### Post by wolfie2x on 2008-09-24
I had flash probs in 3.0.1 and got'em fixed by installing Flash 10 plugin.

follow this to install: [http://ubuntuforums.org/showpost.php?p=5587712&postcount=472]("http://ubuntuforums.org/showpost.php?p=5587712&postcount=472")

---

### Post by zorblek on 2008-09-24
Thanks for the suggestion. I gave it a try, but it looks like I've still got the same issues.

---

### Post by wolfie2x on 2008-09-24
> **zorblek said:**
> Thanks for the suggestion. I gave it a try, but it looks like I've still got the same issues.

hmm.. weired.. 
does tools>add-ons>plugins show "Shockwave Flash 10.0 r12"? are there any other flash plugins besides this? if so u need to disable/uninstall them.

if nothing else works, u can try flashblock FF addon. it'll block all flash by default and gives u a play button so that u can view only the flash stuff u need. I have this installed, and maybe that's why I don't experience many crashes..

---

### Post by zorblek on 2008-09-24
Everything looks to be in order there. I've got the 10.0 r12 version, and I don't see anything else that looks flash-related.

I do use NoScript, which blocks flash objects as well, which helps prevent random crashes. But it's no help when I want to actually watch something.

---

