---
title: "Samba does not show up on LAN without GUI login"
date: 2014-02-16
forum: New to Ubuntu
---

### Post by lalx on 2014-02-16
hi,

i have been pulling my hair out on this one and would appreciate any help.

i have set up a kubuntu server (12.04) with samba shares on a lan. 

my issue is that the shares are not accessible when i start the server up (in both text or gui mode). the shared folders show up when i login in gui mode only and i can access the files. when i login in text mode - nothing happens.

i checked the status of nmbd and smbd while in both modes and they are both running fine.

for the shares to be usable on lan - i HAVE to login in gui-mode and then everything works fine.

does this have anything to do with konqueror as i have modified some shares with that as well as the samba gui tool. i even tried ajenti. i have a feeling that messing around with multiple tools might have something to do with this issue.

---

### Post by tfrue on 2014-02-16
> for the shares to be usable on lan - i HAVE to login in gui-mode and then everything works fine.
Well, you probably have shares defined in the smb.conf file and defined usershares. So you need to decide if you want to continue using the GUI, or just the CLI mode(text) so we don't have conflicts.

> my issue is that the shares are not accessible when i start the server  up (in both text or gui mode). the shared folders show up when i login  in gui mode only and i can access the files. when i login in text mode -  nothing happens.
You have to define mount points in the /etc/fstab file for mounting at boot.

Here is a link that will help you edit that file:
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Post the output of:
```
testparm -s /etc/samba/smb.con
```
(This will output the contents of the smb.conf file)
and
```
 ls -l /var/lib/samba/usershares && cat /var/lib/samba/usershares/*
```
(This will tell us if we have a defined usershare, and the parameters associated with it.)

Thanks, 
Chris

---

