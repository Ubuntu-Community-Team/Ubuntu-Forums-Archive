---
title: "mkv/divx streaming fullscreen issues"
date: 2012-03-06
forum: New to Ubuntu
---

### Post by SeanChet on 2012-03-06
Okay, so I like to stream Tv shows and movies.  My new ubuntu 11.10 computer has a larger screen and so I have to use sites that stream divx and mkv to get a pixel rate to match the screen. Unfortunately, I can't get the player to toggle fullscreen, or pause for that matter.  The videos play but I have no control over them afterwards. I'm running firefox, I have the restricted set, 8gig ram, integrated video chip on the mother.  Let me know what I should do.  Thanks!

---

### Post by d4m1r on 2012-03-06
What media player are you using? I'd recommend checking out VLC 2 (google install vlc 2 ubuntu). It has many more features than the default media player installed with 11.10 at least.

---

### Post by SeanChet on 2012-03-06
I wasn't using a player, I'm unable to get the in-firefox player to allow me access to the controls. Also, I was looking around this forum and found this: [http://ubuntuforums.org/showthread.php?t=766683&highlight=divx+fullscreen](http://ubuntuforums.org/showthread.php?t=766683&highlight=divx+fullscreen) . I downloaded some of the stuff, basically whatever I could get to download, and nothing has changed for the better and now my banshee dvd player is making the top of bottom of the picture wobble. The distortion doesn't happen in vlc, which makes me think I changed something only being accessed by the banshee player, oh and I'm not using vlc 2 I'm using 1.1.12. Any ideas?

---

### Post by lovinglinux on 2012-03-08
Type *[noparse]about:plugins[/noparse]* in the address bar and check which plugins you have. If you can't see the video controls, then most likely that you have VLC plugin installed, which I don't recommend. The standalone VLC player is great, but the browser plugin isn't. I recommend removing or disabling VLC and Totem plugins, then installing gecko-mediaplayer.

---

