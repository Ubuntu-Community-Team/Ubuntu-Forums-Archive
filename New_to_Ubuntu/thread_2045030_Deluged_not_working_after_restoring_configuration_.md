---
title: "Deluged not working after restoring configuration backup"
date: 2012-08-20
forum: New to Ubuntu
---

### Post by mafi127 on 2012-08-20
sry for poping old post, I made I backup my deluge config and reinstalled my ubuntu and now when I tryed to restore it then I cant get my deluged to get work aigan, I dont have any seeding torrents any more :( plz help me.

---

### Post by sandyd on 2012-08-20
[I][B]Moved post to own thread
[/B][/I]
- Please don't resurect old threads, open a new one instead.

---

### Post by mafi127 on 2012-08-21
Got it workin. What I did was

```

apt-get install deluged deluge deluge-webui

su - your_username_here
deluged
screen -fa -d -m -S deluge-web deluge-web 			 		

```

started deluge and then exited and copyed my backup config to ~./.config/

---

