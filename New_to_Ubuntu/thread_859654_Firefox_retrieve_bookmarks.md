---
title: "Firefox retrieve bookmarks"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by raedbenz on 2008-07-14
Hi,,
the bookmarks of firefox , in which are they saved ?

thanks

---

### Post by scragar on 2008-07-14
~ = home directory
* = depends, you may have more than 1 folder matching actualy, latest modified by date = one you want.

~/.mozilla/firefox/*.default/bookmarks.html

---

### Post by raedbenz on 2008-07-14
> **scragar said:**
> ~ = home directory
* = depends, you may have more than 1 folder matching actualy, latest modified by date = one you want.

~/.mozilla/firefox/*.default/bookmarks.html
hi

how can i access this path.
i get errors when i type 
```
cd /*.defaults
```

thanx

---

### Post by scragar on 2008-07-14
use ```
ls -l
```
to find the files, your looking for the one ending in .default with the latest modified date.

---

### Post by raedbenz on 2008-07-14
> **scragar said:**
> use ```
ls -l
```
to find the files, your looking for the one ending in .default with the latest modified date.

hi, i cant copy the the whole folder ".default" i get errors "error while copying" .
is there a specific file i only need it? or i can change permissions to copy it?
thanks

---

### Post by scragar on 2008-07-14
huh? there isn't a single folder called .default, you have a few with names like:
**0366lv64.default** or **7r2067zq.default** etc.

inside should be a file called bookmarks.html, that's your bookmarks.

Just realised firefox has an export bookmarks option for you as well, if that's any better:
**Bookmarks > Organise Bookmarks**
click **import and Backup**, then choose **Export as HTML**

---

### Post by estyles on 2008-07-14
The file is "bookmarks.html", in ~/.mozilla/firefox/*.default
where '*' is some apparently random string of characters.

Just in case you're having trouble getting to there, open up a terminal window and type the following: 
```
cd ~/.mozilla/firefox
ls

```

That ls will show you a list of the files and directories.  The one you want ends in .default.  Lets say yours is called 8blahblah.default.  Then, while still in the firefox directory type ```
cp 8blahblah.default/bookmarks.html *destination*
``` Replace *destination* with the place you want to copy it to.

---

### Post by raedbenz on 2008-07-14
> **estyles said:**
> 
That ls will show you a list of the files and directories.  The one you want ends in .default.  Lets say yours is called 8blahblah.default.  Then, while still in the firefox directory type ```
cp 8blahblah.default/bookmarks.html *destination*
``` Replace *destination* with the place you want to copy it to.

usually what is the size of this file "bookmarks.html"?
thanks

---

### Post by scragar on 2008-07-14
depends entirely on the bookmarks you have stored, the more bookmarks the bigger the file, it's unlikly to be anything more than a few kb in size though.

---

### Post by cariboo on 2008-07-14
It might be way easier just to export your bookmarks. If you are using Firefox 3 got to Bookmarks-->organize Bookmarks-->Import and Backup-->Export HTML. Save the file as <filenamer>.html where filename is the name you give to the file.

Jim

---

### Post by raedbenz on 2008-07-14
> **scragar said:**
> depends entirely on the bookmarks you have stored, the more bookmarks the bigger the file, it's unlikly to be anything more than a few kb in size though.

mine is 7kb,,,
but the thing is i did "right click --> properties" and the date for modification and access  is old. and i have added bookmarks the last time yesterday.
thanx

---

