---
title: "[SOLVED] Public Key Auth for SSH"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by Nxion on 2008-08-18
I have been trying to setup  my server so when I ssh to it, it will prompt me for a pass phase and not for the password. But I have been unable to get that to work. I have generated the keys but I cant get this implemented. when I ssh to a machine to test it. it prompts me to enter a password. For some reason it wont use the public keys for authentication.

Am I missing a step here? Can some one point me in the direction of a guide? Or help me pin point where I went wrong :).

Thanks!

---

### Post by eldragon on 2008-08-18
you generated your keys with the client machine?

once you got the public/private par with the client machine. you have to append the public key to ~/.ssh/authorized_keys in the server

and of course, your private key must stay on the client's machine at ~/.ssh/

when generating the keys, you should have set the passphrase. thats it.

---

### Post by Nepherte on 2008-08-18
[https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html](https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html)

---

### Post by Nxion on 2008-08-18
> **Nepherte said:**
> [https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html](https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html)

So am I to understand that where it stats in the SSH Keys section of the OPen SSH guide, I have to run all those commands on the server correct?

---

### Post by Nepherte on 2008-08-18
You can generate the public/private key pair on your own computer. This is something you have already done. Afterwards you put the public key on the remote computer (by ssh, ftp, ...). From then on, you have to run the specified commands on that remote computer, as you figured out already.

---

### Post by CautionaryX on 2008-08-18
This might have some more information which can help you out:

[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

---

### Post by Nxion on 2008-09-11
Thanks everyone. It works now :)

---

