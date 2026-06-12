---
title: "SSH Connection timed out"
date: 2013-06-21
forum: New to Ubuntu
---

### Post by mrenfro on 2013-06-21
Hi!

I have been trying to resolve this issue for quite a while now. What I  intend to do is connect to a remote server that my campus has through  SSH. This server requires a username and a password. Currently, I have  only been able to enter username@hostname before I  get this message  from my terminal ```
ssh: connect to host hostname port  22: Connection timed out

```

  I have been browsing several forums and here are the tips others have suggested:

1.) Change the default port from 22 to something else
2.) Remove ssh and install again

Unfortunately, neither of these have been succesful. I am open to any  suggestions and if more information is needed, I would be happy to give  it upon request.

---

### Post by prodigy_ on 2013-06-21
Um, where to begin...

How do you know the server is even running SSH?

---

### Post by mrenfro on 2013-06-21
Thanks for your reply. Yes, the server is running SSH (the person who updates the files on the server recommended I use it).

---

### Post by prodigy_ on 2013-06-21
Okay. Assuming you're connecting from another network via the Internet, you need to know at least:
1) DNS name or public IP address of the server (public IP means it is provided by an ISP).
2) TCP port the SSH service is bound to on the server.

You can test connectivity with telnet: **telnet DNS_name_or_IP port**. Example: ```
telnet server.example.com 22
``` The response could be something like **SSH-2.0-OpenSSH_5.9p1 Debian-5ubuntu1.1**. If telnet times out, you need to find out what's blocking the connection.

---

### Post by mrenfro on 2013-06-26
Thank-you so much! I think my ISP blocks certain ports. I was finally able to connect when I used a different network.

---

