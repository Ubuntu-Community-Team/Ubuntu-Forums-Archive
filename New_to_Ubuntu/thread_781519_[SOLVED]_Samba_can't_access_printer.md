---
title: "[SOLVED] Samba: can't access printer"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by Stefanie on 2008-05-04
I have an Ubuntu laptop and a Windows pc. The windows pc is connected to a printer and network printing is enabled. when i boot my laptop into windows xp, i can connect to the home network and send my print jobs to the pc. 

i wanted to do the same in ubuntu so i followed this [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba) guide. However there is a problem when I try to browse the network. I go to places -> network -> windows network. Then i'm supposed to see the computers in the network,  but i don't see anything...

when i enter  smbclient -L //server -U user in the command line i get an error: "Connection to server failed (Error NT_STATUS_BAD_NETWORK_NAME)" , but I'm sure i entered the correct name of the home network. 

what am i doing wrong? i am using gutsy.

---

### Post by superprash2003 on 2008-05-04
is the ubuntu laptop able to ping the windows machine?

---

### Post by Stefanie on 2008-05-04
I don't know, I'm on campus now (windows pc is at home) so I'll try next weekend.

---

### Post by Stefanie on 2008-05-10
yup, the windows machine can be pinged but still not browsed ...

---

### Post by Stefanie on 2008-05-17
i found a solution, you have to type smb://<ipaddressofothercomputer> in nautilus. sometimes it doesn't work, though.

---

