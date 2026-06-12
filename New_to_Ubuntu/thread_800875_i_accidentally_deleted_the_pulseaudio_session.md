---
title: "i accidentally deleted the pulseaudio session"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by Sonic Reducer on 2008-05-20
i was adding x360MediaServe to my startup sessions when i noticed pulseaudio, i was curious because i have never heard of it, and when i went to click "edit" to see what the command was at startup i accidentally clicked remove.

what was the entry in System>Preferences>Sessions for pulse audio?

---

### Post by Milk &amp; Toast &amp; Honey on 2008-05-20
```

Name: PulseAudio Session Management
Command: pactl load-module module-x11-xsmp
Comment: Load module-x11-xsmp into PulseAudio

```

---

