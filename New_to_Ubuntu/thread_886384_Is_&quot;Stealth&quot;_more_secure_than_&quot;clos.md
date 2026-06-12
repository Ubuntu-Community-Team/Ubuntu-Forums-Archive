---
title: "Is &quot;Stealth&quot; more secure than &quot;closed&quot; ports?"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by Brian_Newbie on 2008-08-11
I've heard that it's better to be in "stealth mode" when surfing the internet than my computer's ports showing simply as "closed." Is this true for Linux? I run hardy Heron 8.04 on an Acer 4315 laptop.

---

### Post by iaculallad on 2008-08-11
The difference is that, "close" port sends a response to the sender that the port is closed/inaccessible while a "stealth" port doesn't send any response.
So when you speak of being secure, you could just "Close" your desired port so nothing will even come from the outside.

*To the other side, it would just be a trial and error if you had it on stealth mode though*

---

### Post by Vivaldi Gloria on 2008-08-11
> **bodhi.zazen said:**
> "Stealth" is a bad term.

See this link :

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch14_:_Linux_Firewalls_Using_iptables#Table_14-2_Descriptions_Of_The_Most_Commonly_Used_Targets](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch14_:_Linux_Firewalls_Using_iptables#Table_14-2_Descriptions_Of_The_Most_Commonly_Used_Targets)

The options are "Reject" and "Drop"

Reject sends an error message, drop does not. Most people feel they are equal in security (security through obscurity is no security), although opinions vary.

Thus "stealth" == "drop" and a close port is as secure as a stealth port, you are worried about open ports or the "accept" option (unless you are running a public server ...)

from

[http://ubuntuforums.org/showthread.php?t=874899](http://ubuntuforums.org/showthread.php?t=874899)

---

### Post by Brian_Newbie on 2008-08-11
I've read some posts here where ports can be "brute forced" open or entered. If this is true, could my computer's reply that a port is closed be used by a hacker or automated program to open that port? - at least more easily than a Stealthed port (a non-responding port)?

If so, then how can I put my laptop into "stealth mode.?" (or is it worth the bother?

---

### Post by mcduck on 2008-08-11
Actually using the stealth mode could be less safe. Because thet still tells the possible attacker that there is a computer in that IP address, and that the computer admin has decided to stealth the ports. If there wasn't a computer, trying to access the IP would result in a response that there is no computer in that address, while stealth results in no response at all.

So the attcaker might see the machine as more interesting challenge, something worth trying to hack into.

---

### Post by Brian_Newbie on 2008-08-11
> **Vivaldi Gloria said:**
> from

[http://ubuntuforums.org/showthread.php?t=874899](http://ubuntuforums.org/showthread.php?t=874899)

Thanks for the links. Lots of useful info that I can learn from.

---

### Post by Brian_Newbie on 2008-08-11
> **mcduck said:**
> Actually using the stealth mode could be less safe. Because thet still tells the possible attacker that there is a computer in that IP address, and that the computer admin has decided to stealth the ports. If there wasn't a computer, trying to access the IP would result in a response that there is no computer in that address, while stealth results in no response at all.

So the attcaker might see the machine as more interesting challenge, something worth trying to hack into.

I would take that as a challenge too. I think it's best to leave my Ubuntu's default as it is - with the ports showing as closed (I used Steve Gibson's grc.com website to check my port status).

---

### Post by Vivaldi Gloria on 2008-08-11
Actually in the default ubuntu install all ports in ubuntu are open (no firewall running) but there are no services listening to any port. So it's very secure.

If you have a router then probably grc.com is scanning your router, not your computer.

---

### Post by iaculallad on 2008-08-11
To test your local PC, install the NMAP utilty:

```
sudo apt-get install nmap
```

and try to port-scan your OWN computer using  your private IP address:

```
nmap -A -T4 your_private_pc_IPaddress
```

You could use other switches when using the nmap utility.

```
man nmap
```

for more details.

---

### Post by Brian_Newbie on 2008-08-11
> **Vivaldi Gloria said:**
> Actually in the default ubuntu install all ports in ubuntu are open (no firewall running) but there are no services listening to any port. So it's very secure.

If you have a router then probably grc.com is scanning your router, not your computer.

It must be built into my laptop as I have no external router and my wireless connections work just fine. 

It's nice to know that Ubuntu's default installation is very secure. However, how do I check if my computer ports are open - and if so, should I close them even though I'm behind a router?

---

### Post by Vivaldi Gloria on 2008-08-11
> should I close them even though I'm behind a router?

Since there is no service responding to any packet that arrives at any port the outside world thinks that the ports are closed. So there is no point of closing ports using a firewall. If you really want then try ufw. Read

```
man ufw
```

in a terminal and especially look at the EXAMPLES section.

---

### Post by t0p on 2008-08-11
> **Brian_Newbie said:**
> I've read some posts here where ports can be "brute forced" open or entered. If this is true, could my computer's reply that a port is closed be used by a hacker or automated program to open that port? - at least more easily than a Stealthed port (a non-responding port)?


*Nahhh*... I don't think so anyway.  If a port's closed, it's closed.  Unless the evil hacker in question's gonna come round your house and *kick* the ports in... ;)

---

### Post by Brian_Newbie on 2008-08-11
Thanks to everyone that responded. I installed the NMAP utility and will test my pc. However it doesn't look like I'll even need to use UFW from  what I read here. 

I come from a Windows background and I found that even the most effective firewalls and anti-virus programmes failed. I'm happy to know that security is not an afterthought for the Linux operating system. 

I'm glad I made the switch!

---

### Post by iaculallad on 2008-08-11
> **Brian_Newbie said:**
> Thanks to everyone that responded. I installed the NMAP utility and will test my pc. However it doesn't look like I'll even need to use UFW from  what I read here. 

I come from a Windows background and I found that even the most effective firewalls and anti-virus programmes failed. I'm happy to know that security is not an afterthought for the Linux operating system. 

I'm glad I made the switch!

That's the best choice. Welcome to Ubuntu.

---

