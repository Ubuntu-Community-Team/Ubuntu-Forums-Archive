---
title: "Permissions issue. Can't touch files in directory I have group access to."
date: 2018-07-04
forum: New to Ubuntu
---

### Post by Tadaen_Sylvermane on 2018-07-04
```
jason@failbox:/snapraid/pool/music$ ls -al | grep root
drwxrwxr-x 61 root  ourmedia 4096 Jul  4 13:46 .
drwxr-xr-x 15 root  root     4096 Jul  3 18:15 ..
jason@failbox:/snapraid/pool/music$ touch lol
touch: cannot touch 'lol': Permission denied
jason@failbox:/snapraid/pool/music$ groups
jason adm cdrom sudo dip plugdev lxd lpadmin sambashare mythtv ourmedia
```

Self explanatory. Can't figure out why I can't create files even though I have group permissions set. Suggestions?

Found this problem when trying to give my wife a writable samba mountpoint to drop media in the storage system.

*EDIT* I don't consider chmod 777 a proper answer. maybe the easy way but there has to be a legitamate fixable reason for this.

---

### Post by TheFu on 2018-07-04
Don't have root as the owner.  Some security things get triggered with root owning files over network shares.
Might also try **chmod g+s /snapraid/pool/music** to force the group to be the default for all new files.

---

### Post by Tadaen_Sylvermane on 2018-07-05
Tried that today. Still no dice with the ourmedia group. If i change the permissions to root:jason it works fine. Or my user of course works.

---

### Post by TheFu on 2018-07-05
> **TheFu said:**
> Don't have root as the owner.  Some security things get triggered with root owning files over network shares.

Did that not work?  NFS treats root-owned files/directories in odd ways.

---

### Post by SeijiSensei on 2018-07-05
What are the permissions on /snapraid and /snapraid/pool?  In particular, if they do not have at least the execute bit turned on for non-root users, then you can be blocked from subdirectories.

---

