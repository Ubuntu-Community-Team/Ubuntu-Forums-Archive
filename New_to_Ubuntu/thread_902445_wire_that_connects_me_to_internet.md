---
title: "wire that connects me to internet"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by adamogardner on 2008-08-27
I realize there are different internet connections.  the one I'm working with is my roomates.  it connects to the tv cable to a box with lights(modem?) to a power outlet, and to my computer with a big phone jack connector.  Whats that called?
I plugged it in and started my computer but it doesn't connect.  I have tried adjusting things poking around, but I'm not getting a connection though he has no problem.  
I have a 2 day old Acer AspireOne.  Does his computer need to give me permission or something?  I just don't get it because My guru had it plugged in to his wire last night and it detected it instantly.

---

### Post by phidia on 2008-08-27
The big "phone" cable is an ethernet cable. 
When you plug the cable in provided you are plugging it into the correct port the OS should "see" the connection. You could try restarting with the ethernet connected.

---

### Post by adamogardner on 2008-08-27
ok apparently there was recognition I typed ifconfig into terminal and got:

"eth0:avahi Link encap:Ethernet HWaddr 00:1e:ac:32:50
inet addr:163.221.3.78 Bcast:169.242.244.244 Mask:123.123.12.1
UP BROADCAST RUNNING ,MULTICAST MTU:1500 Metric:1
Interupt:219 Base address:0xe000"

When I unplug the wire that entry isn't there. I can't browse or apt-get even though it shows up.

---

### Post by porchrat on 2008-08-27
As Phidia said it should auto-detect.

However if it doesn't for some strange reason find out from your friend what the IP address of the modem/router is so that you can at least ping it or type that IP address into a browser (e.g. firefox) so that you can at least see whether or not your PC can at least see the router.

to ping something type:
```
ping IP_address
```
where IP_address is the IP address of the router...then use ctrl+C to stop it pinging.  If none of the data packets come back to you then you have no connection and your network manager's settings need to be fiddled with

I hope that helps

---

### Post by lazyart on 2008-08-27
I find with my ISP that when I change the device that plugs into the modem I have to power cycle the modem itself to connect anywhere.  In the many homes where I have done troubleshooting, installed routers and such and the common thread being a cable modem, unplug the modem, count to 10 then plug it back in.  Tada-- connection.  Until of course, you plug in a different device.

Worth a shot.

---

### Post by adamogardner on 2008-08-28
lazyart, your so smart!
Now I can download kppp and get my aircard working using the instructions you gave me some months ago.  Regarding that, I had tried the same configuration previously on another operating system (backtrack) but it was to no avail.  any insight on that?  hoping it won't happen again with my acer.

---

