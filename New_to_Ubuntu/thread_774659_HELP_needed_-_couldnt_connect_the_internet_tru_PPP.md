---
title: "HELP needed - couldnt connect the internet tru PPPOE"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by umteht on 2008-04-29
i have just installed Ubuntu couple days ago..and i tried to connect to the Internet by following the instruction stated in the help page. --> i do the following things
1. "type" sudo pppoeconf (in the terminal)
2. enter yes for all the instructions shown
3. "type" the correct username
4. "type" the correct password
5. "type" sudo pon dsl-provider (in the terminal)
6. type plog

but i cannt connect to the internet. error msg shown:
//-------------------------------------------------------------
euwern@euwern-laptop:~$ sudo pppoeconf
[sudo] password for euwern:
Plugin rp-pppoe.so loaded.
euwern@euwern-laptop:~$ sudo pon dsl-provider
Plugin rp-pppoe.so loaded.
euwern@euwern-laptop:~$ plog
Apr 29 14:16:02 euwern-laptop pppd[6168]: Connection terminated.
Apr 29 14:16:20 euwern-laptop pppd[6175]: Plugin rp-pppoe.so loaded.
Apr 29 14:16:20 euwern-laptop pppd[6177]: pppd 2.4.4 started by root, uid 0
Apr 29 14:16:20 euwern-laptop pppd[6177]: PPP session is 47263
Apr 29 14:16:20 euwern-laptop pppd[6177]: Using interface ppp0
Apr 29 14:16:20 euwern-laptop pppd[6177]: Connect: ppp0 <--> eth0
Apr 29 14:16:22 euwern-laptop pppd[6177]: Remote message: Authentication failure
Apr 29 14:16:22 euwern-laptop pppd[6177]: PAP authentication failed
Apr 29 14:16:22 euwern-laptop pppd[6177]: Connection terminated.
euwern@euwern-laptop:~$ 
//---------------------------------------------------------------

for your information, i hv window xp os and ubuntu os at the same time. i can connect to the internet tru window xp. for window xp
i just go to my network connection->create new connection->click connect to the internet->click set up my connection manually-> click connect using a broadband connection that requires a user name and password(pppoe)->enter my ISP name->enter my username and password.

please help.. thank you so so much for any help given

---

### Post by lucky.developer on 2008-05-03
i have the same problem dude... i have just created a thread for it...

---

### Post by umteht on 2008-05-08
i hv figured it out..^^

i reset my router settings and make it connects to the modem tru 
PPPOE.. then just plug the cable (connecting my router and my pc)

thx anyway^^

---

### Post by sujoy on 2008-05-08
> Apr 29 14:16:22 euwern-laptop pppd[6177]: Remote message: Authentication failure

i guess that means you entered the wrong password, i am using bridge mode myself and it works fine. one more thing,

> euwern@euwern-laptop:~$ sudo pppoeconf
[sudo] password for euwern:
Plugin rp-pppoe.so loaded.

it shouldn't show rp-pppoe.so loaded after pppoeconf, the plugin is loaded only when you dial the connection using pon <connection-name>

---

### Post by SupaSonic on 2008-05-08
It does show if you choose 'connect now' in pppoeconf

---

