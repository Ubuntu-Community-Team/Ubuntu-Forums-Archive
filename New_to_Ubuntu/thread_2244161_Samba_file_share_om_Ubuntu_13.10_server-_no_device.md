---
title: "Samba file share om Ubuntu 13.10 server- no device can connect"
date: 2014-09-14
forum: New to Ubuntu
---

### Post by Ekeout on 2014-09-14
Hi all.

Did search for this query and found variants, however I am still unable to get anything on the same LAN as my iMac running 13.10 server to connect to its file sharing service (via samba, where "anything" is my Win 7 PC and a Nexus 7 with ES File explorer)
.
Have done [https://help.ubuntu.com/community/How%20to%20Create%20a%20Network%20Share%20Via%20Samba%20Via%20CLI%20%28Command-line%20interface/Linux%20Terminal%29%20-%20Uncomplicated,%20Simple%20and%20Brief%20Way](https://help.ubuntu.com/community/How%20to%20Create%20a%20Network%20Share%20Via%20Samba%20Via%20CLI%20%28Command-line%20interface/Linux%20Terminal%29%20-%20Uncomplicated,%20Simple%20and%20Brief%20Way)!
and have tried connecting with just the default smb.conf - both other LAN devices say they can't find the server.


->The iMac is connected to the LAN via a usb-ethernet adapter (lightning claimed the ethernet port) and this interface is known as eth1.

Both other devices on the LAN receive a reply to ping from the iMac.

I try to connect using \\<IP>\<sharedfolder> from the Win 7 PC and the same minus the initial \\ from ES File explorer on the Nexus 7. Have tried just the IP with the default samba settings, same issue.

If anyone could shed some light on this I'd be grateful.

Cheers

---

### Post by bab1 on 2014-09-14
> **Ekeout said:**
> Hi all.

Did search for this query and found variants, however I am still unable to get anything on the same LAN as my iMac running 13.10 server to connect to its file sharing service (via samba, where "anything" is my Win 7 PC and a Nexus 7 with ES File explorer)
.
Have done [https://help.ubuntu.com/community/How%20to%20Create%20a%20Network%20Share%20Via%20Samba%20Via%20CLI%20%28Command-line%20interface/Linux%20Terminal%29%20-%20Uncomplicated,%20Simple%20and%20Brief%20Way](https://help.ubuntu.com/community/How%20to%20Create%20a%20Network%20Share%20Via%20Samba%20Via%20CLI%20%28Command-line%20interface/Linux%20Terminal%29%20-%20Uncomplicated,%20Simple%20and%20Brief%20Way)!
and have tried connecting with just the default smb.conf - both other LAN devices say they can't find the server.


->The iMac is connected to the LAN via a usb-ethernet adapter (lightning claimed the ethernet port) and this interface is known as eth1.

Both other devices on the LAN receive a reply to ping from the iMac.

I try to connect using \\<IP>\<sharedfolder> from the Win 7 PC and the same minus the initial \\ from ES File explorer on the Nexus 7. Have tried just the IP with the default samba settings, same issue.

If anyone could shed some light on this I'd be grateful.

Cheers
From the server post the output of these 2 commands```
cat /etc/samba/smb.conf

smbtree -d3
```

Place the text inside [code] blocks so the formatting is preserved.  You can do this by clicking on the **[SIZE=4]#[/SIZE]** icon at the top right of the advanced editor and placing the text inside.

---

### Post by Vladlenin5000 on 2014-09-14
Please note that 13.10 is EoL and not supported in this forums.

---

