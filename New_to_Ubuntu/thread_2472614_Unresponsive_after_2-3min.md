---
title: "Unresponsive after 2-3min"
date: 2022-03-06
forum: New to Ubuntu
---

### Post by cnull2 on 2022-03-06
Recently I upgraded to Ubuntu 20.04 ever since I have had problems with my system losing network at about 2-3min. I use plex and it just stops.  I don't think it's network, although I kind of stink at troubleshooting. When I check what's going on, often the whole server is running slow and network seams to be down. I have looked though the syslog, dmsg etc... and don't see anything that appears like an issue. Where would I start with something like this?

Chris

---

### Post by MAFoElffen on 2022-03-07
I would suggest installing and monitoring with 'glances'. It is similar to 'top', but shows more info. What you need to look at is %CPU, %MEM, Load and Network... 

You say it happens in 2-3 minutes, so you wouldn't have to watch it for long...

When it does happen, can you reset your network and does it come back up? Or just remain locked up?

---

### Post by ActionParsnip on 2022-03-08
Can you SSH to the server from another system and read logs OK? Do they give clues?

---

