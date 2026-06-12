---
title: "Samba Transfer Speed Is Slow"
date: 2016-04-24
forum: New to Ubuntu
---

### Post by lino3 on 2016-04-24
Hello.
I have a headless server on Ubuntu 14.04 which runs Plex and nothing else.
When I download a file from this server from a Windows PC, I get a maximum speed of about 7 mbps.
When I download a file using the Plex application (again on the same Windows PC), the speed ramps up to about 30 mbps.
Same server, same PC, and yet such a significant change in speed.

Any idea how I can speed Samba up?

It's hooked in by Ethernet using a Broadcom 4401 card.

I am a Linux idiot, but I can follow instructions pretty well.

Thanks

---

### Post by Magneto on 2016-04-24
what do you seen when running top while performing both tasks? Have you searched for slow Samba issues in Google or wherever? May be a known issue. If your headless server is multicore it may be that Plex is using more than one core and samba isn't. Was the file you were transferring between systems on the same filesystem on your headless box? If you transferred a file on a usb2.0 external drive to the win system and then transferred the same file on a sata internal drive that would account for the speed difference too. Just trying to help. Hopefully someone with more recent Samba knowledge can shine some light on this for you.

---

