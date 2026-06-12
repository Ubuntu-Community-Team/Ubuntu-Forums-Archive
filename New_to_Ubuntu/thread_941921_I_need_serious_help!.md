---
title: "I need serious help!"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by neonjuice on 2008-10-08
Hi Folks.

Well i got me in a mess. I was installing the Avant windows dock and was following the instructions to delete the bars so the dock would be on its own. Here is the guide i was using [http://news.softpedia.com/news/Install-AWN-on-Hardy-Heron-82611.shtml](http://news.softpedia.com/news/Install-AWN-on-Hardy-Heron-82611.shtml)

So any I was a tip 3 and well I forgot to add the items from my top nav bar to my dock and now they have all vanished and I cant get em back. I cant access anything but the internet. All i get when i log on is the avant dock and my background image. I am new to linux and really messed this up. How can i resolve this issue?. I need help. :(

I have the latest relase of Ubuntu Hardy. 

Please help me. Thank you.

---

### Post by mikewhatever on 2008-10-08
Try alt+f2, and if a line appears, type gnome-panel.

---

### Post by maybeway36 on 2008-10-08
What you might be able to do is:
1. Press Ctrl+Alt+F1
2. Log in to the terminal
3. Trype ```
rm -rv .gnome* .gconf*
```
4. Reboot the computer
This removes any customizations you have made to GNOME.

---

### Post by abrianb on 2008-10-08
try this
[http:///answers.launchpad.net/ubuntu/+source/gnome-panel/+question/3179]("http://answers.launchpad.net/ubuntu/+source/gnome-panel/+question/3179")

---

