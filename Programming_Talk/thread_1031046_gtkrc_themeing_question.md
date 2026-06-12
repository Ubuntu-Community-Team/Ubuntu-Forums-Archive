---
title: "gtkrc themeing question"
date: 2009-01-04
forum: Programming Talk
---

### Post by | MM | on 2009-01-04
Hi,

I am editing the Clearlooks Human gtkrc, incorporating some Aurora aspects that i like.  So my theme is Clearlooks based with aurora bits added.  I would like to know how to override the style of the following widgets:

1) I would like to override the side arrow widget style in menuitmes.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=98779&stc=1&d=1231130755[/IMG]
Note that i have already setup my own style for ```
class "GtkArrow"     style "clearlooks-arrow"
```

2) I would also like to override the style for the panel separator you see below
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=98780&stc=1&d=1231130755[/IMG]

So if someone could let me know what class i need to override to affect style changes for the aforementioned widgets it would be much appreciated.

---

### Post by mike_g on 2009-01-05
I made my own custom theme and IIRC they were stored as PNGs in some directory. Unfortunatly I forgot what the directory was and I'm not on a ubuntu machine atm to check. Although each theme had a its own image directory named after it so you if could locate the directory named after ther theme you should be able to find where the images are stored and modify them. Thats what I did at least.

---

