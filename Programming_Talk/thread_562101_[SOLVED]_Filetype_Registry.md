---
title: "[SOLVED] Filetype Registry"
date: 2007-09-28
forum: Programming Talk
---

### Post by Kenobi on 2007-09-28
Hi,

which file in Ubuntu stores which extension (e.g. .mp3) opens with which programs (e.g. vlc, totem, with totem being the default) ???

---

### Post by LaRoza on 2007-09-28
Linux doesn't use file extensions, it goes by file type.

Open a terminal, and use the command "file" followed by a file or directory. It will detect the file type no matter what the exension is, unlike Windows.

I think in is in preferences->prefered applications, but I am not sure, I don't use GNOME.

---

### Post by amendt on 2007-09-28
In your file manager (Nautilus) right click on the file and go properties. From there you can select which program to use for a specific file extention.

---

### Post by Kenobi on 2007-09-28
yeah, I know you can go and use nautilus, this is exactly what I mean. Thanks for mentioning file, it is a surely interesting part I'll have a look at. But I need that information of nautilus...

Where does nautilus *STORE* that information? I'm writing a program and it can't just open and click into nautilus, it needs the exact file of that information in ubuntu.

---

### Post by Perfect Storm on 2007-09-28
Thread moved. Better chance you getting the right help here with your problem.

---

### Post by mssever on 2007-09-28
See the files /etc/mailcap and /etc/mime.types. Nautilus probably stores changes from the system-wide defaults in gconf somewhere.

---

### Post by Kenobi on 2007-09-29
Hi,

thanks alot mssever, that's exactly what I needed. I found that the user specific data is stored in /home/[usr]/.local/share/applications/.

thanks to everyone who participated in this thread!

---

