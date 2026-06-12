---
title: "QtCreator problem with linking"
date: 2009-05-31
forum: Programming Talk
---

### Post by mdurham on 2009-05-31
Hi, I want to include 'libjpeg' in the link, but can't see a way of doing this in the QtCreator IDE. There doesn't seem to be a way of linking in other libraries. If someone can tell me how to do it I'd be very grateful.
Cheers, Mike

---

### Post by haTem on 2009-06-01
You have to edit your qmake project's .pro file manually. I don't think Qt Creator lets you do this from the gui.

Have a look [[here]]("http://doc.trolltech.com/4.5/qmake-project-files.html#declaring-other-libraries"). It also may be worthwhile to look at the bit about pkg-config in the previous section.


I believe, in your case, you can get away with just adding this line to your .pro file:
```
LIBS += -ljpeg
```

---

### Post by mdurham on 2009-06-01
Thanks a lot haTem, you are exactly right. I'm duly very grateful for your advice. It seems odd that the creators of QtCreator didn't include some method of doing this. Maybe they will at some later stage??? I did search through the docs quite a bit but obviously never found the bit that you pointed out to me. I think tabs would be nice to have too.
Thanks again. Mike

---

