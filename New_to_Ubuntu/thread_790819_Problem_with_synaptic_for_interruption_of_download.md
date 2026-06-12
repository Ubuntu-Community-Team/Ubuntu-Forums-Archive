---
title: "Problem with synaptic for interruption of download"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by jontxu01 on 2008-05-11
Hy all.
I'm new with Ubuntu and I have the same problem as i see arround, when trying to download flash player for firefox I cancell th download and no Synaptic give me an error:

[COLOR="Red"]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/COLOR]

I'll try what th people arround said:

[COLOR="Red"]$ sudo dpkg --configure -a[/COLOR]

But it start to download and stay in:

[COLOR="Red"]Setting up flashplugin-nonfree (9.0.124.0ubuntu2) ...
Downloading...
--00:04:26--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 84.53.170.70
Connecting to fpdownload.macromedia.com|84.53.170.70|:80... connected.
HTTP request sent, awaiting response... Read error (Connection reset by peer) in headers.
Retrying.

--00:17:00--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
  (try: 2) => `./install_flash_player_9_linux.tar.gz'
Connecting to fpdownload.macromedia.com|84.53.170.70|:80... connected.
HTTP request sent, awaiting response... 
[/COLOR]
And stay there forever.
Any coments of what I can do about it?
Thanks in advance

---

### Post by Ebuntor on 2008-05-11
It's possible the Adobe servers are/were a little busy. I once had a similar problem and looking at the output you posted I see no reason how this could be problem with your system after entering "[COLOR=Black]sudo dpkg --configure -a" (I could be wrong though).

Maybe if you try it a while later it might download. Hope that helps. :)
[/COLOR]

---

