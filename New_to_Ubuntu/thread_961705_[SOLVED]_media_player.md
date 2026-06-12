---
title: "[SOLVED] media player"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by johntravis on 2008-10-28
I have the totem player installed with gstreamer. I installed totem-xine thinking it would be better. When I use the player totem comes up but which one-- gstreamer or xine. Does it matter or should I remove one? Trying to understand but need to ask questions.

---

### Post by mc4man on 2008-10-28
With the player open click on help -> about. Will say either Movie Player using xine-lib version 1 or using gstreamer ...

If you go -> right click on Applications -> edit menus -> highlight sound & video you should see Movie player enabled as a menu item (default totem)
There should also be separate choices for '*Movie player *(xine)" and '*Movie player* (gstreamer)'.

Odds are totem-gstreamer is the 'default', so enable the totem-xine one in edit menus.

you can change the default totem player to totem-xine though some recommend leaving the default at totem-gstreamer.

To change if you wish run in terminal and choose 2
```
sudo update-alternatives --config totem
```

You can leave totem-gstreamer as the default totem but add totem-xine as a choice for default dvd player (autorun) - let me know

---

### Post by johntravis on 2008-10-28
Right clicked on applications> clicked on edit menus> left pane sound&video, right pane showed both movie player's but neither were clicked so I clicked oh movie player-xine, now when I go into application> sound&video it shows movie player-xine v-1.1.11.1.  I never had sound playback before, now I do but at a reduced volume so I right clicked the volume control icon and raised the volume from 80% to 100% (at 80% could not here movie,at 100% audible but low. If you can help with the volume,great, if you cannot that is ok for you have helped me,and other whom are reading this post,immencely
THANK YOU FROM ALL OF US.

---

