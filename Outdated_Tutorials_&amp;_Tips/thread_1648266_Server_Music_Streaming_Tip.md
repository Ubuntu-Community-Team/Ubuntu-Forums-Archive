---
title: "Server Music Streaming Tip"
date: 2010-12-18
forum: Outdated Tutorials &amp; Tips
---

### Post by scottuss on 2010-12-18
I just wanted to share a quick tip based on the experience I've had over the past week or so.

I have a Linux server that needs to share it's media (music) with a couple of Linux clients and a couple of Macs.

I tried mt-daapd (Firefly) and this was flaky. It didn't detect new media very well, it was a little buggy and isn't under active development.

The next thing was MediaTomb which was all well and good but clients connecting didn't "see" all of the media that was availalble. It wasn't a client issue because I tried many various combinations of clients. Also, iTunes does not show shared media from MediaTomb, which was no good for me.

In the end, I've got a possibly strange but very effective solution:
I'm running Rhythmbox on the server with the DAAP plugin.

It shares all of the music, without any hitches. Playlists are availalbe, and any new media added is served within seconds.

I know this isn't useful for headless servers, but for those people who have set up a GUI on their servers, this could be very useful.

There are other solutions, but Rhythmbox and the DAAP plugin are the best as far as I can see.

---

### Post by tgalati4 on 2010-12-18
Yes, I have come to the same conclusion as well.  For small mp3 collections (under 10k files) gnump3 also works well.  You could load the desktop environment files and rhythmbox on a headless server and run a remote X11 session with rhythmbox, but that kind of defeats the purpose of having a headless server.

And yes, it works well with many (perhaps all?) versions of iTunes, so you can see your DAAP shares and play them with ease.

apt-cache search daap

This brings up two other possibilities XMMS2 with a DAAP plug-in and tangerine.  I played with a mac-compiled version of tangerine and it worked OK.  Haven't played with it under Ubuntu or between Mac and Ubuntu.

---

### Post by scottuss on 2010-12-19
> **tgalati4 said:**
> Yes, I have come to the same conclusion as well.  For small mp3 collections (under 10k files) gnump3 also works well.  You could load the desktop environment files and rhythmbox on a headless server and run a remote X11 session with rhythmbox, but that kind of defeats the purpose of having a headless server.

And yes, it works well with many (perhaps all?) versions of iTunes, so you can see your DAAP shares and play them with ease.

apt-cache search daap

This brings up two other possibilities XMMS2 with a DAAP plug-in and tangerine.  I played with a mac-compiled version of tangerine and it worked OK.  Haven't played with it under Ubuntu or between Mac and Ubuntu.

Tangerine is still broken on 10.04. The tangerine-preferences GUI application part of it doesn't open and although there is a workaround, it is still not perfect. The solution if using tangerine is to edit the config file manually, but if you open the tangerine-preferences application, the config file gets ruined.

There are numerous bug reports for this, and a fix for later versions but not for 10.04, and after all, who would be crazy enough to run a non-LTS release on a server? ;)

---

