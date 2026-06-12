---
title: "Vlc does not play disc automatically"
date: 2014-07-28
forum: New to Ubuntu
---

### Post by monkeybrain20122 on 2014-07-28
I guess this is really a question about thunar rather vlc. 

In Ubuntu when I insert an audio CD or a Video DVD and open with vlc it will play automatically (if vlc is set to be the default application it will popup and play automatically when media is inserted), but in Xubuntu vlc would just open and do nothing, one has to choose open Disc and play from the menu. Is there something that can be done so it would play media automatically like in Unity or gnome?

xubuntu 14.04

Thanks.

---

### Post by Dennis N on 2014-07-28
My Xubuntu 14.04 will autoplay a CD with Parole by default when a disk is inserted into the drive. I don't have a DVD handy to test right now. I can change the player to audacious in Settings > Removable Drives and Media > Multimedia Tab and then audacious autoplays the CD. Did you use that to set VLC to autoplay?

The command I used was [FONT=Courier New]**audacious cdda://**[/FONT]

---

### Post by monkeybrain20122 on 2014-07-28
Hi,

Changing the command from /usr/bin/vlc to /usr/bin/vlc cdda:// ( or just "vlc cdda://" for audio CDs) and /usr/bin/vlc dvd:// (for video DVDs) work now. In Natulilus just need to choose vlc from the drop down.

Thanks. I will mark this as solved.

---

### Post by mc4man on 2014-07-28
> **monkeybrain20122 said:**
>  In Natulilus just need to choose vlc from the drop down.

The one thing that has bugged me in Ubuntu is that while vlc can be set to auto play audio cd's is that when opened that way vlc never retrieves cddb info. 
(maybe it's just me...

To alter that I had to create a .desktop just for vlc auto play on cd's & set that as the default.

---

### Post by Dennis N on 2014-07-28
> **mc4man said:**
> The one thing that has bugged me in Ubuntu is that while vlc can be set to auto play audio cd's is that when opened that way vlc never retrieves cddb info. 
Neither does Parole, but Audacious does retrieve the cddb information.

---

### Post by Dennis N on 2014-07-29
Autostart CD play with Parole:
In Xubuntu 14.04, autostart of the music player Parole does not work when a CD is inserted into the drive unless the command is changed:

In: Settings> Hardware> Removable Drives and Media> Multimedia Tab> Audio CDs 
change: 
```
parole --device=%d
``` to 
```
parole --device=% cdda://
```
Parole now autostarts when a CD is inserted.
Bug report:
[https://bugs.launchpad.net/ubuntu/+source/parole/+bug/1322384](https://bugs.launchpad.net/ubuntu/+source/parole/+bug/1322384)

---

### Post by mc4man on 2014-07-30
For vlc I create a new .desktop such as - 
```
[Desktop Entry]
Version=1.0
Name=VLC Cd Player
Comment=Auto plays audio cd's
Exec=vlccd %U
Icon=vlc
Terminal=false
Type=Application
Categories=AudioVideo;Player;
MimeType=x-content/audio-cdda;
```

For a single drive the Exec= could be specific, such as Exec=vlc cdda:///dev/sr0
In the above case it's for multiple drives so I use a script in $PATH (vlccd

```
#!/bin/bash
CD=/dev/`echo $1|sed -e "s/.*\(sr[0-9]\).*/\\1/"`
vlc cdda://$CD
```

---

