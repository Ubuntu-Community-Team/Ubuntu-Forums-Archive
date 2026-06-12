---
title: "empathy-chat eating (causing high) CPU"
date: 2011-06-21
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by jfernyhough on 2011-06-21
Since my clean install empathy is screwing with me. While I'm grateful I can log in, whenever I open a chat window empathy-chat jumps to 100% CPU and stays there. If I do nothing else I can $ killall empathy-chat, or $ kill -9 PID and get out, but if I open a menu I lose keyboard input. Sometimes I can CTRL-ALT-F1 to a console, other times I need to REISUB.

I've tried removing ibus, disabling logging and spell checking, and I'm stuck for ideas. Pidgin works fine (as does Gmail chat, completely unsurprisingly).

I've tried all other GTK3 themes I have available (including Ambiance, Radiance, Zukitwo), and tried with Compiz, Metacity and Mutter. All the same. :(

I've had a look using empathy-debugger but can't see anything obvious that happens when I open a new chat. Does anyone have any ideas where to start looking for the cause of this?

---

### Post by terry_gardener on 2011-06-21
i have similar problem when i try and use the new chat it opens the window and then nothing happens.

---

### Post by TechKing89 on 2011-06-21
On my version of 11.10 I cant even see the text in the chat menu is there a way to fix this?

---

### Post by Barbalras on 2011-07-10
similar issue here

I'm using gnome 3 and I've got the feeling that the issue is related to it.

Empathy connects with no problem but I cannot open any chat window. I double-click in any contact and nothing. But when someone starts talking to me, the cpu usage increases A LOT 

any thoughts?

---

