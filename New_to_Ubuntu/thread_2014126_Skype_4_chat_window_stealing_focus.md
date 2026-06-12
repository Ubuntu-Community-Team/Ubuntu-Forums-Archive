---
title: "Skype 4 chat window stealing focus"
date: 2012-07-01
forum: New to Ubuntu
---

### Post by UpSignal on 2012-07-01
Hey there. That's pretty much it. if someone sens a chat message to me, that window pops up right in front. it's super annoying, i end up typing half of my text in a chat window.

running ubuntu 12.04 gnome shell, and skype 4.0.0.7 (deb downloaded from their site)
anyone got a fix for this? i need to use skype, but this drives me insane.
oh, and i have the "create a minimized chat window" checked. but it doesn't help

---

### Post by UpSignal on 2012-07-01
just found this workaround, but i can't get it to work on gnome shell;

[http://www.omgubuntu.co.uk/2012/05/skype-wrapper-adds-call-actions-notification-fixes-ubuntu-12-04-support](http://www.omgubuntu.co.uk/2012/05/skype-wrapper-adds-call-actions-notification-fixes-ubuntu-12-04-support)

---

### Post by UpSignal on 2012-07-02
can't solve this guys. any idea pls? at least some kind of hack to block the damn chat window from popping in my face :S
i saw ppl complaining in skype forum, no replies. i guess we're getting no help

---

### Post by UpSignal on 2012-07-03
just tried editing this file:

> /usr/share/gnome-shell/js/ui/windowAttentionler.js

And changed the line, from:

> if (!window || window.has_focus() || window.is_skip_taskbar())

to...

> if (!window || window.has_focus() || window.is_skip_taskbar() || window.get_wm_class() == "Skype")

According to a tutorial i saw. but it's still not working! that tutorial was for linux mint btw

---

### Post by UpSignal on 2012-07-03
Bump!

come on guys, any expert to help me sort this out? I can't figure out if there's something wrong with those codes, or if it can't be done.
Also, i need to know if this is gnome shell related or not

---

### Post by UpSignal on 2012-07-04
bump

---

### Post by UpSignal on 2012-07-04
solved. went back to Ubuntu 10.04. thanks all for the help

---

