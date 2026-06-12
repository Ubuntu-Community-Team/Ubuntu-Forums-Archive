---
title: "how do I list my RSA key fingerprint SSH question."
date: 2008-05-10
forum: New to Ubuntu
---

### Post by daimaru on 2008-05-10
I'm trying to log into my laptop from my desktop and vice versa using ssh. I get the RSA key message, because I just deleted my known_hosts file. 

```
The authenticity of host '192.168.178.30 (192.168.178.30)' can't be established.
RSA key fingerprint is 83:d7:be:fe:5e:91:98:f2:14:0b:a4:f6:2c:e5:21:5a.
Are you sure you want to continue connecting (yes/no)? yes
```What I would like to know is how can I display my RSA key fingerprint on my desktop or laptop pc ? So I know that this is the right fingerprint.

---

### Post by jrib on 2008-05-12
ssh-keygen -l -f /etc/ssh/ssh_host_rsa_key

---

### Post by daimaru on 2008-05-13
> **_jason said:**
> ssh-keygen -l -f /etc/ssh/ssh_host_rsa_key
thx jason that was what i was looking for.

---

