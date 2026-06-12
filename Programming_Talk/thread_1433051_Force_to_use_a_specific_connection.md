---
title: "Force to use a specific connection"
date: 2010-03-18
forum: Programming Talk
---

### Post by Scatarro on 2010-03-18
Hi guys,

I am working with python and c++: the problem is that python part of the software works fine on ethernet connection but the c++ part works fine only on 3G key connection (ppp). 

I wonder if it is possible to force the c++ part to use the PPP connection while the rest of software continues to use the ethernet connection.  

Thank you.
Pietro

---

### Post by cariboo on 2010-03-18
You may get better answers here.

---

### Post by gmargo on 2010-03-18
The routing table controls an IP packet's outbound interface based on the destination IP address.

---

### Post by Ferrat on 2010-03-18
Hard to give much resopnse when you don't say exactly what you are trying to do with the connections but I'm guessing it has to do with mobile devices, can't you try sensing what types of connection is possible and then make a internal "tunnel" between Python and C++ depending on what connections are available?

if only 3G then 
C++ main out
and
Python -> C++ 

if Eth then
Python main out
and
C++ -> Python

---

### Post by soltanis on 2010-03-19
What exactly are you trying to accomplish, and what platform are you developing for?

---

### Post by Scatarro on 2010-03-23
Hi guys,

thank you for the answers. I am doyng some measurement based on traceroute and multicast stuff. I will try to follow your way Ferrat.  ;)

---

