---
title: "I need a little help trying to view this (activex) site"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by pluckypigeon on 2008-09-17
It says not available in linux so I installed the User Agent Switcher Firefox plugin.

Now I get, run activeX disabled.

I am aware that you can't get activeX with Firefox (or maybe even with linux, but I'm not sure) but is there another way I could view this?

[http://tv.arsenal.com/](http://tv.arsenal.com/)

Thanks in advanced!!

---

### Post by melojo on 2008-09-17
The only way that I know is to use virtual box and install windows.
[http://www.virtualbox.org/](http://www.virtualbox.org/)

Someone else may have a better solution.

---

### Post by pluckypigeon on 2008-09-17
> **melojo said:**
> The only way that I know is to use virtual box and install windows.
[http://www.virtualbox.org/](http://www.virtualbox.org/)

Someone else may have a better solution.

Thanks for your quick reply. I only have windows 98. I don't really want to install that though. I'm not going to install any other Windows

---

### Post by alienexplorers on 2008-09-17
Read this page:
[http://support.mozilla.com/en-US/kb/ActiveX]("http://support.mozilla.com/en-US/kb/ActiveX")

---

### Post by tarps87 on 2008-09-17
You can try wine and wine doors. If you got to [http://www.wine-doors.org/wordpress/?page_id=3](http://www.wine-doors.org/wordpress/?page_id=3) and download the deb file this will also install wine and I believe on of the packages you can install using it is activex, you will need to install firefox or ie under wine as well.
Wine is a windows emulator and will allow you to run some windows software. It is also open source, the website is:
[http://www.winehq.org/](http://www.winehq.org/)

---

### Post by pluckypigeon on 2008-09-17
> **alienexplorers said:**
> Read this page:
[http://support.mozilla.com/en-US/kb/ActiveX]("http://support.mozilla.com/en-US/kb/ActiveX")

Thanks for your reply. I should have mentioned that I have already read that.

I was hoping that their is some other way to view the site in question though.

---

### Post by pluckypigeon on 2008-09-17
> **tarps87 said:**
> You can try wine and wine doors. If you got to [http://www.wine-doors.org/wordpress/?page_id=3](http://www.wine-doors.org/wordpress/?page_id=3) and download the deb file this will also install wine and I believe on of the packages you can install using it is activex, you will need to install firefox or ie under wine as well.
Wine is a windows emulator and will allow you to run some windows software. It is also open source, the website is:
[http://www.winehq.org/](http://www.winehq.org/)

Sorry. I took ages to reply. I already had Wine Doors but it doesn't seem to be downloading / working properly. I'll keep you posted.

---

### Post by pluckypigeon on 2008-09-17
> **pluckypigeon said:**
> Sorry. I took ages to reply. I already had Wine Doors but it doesn't seem to be downloading / working properly. I'll keep you posted.



apparently wine-doors is broken at the moment:confused:
[http://www.wine-doors.org/wordpress/?p=57](http://www.wine-doors.org/wordpress/?p=57)

---

### Post by tarps87 on 2008-09-17
Have you tried installing the windows version of firefox under wine?
```

sudo apt-get wine

```
If wine is not installed

---

