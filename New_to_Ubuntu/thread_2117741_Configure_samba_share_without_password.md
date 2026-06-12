---
title: "Configure samba share without password"
date: 2013-02-19
forum: New to Ubuntu
---

### Post by asmiguel on 2013-02-19
Hi,

I've having some problems with configuring my samba network.
I want 1 network share with folders that can only be access by an username without password. The folders in the share must have full access also without authentication.

I've tried different things and im realy confused right now.

What are the requirements in de smb.conf at the global tab so i can realize this?

---

### Post by thermion on 2013-02-19
Add *guest ok = yes* to your smb.conf file

This has to be within the section of your smb share you want to grant guest access to.

---

### Post by asmiguel on 2013-02-19
> **thermion said:**
> Add *guest ok = yes* to your smb.conf file

This has to be within the section of your smb share you want to grant guest access to.

thanks for your quick reply. i dont want this for the share i mean when you get at the network with the shared folders

---

### Post by thermion on 2013-02-19
I'm affraid I don't fully understand what you're trying to do.
Basically, you wan't to access your shares with a specific user, but without a password?

I'm not sure if this is possible, but you could try to create this user (if it does not exsist), then run *smbpasswd [username]* and see if it accepts empy passwords. Also, you'll need to add the folowing line to your smb.conf file and restart smbd (not 100% sure about this):

*security = SHARE*

---

### Post by gordintoronto on 2013-02-19
This is the source of confusion:
"I want 1 network share with folders that can only be access by an username without password."

Could you restate it with different words?

---

