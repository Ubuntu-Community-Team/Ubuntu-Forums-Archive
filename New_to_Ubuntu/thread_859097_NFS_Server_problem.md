---
title: "NFS Server problem"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by shoaibi on 2008-07-14
Ubuntu 8.10 LTS
Fully updated.

My IP: 192.168.40.119

Following Guide at:
[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)


My Export File:
```

#/etc/exports

# /etc/exports: the access control list for filesystems which may be exported
#               to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync) hostname2(ro,sync)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt)
# /srv/nfs4/homes  gss/krb5i(rw,sync)
#


/freebsd7 192.168.40.146(ro,async)

```

My Problem:
```

$ sudo exportfs -a
exportfs: /etc/exports [3]: Neither 'subtree_check' or 'no_subtree_check' specified for export "192.168.40.146:/freebsd7".
  Assuming default behaviour ('no_subtree_check').
  NOTE: this default has changed since nfs-utils version 1.0.x

```

and the NFS share isnt available...

---

### Post by Cypher on 2008-07-14
What does the following command show?
```

exportfs

```

---

### Post by shoaibi on 2008-07-14
```

 exportfs
/freebsd7     	192.168.40.146

```

---

### Post by weirdfox on 2008-07-14
This was just a warning.
To pervent it from reapearing, you will have to add no_subtree_check or subtree_check to your config (with ro,async).


Info from [http://gentoo-wiki.com/HOWTO_Share_Directories_via_NFS](http://gentoo-wiki.com/HOWTO_Share_Directories_via_NFS)
[INDENT]**no_subtree_check** 
[INDENT]If only part of a volume is exported, a routine called subtree checking verifies that a file that is requested from the client is in the appropriate part of the volume. If the entire volume is exported, disabling this check will speed up transfers.[/INDENT] [/INDENT]

---

