---
title: "HOWTO: Open media files on CIFS via nautilus with mplayer"
date: 2008-05-06
forum: Outdated Tutorials &amp; Tips
---

### Post by AlienM1nd on 2008-05-06
Prerequisites:
- You hate totem, and love mplayer
- You have your movies on a samba share
- You don't want to do a smbmount

With following script, you can open files with mplayer residing on a place you opened via Go->Network in Nautilus.
1) Just name the script "mplayerwrapper.sh".
2) (only once for filetype) Right click on wanted file -> Properties -> Open with -> Add -> Use custom command -> Enter: <path-to-script>/mplayerwrapper.sh "%U"

Script content follows:
```
#!/bin/bash
SMBUSER=usernameForTheShare
SMBPASSWD=passwordForTheShare
export PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
URL=$1
NEWURL="`echo ${URL}|sed 's/smb:\/\//smb:\/\/'${SMBUSER}':'${SMBPASSWD}'@/'`"
#the following makes Blake's%20 out of 'Blake'\''s%20'
NEWURL=`eval echo $NEWURL`
xterm -e mplayer $NEWURL

```

---

