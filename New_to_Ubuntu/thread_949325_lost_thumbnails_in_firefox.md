---
title: "lost thumbnails in firefox"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by LeftNut on 2008-10-16
Hey all,

       I was browsing around on gnome-look.org everything was going fine till I pressed something and I lost all the thumbnail previews on that site and a few others. If anyone knows what I did or how to reverse it. That would be very appreciated.

Thank you,
Gary

---

### Post by LowSky on 2008-10-16
backup your bookmarks, then got to you home folder and delete the .firefox folder, restart firefox reimport your bookmarks and all should be back to normal

---

### Post by LeftNut on 2008-10-16
> **LowSky said:**
> backup your bookmarks, then got to you home folder and delete the .firefox folder, restart firefox reimport your bookmarks and all should be back to normal
i dont have a .firefox folder in my home folder. is there anywere else this could be? i did a search and it came back with several firefox folders through out the system.



Thank you,
Gary

---

### Post by handydan918 on 2008-10-16
> **LeftNut said:**
> i dont have a .firefox folder in my home folder. is there anywere else this could be? i did a search and it came back with several firefox folders through out the system.



Thank you,
Gary
I think lowsky meant  the .mozilla directory. Keep in mind that all filenames prepended with a "." are hidden.
If you can't find it open a terminal and do ```
cd
```
and then ```
ls -a
```

---

### Post by Irony on 2008-10-16
He means the .mozilla folder, i.e go to your home folder press ctrl+h to reveal hidden folders then delete the .mozilla folder.

Make sure you export your bookmarks first though, i.e. bookmarks > organise bookmarks > import and backup > export html

By deleting your mozilla folder you'll delete any errors in it. When you start up firefox it will be created again in its default mode - you then import your exported bookmarks.

---

### Post by handydan918 on 2008-10-16
I'm not sure all of this addresses the post. Losing thumbnails isn't the same as losing bookmarks.

---

### Post by LeftNut on 2008-10-16
> **handydan918 said:**
> I think lowsky meant  the .mozilla directory. Keep in mind that all filenames prepended with a "." are hidden.
If you can't find it open a terminal and do ```
cd
```
and then ```
ls -a
```

ya deleting he modzilla folder worked for me.


thank you very much,
Gary

---

