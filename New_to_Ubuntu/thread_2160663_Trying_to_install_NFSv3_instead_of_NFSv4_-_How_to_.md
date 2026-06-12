---
title: "Trying to install NFSv3 instead of NFSv4 - How to do this?"
date: 2013-07-07
forum: New to Ubuntu
---

### Post by ped5 on 2013-07-07
Hello everyone,

I'm not brand new to linux, but it has been awhile.

I recently stumbled upon the virtues of using NFS instead of Samba for sharing with XMBC on an ATV2.  I'm not here to understand how to get the ATV2 working... that part I think I'm good.  Have had it working with SMB for over a year.

However what I am at a loss is knowing how to setup a proper NFSv3 configuration given I understand the release of XBMC v12.1 Frodo that I'm using doesn't support NFSv4 natively.  Specifically it relates to:  *[COLOR=#000000][FONT=Verdana]Xbmc does support NFS natively via libnfs, but only NFSv3.[/FONT][/COLOR]*[COLOR=#000000][FONT=Verdana] If that helps with specifics, even better. :)
[/FONT][/COLOR]
Some background:

[LIST]
[*]Running Ubuntu 11.10
[*]Already followed the instructions how to install NFSv4
[*]Wondering if I need to uninstall NFSv4, and how to do that?
[/LIST]

So here I am, after searching several articles... including some Ubuntu How-to's that always refer to the newer NFSv4, and makes some references to v3, saying it's more difficult etc etc.  Really have no idea how to configure for v3 if that's exactly what I desire. 

So appreciate any references you may have, or can point me in the right direction.  In addition any long list of command lines, would be great to know the meaning behind them as well, why they are edited, why the context as well.  Hoping to learn a tad about NFS as well. 

Just as a point of reference, my current /etc/exports is listed as such:

```
/export         192.168.0.1/24(rw,all_squash,insecure,no_subtree_check)
/export/movies  192.168.0.1/24(rw,all_squash,insecure,no_subtree_check)
/export/tv      192.168.0.1/24(rw,all_squash,insecure,no_subtree_check)

```
Warm regards,
-ped5

---

### Post by ped5 on 2013-07-14
Bump. 
Not urgent but any direction would be appreciated.

---

### Post by ped5 on 2013-07-16
Either the question is obviously stupid or extremely difficult.  No one have any idea?  Or perhaps post on another sub forum?  Thanks.

---

### Post by howefield on 2013-07-16
> **ped5 said:**
> Either the question is obviously stupid or extremely difficult.  No one have any idea?  Or perhaps post on another sub forum?  Thanks.

You may be an absolute beginner but the question is absolutely not an absolute beginner question, so would probably be better suited elsewhere. Do you wish it moved ?

---

### Post by SeijiSensei on 2013-07-17
Install **nfs-kernel-server**, then look at /etc/default/nfs-kernel-server.  Edit the entry for RPCMOUNTDOPTS like this:

```

RPCMOUNTDOPTS="--manage-gids --no-nfs-version 4"

```

Then issue "sudo service nfs-kernel-server restart".  Your server should now be using version 3.

---

### Post by ped5 on 2013-08-09
> **howefield said:**
> You may be an absolute beginner but the question is absolutely not an absolute beginner question, so would probably be better suited elsewhere. Do you wish it moved ?

Fair enough.  You can move it to the appropriate forum.

> **SeijiSensei said:**
> Install **nfs-kernel-server**, then look at /etc/default/nfs-kernel-server.  Edit the entry for RPCMOUNTDOPTS like this:

```

RPCMOUNTDOPTS="--manage-gids --no-nfs-version 4"

```

Then issue "sudo service nfs-kernel-server restart".  Your server should now be using version 3.

Great, will give this a shot.  Didn't know I had replies until the forum came back up.  

Cheers to you both.

---

