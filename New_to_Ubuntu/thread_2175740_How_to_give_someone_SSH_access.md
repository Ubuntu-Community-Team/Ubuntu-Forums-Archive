---
title: "How to give someone SSH access?"
date: 2013-09-20
forum: New to Ubuntu
---

### Post by lakz on 2013-09-20
Hi,

I have an issue with a specific software, and the developer needs SSH access to my Ubuntu Server 12.04 LTS.

Could someone help me with this? I'd need idiot-proof step-by-step instructions.

Thanks :rolleyes:

---

### Post by never2far on 2013-09-20
Hello,

I think the best way is to request his ssh public key. That key must be copied in /home/user/.ssh/authorized_keys

Of course your server must have SSH server started ( run this in your terminal: status ssh  it should look like this: ssh start/running, process 1327)

---

### Post by nerdtron on 2013-09-21
Do you trust this developer? The developer might need root access to modify some files. Here's the official doc to add a user with sudo access
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) 
Create and account for him and after his session, delete his account.

---

### Post by DuckHook on 2013-09-21
> **nerdtron said:**
> Do you trust this developer?

+++1

It gives me the willies to grant root SSH access to *anybody*, even myself. On my boxes, I allow myself only strictly limited SSH access privileges. Under no circumstances leave such SSH access password enabled. Allow only certificate-based access. If the developer does not need root, then create an account with no root privileges. Once you grant root access just once, a rogue developer essentially has unlimited access to your box thereafter, even if you subsequently delete the initial account.

Not to imply that your developer is rogue, but you are potentially playing with fire here, so understand your risks and make informed decisions.

---

