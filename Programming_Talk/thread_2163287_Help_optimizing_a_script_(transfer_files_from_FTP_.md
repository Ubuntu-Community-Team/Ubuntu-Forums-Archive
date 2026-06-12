---
title: "Help optimizing a script (transfer files from FTP to VPS)"
date: 2013-07-17
forum: Programming Talk
---

### Post by vikler on 2013-07-17
Hello everyone!

So, I have the following issue:
I have a VPS (site A) and a FTP access to a different site (site B)
Lets say, I need to have a copy of all files from a certain directory of site B to be hosted on my site A. The problem is that site B's directory gets cleaned VERY quickly, and the script need to quickly grab all the new files to transfer them to site A.
here is what i've made (I run this script in ssh for site A, where I have ubuntu server installed)
```

while true; do lftp -c "set ftp:list-options -a;open [ftp://username:password@siteBhost.com;](ftp://username:password@siteBhost.com;) cd /siteBdirectory; mirror --only-newer"; done

```



of course it's not the best solution. It's not the best idea to do scripts in while true loop. Besides, it is still a bit ....slow? sometimes I notice incomplete files on my site A (especially it is noticable for .jpg files), some files are being missed, etc... Any ideas? thanks a lot in advance and forgive me for my "n00bness"

---

### Post by trent.josephsen on 2013-07-17
I'm not sure I understand what you mean by "site B's directory gets cleaned" -- is something deleting the files remotely and you need to download them before that happens? Because if *all* you have is FTP access (i.e. no ssh/scp/rsync/etc. and no way to set up scripts on the remote server) I don't think you can improve on a solution similar to the one you have.

If it's simply a question of speed, you might be able to get away with just compressing the data first. 

Where's this data coming from? Could your VPS somehow be notified when new data becomes available?

---

### Post by vikler on 2013-07-18
> **trent.josephsen said:**
> I'm not sure I understand what you mean by "site B's directory gets cleaned" -- is something deleting the files remotely and you need to download them before that happens? Because if *all* you have is FTP access (i.e. no ssh/scp/rsync/etc. and no way to set up scripts on the remote server) I don't think you can improve on a solution similar to the one you have.

If it's simply a question of speed, you might be able to get away with just compressing the data first. 

Where's this data coming from? Could your VPS somehow be notified when new data becomes available?
yeah you are right, the files are being deleted or moved to a different place remotely, and I need to download them before they are gone... I guess really there is no magic, and this can't be performed better *sigh* thanks for the reply though

---

