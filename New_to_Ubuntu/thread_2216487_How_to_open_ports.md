---
title: "How to open ports"
date: 2014-04-12
forum: New to Ubuntu
---

### Post by richaustin on 2014-04-12
Hi All

I've just upgraded to Ubuntu 14.04 and for some reason it seems that ports 80, 443 and 8200 are closed. I need at least one of them open in order to use GotoMyPC which worked perfectly on 13.10. Something has obviously changed but I'm no expert on ports or networking. I've checked for open ports with the following command:

sudo netstat -ntlp | grep LISTEN

None of the three ports, 80, 443, 8200 are listed. I assume they were in Ubuntu 13.10 - I never checked, it just worked. I can't find any information on how to set the ports to listen. Can anyone give me a pointer on how to do it?

Thanks in advance
Richard

---

### Post by Sef on 2014-04-12
> [COLOR=#000000]I've just upgraded to Ubuntu 14.04 and for some reason it seems that ports 80, 443 and 8200 are closed.[/COLOR]

Sounds like the upgrade went wrong.  Port 80 is http, and port 443 is https; those ports are always left open. 

> [COLOR=#000000]sudo netstat -ntlp | grep LISTEN[/COLOR]

Please post your results of the above command. 

Mine were

tcp        0      0 127.0.1.1:53            0.0.0.0:*               LISTEN      1767/dnsmasq    
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      22502/cupsd     
tcp6       0      0 ::1:631                 :::*                    LISTEN      22502/cupsd

---

### Post by ajgreeny on 2014-04-12
Have you enabled the ufw firewall but not opened any ports after doing so?
The default for ufw is to deny passage through all ports, so you will need to add some rules or enable the specific ports you need.

Have a look at **man ufw** in terminal, one of the more easily understood manuals available or see:-
[https://wiki.ubuntu.com/UncomplicatedFirewall](https://wiki.ubuntu.com/UncomplicatedFirewall)
[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

---

### Post by richaustin on 2014-04-13
HI

I haven't enabled the firewall, it's just a normal installation with nothing fancy other than I installed Gnome. The output from sudo netstat -ntlp | grep LISTEN I get is as follows:

tcp        0      0 127.0.1.1:53            0.0.0.0:*               LISTEN     $
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN     $
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     $
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN     $
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN     $
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN     $
tcp6       0      0 :::22                   :::*                    LISTEN     $
tcp6       0      0 ::1:631                 :::*                    LISTEN     $
tcp6       0      0 :::445                  :::*                    LISTEN     $
tcp6       0      0 :::139                  :::*                    LISTEN     $
tcp6       0      0 :::80                   :::*                    LISTEN     $

I wasn't initially getting a listener on port 80, installing a LAMP stack gave me one. 

I still can't get a connection via GotoMyPC unfortunately, it just attempts to connect but it appears not to be getting a signal back from the remote PC. It always worked perfectly in 13.10 so I'm mystified as to what's changed. I noticed the same thing in Gnome Ubuntu 14.04 as well. The only thing I can think of is the ports but now I have a listener on 80 I'm not so sure it's ports causing the problem. Enabling ports 443 and 8200 might resolve the problem but according to the information GotoMyPC should work on any of the three ports.

[Edit]
I've now also got port 443 working by enabling SSL in Apache: "sudo a2enmod ssl" but GotoMyPC still doesn't connect. Wine issue perhaps?
[/Edit]

---

### Post by yXmNpV8z on 2014-04-13
> **richaustin said:**
> HI

I haven't enabled the firewall, it's just a normal installation with nothing fancy other than I installed Gnome. The output from sudo netstat -ntlp | grep LISTEN I get is as follows:

tcp        0      0 127.0.1.1:53            0.0.0.0:*               LISTEN     $
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN     $
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     $
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN     $
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN     $
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN     $
tcp6       0      0 :::22                   :::*                    LISTEN     $
tcp6       0      0 ::1:631                 :::*                    LISTEN     $
tcp6       0      0 :::445                  :::*                    LISTEN     $
tcp6       0      0 :::139                  :::*                    LISTEN     $
tcp6       0      0 :::80                   :::*                    LISTEN     $

I wasn't initially getting a listener on port 80, installing a LAMP stack gave me one. 


You've got port 80 listening on IPv6 but not IPv4. Are you trying to connect using IPv4 or IPv6?

Gav.

---

