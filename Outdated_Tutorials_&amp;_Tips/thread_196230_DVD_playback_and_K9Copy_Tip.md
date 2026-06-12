---
title: "DVD playback and K9Copy Tip"
date: 2006-06-13
forum: Outdated Tutorials &amp; Tips
---

### Post by Stelmate on 2006-06-13
I came across a problem with my dapper install, I couldn't read DVDs on k9copy (when I did a open disc, libdvdread would fail out on every sector) and playback was finky on VLC,Xine and Mplayer so here is the fix that worked for me...
Dapper didn't correctly put my dvd burner and cd burner in my fstab..
so check your /etc/fstab entries, I had to add the following:

/dev/hdc        /media/dvd      udf,iso9660 noauto,users,ro,dev     0       0
/dev/hdd        /media/cdrom0   udf,iso9660 noauto,users,ro,dev     0       0


NOTE for the newbs: hdc and hdd will need to reflect your specific devices, don't just copy mine or it might not work.

Well thought I'd share a solution to a problem I found incase anyone else ran across it.

---

