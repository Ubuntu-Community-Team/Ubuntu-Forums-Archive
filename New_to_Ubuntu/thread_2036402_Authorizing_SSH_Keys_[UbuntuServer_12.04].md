---
title: "Authorizing SSH Keys [UbuntuServer 12.04]"
date: 2012-08-01
forum: New to Ubuntu
---

### Post by Banana937 on 2012-08-01
I recently built a server to be used as a webserver, a Minecraft server, and a TeamSpeak server. I want to run the webserver and the TeamSpeak server from the root account, but I want to run the minecraft server from a separate account (mcsa) so I don't have the co-owners of my server messing with my website. I created a new account with the command:
```
sudo adduser mcsa
```
And when I SSH in as mcsa, there is no ".ssh" directory with an "authorized_keys" file. Should I simply create this directory and the file, or is there a way to properly set up this file? I don't want to give them the password to the account, I simply want to authorize their key so I can easily remove their SSH privileges if I need to.

---

### Post by papibe on 2012-08-01
Hi Banana937.

By default there's no keys provided. Follow this [guide]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys") to create and copy your keys.
> **Banana937 said:**
> I want to run the webserver and the TeamSpeak server from the root account, ...

NOT recommended! A crash or security breach of any of those services can compromise your whole machine.

Regards.

---

### Post by Banana937 on 2012-08-01
> **papibe said:**
> Hi Banana937.

By default there's no keys provided. Follow this [guide]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys") to create and copy your keys.


NOT recommended! A crash or security breach of any of those services can compromise your whole machine.

Regards.

I followed that guide and generated the keys, but there is still no "authorized_keys" file.

---

### Post by papibe on 2012-08-01
Could you post the log an connection attempt using the triple verbose options?
```
ssh -vvv ...
```
Regards.

---

### Post by Banana937 on 2012-08-01
> **papibe said:**
> Could you post the log an connection attempt using the triple verbose options?
```
ssh -vvv ...
```
Regards.

Apologies -- I skipped the section on transferring the key to the server. It works now.

Thanks!

---

