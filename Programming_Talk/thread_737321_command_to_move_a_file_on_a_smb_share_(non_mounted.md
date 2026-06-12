---
title: "command to move a file on a smb share (non mounted)"
date: 2008-03-27
forum: Programming Talk
---

### Post by jobsonandrew on 2008-03-27
Hi,
I have an Icon on the desktop that takes me to my nas drive.. I put it there by going to places -> connect to server -> windows smb
its path is:
```
smb://fnd/PUBLIC/
```

im trying to write a script that has the ability to rename files on that smb share, without going through all the crap of mounting it to /media/

The script is actually supposed to remove spaces from the names of the selected files in nautilus.. Nautilus can get the URI of files on the smb share, but theres no terminal command that can talk to the smb share, eg:
```
mv smb://fnd/PUBLIC/filename%20with%20spaces smb://fnd/PUBLIC/filename_with_spaces
```
doesnt work at all.. I made it copy a file from the smb sever with:
```
gnomevfs-copy <source_on_smb> <local_destination>
```

But I cant find a command to move/rename a file there..(P.S. I'm trying to do this without mounting the share to /media/.. I dont believe I need to mount it if some commands can talk to 'smb://' paths)???

Any help appreciated, Thanks :)

---

### Post by mssever on 2008-03-27
> **jobsonandrew said:**
> But I cant find a command to move/rename a file there..
If you type ```
gnomevfs-<tab><tab>
``` you'll see a whole set of interesting commands.

---

