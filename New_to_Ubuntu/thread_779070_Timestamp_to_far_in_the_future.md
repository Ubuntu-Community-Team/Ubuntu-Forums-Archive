---
title: "Timestamp to far in the future?"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by Ikith on 2008-05-02
Woah so I'm doing an ATI graphics driver install and when I goto edit xorg.conf I get:

Error: Timestamp to far in the future.

Both the ubuntu clock and system clock are set correctly.

---

### Post by Virtual_Ron on 2008-05-02
are you using sudo to edit your xorg.conf?  If so, in a terminal run "sudo -k".  it will clear sudo's saved user timestamp.

---

