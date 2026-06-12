---
title: "Thin client not seeing LTSP server"
date: 2014-09-16
forum: New to Ubuntu
---

### Post by marc34 on 2014-09-16
I have a Ubuntu 14.4 LTS that is not being picked up by any of my thin clients. A windows S8 R2 is handeling the DHCP.

---

### Post by marcel9 on 2014-09-25
With a lot of respect of people who make guides here its still for me in some cases abracadabra and up in the end with Google, its still my best friend. I found an out of the box guide which brought me without any hassle to a working LTSP server and also could connect any device on its network and boot. Remind that with installing LTSP you arent finished, you need to know that you have to change a lot config files which i also didnt found on the ltsp project site, nor here. I think most people expect that you arent a rookie and have some good experience how linux works :) Despite im born with Windows, wish it was different, it would make my life with linux a lot better. 

To get your system working follow this link [http://www.thefanclub.co.za/how-to/how-create-ubuntu-1104-x64-ltsp-server-32bit-thin-clients](http://www.thefanclub.co.za/how-to/how-create-ubuntu-1104-x64-ltsp-server-32bit-thin-clients)

I started with 12.04 LTS and works, then i upgraded to 14.04 and still working like a charm.

if i get there as a linux noob you will get there too :)

---

### Post by chujen on 2014-10-09
Thanks Marcel9 for that link. It is very usefull but I still cannot connect thin clients.
I am using 14.04
What I am doing different? 
Instead of 192.168.1.1 I put 192.168.2.1 because the modem has by default 192.168.1.254 and assigns numbers to each device that connects wired or wireless. So I decided to assign 192.168.2.1 to the server machine.
My Internet access is wireless with automatic DHCP and I have used the cable eth0 to connect the switch to put the clients. 
I followed all the instructions and changed where indicates 192.168.1.1 I put 192.168.2.1
After restarting I try: "sudo /etc/init.d/isc-dhcp-server status" and the answer is "Status of ISC DHCP server: dhcpd is not running"

I tested a client and connect through network boot but it did not show the login screen. I tested the bios network boot and a CD with GPXE.
In both cases it finished with a blank screen and the cursor blinking at the left corner.

What am I doing wrong? What do you recommend?

---

### Post by chujen on 2014-10-09
I just made another change. I am testing with only one client now... I connected directly client to server (without the switch) and I got the ubuntu login screen. I write the login and the password but it goes again to ask the user login.

The user I made to test has all the user permision but it is not administrator. If I login with administrator name and password it works!
I am now working in the client but with my administrator login.... that is not what I want :-(
I am still missing something or doing some thing wrong.
I will try tomorrow with another machine with 8GB RAM and another switch.
Any suggestions?

---

