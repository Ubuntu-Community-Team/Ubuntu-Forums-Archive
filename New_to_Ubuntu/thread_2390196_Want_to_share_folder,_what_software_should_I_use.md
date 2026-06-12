---
title: "Want to share folder, what software should I use?"
date: 2018-04-26
forum: New to Ubuntu
---

### Post by reddioment on 2018-04-26
So I have a media drive with subfolders and video files. I want to share this on my network like a LAN media server. I want to access this drive from other computers and smart TVs.

[LIST=1]
[*]I tried to simply share the drive but while it showed up as a network folder but I cannot access the internals.
[*]I tried Plex but it didn't recognise the video files and I also found out that it is a paid service.
[/LIST]

**What software should I use?** I don't need fancy UI like plex (although it would be nice), it is enough if I see the files.

Thanks for the support in advance!

---

### Post by TheFu on 2018-04-26
Plex is NOT a paid service.  They just push everyone that direction as part of their marketing.

The sort of clients will determine which protocol is best.   
For Unix-to-Unix, nfs is best when on the same network.
For Unix-to-Windows, CIFS/Samba is best when on the same network.
For Unix-to-Android, something like DLNA is best when on the same network.

For plex to see media files, the file & directory permissions need to be set correctly.
Kodi is also popular.
Smart TVs are harder. I think they'd like DLNA over other protocols.  I don't have any TVs, so only know.
I do have a roku, multiple kodi systems, android, and a plex server. They all work together, generally through plex, but sometimes through NFS.

And just for clarification, to use plex, you do not need to use a "plex client" or have a plex account.

---

