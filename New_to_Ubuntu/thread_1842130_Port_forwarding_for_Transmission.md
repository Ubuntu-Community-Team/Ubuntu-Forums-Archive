---
title: "Port forwarding for Transmission"
date: 2011-09-10
forum: New to Ubuntu
---

### Post by mikee55 on 2011-09-10
Hi all, Please, can someone tell me why Transmission always has its port closed, yet I open it in the routers setup??

The DHCP client list says my IP address is 192.1.168.4. I'm confused.

Thank you

Mike

---

### Post by papibe on 2011-09-10
That setup page looks very strange to me. I've never see the block part when configuring port forwarding.

Are you sure you are opening the ports instead of blocking them?
What is your router's brand and model? 

Regards.

---

### Post by haqking on 2011-09-10
> **mikee55 said:**
> Hi all, Please, can someone tell me why Transmission always has its port closed, yet I open it in the routers setup??

The DHCP client list says my IP address is 192.1.168.4. I'm confused.

Thank you

Mike


Opening it on the router does not open it in the client app.

The router means pass all traffic destined for port x to this IP address, your client needs to be using that port though.

Can you show us a transmission screen dump, why do you think it is closed ?

And that doesnt look like your port forwarding page on your router

---

### Post by mikee55 on 2011-09-10
Belkin	F5D7234-4 v3 (01)

I can only show Client IP filters!! Transmission hogs my bandwidth, I set Download limit to 500k it averages 10k tops, upload is worse.
Thank you 
Mike

---

### Post by haqking on 2011-09-10
> **mikee55 said:**
> Belkin    F5D7234-4 v3 (01)

I can only show Client IP filters!! Transmission hogs my bandwidth, I set Download limit to 500k it averages 10k tops, upload is worse.
Thank you 
Mike


See [http://portforward.com/english/routers/port_forwarding/Belkin/F5D7234-4/Nomado.htm](http://portforward.com/english/routers/port_forwarding/Belkin/F5D7234-4/Nomado.htm)

and substitiue your ports and IP for the ones shown.

Also are you running a firewall locally on your machine ?

---

### Post by mikee55 on 2011-09-10
No firewall!
Thank you

Mike

---

### Post by haqking on 2011-09-10
> **mikee55 said:**
> No firewall!
Thank you

Mike


OK cool in which case follow the link and set up your virtual server info and should be good

---

### Post by mikee55 on 2011-09-10
??
Thank you
Mike

---

### Post by haqking on 2011-09-10
> **mikee55 said:**
> ??
Thank you
Mike


show me the setup without the error as i cant see what youve put in.

All you need to do is set up the ports to your IP address.

You dont need a router entry

one entry. choose both from the tc/udp drop down.

put in a name of the app such as transmission then your IP address and the port range

---

### Post by mikee55 on 2011-09-10
I didn't do the first entry, am I missing something? I've been messing around with this for ages, I'm getting tired. Sorry.

Thank you 
Mike

---

### Post by haqking on 2011-09-10
> **mikee55 said:**
> I didn't do the first entry, am I missing something? I've been messing around with this for ages, I'm getting tired. Sorry.

Thank you 
Mike


as i said above.

enter one entry, your IP address, the port and name it transmission and choose both TC/UDP and thats it.

i cant see the page cos you blocked it with an error message ;-)

---

### Post by mikee55 on 2011-09-10
Nope, same error

Thank you
Mike

---

### Post by papibe on 2011-09-10
That's looks good to me. Did you delete the previous entries on the initial blocking page?

Regards.

---

### Post by haqking on 2011-09-10
> **papibe said:**
> That's looks good to me. Did you delete the previous entries on the initial blocking page?

Regards.


+1

yes make sure you did this, the ports look fine now as for forwarding, though your active worlds one is not forwarding to any IP ?

but your transmission ones look fine.

---

### Post by mikee55 on 2011-09-10
Yep:)
Thank you
Mike

---

### Post by haqking on 2011-09-10
> **mikee55 said:**
> Yep:)
Thank you
Mike


OK so old blocks are removed ?
New virtual servers are saved in the config ?

no firewalls running on local machine ?

you might want to restart your router possibly and make sure changes have remained.

also perhaps reconnect your connection to refresh though shouldnt matter

---

### Post by mikee55 on 2011-09-10
:confused:
Port Closed :(

Thank you
Mike

---

### Post by haqking on 2011-09-10
> **mikee55 said:**
> :confused:
Port Closed :(

Thank you
Mike


mmm see here and work through it. [https://trac.transmissionbt.com/wiki/PortClosed](https://trac.transmissionbt.com/wiki/PortClosed)

saves me asking question after question as i cant see what you see

---

