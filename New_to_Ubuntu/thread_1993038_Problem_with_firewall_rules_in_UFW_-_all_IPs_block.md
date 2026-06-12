---
title: "Problem with firewall rules in UFW - all IPs blocked!"
date: 2012-06-01
forum: New to Ubuntu
---

### Post by zozza on 2012-06-01
Here are my ufw rules:

Status: active
Logging: on (low)
Default: deny (incoming), deny (outgoing)
New profiles: skip

To                         Action      From
--                         ------      ----
93.111.222.255             ALLOW IN    93.111.118.0

93.111.222.255             ALLOW OUT   93.111.118.0

AIUI, these say that all incoming and outgoing traffic to any IP address is prohibited unless the IP is between 93.111.118.0 and 93.111.222.255.

I try to connect to the IP address 93.111.120.5.  However, I can't because it's blocked.  In fact, all IP addresses are blocked.

I cannot see why this is the case?  Can anyone please advise me?

---

### Post by Cheesemill on 2012-06-01
The rules you have created only allow connections between  93.111.222.255 and 93.111.118.0, you haven't specified a range of IP addresses anywhere.

---

### Post by 2F4U on 2012-06-01
The default profile for both incoming and outgoing is deny:

Default: deny (incoming), deny (outgoing)

To change the default outgoing rule to allow, use

sudo ufw default allow outgoing

---

### Post by zozza on 2012-06-01
I obviously failed to explain my intentions very well.

I want to send all my traffic through a VPN.  The VPN uses the IP addresses between 93.111.118.0 and 93.111.222.255.

Me -----> VPN -----> Destination (HTTP / FTP / POP3 / etc)

Destination -----> VPN -----> Me

Hence, I assumed that I needed to allow the range 93.111.118.0 and 93.111.222.255 for both outgoing and incoming connections.

But, also, I needed to deny all other traffic hence: deny (incoming), deny (outgoing)

However, I am doing something wrong because this does not allow me to connect to any IP.

> The rules you have created only allow connections between   93.111.222.255 and 93.111.118.0, you haven't specified a range of IP  addresses anywhere.     I don't understand - I would have through that the range are the connections between the addresses 93.111.118.0 and 93.111.222.255.

No?

> To change the default outgoing rule to allow, use
sudo ufw default allow outgoing     This certainly works but means that I can connect to any IP which defeats the point of restricting access to a certain range.

---

### Post by Cheesemill on 2012-06-01
> **zozza said:**
> I don't understand - I would have through that the range are the connections between the addresses 93.111.118.0 and 93.111.222.255.

You haven't declared a range. You've declared 2 single addresses.
Your rules allow traffic from 93.111.118.0 to 93.111.222.255 and from 93.111.222.255 to 93.111.118.0. If neither of these are your machines IP then of course no traffic at all is allowed.
Fore more information see:
```
man ufw
```

Or you can install [gufw]("apt://gufw") if you want a GUI to configure your rules.

---

### Post by zozza on 2012-06-01
Sorry...I forgot to mention I set up the rules in GUFW rather than directly in UFW

See the attachment for how I configured the IP addresses.

Thanks again!

---

### Post by Cheesemill on 2012-06-01
To and From aren't the start and end of an address range, but the source and destination computer.

You would need a rule that looks something like:

```
TO                ACTION          FROM
Your IP           ALLOW IN        93.111.118.0/22
93.111.118.0/22   ALLOW OUT       Your IP
```

(Where 93.111.118.0/22 means 93.111.118.0 to 93.111.222.255)

---

### Post by zozza on 2012-06-01
> (Where 93.111.118.0/22 means 93.111.118.0 to 93.111.222.255) 	

Can you explain to a novice why the /22 signifies an address range of 118.0 to 222.255?

If, for example, I wanted to go from 93.111.118.0 to 93.111.140.255 then how would that be done?

Thanks again!

---

### Post by Cheesemill on 2012-06-01
Do some research on CIDR (Classless Inter-Domain Routing) and netmasks.

There are plenty of tutorial and information sites on the subject that will go into more detail than I could ever give you here.

---

### Post by zozza on 2012-06-02
What I didn't understand was that /22 - as I understand it - allows 1,022 subnet hosts.

However, 118.0 to 222.255 is 256x5 -10 which is 1,270 hosts.  So should it not be /21?

I also made a mistake about the IP range of my VPN.  

If it is (for example) 100.100.1.0 to 100.100.23.255 then that is 256x22 -44 which is 5,588 hosts.  This is, I believe, /19.

However, when I use my IP (from my ISP) as the to and then 100.100.1.0/19 as the from and then vice versa, I have the same problem - I can connect to my ISP but all IPs are then blocked.

I have obviously misunderstood something - but what?

Thanks for your help - really appreciated.

---

