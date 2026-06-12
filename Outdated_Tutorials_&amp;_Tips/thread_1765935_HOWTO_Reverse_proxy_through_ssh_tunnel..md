---
title: "HOWTO: Reverse proxy through ssh tunnel."
date: 2011-05-23
forum: Outdated Tutorials &amp; Tips
---

### Post by schmick on 2011-05-23
Situation:
[LIST]
[*]You got access to a client's computer behind a firewall through ssh.
[*]The client's computer hasn't got internet access. It's in an intranet.
[*]You need to install software, so you must give that box internet access for some time.
[/LIST]

Procedure:
[LIST]
[*]Install a proxy (squid) in your box.
[*]Configure it using any port you like (3128 in my case).
[*]For security, give it just localhost access. (bind only to localhost)
[*]SSH to your client's machine with a reverse tunnel (-R). This will open a port on the client's side to tunnel to the host (your) box. (ssh -R 3128:localhost:3128 user@client_ip)
[/LIST]

Done that, you can define the proxy to use for apt
Insert in /etc/apt/apt.conf the following line:
  ```
Acquire::http::Proxy "http://localhost:3128";
```
Now, this should be your situation:
On the client's box, APT uses localhost:3128 as proxy, which tunnels back to your box, to your squid, which is running on localhost:3128.

The procedures on using ssh and installing and configuring squid are outside the scope of this howto, and it's intended for the average-advanced user.
For information on how to install squid and how to use ssh for tunneling, please refer to the man pages or search the forums.

---

