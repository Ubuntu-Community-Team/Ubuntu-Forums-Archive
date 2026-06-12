---
title: "Proxy how does it work?"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by 7raTEYdCql on 2008-08-09
I am at present in university where the internet is connected via a proxy. How does the proxy work. Can someone give me the basic explanation.

---

### Post by ibizatunes on 2008-08-09
Basically a proxy server is filter of the internet, it can filter on content, ip address, port and application
Basically design to stop you abusing your uni IT system - ie no porn, and no file sharing (anything that could put the uni at risk)

---

### Post by 7raTEYdCql on 2008-08-09
See there was a restriction put on the per download one user is allowed to do. I got around it when some of my friends told me to use something like proxychains. Dont know what i really does but i can download packages which are more than 5mb. But unfortunatley cant download torrent files<they are also blocked>. is there a way to go around it. [I hope.]

---

### Post by pi.boy.travis on 2008-08-09
You probably shouldn't circumvent your university's proxy rules.  That could get you in some serious trouble. . .

---

### Post by st33med on 2008-08-09
> **pi.boy.travis said:**
> You probably shouldn't circumvent your university's proxy rules.  That could get you in some serious trouble. . .

But then, what are college students supposed to do ;)
Yeah, you probably shouldn't try to get around it. You can connect to your college's proxy in Firefox by going to Edit>>Preferences>>Advanced>>Network And hit the Settings... button below Connection.

---

### Post by 7raTEYdCql on 2008-08-09
I can do all that. I have gone around the 5mb rule using proxychains. Can someone explain to me what does this package do. And how it works. I just simply followed my friend, and didnt understand what they told me.

---

### Post by kshtjsnghl on 2008-08-16
in the command terminal type type 
 sudo gedit /etc/proxychains.conf
and then in the add your http proxies more than one
and then when you come to your web browser - select no proxy in network connections.

what it actually does i think it lets you access the internet through some other private server and hence you can overcome the restrictions.

---

### Post by Vishal Agarwal on 2008-08-16
Proxy server are used to control the users, from using the internet.
Using the Proxy server the server administrator can control the user in any manner.
in your case, if you are restricted to download less then 5 MB, then u cannot download anything more then 5MB.

How you are connected to your network ?

If it is a DHCP server or it is a static IP ?

---

### Post by Midahed on 2008-08-16
> **i.mehrzad said:**
> I am at present in university where the internet is connected via a proxy. How does the proxy work. Can someone give me the basic explanation.
A proxy server is a sort of intermediary between you and the internet or other servers on your local network.  The ability (or otherwise) to download torrents might be implemented through a rule on a firewall, rather than being a function of the proxy server.  

Proxy servers are also used to reduce the bandwidth requirement on your University's internet connection by caching frequently requested downloads locally, rather than going out onto the internet to service each individual request for that file or web page

If the IT guys supporting your system are on the ball, they should be capable of preventing you circumventing the proxy if that's what they really want. ;)

---

### Post by 7raTEYdCql on 2008-08-17
I have got around the "maximum download of 5mb" rule that is implemented in campus by using proxychains. But however my torrents are still blocked. Is there anyway i can get around that. I know this forum is not meant for this kind of questioning but if someone can help...

---

### Post by 7raTEYdCql on 2008-08-17
I think i am connected via a static IP. In the sense i actually enter the IP address in the connection settings.

---

### Post by TJCIB on 2008-08-17
Be careful "circumventing" university systems.  You should check your user agreement/internet policy.

For example, a few years ago Duke University did a big crack down on music/file sharing.  Hundreds of students were fined big bucks, and a number of students were caught breaking other policies in the process and expelled from school.

Its not really worth risking your enrollment.  If you want unlimited access...live off campus...

---

### Post by Vishal Agarwal on 2008-08-19
> **i.mehrzad said:**
> I think i am connected via a static IP. In the sense i actually enter the IP address in the connection settings.

1. R u using UBUNTU or Windows on client side ?

If u are using windows then issue the below command in command prompt
> ipconfig /all
to see your IP
and then 
> ipconfig /renew
to see if the ipaddress change. Also it will show you the DHCP settings.

2. First of all u confirm that you have a static ip / dynamic ip.

---

### Post by 7raTEYdCql on 2008-08-19
ipconfig doesn't seem to be a command

---

### Post by kk0sse54 on 2008-08-19
> ipconfig doesn't seem to be a command 

Yes ipconfig is a command for windows, it is not a command under Ubuntu however. A similiar command under Ubuntu would be ifconfig

---

### Post by Vishal Agarwal on 2008-08-20
What is the output of your command ?
Did you recognize your IP type Static/Dynamic ?

---

### Post by 7raTEYdCql on 2008-08-20
This was the output of ifconfig

```

mehrzad@mehrzad-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:24:f4:4d:8e  
          inet addr:10.3.12.84  Bcast:10.3.12.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:24ff:fef4:4d8e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13845 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1894 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1951473 (1.8 MB)  TX bytes:219158 (214.0 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1606 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1606 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:80300 (78.4 KB)  TX bytes:80300 (78.4 KB)

mehrzad@mehrzad-laptop:~$ 


```

---

