---
title: "How to access Synology NAS from Ubuntu?"
date: 2012-06-16
forum: New to Ubuntu
---

### Post by Houmie on 2012-06-16
In the bginning I was able to go to NETWORK -> BROWSE NETWORK in Ubuntu and see my Diskstation.

Since the last time I said "Remember always my credentials", I can't seem to see Diskstation under network anymore.

Is there anyway to reset this, or egenerally how do you mount to the Files, Audio, Pictures of your File Station on NAS?

Many Thanks,
Houman

---

### Post by daslinkard on 2012-06-17
This [link]("http://www.markinthedark.nl/news/ubuntu-linux-unix/85-howto-mount-synology-nas-ds211j-to-ubuntu.html") here has a wide range of answers that I think may be useful to you....good luck!

---

### Post by Houmie on 2012-06-18
yeah that did it. Thank :)

---

### Post by Roadfighter on 2012-09-18
> **daslinkard said:**
> This [link]("http://www.markinthedark.nl/news/ubuntu-linux-unix/85-howto-mount-synology-nas-ds211j-to-ubuntu.html") here has a wide range of answers that I think may be useful to you....good luck!

Hello, I did the same thing but my fstab is a little different than in Mark his blog.
Mark's blog fstab:```
IPADDRESS-OF-YOUR-NAS:[COLOR=#000000]**/**[/COLOR]volume1[COLOR=#000000]**/**[/COLOR]photo [COLOR=#000000]**/**[/COLOR]mnt[COLOR=#000000]**/**[/COLOR]CHOOSE-NAME[COLOR=#000000]**/**[/COLOR]photo nfs nouser,atime,auto,rw,dev,[COLOR=#7a0874]**exec**[/COLOR],suid [COLOR=#000000]0[/COLOR] [COLOR=#000000]0[/COLOR]
```My fstab entry:```
192.168.178.50:/volume1/Documenten/        /media/Documenten        nfs    rsize=8192,wsize=8192,timeo=14,intr
```Now i have the following questions,
1. Can someone discribe the differents between the 2 fstab entries.?
2. how can i place and acces files from two different ubuntu pc's without having trouble with file permissions?
3. The users on the synology are 1026 and 1027 but the user id from both ubuntu pc are 1000.
Is it also possible to make a user on the synology with id 1000 ?

---

