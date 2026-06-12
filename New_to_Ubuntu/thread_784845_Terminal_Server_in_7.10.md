---
title: "Terminal Server in 7.10"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by Lisa Y on 2008-05-06
Hey guys,

I was wondering if anyone could be a great help and tell me what i am doing wrong...There are a few servers at work and i normally remote into them...through a windows machine though...

I enter the server name...leave the domain,User and pass blank...click connect and get those errors...

Autoselected Keyboard map en-us
ERROR: origin: unable to resolve host

Now my question is...is there any need to forward a port like i do in a windows machine (3389). Or what am i missing that im not able to remote into the server...?

Any help would be greatly appreciated...Thanks

---

### Post by quelx on 2008-05-06
Have you tried to ping the hostname you are trying to which RDP?  **Applications**>**Accessories**>**Terminal**

Then "ping servername"

If you get responses make sure you are using **RDP** (or maybe **RDPv5**?) in the **Terminal Server Client** under **Protocol**.

---

### Post by Monicker on 2008-05-06
Sounds like a problem with dns resolution.  I think it will work if you enter the ip address of the server.  Are you connecting to these machines directly over the internet, or by way of a vpn tunnel?

---

### Post by Lisa Y on 2008-05-08
hmm...sorry for the late reply been working with these servers...they have been giving me a slight problem lately...


i have pinged the server by name and IP  and it seems to give me "unknown host"...dont know why...i ping it from my windows machine and it pings just fine. At least i know my servers seem to be more or less online, yet I can't ping in ubuntu. :(

I believe its one of two things, the wireless....( now that im think about it )...or the fact that i connect to the wireless by router...and just remembered that the 3389 port it not forwarded....

any other suggestion would be great...thanks

---

