---
title: "Can join Domain but can't ping computer name"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by ambar_N on 2008-08-16
Hii...

I try to study ubuntu in my company, I got a problem when connect to my network. My Domain using win2k.

I can login using user in domain Active Directory, but I can't ping another computer from my ubuntu workstation using the computer name.

I join domain uing likewise-open.

Please help me to solve thi problem,
Thanks.

---

### Post by brettg on 2008-08-16
OK, clearly english is not your first language which is fine but I am having trouble understanding what you are asking for.

Are you saying you can log into  a Windows domain from your ubuntu box but you can't resolve names using dns?

If that is the case then you need yo take a look at what address(s) you have in /etc/resolv.conf. Is the address in there the correct one? You can confirm it by checking another PC that can ping by dns. If you need to do that on Windows open a command prompt and type ipconfig /all.

If that gives you the same dns resolvers as your ubuntu box then you can try pinging the dns server direct by ip address and see if it responds that way.

If you can't ping it then you may have a routing problem, if you can ping it and it is the same dns server as other working pc's on your network, then it really should be working.

Another thing you can try is to use the opendns servers. I can't remember the address's but you can get them by browsing [www.opendns.org](www.opendns.org). Put their IP's into /etc/resolv.conf and see how that goes. Note that opendns will only resolve addresses on the internet, not local addresses on your LAN

---

### Post by ambar_N on 2008-08-19
Thanks brettg for your effort,

Yesh.. english is not my first lenguage, couse I'me live in Indonesia.
I'm sorry for my english.:biggrin::biggrin:

What I mean is, I can log in using user name in Domain active directory (like usually I log in to windows box).
I can share file with other PC, I can ping other PC or my DNS using IP but can't ping using PC name.

I'm sure if my DNS address in /etc/resolv.conf is correct.

Oh ya, in my company have internal web, usually we access this web using [http://servername/webname](http://servername/webname) (using windows)
But in ubuntu box we must using the ip like : [http://111.11.11.1/webname](http://111.11.11.1/webname).

I need my ubuntu box to resolve address on my LAN, not from internet.

Hope you understand what I mean....:):D:D
Thanks for your help...

---

