---
title: "[SOLVED] Problem with my connection speed"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by LastWho on 2008-09-30
Hi, i m using linux from 2 weeks now

here is my problem with as much details as i could 


**Short story:**
When i installed ubuntu, everything was doing fine, (i was able with 128 kb/s to listen to radio station, download, and surf on websites at the same time.. which was impossible under wintoz) till i started using azureus, which was showing me constantly a red lamp saying that i ve a NAT problem... and from that i finished with having a half speed connection; 

[B]
Long story:[/B]
at first, i tried to fix the NAT problem by following the steps in [azureuswik]("http://www.azureuswiki.com/index.php/NAT_problem")i, and what i did is:
> 
1- Modem:[INDENT]Create a static IP address:
i clicked on "wired network connection" --> manuel configuration --> and i set up a static ip
[/INDENT][INDENT]Port Forwarding:
i followed theses instructions: [Portforwording.com]("http://www.portforward.com/english/routers/port_forwarding/Huawei/SmartAX-MT880/Azureus.htm")
the port i ve chosen a port "xxxxx" a number from  49125 to 65535 .. i added it to the modem's NAT as recommended in the link above

[/INDENT]2- Port Forwarding on Ubuntu:[INDENT]in a terminal:
```

sudo iptables -I INPUT -p tcp --dport xxxxx -j ACCEPT
sudo iptables -I INPUT -p udp --dport xxxxx -j ACCEPT
```then i created with nano this file:
```
sudo nano etc/init.d/iptables_azureus  
      
(sleep 120
         /sbin/iptables -I INPUT -p tcp --dport xxxxx -j ACCEPT
         /sbin/iptables -I INPUT -p udp --dport xxxxx -j ACCEPT ) &
 
```[/INDENT][INDENT]Then: 
```
sudo chmod +x /etc/init.d/iptables_azureus
sudo update-rc.d iptables_azureus start 51 S .
```

And here is the result:
```
sudo iptables -L

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     udp  --  anywhere             anywhere            udp dpt:xxxxx
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:xxxxx

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination   

```[/INDENT]after all that i restarted my PC and my modem, to find that the azureus red lamp is always present...
Next i tried to change my ip address --> so i couldn't access to my modem by using mozilla till i pushed the "reset button" of my modem .. i restarted my pc .. then i reconfigured my modem as i did the first day i bought it :D

.......

Now my connection is back, i ve a new ip address (but not static, i let the modem/pc pick one) my iptables -L results are the same, ... but [COLOR=Red]**the problem**[/COLOR] is that i ve not the same download speed i m used to ve (16 kb/s --> 9 kb/s) .. (not by using P2P but direct download)
i checked also my internet connection speed with [website]("http://mire.ipadsl.net/speedtest.php") provided by my ISP: 
88.40 Kbps  (11.05 Ko/sec) --> it used to be: 128 Kbps  (16 Ko/sec)

and of course the freaking red lamp of the azureus is still there :(

Should i reinstall ubuntu or what? :(
(because i really want to get back the privileges i had when i started using it)


(ps sorry for my bad eng)

---

