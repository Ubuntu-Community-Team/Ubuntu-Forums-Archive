---
title: "Link content directory"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by dominik_ap on 2008-05-09
Hello,
I'd like to have content of one directory linked in other directory.

Let's say that I have /home/data/images/wallpapers/ and there i have directories: art, unsorted, linux...

I d like to have images from these directories in /usr/share/wallpapers/ as links.

I tried 
```

sudo ln -s /home/data/images/wallpapers/art /usr/share/wallpapers

```but it created symlink /usr/share/wallpapers/art -> /home/data/images/wallpapers/art
I wanted to have the content of /home/.../art in /usr/share/wallpapers/


Or help me in other way:
I am using Kubuntu and when user wants different wallpaper, they are listed from /usr/share/wallpapers and from /home/user's_home/.kde/share/wallpapers/ , I want to show him wallpapers from /home/data/images/wallpapers/art linux unsorted and others..
How to do it? Don't you know?


Thank you very much
Dominik Franek

---

### Post by dominik_ap on 2008-05-09
Help, is here somebody who will read this thread???

Thanks

Dominik

---

