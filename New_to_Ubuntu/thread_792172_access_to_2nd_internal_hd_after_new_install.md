---
title: "access to 2nd internal hd after new install?"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by northwestuntu on 2008-05-12
i have 2 internal hd on my system now.  i want to do a fresh install of hardy.  if i moved all my files to my extra hd and disconnected it and did a fresh install with my main hd.

when i reconnect the extra hd with all my files.  will i have access to them still?

my extra drive is currently /media/disk

hope i explained that well enough.

---

### Post by jnorth on 2008-05-12
> **northwestuntu said:**
> i have 2 internal hd on my system now.  i want to do a fresh install of hardy.  if i moved all my files to my extra hd and disconnected it and did a fresh install with my main hd.

when i reconnect the extra hd with all my files.  will i have access to them still?

my extra drive is currently /media/disk

hope i explained that well enough.

If I understand correctly, your "internal hd" is the one that currently has Ubuntu on it, and your "storage disk" is just that, storage or backup, mounted on your desktop (from /media/disk)?

If that's so, then yes, as long as your "extra hd" has a filesystem on it that Ubuntu can read, and does not have something odd like lvm or software raid set up on it you will be able to see it.

I do always unplug any storage drives I have (I have a few firewire drives daisy chained to my mythtv box) just to make sure I don't make a boneheaded mistake like installing over my music/videos by accident or just clicking though the installer - I think that is a good idea.

HTH

---

### Post by northwestuntu on 2008-05-12
yep that's just what i was talking about. 

thanks

---

### Post by jnorth on 2008-05-12
> **northwestuntu said:**
> yep that's just what i was talking about. 

thanks

Should be good to go then - cheers!

---

