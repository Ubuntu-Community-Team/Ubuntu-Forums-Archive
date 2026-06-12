---
title: "Deleted my files accidentally in samba server"
date: 2015-03-12
forum: New to Ubuntu
---

### Post by Christopher_Subala on 2015-03-12
Hi, ):P

i badly needed help, i accidentally delete my files in our samba server...where can i locate my file like in windows you can check it to recycle bin but in ubuntu no files have been shown...
please help me...

thanks

---

### Post by Holger_Gehrke on 2015-03-12
There is a recycle bin (vfs_recycle) in samba, but it's optional and must be configured in the smb.conf. Ask your network administrator whether he has set it up and where it is. If he has not set it up, then your files are gone and the only way to get them back would be to shut down the server AT ONCE so the freed up blocks that held your files don't get overwritten and use testdisk and / or photorec to recover them. 
I don't know how a windows client handles this situation, but in all Linux file managers I've tried you should have gotten a warning that there's no recycle bin and your files are going to be completely erased.

---

### Post by Christopher_Subala on 2015-03-13
Thank you [**[COLOR=#000000]Holger_Gehrke[/COLOR]**]("http://ubuntuforums.org/member.php?u=1961578")....
[COLOR=#ff0000]
There is a recycle bin (vfs_recycle) in samba, but it's optional and  must be configured in the smb.conf. Ask your network administrator  whether he has set it up and where it is. If he has not set it up, then  your files are gone and the only way to get them back would be to shut  down the server AT ONCE so the freed up blocks that held your files  don't get overwritten and use testdisk and / or photorec to recover  them.[/COLOR]

i will try this and i will inform you immediately if this works for me...

thanks a lot!!! =d>=d>=d>

---

