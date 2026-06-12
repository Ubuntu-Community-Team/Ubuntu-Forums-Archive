---
title: "video player for 16.04"
date: 2016-11-15
forum: New to Ubuntu
---

### Post by wfriedwaldgmail.c on 2016-11-15
I just installed / upgraded to 16.04.

I had planned to install VLC, but I gather that this is only supported (by VideoLan) up to Ubuntu 13.10.

Can anyone recommend a VLC-like player for the OS?  something that handles pretty much every video format (MP4, MPG, MOV, MKV, AVI etc) ??

thanks very much in advance,

W

---

### Post by howefield on 2016-11-15
VLC is available to install from the 16.04 repositories. If you are not averse to using the terminal, use the following..

```
sudo apt update
```
```
sudo apt install vlc
```

---

### Post by wfriedwaldgmail.c on 2016-11-15
yes! that worked very well.

thanks very much!

w

---

### Post by howefield on 2016-11-15
Indeed, it would and you're welcome.

Feel free to mark the thread as solved.

---

### Post by ajgreeny on 2016-11-15
> **wfriedwaldgmail.c said:**
> I just installed / upgraded to 16.04.

I had planned to install VLC, but I gather that this is only supported (by VideoLan) up to Ubuntu 13.10.
W

I'm curious; where did you get the info that VLC was not supported beyond 13.10?

VLC has been my #1 choice as video player for many years and has almost never let me down.  The only files it can't play, as far as I'm aware, are a few proprietary file-types from such things as CC security cameras.

---

### Post by SeijiSensei on 2016-11-16
I've used SMPlayer rather than VLC for many years now.  These days I use mpv as the player engine rather than mplayer.  I generally use Doug McMahon's versions of these programs; for 16.04 see [https://launchpad.net/~mc3man/+archive/ubuntu/xerus-media](https://launchpad.net/~mc3man/+archive/ubuntu/xerus-media) plus [https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests](https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests) for mpv.

For those like me that are still using 14.04, there's [https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media](https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media)

---

### Post by deadflowr on 2016-11-16
> **ajgreeny said:**
> I'm curious; where did you get the info that VLC was not supported beyond 13.10?

VLC has been my #1 choice as video player for many years and has almost never let me down.  The only files it can't play, as far as I'm aware, are a few proprietary file-types from such things as CC security cameras.

videolan actually builds a snap daily vlc.
```
sudo snap install vlc
```
will bring in the daily build as a snap package on 16.04+.

(Note I used the cli, as I have no idea what the state of installing it through the Ubuntu Software is, since the software center requires users to sign in with their U1 accounts and had been broken for some time on the Ubuntu Software)

---

### Post by ajgreeny on 2016-11-16
Like deadflowr, I have no idea about Ubuntu-software for installing packages either as I use cli or synaptic.
I never ever used the Software-centre either since whenever it was that it replaced synaptic, as it does not offer every package in such a brilliantly searchable manner as synaptic does.

---

