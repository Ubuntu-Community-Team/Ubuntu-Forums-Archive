---
title: "share file with windoze"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by majikhotline on 2008-08-09
Hello ubuntu country,

how do i share a file with the windoze network?

---

### Post by loell on 2008-08-09
simply right click the folder click **sharing options**

---

### Post by majikhotline on 2008-08-09
and then what, where do i find the file?
and how do i set the correct permissons to access the file?
and how do change the workgroup name?

---

### Post by pi.boy.travis on 2008-08-09
Depends on what version of Windows.  Look for network files/shared files or something similar.

---

### Post by majikhotline on 2008-08-09
well found the file but dont have access to it and i also would like to change the workgroup name......im working with XP

---

### Post by aloshbennett on 2008-08-10
You can share the files across network using Samba. When you do a right-click on the folder and share, you are using Samba.

Samba maintains a list of ubuntu users (and passwords) it uses to authenticate. The files can be accessed using an Ubuntu username (alternatively, you could check the Guest Sharing option).

If you are still having trouble with permissions, check the access permissions of the files an folders you are sharing in Ubuntu.

---

### Post by doas777 on 2008-08-10
I had some trouble with this myself.

first you need to install samba with:
```

sudo apt-get install samba 
```

then you need to tweak up your /etc/samba/smb.conf to set the rules and add your shares (I've never been able to get the R-Click option to work right for adding shares).

This tutorial looks to cover all the bases, so give it a try: [URL="https://help.ubuntu.com/community/SettingUpSamba"]https://help.ubuntu.com/community/SettingUpSamba
[/URL]
a hint, if your using vista or get a never-ending prompt for username and password, make sure your NTLM authentication levels are correct for your network. on my net you have to add 
```
client NTLMv2 auth = yes
```
to the authorization section of the smb.conf.

hope that helps,
Franklin

---

