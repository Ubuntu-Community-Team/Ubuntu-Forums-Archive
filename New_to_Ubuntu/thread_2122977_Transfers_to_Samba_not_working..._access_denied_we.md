---
title: "Transfers to Samba not working... access denied well after beginning transfer."
date: 2013-03-06
forum: New to Ubuntu
---

### Post by lithog on 2013-03-06
I'm pretty newb so please have patience. I set up a headless Ubuntu server with samba so I could back up my media and such. I created two shares, one requiring a password (for the slightly more sensitive stuff) and one without for media to be accessed by my TV,etc... but I'm having a hard time backing stuff up because all the folders and such I've created are always appearing as read-only! It is very frustrating.

smb.conf is as follows:

[Shared]
    comment = Ubuntu File Server Share
    path = /srv/samba/share
    browsable = yes
    guest ok = yes
    read only = no
    hide dot files = no
    security = share
    writable = yes


[Nonshared]
    comment = Non Guest access share
    path = /srv/samba/nonshare
    browseable = yes
    read only = no
    security = user
    valid users = chosen
    hide dot files = no
    guest ok = yes
                       
Any help appreciated!

Edit: I think actually I may have misunderstood the nature of the problem. Files will begin transfer for backup but suddenly access will be lost even though the share appears. I had played with the read-only square and it seemed to solve the problem, hence my confusion. I did not realize that this blue box in the folder attributes did not necessarily mean the files were read only, so I apologize for the confusion. It turns out it was still having the problem, it was just taking longer to manifest. I am transferring nearly 100GB of files... it goes very slowly then eventually will stop saying there is no access.

---

