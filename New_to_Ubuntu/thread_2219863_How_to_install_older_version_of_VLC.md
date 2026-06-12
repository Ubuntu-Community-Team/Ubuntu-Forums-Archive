---
title: "How to install older version of VLC?"
date: 2014-04-25
forum: New to Ubuntu
---

### Post by socrates2 on 2014-04-25
Hello!

I'm using Lubuntu 14.04 LTS.

In the new version of VLC player (2.1.3) plugin vlsub doesn't work.
Vlsub is showing in vlc menu but don't run.

I want to install vlc version 2.0.8 but I don't know how to.

I tried to force package in synaptic but that option is grayed.
Also I have tried to download vlc 2.0.8 deb package but package installer can't install it.

Does anyone knows right way to install vlc 2.0.8 in lubuntu 14.04?

Thanks.

---

### Post by monkeybrain20122 on 2014-04-25
What do you mean by it doesn't work? I suppose it will still work if you just download the .lua file and move it to ~/.local/share/vlc/lua/extensions
[http://www.webupd8.org/2012/02/vlsub-vlc-extension-to-search-and.html](http://www.webupd8.org/2012/02/vlsub-vlc-extension-to-search-and.html)
Anyway there are many ways to get subtitles, I wouldn't go through the trouble of downgradng.

---

### Post by socrates2 on 2014-04-25
After install vlsub is in menu but it doesn't run.

This plugin is great because automatically download subtitles.
I have read somewhere that until a new version of VLC vlsub will not work with current version.

I thought it was easier to install old version of some program/package. :)
So I will wait new version of VLC or vlsub.

---

### Post by monkeybrain20122 on 2014-04-25
Smplayer has a similar function, not sure if it works though. I see the option in vlc 2.1.4 (I compiled it) but never use it. Usually I just get them from open substitles which is where the apps search for subtitles anyway.

---

### Post by lt-marys on 2014-04-27
I can confirm this. There is something wrong with VLC version 2.1.2. There is button "VLsub 0.9.10" but it only works when no media is playing. While something is playing the terminal outputs: "[0x7f8e70350e88] lua generic error: Could not activate extension!". I suppose this is a bug.

---

### Post by sandyd on 2014-04-27
fyi, issue above is in reference to the issue described at [https://github.com/exebetche/vlsub/issues/28](https://github.com/exebetche/vlsub/issues/28)

---

### Post by Rob Sayer on 2014-04-27
> **monkeybrain20122 said:**
> Smplayer has a similar function, not sure if it works though. I see the option in vlc 2.1.4 (I compiled it) but never use it. Usually I just get them from open substitles which is where the apps search for subtitles anyway.

I've found it doesn't always work ... it's looked at opensubtitles.org like it's supposed to and not founs anything.  Then I immediately went to their site and the sub was there.

That doesn't stop it from being my default video player though.

At any rate, I think it'd be easier for a beginner to just search sub  sites than to figure out how to install an old vlc version and hold it.

Besides, if you use vlc for streaming you may be open to security bugs that way.  This happened before with vlc.  As of v. 2.0 you can't adjust the local file cache.  This is ridiculous.  But if you run older versions of vlc you can't safely use it to stream anymore.

---

