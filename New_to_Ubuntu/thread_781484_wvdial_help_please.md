---
title: "wvdial help please?"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by rbcl15 on 2008-05-04
Wvdial ran 'almost' successfully for me,connecting to my mobile phone and everything, with the exception of pap and chap files denying me permission. Does anyone know how to proceed in this? 

This may affect why I can't get Firefox to manifest any web pages?
 
I was even shown 2 DNS addresses, a local ip address and a remote ip address, though all arn't the address provided by my Network (the gateway address I think it's called). Any advice on how I might fulfill internet connection from here?

---

### Post by spiderbatdad on 2008-05-04
try running sudo wvdial

Also wvidialconf should have be run as root.

You will need to set up chap-secrets...[http://www.linux.org/docs/ldp/howto/PPP-HOWTO/x1005.html](http://www.linux.org/docs/ldp/howto/PPP-HOWTO/x1005.html)

In /etc/resolv.conf you should also have something similar to:

search yourisp.com
nameserver xxx.xx.xxx.xx
nameserver xxx.xx.xxx.x

where the nameservers are those use by your isp, or you could some public nameserver like 4.2.2.1  4.2.2.6

If you have a winmodem, IDK if it will ever work right. Hopefully you are using an external modem.

---

### Post by rbcl15 on 2008-05-04
Yay, thanks spiderbatdad I have no more pap and chap errors and it's struggling through. Why though is it so slow?

---

### Post by spiderbatdad on 2008-05-04
Glad it is working.
My guess, as an answer to you question, is, it has to do with the type of modem. Conexant, Rcokwell, and US Robotics provide good support for Linux. Internal Winmodems are unlikely to work consistently, if at all.

---

