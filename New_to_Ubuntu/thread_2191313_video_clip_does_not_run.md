---
title: "video clip does not run"
date: 2013-12-02
forum: New to Ubuntu
---

### Post by Matrix01 on 2013-12-02
i clicked a video clip which is saved in dwonload file, but this does not work. anyhelps??

---

### Post by rabbyx7xafc on 2013-12-02
more details will be helpful... what is the extension of the video file...? do you have ubuntu restricted extras installed? which software are you tyring to open the video file in?

---

### Post by Matrix01 on 2013-12-02
[ATTACH=CONFIG]248268[/ATTACH][ATTACH=CONFIG]248267[/ATTACH]
when this video file is clicked, this shows up,
and file ext, is webm.

i am not sure restricted extra is installed.
i clicked ok, but none happened, so closed terminal.
this Lubuntu has Audacious.

---

### Post by rabbyx7xafc on 2013-12-02
install restricted extras and vlc media player. and you should be fine... vlc can play all formats out there.... i myself have played .webm with vlc.....

---

### Post by oldos2er on 2013-12-02
> **Matrix01 said:**
> [ATTACH=CONFIG]248268[/ATTACH][ATTACH=CONFIG]248267[/ATTACH]
when this video file is clicked, this shows up,
and file ext, is webm.

i am not sure restricted extra is installed.
i clicked ok, but none happened, so closed terminal.
this Lubuntu has Audacious.

If you just closed the terminal, restricted-extras hasn't fully installed. Run ```
sudo dpkg --configure -a
``` and when the EULA comes up again, use the Tab or arrow keys to highlight "Ok", then press Enter.

---

### Post by BenjaminCHILOE IS. on 2013-12-02
Hi Matrix01,

I agree I would install VLC from the icon Software Center, that very complete  media app will do fine supporting lots of video codecs necessary to run DVDs or CDs or Flash web vids

The best

---

