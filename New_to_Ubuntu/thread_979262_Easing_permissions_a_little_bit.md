---
title: "Easing permissions a little bit"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by lookitseman on 2008-11-11
Two related issues:

From what I've seen, Samba through Nautilus fails on 8.10, citing the need for root privileges.  That's fine, except that once the share is made, the shared icon which sits on the folder icon only shows up in Nautilus when you're using it as root and not as my user account.

I guess I'm trying to figure out how I can do Samba as myself.

========

I'll mention one more.  This one may be simple, I'm just still new-ish to permissions.

When I plug in my USB drives or load up my NAS devices, I frequently run into issues where I'd create a folder on the device, which would instantly lock itself up with root privileges so I can't open or add files to the folder.  It's no doubt a permissions issue, but how do I detect and get around things like this?

========

I was messing with the users and groups panel today, and added myself to the "root" group, so I think that's a start, but what else could I do to make this easier?

---

### Post by lookitseman on 2010-02-26
Reading this more than a year later, I realize I need to get better at describing my issues :).  I have found a solution to issue #1.

The command to mount the share would be similar to:

```

sudo mount -t cifs //SERVER/SHARE /mnt/DESTINATION -o username=SMB_USER,uid=A_LOCAL_USER

```

The "uid" part was the key.  Without it, root inherits ownership of the mounted files.  By specifying your *local* username in place of A_LOCAL_USER, you become the owner of the mounted files.

See this page for far better documentation.
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

I have a good feeling that a similar answer will solve issue #2, I just need to look into it some more.

---

