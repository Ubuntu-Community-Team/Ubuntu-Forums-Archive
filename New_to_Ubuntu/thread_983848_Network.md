---
title: "Network"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by andrewvanzyl on 2008-11-16
Hi All
Just installed 8.1 on dual boot with XP Professional SP2 on my home desktop. My notebook is part of a work domain. I have a twisted pair cable connecting the two computers. I used to have a mapped drive to my desktop in windows.

How do I configure Ubuntu to accept a connection from my notebook as I had have in XP?

Thanks, Andrew

---

### Post by Scene on 2008-11-16
I'm new to Ubuntu but I'm using some logic.
Maybe add it to a firewall or something?
I'm not too sure.

---

### Post by andrewvanzyl on 2008-11-16
No firewall installed. Works perfectly XP to XP with a mapped drive.

---

### Post by Scene on 2008-11-16
Try this. I found it.
[http://www.techotopia.com/index.php/Configuring_Ubuntu_Linux_Wireless_Networking](http://www.techotopia.com/index.php/Configuring_Ubuntu_Linux_Wireless_Networking)

---

### Post by andrewvanzyl on 2008-11-16
It's a wired connection, PC to pc, not wireless

---

### Post by prshah on 2008-11-16
> **andrewvanzyl said:**
> 
How do I configure Ubuntu to accept a connection from my notebook as I had have in XP?

Do you mean you want to create a share on your ubuntu computer that can be accessed from XP? In that case, press Alt+F2, and give the command ```
shares-admin
```, then click "Unlock" (You'll have to enter your password) and create shares as you want. Note: shares-admin has been moved under PolicyKit, so no "sudo"

---

