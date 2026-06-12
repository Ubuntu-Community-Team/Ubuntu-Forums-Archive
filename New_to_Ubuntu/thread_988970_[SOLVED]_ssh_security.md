---
title: "[SOLVED] ssh security?"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by nakama85 on 2008-11-21
I read the document about turning off the password confirmation and only using pub. keys... However I did not really understand how to set it up.

Can someone help?

Thanks

---

### Post by Peter09 on 2008-11-21
The easiest way to set up public key encryption in ubuntu is to use seahorse


Application->Accessories>Password and Encryption Keys

then uses the keys menu to setup a new ssh keyring - from there is automatic.

You will need your ssh server to be working before you do this.

---

### Post by nakama85 on 2008-11-21
> **Peter09 said:**
> The easiest way to set up public key encryption in ubuntu is to use seahorse


Application->Accessories>Password and Encryption Keys

then uses the keys menu to setup a new ssh keyring - from there is automatic.

You will need your ssh server to be working before you do this.

Thanks. I do have my ssh server up and running already.

---

### Post by Peter09 on 2008-11-21
Note - I should have said that you use seahorse on the client, not the server.

-comment was a bit late:)

---

### Post by johnkzin on 2008-11-21
> **Peter09 said:**
> The easiest way to set up public key encryption in ubuntu is to use seahorse


Application->Accessories>Password and Encryption Keys

then uses the keys menu to setup a new ssh keyring - from there is automatic.

You will need your ssh server to be working before you do this.

Doesn't that merely set up/allow the use of keys, and not require the use of keys?

---

### Post by Peter09 on 2008-11-21
It sets the keys up on both the client and the server. It depends on the configuration file on the server as to whether you **must** use keys.

---

