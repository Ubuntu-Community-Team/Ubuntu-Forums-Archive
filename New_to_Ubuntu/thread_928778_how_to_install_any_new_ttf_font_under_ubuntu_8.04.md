---
title: "how to install any new ttf font under ubuntu 8.04"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by kshmya on 2008-09-24
Hello there,

I am trying to read news through [www.gujaratsamachar.com](www.gujaratsamachar.com) using forfox under ubuntu. but i am unable to . I need to download font " gopika.ttf" and i did that on desktop but dont know how to take this font under ubuntu . Can ne one help me for the same.

---

### Post by anotherdisciple on 2008-09-24
This should have everything you need to know...

[https://wiki.ubuntu.com/Fonts]("https://wiki.ubuntu.com/Fonts")

---

### Post by billgoldberg on 2008-09-24
create a new folder called

> .fonts

in you home directory.

*(don't forget the dot. You'll need to press "ctrl+h" afterwards to see the hidden folder).*

Paste the font in there and it's installed.

---

### Post by ellalan on 2008-09-24
Hi
Download the font to your Desktop.
Press Alt+F2, Enter gksudo nautilus then navigate to .fonts folder, find ttf fonts folder and copy your gopika.ttf and paste in the ttf fonts folder.
usr/share/fonts/ttf fonts. HTH.

---

### Post by Dan_Dranath999 on 2008-09-24
I have +2000 fonts, (can't install all of them - i assume that massive number of fonts loading, would crash the system or at least make it unstable or really slow)

I use a font manager to activate/deactivate the fonts i need in a project, without having to install them.

Download FontMatrix from getdeb.net

[http://www.getdeb.net/search.php?keywords=font](http://www.getdeb.net/search.php?keywords=font)

---

### Post by kshmya on 2008-09-28
> **anotherdisciple said:**
> This should have everything you need to know...

[https://wiki.ubuntu.com/Fonts]("https://wiki.ubuntu.com/Fonts")
I read the link you provided but no luck . would appreciate if help if possible

---

### Post by steveneddy on 2008-09-28
> **kshmya said:**
> I read the link you provided but no luck . would appreciate if help if possible

See post #3 from billgoldberg

---

### Post by engtg on 2008-09-28
Has anyone tried font install in Application-Other-Fonts Installer before and how does this work.[IMG]http://ubuntuforums.org/attachment.php?attachmentid=86687&stc=1&d=1222643668[/IMG]

---

### Post by kshmya on 2008-09-28
i did as per the post  #2 , #3 from billgoldberg and also as per post # 4 but no luck

---

### Post by kshmya on 2008-09-28
how did you get configure - KDE control  moduole

---

### Post by steveneddy on 2008-09-28
OK

Simply open your /home folder.

Hit the ctrl+h keys and search for a folder named

**.fonts**

with the dot at the beginning.

If it is not there, create it.

Right click inside of your /home folder and select Create Folder

Name it **.fonts**

Now open that folder and drag your font from the desktop to that folder.

Close the folder and your /home folder.

Open a terminal and type

```
fc-cache -fv
```Now open up the application that you needed the font in and it should work.

---

### Post by Surkow on 2008-09-28
> **kshmya said:**
> i did as per the post  #2 , #3 from billgoldberg and also as per post # 4 but no luck

Reload your font cache. This can be done with this command:

```
sudo fc-cache -fv
```

Or you can just restart your pc.

---

### Post by kshmya on 2008-09-28
I am using GNOME and trying to read [www.gujaratsamachar.com](www.gujaratsamachar.com) using firefox under ubuntu

---

### Post by kshmya on 2008-09-28
Trust me man I did that. Exactly the same.

---

