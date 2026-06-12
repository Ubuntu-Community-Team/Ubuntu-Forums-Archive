---
title: "xubuntu shows network but won't connect........"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by jestanuff on 2008-05-22
i just installed xubuntu on a dell inspiron 4000 everything works, fine even the usb network card. however i can't connect  to the intra-web thingy. I know this is probably easy but............



thanks

---

### Post by superprash2003 on 2008-05-22
can you connect to other networks?

---

### Post by iaculallad on 2008-05-22
Try to ping (at the terminal) other workstations within your intranet to test you connection with the network.

---

### Post by jestanuff on 2008-05-22
first off thanks .......now i seemed to get on the network and the com-pewter icons don't have the red x 'but firefox doesn't work or add\remove either........:confused:

---

### Post by iaculallad on 2008-05-22
with the issue of add/remove not working: Check to it that Synaptics Package Manager is not open.

---

### Post by ryanhaigh on 2008-05-23
Your internal network may use a proxy server which, if it exists, you will need to configure your system for. How have you determined that you are able to connect to the network? What is the output of the command ifconfig when you run it in the terminal (sorry can't tell you where that is on xubuntu). Is the network card wired or wireless?

---

### Post by jestanuff on 2008-05-23
it's an external wireless usb card...it's supported (according to this list i found)when i disconnect it i get an x on the network icon , thats why i think it's connected . It also picks up public signals but not my home wifi. i put in the password and all

---

### Post by fontenot_1031 on 2008-05-23
You need a wireless network manager.  Xubuntu does not come with one out of the box.  Wicd works as well as wifi-radar.

---

### Post by ryanhaigh on 2008-05-23
Can you please post the output of the command ifconfig when run in a terminal when you are connected to the wireless network.

---

### Post by jestanuff on 2008-05-23
> **ryanhaigh said:**
> Can you please post the output of the command ifconfig when run in a terminal when you are connected to the wireless network.

hobo@unbuntu:~ifconfig
lo                    link encap:local loopback
                       inet addr:127.0.0.1 mask:255.0.0.0
                       inet6 addr: ::1/128 scope:Host
                       UP LOOPBACK RUNNING MTU:16436 meteric:1
                       RX packets:50 errors:0 dropped:0 overruns:0 frame:0
                       TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
                        collisions:0 txqueuelen:0
                        RX bytes:3484 (3.4)  TX bytes:3484 (3.4)

wlan0               Link encap:Ethernet  HWaddr 00:18:f8:28:64:fc
                        inet addr:169.254.8.253 Bcast:169.254.255.255 mask:255.255.0.0
                        UP BROADCAST RUNNING MULTICAST MTU :1500 Metric:1

wmaster0 link encap:UNSPEC  HWaddr 00-18-f8-28-64-fc-00-00-00-00-00-00-00-00-00-00
                       UP BROADCAST RUNNING MULTICAST  MTU:1500 Metric:1
                       RX packets:0 error:0 dropped:0 overruns:0 frame:0
                       TX packets:0 error:0 dropped:0 overruns:0 carrier:0
                       RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)








fwwwuuu that was some typing

---

### Post by ryanhaigh on 2008-05-24
> wlan0 Link encap:Ethernet HWaddr 00:18:f8:28:64:fc
inet addr:**169.254.8.253** Bcast:169.254.255.255 mask:255.255.0.0

This is the network information for your wireless card, the bold part is the ip address and unfortunately indicates that your are infact not connected to the network or at least that you are not getting an ip address. This is a sort of fallback address the same as under xp (in xp it would say limited or no connectivity). You can use the command ```
iwconfig wlan0
``` to determine if you are indeed associating with the wireless access point. You might want to look at trying wicd for managing the wireless network connection as was mentioned earlier. It might also be benefitial if you could provide some more details about your wireless card, the output of ```
lsusb
``` could be helpful there.

One last not, rather than typing it all out you could copy and paste into a text file and put that on a usb, boot into windows and post back.

---

### Post by jestanuff on 2008-05-25
i use the other proprietary OS...... but thanks.....the other con-pewter is old......

---

