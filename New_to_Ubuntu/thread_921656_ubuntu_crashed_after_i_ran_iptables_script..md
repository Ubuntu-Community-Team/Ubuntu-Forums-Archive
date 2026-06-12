---
title: "ubuntu crashed after i ran iptables script."
date: 2008-09-16
forum: New to Ubuntu
---

### Post by cheeky_lankan on 2008-09-16
hey; last night i was talking to some one on irc and he said he would help me with setting up my iptables; instead of explaining me he sent me a bash script with this: 

#!/bin/sh
#
# Run iptables scripts

### flush existing rules and set chain policy setting to DROP
iptables -F
iptables -F -t nat
iptables -X

iptables -P INPUT DROP
iptables -P OUTPUT ACCEPT
iptables -P FORWARD DROP

### state tracking rules
iptables -A INPUT -m state --state INVALID -j DROP
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT


### ACCEPT rules
iptables -A INPUT -i lo -j ACCEPT
# iptables -A INPUT -p icmp --icmp-type echo-request -m limit --limit 10/second -j ACCEPT



... so i listen to him.. and chmod it and ran the file..After that i did a 
"ipconfig -L" and my iptables listen the new configuration.

i didnt have any clue about what the tables were and what not. He told me to ping my box .. that i wouldnt be able to do it; as my box in now secure .. but when i did ping it..it worked... so then he told me .. to flush the tables .. i did "ipconfig -F"; after i ran that command .. my  computer froze .. so i had to restart it and i have no clue what damage had been done or where i stand. Can anyone tell me the settings on this ..script was something wrong with it .. or what mad my comp freeze 

thnak you 

cheeky_lankan

---

### Post by billgoldberg on 2008-09-16
Use ufw (there is a gui for it called gufw on the internet) to set up your iptables.

UFW is really easy to use. (see man page)

---

### Post by cheeky_lankan on 2008-09-16
So is there something wrong with the script that was sent to me and run on my box ...?

---

