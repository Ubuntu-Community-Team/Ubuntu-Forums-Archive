---
title: "desktop not loading after stupid decision (on my part)"
date: 2012-05-14
forum: New to Ubuntu
---

### Post by thomasg62 on 2012-05-14
I am using Kubuntu 12.04

For no fathomable reason, whilst trying to resolve a sudden slow-down on performance I unchecked what was in my Start-up. 

Net result: I login to a completely blank desktop with no mouse response whatsoever. When I Ctl-alt-del I get back to the login but none of the other options, including KDE failsafe, makes any difference. There is an 'open box' session but that only gets me the ability to rightclick on my mouse and then unfamiliar options - I could get to a terminal but don't know what to do there to resolve this. 

I am prepared to re-install - if thats what it comes to - but if thats the advice can you tell me what to backup (I can get access to files from my dual-boot distro - Peppermint) so that I can get things back to where they were - I would hate to lose all of my settings, and ideally my installed progs. I am pretty new to all of this but enjoying the learning!

Any help appreciated

---

### Post by thomasg62 on 2012-05-14
...phew! Managed to sort this by navigating to /home/tom/.kde/share/autostart then changing the 'Hidden=true' to hidden=false'. This worked when I re-booted. Relief!

---

