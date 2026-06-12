---
title: "setting preffered video player ??"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by Tubby on 2008-05-22
I have downloaded a file through aMule but when i want to view it, i get this message below-

Please set your prefered video player on preferences.
Meanwhile, aMule will attempt to use mplayer and you will get this warning on every preview
so i click ok on the tab and get -

xterm: Can't execvp mplayer: no such file or directory.

Could someone please explain what to do.
thanks

---

### Post by atomkarinca on 2008-05-22
In the Preferences window under Directories tab there's a textbox titled "Video Player". You should specify your player there e.g. "/usr/bin/vlc" (without the quotes).

---

### Post by iaculallad on 2008-05-22
> **Tubby said:**
> I have downloaded a file through aMule but when i want to view it, i get this message below-

Please set your prefered video player on preferences.
Meanwhile, aMule will attempt to use mplayer and you will get this warning on every preview
so i click ok on the tab and get -

xterm: Can't execvp mplayer: no such file or directory.

Could someone please explain what to do.
thanks

Seems like you do not have mplayer installed. You can install it using Synaptics. Once installed, right-click on the file you downloaded through amule and select "Properties", select the "Open With" tab and select an application that could be used to play that file (i.e: mplayer if installed). A way of saying to Ubuntu that you always open this file type with this application.

---

### Post by Tubby on 2008-05-22
Ok, thanks very much.

---

### Post by atomkarinca on 2008-05-22
No problem.

---

### Post by iaculallad on 2008-05-22
You're welcome. Go Ubuntu

---

### Post by peteragardi on 2008-08-01
This is for watching previews... Could someone guide me through how to change my video player preferences in amule? I have mplayer as default, but it's not letting me scroll through the selected preview.

---

