---
title: "[SOLVED] Transmission: I want to download a torrent"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by the badger on 2008-11-30
I want to download a torrent from isohunt, but the prompt dialogue is not automatically recognising 'Transmission'. (I have downloaded successfully from mininova, as it prompts me to use Transmission). If I could find Transmission in the file system, I could download the torrent. I *think* it should be in usr/lib (?) but I cannot find it. Can anyone tell me where I would find the file I need, and what it's called/file type?

Many Thanks!

---

### Post by taurus on 2008-11-30
Actually, it's in /usr/bin.

---

### Post by MrWES on 2008-11-30
I'm assuming you're using FireFox. If so, go to Edit | Preferences and then the Applications tab. Scroll down until you see 'bittorrent seed file' and choose transmission as your default application on the right side. Now when you download a torrent seed file, Transmission should automagically start with and add the file.

Bill

---

### Post by lukjad on 2008-11-30
Well, if you want to download, let's say, an Ubuntu ISO through torrents, I think you need to install a bittorrent program. There are a few. The one I use is called KTorrent. Though I have heard of one called RTorrent that is for the command line, I have never used it. I am not sure exactly what you are looking for, but I hope this helps.

EDIT: It seems I missed something.

---

### Post by the badger on 2008-11-30
Thanks! I found the correct file in usr/bin and set my preferences in Firefox accordingly. All's good... :)

---

