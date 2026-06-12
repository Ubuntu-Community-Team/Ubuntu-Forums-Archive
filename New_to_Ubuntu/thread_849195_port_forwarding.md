---
title: "port forwarding"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by ub007 on 2008-07-04
Sorry for starting a new thread,but its urgent as the weekend is bout to begin and i need access to the server form home...

Could anyone tell me how to do a port forward on ssh.

Scenario:
I got a single PC(ubuntu server) connected to my uni network and can access the internet via uni lan.I installed ssh,n i was able to access the ubuntu host from windows vista running on my laptop(connected to uni wireless neytwork).(using PuTTy s/w here)

However when i ask my friend residing in a different country to attempt ssh connection using puTTy,the terminal opens up n then gives an error msg -network error..conection timed out

I am able to ping his machine from my ubuntu host though...

I was told to use port forwarding,but i do not know how to establish that

Cheers
David

---

### Post by dacorr on 2008-07-04
you need access to the router and network infrastructure.

the router will forward incoming connections on the specified port to a specific IP such as the Ubuntu server.

Dac

---

### Post by ajmorris on 2008-07-04
hi there,
as well as forwarding your ssh port in your router, you must allow it in your software firewall if you have one, and also, put ```
port #  (where # is the port number you want to use for ssh (default is 22))
``` in /etc/ssh/sshd_config (make sure it is the same port your forwarded on your router and software firewall) then restart your sshd daemon script in /etc/init.d

AJ

---

### Post by ub007 on 2008-07-04
> you need access to the router and network infrastructure.
the router will forward incoming connections on the specified port to a specific IP such as the Ubuntu server.

i do not have access to the network router,its just that i'm connected to the uni n/w....so guess....i'm stuck there..thanks anyways

---

### Post by ajmorris on 2008-07-04
> **ub007 said:**
> i do not have access to the network router,its just that i'm connected to the uni n/w....so guess....i'm stuck there..thanks anyways

You could run a port scan on your uni network, and find it's open ports, then just run your ssh server on one of those ports.

AJ

---

### Post by txcrackers on 2008-07-04
> **ajmorris said:**
> You could run a port scan on your uni network, and find it's open ports, then just run your ssh server on one of those ports.

AJ

And get all your rights to the university network revoked when the admins catch you. Network/system administrators very rightfully take large exception to users "back-door"ing their systems as it is a basic security violation.

When your laptop is wirelessly connected, both it and the Ubuntu machine are within the university's firewall, so they can quite naturally "see" each other. The only way you can get your friend to "see" the Ubuntu machine is to get him/her on the university network - which if they're not associated with the university is most likely a violation of the university's TOS.

**Ask** the university system administrators if there's an approved method they have for this situation. If not, buy some server space with an external provider if it's that important, or use some P2P sharing system - if you can.

---

### Post by ub007 on 2008-07-04
> Originally Posted by ajmorris :You could run a port scan on your uni network, and find it's open ports, then just run your ssh server on one of those ports
that sounds very interesting,I could find out the open ports easily....but could you plz give me more details on how to run the ssh server on one of those ports?that part seems a bit confusing....

> And get all your rights to the university network revoked when the admins catch you. Network/system administrators very rightfully take large exception to users "back-door"ing their systems as it is a basic security violation.

hehe,i like the way u put it,anyways I would like to experiment with the idea,just to know how it cud be done...i hope to get away with that cz i'm doing a project on security stress testing...i understand its not a solution and the uni n/w guys wont appreciate that...

> The only way you can get your friend to "see" the Ubuntu machine is to get him/her on the university network 
Actually I asked my friend to access the server only for testing whether the ssh works from a diff n/w...The real purpose was for me to access it from home wn outside the uni n/w.so theres no violation in that aspect since i'm associated with the uni...But how do i get on the uni n/w once i'm out of the coverage area ??

---

### Post by txcrackers on 2008-07-04
> **ub007 said:**
> But how do i get on the uni n/w once i'm out of the coverage area ??
Most universities use VPN to allow outside access.

---

