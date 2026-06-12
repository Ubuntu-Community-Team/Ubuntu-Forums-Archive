---
title: "PDF Editor works in Kubuntu, but not Ubuntu"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by njd4k on 2008-05-26
Hi,

One problem I found trying to use GNOME/Hardy was that PDFedit (called PDF Editor in the add/remove menu) doesn't work. As far as i can tell this is the only software that lets me markup PDFs with highlighting, comments and text, essential for the notetaking I like to do on PDFs of academic papers. When I try to open a PDF, a nondescript error tells me it can't.

Since I saw it was a KDE app I tried an installation of Kubuntu and in that desktop environment the program works perfectly. But I don't like KDE and don't want to keep it.

I know Linux apps are often optimized for one desktop or another, but aren't they supposed to at least run in all desktop environments? Does anybody know what might be the problem with this?

(Also, if anybody knows when GNU Juggler might start testing, I am one Linux novice who would love to try.)

Thank you
njd4k

---

### Post by Sarah L on 2008-05-26
You're right, KDE apps should be able to work even if you have GNOME as your desktop environment. However, there may be some additional dependencies that you'll have to install for KDE applications to work completely.

It would help if you could elaborate on how exactly pdfedit doesn't work - saying that it's a "nondescript error" doesn't help when you're trying to solve the problem! :)

---

### Post by njd4k on 2008-05-27
> **Sarah L said:**
> You're right, KDE apps should be able to work even if you have GNOME as your desktop environment. However, there may be some additional dependencies that you'll have to install for KDE applications to work completely.

It would help if you could elaborate on how exactly pdfedit doesn't work - saying that it's a "nondescript error" doesn't help when you're trying to solve the problem! :)

Thanks for responding Sarah. IIRC, the error said the PDFs were corrupted, which I know isn't right because they open fine in Windows and in other Linux PDF viewing programs. And they open fine in PDF Edit in Kubuntu.

I tried to reproduce the problem by installing gnome into Kubuntu, but PDF editor works, so apparently even while running gnome it has access to whatever KDE files it needs if both are installed. I'm going to go run regular Ubuntu and see what that error is...

---

### Post by njd4k on 2008-05-27
Well, I uninstalled Kubuntu/wubi and installed Ubuntu/Wubi and tried PDF Editor again. Now it's behaving differently.

I was able to open the same PDF I played with in KDE without the old error message. I don't know what was different about it. What's wrong with it now is that when I try to open scans of documents saved as PDFs in windows, the program closes without putting up any message at all. It just evaporates.

Does anybody else have this problem?

---

