---
title: "Struggling to automounting a network drive"
date: 2021-05-13
forum: New to Ubuntu
---

### Post by yusuo85 on 2021-05-13
So I've followed the instructions for mounting for auto mounting my network drive in fstab, that i found [https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

However I keep getting an error 
mount: /etc/fstab: parse error at line 11 -- ignored

And im guessing that is because the Window share im trying to automount has a space in it, the fstab entry is as below
//192.168.0.115/Media PC /media/share cifs credentials=/home/laptop/.smbcredentials,iocharset=utf8,sec=ntlm 0 0 

I have created the credentials, but on the odd chance i didn't I also tried to enter this entry into fstab but still get the same error
//192.168.0.115/Media PC /media/share  cifs  username=Media,password=*********,iocharset=utf8,sec=ntlm  0  0
(obviously i've blanked my real password) 

I can access the share perfectly through Caja but who wouldn't want it all just to work automatically.

Anyone have any ideas where im going wrong?

---

### Post by TheFu on 2021-05-13
Your guess is correct. Don't allow spaces anywhere in mounts.  Use an  '_' instead.  Spaces are always troublesome in file systems, so the simple answer is DON'T USE THEM.

Also, I really hope that the remote mount doesn't need sec=ntlm - that is a security failure for the last few years.
I use these options to access Win7 shares:
```
iocharset=utf8,rw,vers=2.1,uid=thefu,gid=thefu,file_mode=0660,dir_mode=0770
```
in addition to having a credentials file.
Win8 and later can support newer, faster, CIFS mounts.

---

### Post by Morbius1 on 2021-05-13
Spaces in the name of things in fstab need to be replaced with the following characters:
```
\040
```
That is a zero4zero

So the line would look like this:
>  //192.168.0.115/Media[COLOR=#ff0000]**\040**[/COLOR]PC /media/share cifs credentials=/home/laptop/.smbcredentials,iocharset=utf8,sec=ntlm 0 0 

And what version of Ubuntu are you using because by default the Linux kernel in 20.04 for example starts with a version of the smb dialect that is incompatible with sec=ntlm.

Either add vers=1.0 to your list of options together with sec=ntlm or just remove sec=ntlm. So possible options would be:
>  //192.168.0.115/Media[COLOR=#ff0000]**\040**[/COLOR]PC /media/share cifs credentials=/home/laptop/.smbcredentials,iocharset=utf8[COLOR=#ff0000]**,vers=1.0**[/COLOR],sec=ntlm 0 0 
OR:
>  //192.168.0.115/Media[COLOR=#ff0000]**\040**[/COLOR]PC /media/share cifs credentials=/home/laptop/.smbcredentials,iocharset=utf8 0 0 

And I agree that unless you only want read access to this share you will need to - at a minimum - take possession of the mount by adding a [highlight]uid=your-linux-user-name[/highlight] whatever that is.

---

