---
title: "VLC closes/crashes when mouse is on renderer setting."
date: 2018-03-16
forum: New to Ubuntu
---

### Post by crip720 on 2018-03-16
Have installed VLC 3 by snap in Ubuntu 16.04 to try the casting.  Have been using vlc 2.  VLC 3 seems to work well except when I move the mouse over the renderer setting(no clicking), it then closes/crashes.  Moving mouse over any other setting does not do this and it happens on if vlc is playing a video or is just open with nothing playing or selected.  I have vlc 3.01.  Casting works well with chrome's videostream app.  Do you need more info or does anybody know how to fix this problem.  Renderer is on the playback drop down.  Thank you  Colin.

---

### Post by hibby2 on 2018-03-18
Hey there crip,

This is a known bug in Debian: [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=893284](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=893284)

It's a bug with package libmicrodns0, and it has been fixed upstream so it shall be fixed on the next package upload to Debian/Ubuntu.

---

### Post by crip720 on 2018-03-19
Thanks, looked into the ppa's but they seem to only have vers 2 and vers 4. Snap seems to be the only way right now.  Guess I wait.

---

