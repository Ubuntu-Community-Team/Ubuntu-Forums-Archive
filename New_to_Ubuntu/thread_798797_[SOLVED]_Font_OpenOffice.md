---
title: "[SOLVED] Font OpenOffice"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by Stargazer989 on 2008-05-18
I've added some fonts system-wide using [this tutorial]("http://www.ubuntu1501.com/2007/07/how-to-install-ttf-font-in-ubuntu_11.html") but when i try and use the font in OpenOffice i can't find it! any ideas ?

---

### Post by Stargazer989 on 2008-05-18
will no one answer my dilema ?

---

### Post by forestpixie on 2008-05-18
Try logging out and back in and waiting for people to answer, 15 minutes is probably 23 hours too soon to be bumping a thread

---

### Post by Stargazer989 on 2008-05-18
sorry about that. i just need to type a few things up.

---

### Post by ajgreeny on 2008-05-18
Why not cheat as I have done.  I used to use KDE which makes adding system wide fonts dead easy so I take a leaf out of their book and install **kcontrol,** the kde control centre, I know, it adds all sorts of kde libraries, but so what.  I can then use the font installer in that to add all the fonts I want or need.

Dead easy.  Why can't gnome make it similarly easy?

---

### Post by Stargazer989 on 2008-05-18
well actually, im not sure if i downloaded it or not but i have kcontrol. unfortunately that does not solve my OpenOffice problem, unless i am misinterpreting.

---

### Post by forestpixie on 2008-05-18
Thought you were sorted - when I put my fonts on my system I don't put them in /usr
I make a folder in my home to put them and have never had a problem. The folder needs to be hidden, so make the directory

```
mkdir  ~/.fonts
```

Open nautilus and then Ctrl+H to view hidden files

copy the fonts into your new folder and then

```
sudo fc-cache -f -v
```

You might need to logout I'm not sure, I do it usually right at the beginning of a reinstall so am rebooting anyway.

---

### Post by Stargazer989 on 2008-05-18
ok here's the thing; i have the folder already. ive done```
sudo fc-cache -f -c
```
also, with the tutorial ive been using (there's a link in the original post) ive hadn't any troubles.

---

### Post by forestpixie on 2008-05-18
Yea - saw your link, that makes a folder in /usr/share - mine is in your /home - I've never had a problem with fonts in OO when using .fonts

If you haven't got a problem now can you mark thread as solved.

---

### Post by Stargazer989 on 2008-05-18
the main thing was to get it so that i could make a *.pdf out of it. unknowingly Text Editor could print to file as a *.pdf i was trying to use the Monospace10 font, i found something that resembled it in:
```

/usr/share/fonts/truetype/ttf-bitstream-vera

```
named: vera.ttf or Veramono.ttf

---

### Post by ajgreeny on 2008-05-18
Just as a final point in this discussion, if you want the fonts to be available in OO you need to shutdown OO completely, including the Quickstart button in the system tray.  If you do not shut that down, OO is still running and will not see the fonts until you do so, or reboot.

---

### Post by Stargazer989 on 2008-05-18
i hate to drag this on, but could you explain how i would exit the quickstart in the system tray, cause i can't see it in the system tray.

---

### Post by ajgreeny on 2008-05-19
Perhaps you haven't got it running; you need to set it up in the OO options.  Just look in System monitor to see if you have soffice and sofice.bin running.  If not there is no OO running on your machine.

---

