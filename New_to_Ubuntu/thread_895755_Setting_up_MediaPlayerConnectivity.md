---
title: "Setting up MediaPlayerConnectivity"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by k1ngb0b0 on 2008-08-20
I heard MPC is a good plugin to have for linux because it can help you play quicktime movies etc.  I'm having trouble setting it up though.  When I go to choose which player I want to use for each different video type, I don't know how to choose which one I want.

I'm a long time windows user and just recently started using Ubuntu...I use the 'browse' button to look for the directory with the player program (usually Vlc.exe in windows) but I have trouble finding it.

I have a shortcut for VLC on my desktop and when I see the code used to launch it, it says "vlc %U".  I tried that in the 'player location' area and I still cannot get it to play.

I'm not sure if this is the right forum to use for this message, but the reason I put it in absolute beginning is I'm not sure how to do something basic (path to a program).



Any help would be greatly appreciated.

---

### Post by pi.boy.travis on 2008-08-20
I have never worked with MPC, but it sounds like you need the binaries for VLC.  .exe files do not work in Linux, unless you use WINE or another compatibility layer.  The VLC player is in the repositories.  You can install it via: Applications-Add/Remove (I am speaking of the GNOME menu that should be in the upper left hand corner by default.

Hope this helps!

---

### Post by k1ngb0b0 on 2008-08-20
Well I use VLC fine by itself.  Would I still need those things if I can use VLC?

---

### Post by philinux on 2008-08-20
/usr/bin/vlc

---

### Post by pi.boy.travis on 2008-08-20
If you want to play quicktime movies, there are GStreamer plugins in the repositories.  I think that they may also be in the ubuntu-restricted-extras package.  You can install any of these with the synaptic package manager.  It is in System-Administration-Synaptic package manager.

Hope this helps!

---

### Post by k1ngb0b0 on 2008-08-20
> **philinux said:**
> /usr/bin/vlc


That's exactly what I was looking for, thanks! :)

For some reason I can't play videos from gametrailers.com though, it's so irritating!

I go to this link [http://www.gametrailers.com/player/38592.html](http://www.gametrailers.com/player/38592.html) and the video would just not play.  I got the MPC addon for firefox thinking it would help and it doesn't.

youtube videos work fine, and videos from megavideo.com work fine, I've just NEVER been able to get gametrailers to work and I don't knwo why.

I have gstreamer installed, and I have the restricted extras installed.

Using the quote above, I configured MPC to open VLC to play the movie from my link; VLC opened and then did not play it.



I have no idea how to get these to work but it's really frustrating.

---

### Post by philinux on 2008-08-20
That link is flash video.

Install ubuntu-restricted-extras either from synaptic or terminal

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by k1ngb0b0 on 2008-08-20
I already had the restricted extras installed already and still cannot play the videos.

---

### Post by philinux on 2008-08-20
Type this into the firefox address bar.

```
about:plugins
```

Post the output.

---

### Post by mikewhatever on 2008-08-20
> I go to this link [http://www.gametrailers.com/player/38592.html](http://www.gametrailers.com/player/38592.html) and the video would just not play. I got the MPC addon for firefox thinking it would help and it doesn't.


That only needs adobe flash player, plays fine here.

---

### Post by philinux on 2008-08-20
> **mikewhatever said:**
> That only needs adobe flash player, plays fine here.

Ok Mike we know that, any solution to this guys problem? He's got restricted-extras installed too.

---

### Post by k1ngb0b0 on 2008-08-20
This is the output of about:plugins

application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

---

### Post by mikewhatever on 2008-08-21
> **philinux said:**
> Ok Mike we know that, any solution to this guys problem? He's got restricted-extras installed too.

Well, VLC and MPC were mentioned in the same post, so I thought I'd mention you didn't need them for the provided link. I've not the slightest idea why it wouldn't play on OP's machine. :confused:

---

### Post by k1ngb0b0 on 2008-08-21
It's weird because other video sites always work, but never gametrailers.com

---

