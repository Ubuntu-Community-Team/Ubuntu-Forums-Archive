---
title: "How can someone with a standard account access other partitions?"
date: 2012-07-10
forum: New to Ubuntu
---

### Post by ub07 on 2012-07-10
My computer is a stand-alone workstation used by several people most of whom have standard (non-administrator) accounts. We have data on a Windows partition that apparently they cannot access. As an administrator I can access this partition, but they cannot. 

Is there any way that I can give permission for them to access this partition? Or do I have to make everyone an administrator?

Thanks.

---

### Post by critin on 2012-07-10
> **ub07 said:**
> My computer is a stand-alone workstation used by several people most of whom have standard (non-administrator) accounts. We have data on a Windows partition that apparently they cannot access. As an administrator I can access this partition, but they cannot. 

Is there any way that I can give permission for them to access this partition? Or do I have to make everyone an administrator?

Thanks.

There is a section to allow others access without passwords in the network pages.  If they can see the folders, they should be able to access the files if all permissions allow it.

---

### Post by ub07 on 2012-07-10
> **critin said:**
> There is a section to allow others access without passwords in the network pages.  If they can see the folders, they should be able to access the files if all permissions allow it.

That's just the problem - the partitions don't show up for them. My plan was to add the users to my group and change the permissions on those partitions, but as soon as I tried to change permissions in Nautilus (as root), the permissions sprang back to the default which is to allow no access.

---

### Post by Paqman on 2012-07-10
If it's a non-Linux filesystem you can't set permissions on it normally, you have to do it through /etc/fstab.

If you open the file there will be a line in there that mounts the partition. You can add options such as a "umask" that will control what level of access users are given.

[More info here]("http://ubuntuforums.org/showthread.php?t=1604251").

---

### Post by ub07 on 2012-07-10
Thank you, Paqman. I read that thread and the links provided in that thread, and I'm making progress. I managed to get get the standard users to see the files in the partition by adding the following line to fstab:

/dev/sda5	/media/Shared	vfat	exec,rw,auto,users,sync


The problem is that the standard users still cannot write or make changes to that partition. What am I missing?

---

### Post by ub07 on 2012-07-10
I corrected my fstab entry from what I wrote before:


> 
/dev/sda5	/media/Shared	vfat	exec,rw,auto,users,sync


to:

> 
/dev/sda5	/media/Shared	vfat	rw,auto,users,exec,sync,umask=000	0	0



Apparently even if you specify "rw" and "users," you still need to specify permissions through the umask option.

Thanks to everyone for their help. The link provided by Paqman was extremely helpful. This problem is solved.

---

