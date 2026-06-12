---
title: "DHCP Help"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by mustimasti on 2008-07-14
WELL i m new to ubuntu i just want to explain the network first

i am having sbs2003 server and configured with dns and dhcp and i have installed a new server in current network using static ip address from small business server 2003 dhcp this ip is reserved for ubuntu server i have installed ldap server and i am using dns of sbs2003 server, i m getting internet connection from the sbs server

now i need to configured dhcp server and on ubuntu so that i have 2 different network i will use sbs 2003 server ip address in 1 nic card as internet connection then i want to configure another card as dhcp so which ever computer connect to this network get automatic ip address,

now my conncern is do i need to have DNS installed in the server as i am using sbs 2003 dns and if i installed dns then do i need to change the setting of ldap server as it is using sbs2003 server dns

and please guide me through step by step process

---

### Post by collinp on 2008-07-14
I doubt you need to have dhcp installed, your existing dhcp server should work. Sorry if i am getting the wrong idea, you didnt lay your post out well.

---

### Post by mustimasti on 2008-07-14
well i dont want to use my sbs2003 dhcp i m only static ip from sbs2003 for accessing internet line to my server then i want to configure dhcp on ubuntu server so the machine which i connect in new switch will get ip address from the ubuntu server ok, i have to switch i is for sbs2003 server and i have another spare swithc where i can make another network

---

