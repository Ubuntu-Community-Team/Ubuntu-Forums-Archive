---
title: "Mountmanager malfunction"
date: 2014-03-01
forum: New to Ubuntu
---

### Post by sprintwalk11 on 2014-03-01
I just recently made an old pc into a home/plex server.  i wanted to be able to restart pc without having to mount 2nd hd so i would still have access to my media since i have no screen attached to pc.  i tried doing mountmanager and now hd does not mount at all.  and i dont have a clue what to do in cli since i use gui.

---

### Post by TheFu on 2014-03-02
I have a plex server that also runs XBMC for playback.
In the last few weeks, I've needed to reboot it daily - though previously, it ran for months between reboots.
Anyway - there are lots of systems here, so a simple remote command over ssh from any of them will reboot.
I don't understand the "having to mount 2nd HDD" ... how does that matter?

How is that 2nd disk accessed?  SATA, eSATA, USB, Firewire, network?  
Why wouldn't it be always available? Please explain.

You can use **autofs** to only mount storage when it is accessed. There is a how-to here: [https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)
This is a well-known solution and has been around UNIX systems since .... mid-1990s, perhaps longer.

---

