---
title: "HOWTO: Get Streaming Media Working In Firefox, without M-Player!?"
date: 2005-06-01
forum: Outdated Tutorials &amp; Tips
---

### Post by derrick1985 on 2005-06-01
I was getting REALLY tired of Mplayer-Plugin trying to stream my video on websites, (and slowly at that) and when it finally does, it gets stuck someway through, and won't stream the rest! So, after some searching on the forums, I found a way around it, and put together pieces and made a howto. 

IN NO WAY do I take full credit for this. 

Here is how I FINALLY got everything to work properly.

Follow the multimedia guide located at [http://www.ubuntuguide.org/#codecs](http://www.ubuntuguide.org/#codecs) (This way, we can stream virtually everything on the net)

Install RealPlayer [http://www.ubuntuguide.org/#realplayer](http://www.ubuntuguide.org/#realplayer) (So we can listen to .rm files and anything realplayer based)

Follow the Howto to hear multiple sounds (this way, real player will work without having to kill esd) [http://ubuntuforums.org/showthread.php?t=32063](http://ubuntuforums.org/showthread.php?t=32063)
Install xine-ui [http://www.ubuntuguide.org/#xine-ui](http://www.ubuntuguide.org/#xine-ui)

When following the guides over at Ubuntuguide.org, make sure you read up on EVERY substep, sometimes the littlist thing, can throw things off.

Install the MediaPlayerConnectivity plug-in for Firefox
[https://addons.mozilla.org/extensions/moreinfo.php?id=446](https://addons.mozilla.org/extensions/moreinfo.php?id=446)

Run the Configuration Wizard. Set the Video player for Quicktime to xine-ui (it should detect it) Set RealPlayer to realplay, Windows Media to xine-ui, and finally, your choice for music (mine's xmms for streaming)

The next two settings are up to you, wether or not you want the streams to open up in your desired media players automatically, i choose no, personally, but it's up to you.

(NOTE: In case you CANNOT install firefox extensions (v1.0.4 Ubuntu bug) here is how you can do it:

Open up a new tab (ctrl+t) and type in the address bar about:config

Scroll down until you see general.userage.venderSub

Double click on the line and a popup box will appear, enter in 1.0.4
Now, you can safely get any firefox extension from Firefox's website!

Enjoy.

---

### Post by adamkane on 2006-04-25
Rather than install realplayer, you can use beep-media-player or xmms (along with mediaplayerconnectivity) to stream realmedia. As long as you have mplayer installed, you can use a variety of media players to stream realmedia.

I guess you would miss out on the benefits of using realplayer, so this suggestion is for those who want to avoid proprietary software wherever possible.

---

### Post by nisarg on 2007-10-16
I have recently migrated to Ubuntu from Windows. And so far its been good. But there lot I guess to get used to.
Especially streaming is been an issue for me that I am trying to resolve since I have moved to Ubuntu (2 days :) )
I seem to have installed everything, real player, mplayer, vlc, codecs, Media player connectivity for FF but still I am not able to stream media?
Can you please help?
Thanks

---

