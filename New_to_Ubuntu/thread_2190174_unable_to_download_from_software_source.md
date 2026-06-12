---
title: "unable to download from software source"
date: 2013-11-26
forum: New to Ubuntu
---

### Post by zain033_bchbs on 2013-11-26
Hello:
I am using ubuntu 11.10 and unable to download any thung from software center nor can i check available updates. when i try to downloaad any tthing it says "waiting for jockey-backend to exit" but it never exits.. what could i do,,

---

### Post by howefield on 2013-11-26
Open up System Monitor > Processes tab and end the jockey-backend process.

---

### Post by fantab on 2013-11-26
If you are using 11.10 then its time for you to upgrade to the latest version of Ubuntu. 11.10 has reached 'end of life', you won't get any upgrades or updates for it.

---

### Post by Bucky Ball on 2013-11-26
> **fantab said:**
> If you are using 11.10 then its time for you to upgrade to the latest version of Ubuntu. 11.10 has reached 'end of life', you won't get any upgrades or updates for it.

+1. 11.10 has not been supported for six months. The repos are no longer active which is why you are getting no updates and possibly why you're having trouble with Software Centre.

---

### Post by newb85 on 2013-11-26
... and probably why jockey is hanging, too.

---

### Post by tarnall on 2013-11-28
I am using 13.10.  I am also unable to download - Qalculate package.  after a few minutes of watching the progress circules arrows at the top I finally get a message: Failed to download package file, check your internet connect"  Internet connect IS fine!  I log into Facebook fine and run Thunderbird Mail just fine too.  I do have this little red triangle with an explantion mark at the top, not sure what that means.
I have logged out of all running applications that I see running.
Thanks for any suggestions!

---

### Post by Bucky Ball on 2013-11-28
Click the red arrow explaining mark and see if that gives any clues.

---

### Post by heir4c on 2013-11-28
@tarnall,
Open a terminal and type:
```
sudo apt-get update && sudo apt-get upgrade
```
Do you see any errors?

---

