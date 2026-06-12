---
title: "File manager hanging."
date: 2020-11-26
forum: New to Ubuntu
---

### Post by Tadaen_Sylvermane on 2020-11-26
I'm having difficulties recently. After a day or 2 my file manager takes upwards of a minute to open. My recycle bin on the desktop times out instead of opening. Apps take a good long time to open. This is all solved by a reboot and shouldn't be an issue with an SSD.

My only change since these began is implementing  multi-seat. I'm unsure of how to diagnose or chase this down. Any advice? Or what logs / what to look for in logs?

---

### Post by Tadaen_Sylvermane on 2020-11-29
Bumping after editing to make simpler and clearer.

---

### Post by DuckHook on 2020-11-29
I'm way out of my league responding to anything dealing with multi&#8209;seat (I have no experience with it), but have you looked at your logs? Especially after a freeze-up?

That's the only suggestion I can make.

---

### Post by ajgreeny on 2020-11-29
I have to admit I had no idea what "multi-seat" was until I searched.

Have you seen the page at [https://help.ubuntu.com/community/MultiseatX](https://help.ubuntu.com/community/MultiseatX) ?
Though pretty old now, may give you some clues if you've not already seen it.

---

### Post by Tadaen_Sylvermane on 2020-12-05
I'm going to mark this solved for now. I'm going to have to do some testing and research but I dropped multi-seat, problem remained. Changed my fstab nfs mounts from automount to full time defaults and the problem has disappeared, at least for 3-4 days now. Considering before this I was lucky to make it a day or 2 without a reboot and now I'm 3-4 days and still solid I'd say that's an indicator of something.

I can't help but wonder if something changed with Focals nfs-server. I did upgrade my server to focal a few weeks, month ago or so.

---

