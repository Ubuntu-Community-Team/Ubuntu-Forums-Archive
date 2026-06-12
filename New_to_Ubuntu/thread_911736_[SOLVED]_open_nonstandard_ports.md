---
title: "[SOLVED] open nonstandard ports"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by chenaf on 2008-09-05
Hello, I'm trying to connect to a web server running on this ubuntu computer using an unused port number, 24445, but it could be any random number in port range I suppose. I'd like to use my laptop to connect to the web server on this linux computer.

I can connect to the server using [http://127.0.0.1:24445](http://127.0.0.1:24445) or [http://localhost:24445](http://localhost:24445), but [http://192.168.0.5:24445](http://192.168.0.5:24445) does not work. It also does not work from my laptop.

192.168.0.5 is the ip address of the linux computer.

In contrast, ssh works fine. I can ssh into the linux computer using 192.168.0.5 from the laptop or the linux computer as well as 127.0.0.1 or localhost.

Does anyone have any hints about what I should do? How can I open the 24445 port so that my laptop can see the dev server?

Any help would be appreciated.

---

### Post by knix on 2008-09-05
don't web servers usually run on port 80?

---

### Post by Bakon Jarser on 2008-09-05
You can open ports using universal firewall.  For some reason I can't get ufw to start on boot so you would have to enable it everytime.  You could also use firestarter which has a gui.  You could also add the rules to iptables, which is the linux firewall (firestarter and ufw are frontends for it) but I've never done that before so I don't know how difficult it would be.

---

### Post by chenaf on 2008-09-05
> **knix said:**
> don't web servers usually run on port 80?

yes, but this is just a dev server, not for public use.

---

### Post by chenaf on 2008-09-06
> **Bakon Jarser said:**
> You can open ports using universal firewall.  For some reason I can't get ufw to start on boot so you would have to enable it everytime.  You could also use firestarter which has a gui.  You could also add the rules to iptables, which is the linux firewall (firestarter and ufw are frontends for it) but I've never done that before so I don't know how difficult it would be.

```
sudo ufw status
``` says the firewall is not loaded. I guess I'll try turning it on and playing around with that.


also,

```

$ nmap -p24445 localhost

Starting Nmap 4.53 ( http://insecure.org ) at 2008-09-05 23:50 EDT
Interesting ports on localhost (127.0.0.1):
PORT      STATE SERVICE
24445/tcp open  unknown

Nmap done: 1 IP address (1 host up) scanned in 0.028 seconds
$ nmap -p24445 192.168.0.5

Starting Nmap 4.53 ( http://insecure.org ) at 2008-09-05 23:50 EDT
Interesting ports on 192.168.0.5:
PORT      STATE  SERVICE
24445/tcp closed unknown

Nmap done: 1 IP address (1 host up) scanned in 0.370 seconds

```

I guess this means one side is open and the other side is closed? I'm not sure how to interpret this. Does anyone have more information?

---

### Post by Vivaldi Gloria on 2008-09-06
> **chenaf said:**
> I can connect to the server using [http://127.0.0.1:24445](http://127.0.0.1:24445) or [http://localhost:24445](http://localhost:24445), but [http://192.168.0.5:24445](http://192.168.0.5:24445) does not work. 

You must forward the port in your router.

---

### Post by chenaf on 2008-09-06
> **Vivaldi Gloria said:**
> You must forward the port in your router.

The port is now forwarded and nothing will connect to [http://192.168.0.5:24445](http://192.168.0.5:24445)

I also tried Bakon Jarser's suggestion to use firestarter, yet nothing will connect even after adding a rule to allow the port to everyone. So I turned the firewall back off.

---

### Post by Vivaldi Gloria on 2008-09-06
I wrote the following howto port forward to someone else. Check that you have not omited something.

**1)** Enter the router settings. Every decent router has a setting or table where you can fix the adresses of particular computer (ethernet card). Find that setting which fixes your computer's adress. If there is no such setting then this guide is no good for you.  It can be something of the sorts "Always use the ip 192.168.XX.XX for the computer with the mac adres XX:XX:...". I choose a number like 192.168.1.35. Restart router.

**2)** In a terminal give the command ifconfig. Here is the top lines of its output from my box:

```
vivaldi@narval:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:07:c4:d2:17:ba  
          inet addr:192.168.1.35 ...
...
...
```

Here eth0 is the my main ethernet card. The ip 192.168.1.35 is the ip fixed by the router for that card. So at this step we verify that you indeed get the ip the router reserved for your computer.

**3)** Now since your computer's ip is fixed to 192.168.1.35 you can forward the ports you want to 192.168.1.35. Use your port forward settings (or NAT) of your router to do this. For example when you use an app which uses port TCP 51413 you may need to enable a rule like

start & end ports: TCP 51413, ip:192.168.1.35

in the router.

**4)** Some routers also have a seperate firewall settings in which you may also need to enable ports.

---

### Post by doas777 on 2008-09-06
> **Vivaldi Gloria said:**
> You must forward the port in your router.

are you trying to hit this server from inside or outside of your local network? 192.168.0.5 is a private address, so you can't hit it from outside. if you are inside then you don't need to do anything on the router.

---

### Post by Vivaldi Gloria on 2008-09-06
> **doas777 said:**
> are you trying to hit this server from inside or outside of your local network? 192.168.0.5 is a private address, so you can't hit it from outside. 

In the first post he explains that he's trying it on the server itself!

> if you are inside then you don't need to do anything on the router.

Depends on the router. The sentence 

*"I can connect to the server using [http://127.0.0.1:24445](http://127.0.0.1:24445) or [http://localhost:24445](http://localhost:24445), but [http://192.168.0.5:24445](http://192.168.0.5:24445) does not work"* 

clearly indicates that he can connect on the loopback but not on eth. Only possible blocks I can think of are router and the firewall.

---

### Post by Vivaldi Gloria on 2008-09-06
> **chenaf said:**
> I also tried Bakon Jarser's suggestion to use firestarter, yet nothing will connect even after adding a rule to allow the port to everyone. So I turned the firewall back off.

Firestarter is not a firewall but it's a frontend to iptables which is the firewall that ubuntu comes with. Give the command

```
sudo iptables -L
```

to get a list of current rules. Once you change iptables settings using firestarter, iptables works even if you uninstall firestarter. See

[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

Make sure that the firewall doesn't block your port.

I'm going to sleep now. Goodnight boys & girls.

---

### Post by chenaf on 2008-09-06
> **doas777 said:**
> are you trying to hit this server from inside or outside of your local network? 192.168.0.5 is a private address, so you can't hit it from outside. if you are inside then you don't need to do anything on the router.

Ya, I thought this at first because both computers are on the same side of the router, but that was not the problem. After reading the docs a little more carefully, I realized that I had invoked the server incorrectly. DOH! I had to specify the ip address explicitly otherwise only the loopback ip worked (localhost).

But thanks to everyone that gave advice in this thread. I appreciate your time.

---

