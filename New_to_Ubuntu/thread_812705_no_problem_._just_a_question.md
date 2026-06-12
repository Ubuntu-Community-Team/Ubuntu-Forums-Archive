---
title: "no problem . just a question"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by tactx on 2008-05-30
What would be the ifconfig (or other) equivalent to...
"ipconfig /release"
and 
"ipconfig /renew"?

---

### Post by HotShotDJ on 2008-05-30
I believe the commands are:```
sudo ifdown
sudo ifup
```

---

### Post by HotShotDJ on 2008-05-30
OOPS  -- Try:```
sudo dhclient <device>

```(replace <device> with the network device you are using, for example eth0 or wlan0).

---

### Post by tactx on 2008-05-30
Thanks for the reply, :)  but it does not appear to work for me. I am trying to use the command line to drop my internet connection and then later re-establish it.

---

### Post by sisco311 on 2008-05-30
Try:
```
sudo /etc/init.d/networking stop
```and
```
sudo /etc/init.d/networking start
```or in one line
```
sudo /etc/init.d/networking restart
```

---

### Post by kpkeerthi on 2008-05-30
> **tactx said:**
> What would be the ifconfig (or other) equivalent to...
"ipconfig /release"
and 
"ipconfig /renew"?

Guys,
To be specific....
**/release** releases a DHCP assigned IP address and **/renew **requests for a new IP from DHCP server. The OP is looking for a linux equivalent.

---

### Post by tactx on 2008-05-30
Thanks, HotshotDJ...Irecieved errors executing the command you suggested, but it did drop my connection; however, I could not re-establish it without a reboot. Thanks sisco311, but the command you gave me did not drop my internet conection even though it gave me this message.."* Deconfiguring network interfaces... OK." kpkeerthi is correct..and thanks for clairifying things.

tactx

---

### Post by kpkeerthi on 2008-05-30
This should work:

Release IP:
```
sudo dhclient -r
```

Obtain new IP:
```
sudo dhclient
```

If you are unable to connect online after a new lease, restart your network (but usually not required): ```
sudo /etc/init.d/networking restart
```

---

### Post by tactx on 2008-05-30
Thanks, however "sudo dhclient -r" doesn not release the ipaddress and now niether does the command suggested earlier by HotshotDJ..???

LOL.. breaking my connection is harder than setting it up...

---

### Post by kpkeerthi on 2008-05-30
> The -r flag explicitly releases the current lease, and once the lease has been released, the client exits.
... from [dhclient man page]("http://linux.die.net/man/8/dhclient")

---

### Post by kpkeerthi on 2008-05-30
Also, if a client requests for a new IP, it doesn't mean that the DHCP server should return a unique (different from the last one) IP address. Check how your DHCP server is configured.

---

### Post by tactx on 2008-05-30
Hmmm...When I run the command, I get this..

tactx@Desktop:~$ sudo dhclient -r
[sudo] password for tactx: 
There is already a pid file /var/run/dhclient.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/<mac address>
Sending on   LPF/eth1/<mac address>
Listening on LPF/eth0/<mac address>
Sending on   LPF/eth0/<mac address>
Sending on   Socket/fallback

but then I am still able to browse to new web pages...so I would say that my ipaddress is definately NOT released.

---

### Post by kpkeerthi on 2008-05-30
After running **sudo dhclient -r** wait till it puts you back on a prompt.

---

### Post by tactx on 2008-05-30
I did.. btw thanks for the help..Im not trying to be difficult..from what the mannual says...it should work..,but its not working for me. Have you tryed it? Shouldnt it drop my internet connection?

---

### Post by Joeb454 on 2008-05-30
I get the same thing, even if I specify an interface by running ```
sudo dhclient wlan0 -r
```
I'd imagine it should drop the connection, or at least make you unable to connect to the net, as you *should* have no IP address :confused:

---

### Post by tactx on 2008-05-30
LOL..Thanks JoeB454...I thought it might just be me ...I have also tried specifying eth0 ...my active NIC

---

