---
title: "I can't see picture in libreoffice when inserting them from files"
date: 2013-05-11
forum: New to Ubuntu
---

### Post by Jonatan Formentera on 2013-05-11
Hi, I have Ubuntu and use libreoffice. When I insert a picture or a chart I can't see it. I can just see the frame. I thought it was a problem of my former Ubuntu 11.10, but I've just upgraded it ro Ubuntu 12.04 and the problem goes on. Can anyone help me? Thanks

---

### Post by pfeiffep on 2013-05-11
I'm using Libre Office 4.0.2.2, Ubuntu 13.04 (gnome session fall back) and when I insert a picture from file on a new text document the picture show up jest fine. 

Which Libreoffice version?

Possiby graphics card?

---

### Post by Jonatan Formentera on 2013-05-11
I don't know which version. I have had a look at it and I've found that:
 LibreOffice 3.5.7.2 
Build ID: 350m1(Build:2)
It just happens with the text processor, with Libre calc I don't have any problem
Regards

---

### Post by col48 on 2013-05-11
Jonatan

I reckon I have the same version of LibreOffice as you, in 64bit Precise.

If I open a New document and do Insert > Picture > from File and select (as it happens) a .bmp, the picture appears in place
If I insert a frame (on a new page so I can see it) and (with the frame selected) try to insert a picture, it doesn't do anything
If I insert a frame (on a new page so I can see it) and click outside the frame to deselect it, then click inside (as if I am about to type text) and then insert a picture, it appears as you'd want it (very small unless you sized the frame first!)

I guess you were doing the second of these - try the last.

---

### Post by Jonatan Formentera on 2013-05-11
No, that's not the problem. I've tried it and is the same. The problem is when I try to do: insert>picture>from file and insert a picture. It appears a frame with the inscription: "graphics" in it. I have another lap top and it works perfectly. It must be some kind of little problem with my computer

---

### Post by Impavidus on 2013-05-11
Go to Tools > Options
Select LibreOffice Writer > View
Toggle Graphics and objects

Graphics can be switched off. Maybe you just need to switch them on again.

---

### Post by col48 on 2013-05-11
Jonatan

Maybe this is it? I can stop pictures loading into LibreOffice Writer by unsetting an option.
Tools > Options then picking the LibreOffice Writer heading then unchecking all the boxes under Display gives (if this attachment in the forum has worked!) 

[ATTACH=CONFIG]242469[/ATTACH]

I suspect it's only the graphics one that matters.

If I now insert a picture I get a frame with the text 'graphics1' inside, which sounds like what you have.

So if this is it, then what you'd need to do is go to this option and check the boxes.

Having just done that myself, the picture I just tried to insert appeared immediately, replacing the text.

Hope it works for you.

Impavidus beat me to it!!

---

### Post by Jonatan Formentera on 2013-05-11
Every thing ok. I have activeted Graphics Display from tools-options
Thanks to everyone

---

