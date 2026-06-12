---
title: "Best remote admin solution for a home user behind a home router?"
date: 2012-10-06
forum: New to Ubuntu
---

### Post by cornersolution on 2012-10-06
I'm giving my mom an Ubuntu laptop the next time she visits me. I want to remotely administer it (from my own Ubuntu laptop) when needed. 

All the built-in remote admin methods I know of would require her to have a public IP address, which she doesn't have. She's sitting behind a Linksys router on a home cable internet connection. The IP is dynamic, and I don't want to mess around with port forwarding.

What's the best way for me to access her computer? Is there any way to do it with Ubuntu's built-in tools, if she doesn't have a public IP address? Otherwise, should I try TeamViewer? (Of course I always prefer to use the built-in Ubuntu tools if possible.) Last resort method is Skype screen sharing, which is what we do now.

---

### Post by albandy on 2012-10-06
As with any other OS, you need a remote service provider to acces your computer if you don't want to make port forwarding.

Also a solution is to convert your PC in a neorouter server and your mother's one in a neorouter client. So only your computer have to be port forwarded to the neorouter port.

Neorouter is an easy way to make little vpn's.

So with neorouter and the ubuntu integrated remote desktop (vnc protocol) you can manage your mother's pc.

---

### Post by cornersolution on 2012-10-06
Albandy, perfect information, and perfect reply. Many thanks. I'll proceed with TeamViewer, and will also take a look at Neorouter.

---

