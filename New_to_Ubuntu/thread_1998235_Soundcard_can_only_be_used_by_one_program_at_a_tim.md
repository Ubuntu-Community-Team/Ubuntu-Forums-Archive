---
title: "Soundcard can only be used by one program at a time?"
date: 2012-06-06
forum: New to Ubuntu
---

### Post by VE6EFR on 2012-06-06
I was running a communications program called DVTool that when combined with a [DV Dongle]("http://www.dvdongle.com/DV_Dongle/Home.html")gives me access to the [D-STAR]("http://en.wikipedia.org/wiki/D-STAR") network. While I was waiting for a call I decided to listen to some music and to my surprise, wasn't able to hear it. If I exit DVTool and then open my music player I am able to listen to music no problem. If I then launch DVTool and connect to the D-STAR network I no longer hear any stations on D-STAR but I can still hear the music player.

Is this normal behaviour on Ubuntu to only allow one program to access the soundcard at a time? Or is there a setting that I need to either enable or disable to allow access to the soundcard by multiple programs?

Thanks for the help,

Jeff

---

### Post by blackbird34 on 2012-06-06
No, as far as i know, its not normal for Ubuntu to behave like that. 
DVTool may block the sound channel for some reason (i've never used it myself). You could turn on DVTool and your music player, and then look in System Settings > Sound > Applications tab, it will tell you which apps are using the sound, which ones have been turned off, etc. (See screenshot - i'm in Unity, listening to music on VLC)

---

### Post by VE6EFR on 2012-06-06
Thanks for the reply, blackbird34. After reading your message I did some playing around and found that the "hidden feature" lies with DVTool. As soon as I connect to a D-STAR gateway DVTool captures the soundcard and everything else loses access. However once I disconnect from the gateway behaviour goes back to normal until I connect to another gateway.

Now that I think of it, it's not really a problem though. If I am in the middle of a conversation or handling emergency communications (severe weather net, etc) the last thing I need is to have computer noises go out over the air.

Thanks for the help,

Jeff

---

