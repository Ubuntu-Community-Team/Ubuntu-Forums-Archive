---
title: "Can't open page in firefox?!! strange"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by Sec Expert on 2008-05-26
hi dear co-forumers(it's a totally new word i've made it right now!) whatever! I have a very strange problem, well I've just installed Ubuntu and I think I like it but the first thing I did after that was to try to connect to the Internet I use ADSL 128 PPPoE (I mean it is connected to an NIC) well no problem I succeeded to connect to the Internet.The problem began just after I restarted  after that I can't open any pages in Firefox I know I'm connected to the Internet this is the plog command output:



May 25 18:44:54 kh-power pppd[12753]: PPP session is 901

May 25 18:44:54 kh-power pppd[12753]: Using interface ppp0

May 25 18:44:54 kh-power pppd[12753]: Connect: ppp0 <--> eth0

May 25 18:44:57 kh-power pppd[12753]: Remote message: Welcome to use Quidway ROUTER, Huawei Tech.^M^J

May 25 18:44:57 kh-power pppd[12753]: PAP authentication succeeded

May 25 18:44:57 kh-power pppd[12753]: peer from calling number 00:E0:FC:69:D3:72 authorized

May 25 18:44:57 kh-power pppd[12753]: Cannot determine ethernet address for proxy ARP

May 25 18:44:57 kh-power pppd[12753]: local  IP address 89.165.*.*

May 25 18:44:57 kh-power pppd[12753]: remote IP address 89.165.*.*

kh@kh-power
I couldn't get the output of ipconfig command it sas "command not found"
plz help me,by the way my English is not very well please tell me in simple  formal English!:lolflag:

---

### Post by bwhite82 on 2008-05-26
Make sure that FF isn't in "Offline" mode. File>Work Offline

PS: the command is ifconfig and not ipconfig

---

### Post by Sec Expert on 2008-05-27
oh yeah you know offline mode is too obvious.thanks for editting the command.do you think scanning the output helps:lolflag:

---

### Post by Sec Expert on 2008-05-27
at last I came across a command that I think solved my problem.
This is the command:

echo "nameserver 4.2.2.4" | sudo tee /etc/resolv.conf 


but I don't know what the command did that solved my problem.can anyone of you guys(or gals) explain the command and what it does?

---

