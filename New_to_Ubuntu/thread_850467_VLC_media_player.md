---
title: "VLC media player"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by Norm24 on 2008-07-05
This probably will have an extremely obvious answer.

How do I make VLC the default player?

---

### Post by TeoBigusGeekus on 2008-07-05
Just right click the file with which you want vlc to be associated and select open with vlc. From there on these types of files will be opened with vlc.

---

### Post by sayakb on 2008-07-05
System->Preferences->Preferred Applications->Multimedia
Select **VLC Media Player**, or if not available, select Custom and type in *vlc* in the box.

---

### Post by silkstone on 2008-07-05
Will that make VLC the default player for DVD, or do you have to edit /etc/gnome/defaults.list and change totem.desktop to vlc.desktop in the x-content/video entries?

---

### Post by crysys on 2008-07-05
> **silkstone said:**
> Will that make VLC the default player for DVD, or do you have to edit /etc/gnome/defaults.list and change totem.desktop to vlc.desktop in the x-content/video entries?

No, it does not.  Your suggestion however just scratched a long standing itch of mine.  Thank you.

---

### Post by silkstone on 2008-07-05
Thanks crysys.

So just to confirm...

To make VLC the default DVD player in Hardy, open a Terminal and...

```
gksudo gedit /etc/gnome/defaults.list
```

Press Ctrl+f and search for "x-content/video", then change the "totem.desktop" entries to "vlc.desktop". Save this and exit.

---

### Post by rburkartjo on 2008-07-05
silk, though i didnt start this thread tks for the info i was looking for this/cheesemaker

---

### Post by Norm24 on 2008-07-05
> **silkstone said:**
> Thanks crysys.

So just to confirm...

To make VLC the default DVD player in Hardy, open a Terminal and...

```
gksudo gedit /etc/gnome/defaults.list
```

Press Ctrl+f and search for "x-content/video", then change the "totem.desktop" entries to "vlc.desktop". Save this and exit.

That's just what I did.

---

