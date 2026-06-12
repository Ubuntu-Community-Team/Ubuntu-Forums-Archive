---
title: "[SOLVED] Two &amp;quot;equal&amp;quot; user accounts"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by rockstarrem on 2008-07-27
When I type "users" in terminal my name shows up twice. As far as I can remember I did not create another account for myself. What do I do in this situation? Could it be a program that made me another account? A security breach?

---

### Post by Oldsoldier2003 on 2008-07-27
> **rockstarrem said:**
> When I type "users" in terminal my name shows up twice. As far as I can remember I did not create another account for myself. What do I do in this situation? Could it be a program that made me another account? A security breach?

no its because you are loggin in twice as far as the system is concerned. once in the terminal and once in the gui. Do
```
who
``` and you'll see what I mean.

---

### Post by eightmillion on 2008-07-27
Oldsoldier2003 is correct. I'm logged in twice.
```
$ who
angus    tty3         2008-07-24 06:47
angus    :0           2008-07-26 02:44

```
As you can see, I'm logged in on tty3 and display :0

---

### Post by rockstarrem on 2008-07-27
Alright I have another question. I set up the "Firestarter" firewall and I'm getting a lot of connections from all these random IP addresses. Is this a security concern?

---

### Post by eightmillion on 2008-07-27
Is your computer connected directly to the internet. I.E. you aren't connected to a router?

---

### Post by rockstarrem on 2008-07-27
Yes, I am connected to a router.

---

### Post by eightmillion on 2008-07-27
Chances are these are normal connections. Does firestart tell you whether the connections are UDP or TCP and what port they are on? Your computer makes many connections that you may not be aware of just browsing the web. For example, here's a list of open connections on my PC.
```
$ netstat -a                                                                                                                 
Active Internet connections (servers and established)                                                                                          
Proto Recv-Q Send-Q Local Address           Foreign Address         State                                                                      
tcp        0      0 *:6881                  *:*                     LISTEN                                                                     
tcp        0      0 *:netbios-ssn           *:*                     LISTEN                                                                     
tcp        0      0 *:sunrpc                *:*                     LISTEN                                                                     
tcp        0      0 localhost:7634          *:*                     LISTEN                                                                     
tcp        0      0 *:51708                 *:*                     LISTEN                                                                     
tcp        0      0 *:microsoft-ds          *:*                     LISTEN                                                                     
tcp        0   5521 lappy.local:41509       bas1-london14-108:56611 ESTABLISHED                                                                
tcp        0      0 lappy.local:57425       201-34-82-100.pae:41643 ESTABLISHED                                                                
tcp        0      0 lappy.local:58122       69.60.7.210:www         ESTABLISHED                                                                
tcp        0      0 lappy.local:51099       191-241.amazon.com:www  ESTABLISHED                                                                
tcp        0      0 lappy.local:56230       18981009152.user.:17576 ESTABLISHED                                                                
tcp        0      0 lappy.local:40065       s108p21.home.99ma:33389 ESTABLISHED                                                                
tcp        0      0 lappy.local:51251       78.93.126.95:15435      ESTABLISHED                                                                
tcp        0      0 lappy.local:42407       69.60.7.199:www         ESTABLISHED                                                                
tcp        0      0 lappy.local:57713       69.60.7.199:www         ESTABLISHED                                                                
tcp        0      0 lappy.local:56436       63-144-121-173.dia.:www TIME_WAIT                                                                  
tcp        0      0 lappy.local:38166       205.234.218.73:www      ESTABLISHED                                                                
tcp        0      0 lappy.local:55790       s3.amazonaws.com:www    TIME_WAIT                                                                  
tcp        0      0 lappy.local:42210       unknown.level3.net:www  TIME_WAIT                                                                  
tcp        0      0 lappy.local:59164       s0106001346a7d2e5:51413 ESTABLISHED                                                                
tcp        0      0 lappy.local:37372       201-68-165-109.ds:17940 ESTABLISHED                                                                
tcp        0    171 lappy.local:33988       189-041-102-092.x:51601 ESTABLISHED                                                                
tcp        0      0 lappy.local:42209       unknown.level3.net:www  TIME_WAIT                                                                  
tcp        0      0 lappy.local:46787       20129219136.user.:63643 ESTABLISHED                                                                
tcp        0      0 lappy.local:48129       a72-246-31-18.deplo:www ESTABLISHED                                                                
tcp        0      0 lappy.local:38164       205.234.218.73:www      ESTABLISHED                                                                
tcp        0      0 lappy.local:41438       host166-17-dynami:56297 ESTABLISHED                                                                
tcp        0      0 lappy.local:54081       cpc3-derb1-0-0-cus:9112 ESTABLISHED                                                                
tcp        0      0 lappy.local:60882       cpe-67-9-165-68.a:30584 ESTABLISHED                                                                
tcp        0  15290 lappy.local:48461       adsl-dyn77.78-98-:27795 ESTABLISHED                                                                
tcp        0   2796 lappy.local:49529       85.103.86.56:6881       ESTABLISHED                                                                
tcp        0      0 lappy.local:39258       88-111-153-222.dy:16659 ESTABLISHED                                                                
tcp        0      0 lappy.local:34046       digg.com:www            ESTABLISHED                                                                
tcp        0      0 lappy.local:34052       digg.com:www            ESTABLISHED                                                                
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN                                                                     
udp        0      0 *:901                   *:*                                                                                                
udp        0      0 lappy.local:netbios-ns  *:*                                                                                                
udp        0      0 *:netbios-ns            *:*                                                                                                
udp        0      0 lappy.local:netbios-dgm *:*                                                                                                
udp        0      0 *:netbios-dgm           *:*                                                                                                
udp        0      0 *:53540                 *:*                                                                                                
udp        0      0 *:bootpc                *:*                                                                                                
udp        0      0 *:mdns                  *:*                                                                                                
udp        0      0 lappy.local:49262       192.168.2.1:domain      ESTABLISHED                                                                
udp        0      0 *:sunrpc                *:*                                                                                                
udp        0      0 lappy.local:50160       192.168.2.1:domain      ESTABLISHED                                                                
udp        0      0 *:37875                 *:*                                                    
```

---

### Post by hyper_ch on 2008-07-27
Firestart is NO firewall!

---

### Post by Martje_001 on 2008-07-27
> **hyper_ch said:**
> Firestart is NO firewall!
It's a front-end to ip-tables.

---

### Post by El Conquistador on 2008-07-27
Also another thing is is you do any Bittorrent downloading you will get alot of connections showing up. even after you close your client. just keep that in mind.

---

### Post by rockstarrem on 2008-07-27
> **El Conquistador said:**
> Also another thing is is you do any Bittorrent downloading you will get alot of connections showing up. even after you close your client. just keep that in mind.

Why is this? Is this a bad thing?

---

### Post by El Conquistador on 2008-07-27
no its not a bad thing when using bittorrent you are downloading from other people..so you need multiple connections for all those people.

---

### Post by rockstarrem on 2008-07-27
Yes but why are they connecting after my client is closed?

---

### Post by eightmillion on 2008-07-27
It's just the nature of bittorrent. It often takes some time to propogate the fact that a certain node is no longer on the network so clients will still be trying to connect to you for a while. These connections are just dropped. It's nothing to worry about.

---

### Post by rockstarrem on 2008-07-27
Alright, thanks!

---

### Post by El Conquistador on 2008-07-27
> **eightmillion said:**
> It's just the nature of bittorrent. It often takes some time to propogate the fact that a certain node is no longer on the network so clients will still be trying to connect to you for a while. These connections are just dropped. It's nothing to worry about.

you beat me to it...thanks. and sorry for not answering it in my last post. i guess i was a little confused.

---

