---
title: "Clear recent file list?"
date: 2012-04-24
forum: New to Ubuntu
---

### Post by nifty542 on 2012-04-24
Hi, all
I'm a teacher and often save files before transferring them to a USB memory stick.
When I am working, I often find a long list of files that I have already deleted.
I realise it's not a critical issue, but is there a way of clearing the list of recent files?
Thanks, in advance. You are all so supportive.
David

---

### Post by Cheesemill on 2012-04-24
If you're using Unity:
```
rm ~/.local/share/zeitgeist/activity.sqlite
zeitgeist-daemon --replace
```If you are using Classic UI or Gnome Shell:
```
rm ~/.local/share/recently-used.xbel
```

---

### Post by nifty542 on 2012-04-24
Hi
Thanks for the reply. I did choose Lubuntu in the drop down list, but it hasn't appeared here.
Anyway, Lubuntu 12.04.
So, I don't know if your post will help. I don't want to try until I'm sure I won't mess up my system (although I know a reinstall is easy).
Thanks
David

---

### Post by Cheesemill on 2012-04-24
It may well be the 2nd option above.

To check just navigate to the ~/.local/share/ directory and open the file recently-used.xbel with a text editor. If it doesn't exist then it's obviously not the correct file and you'll have to wait for another answer. If it contains a list of your recent files in xml format then you know it's the correct file to delete.

---

### Post by nifty542 on 2012-04-24
Hi
Thanks for the reply.
I'm about to go to sleep, have a very early start tomorrow. 
Will try this when I get back from work.
Thanks, again
David

---

### Post by nifty542 on 2012-04-24
By the way, I love Reepham!

---

