---
title: "HOWTO: Remove all gnome-panels in interpid"
date: 2009-04-05
forum: Outdated Tutorials &amp; Tips
---

### Post by RuleMaker on 2009-04-05
There is a way to remove all gnome-panels in earlier versions of ubuntu by editing the current session, but since there is no more current session tab in sessions it's not possible anymore.
If you want to use another panel like AWN you surely don't need the gnome-panel.
Here is how:
In gconf-editor go to: desktop/gnome/session/required_components and set the panel's value to an empty string.
Re-login and panel shouldn't appear again.

I found this solution [here]("http://www.linux-archive.org/ubuntu-user/236815-hide-remove-gnome-panel.html").

---

