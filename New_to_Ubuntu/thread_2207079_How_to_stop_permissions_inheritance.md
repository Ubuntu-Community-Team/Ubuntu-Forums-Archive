---
title: "How to stop permissions inheritance?"
date: 2014-02-21
forum: New to Ubuntu
---

### Post by chrbar on 2014-02-21
Hello,

I would like to know if it's possible to stop permissions inheritance?

I've a level-1 folder named "common", wherein all users can read/write.
Inside this folder, I've created a level-2 folder named "private" wherein members of "abc" group can enter/read/write.

I can build correctly this structure, **but I'd like that members of "abc" are not able to rename "private" folder**, and I don't succeed to do that!
I've tried many way, including ACL, but it doesn't work!
I'm not sure, but I think the problem is that members of "abc" group are member of "users" (member of child folder/group are member of parent folder/group)!

Do you know how can I do that?

Thanks for your help,
Chris

\common\private\

root@server:/# getfacl common
# file: common
# owner: root
# group: users
# flags: -s-
user::rwx
group::rwx
other::---

root@server:/common# getfacl private
# file: private
# owner: root
# group: abc
# flags: -s-
user::rwx
group::rwx
other::---

---

### Post by papibe on 2014-02-21
Hi chrbar.

I'd take a look at the at the 'sticky bit' applied to directories. For instance the /tmp directory:
```
$ ls -ld /tmp
drwxrwxrw**[COLOR="#FF0000"]t[/COLOR]** 12 root root 4096 Feb 21 22:37 /tmp

```
To assign it to a directory so that it works as /tmp:
```
chmod 1777 /path/to/common
```
Users can create, rename and delete their own files, but they can't rename or delete other people's files (only read by default). Create the private directory using your user, and nobody would be able to rename, or delete it.

Hope it helps. Let us know if that helps.
Regards.

---

### Post by bab1 on 2014-02-22
> **chrbar said:**
> Hello,

I would like to know if it's possible to stop permissions inheritance?

I've a level-1 folder named "common", wherein all users can read/write.
Inside this folder, I've created a level-2 folder named "private" wherein members of "abc" group can enter/read/write.

I can build correctly this structure, **but I'd like that members of "abc" are not able to rename "private" folder**, and I don't succeed to do that!
I've tried many way, including ACL, but it doesn't work!
I'm not sure, but I think the problem is that members of "abc" group are member of "users" (member of child folder/group are member of parent folder/group)!

Do you know how can I do that?

Thanks for your help,
Chris


You can't really do what you want to do.  If a use has read/write (RW) permissions then they have the right to delete a file or directory inside that directory.

The sticky bit as @papibe has suggested comes the closest, but it only refers to objects *inside *the directory **where the user is not the owner** or group owner of the directory .  This means you would have to allow anyone to RW to the directory above and set the sticky bit on that directory.  This is how the /tmp directory works.  All user have access but can't delete other users files.  See below```

drwxrwxrw[COLOR="#FF0000"]**t**[/COLOR] 11 root root 4096 Feb 21 21:17 /tmp

```...the t (in red) is the sticky bit.  Root is the owner and the group owner.

When you create private directories inside of open directories you should consider that directory to be the root of the file system you are creating.  I feel that the private directory that has more than one user should really be considered a kind of semi public directory.  All users should trust the others to some degree.

You  can't turn inheritance off.   The creator of the file is the owner and that users primary group is the group owner by default.  You can set the GID by setting the sgid bit.  This then has the effect of setting the GID to the GID of the directory you are creating the object.  You can also use the suid bit to set the creator owner.  If you do this incorrectly nobody will be able to read or write to the files they create.

---

