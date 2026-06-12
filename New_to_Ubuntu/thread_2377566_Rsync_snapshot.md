---
title: "Rsync snapshot?"
date: 2017-11-14
forum: New to Ubuntu
---

### Post by Tadaen_Sylvermane on 2017-11-14
Trying to understand rsync. How does it work with a file that is constantly changing. Does it snapshot and sync the file or what?

I ask because i like ramdisks. Gonna set up a terraria server but it doesnt have a console command to disable saving. I dont know of i can rsync a file in flux.

If rsync no good is there another way to get snapshot of a changing file without going lvm or btrfs?

---

### Post by HermanAB on 2017-11-15
No, you cannot rsync a file in flux.

However, you can make snapshots if you use Zfs on the server.  So your server may need to run FreeBSD, not Linux.

Don't panic - Linux is just another kind of BSD...

---

### Post by Tadaen_Sylvermane on 2017-11-15
If filesystem only way to do snapshots then I'm sol i guess. I have my minecraft servers in a ramdisk, every 5 minutes i disable saving and rsync them to the ssd on the server. Is what I was trying to do here. Guess I'll have to settle for ssd storage, not the end of the world... I just love the speed of a ramdisk :)

---

