---
title: "[?] Can't resolve hostname on local network"
date: 2013-03-23
forum: New to Ubuntu
---

### Post by balta on 2013-03-23
Hi there!
I've been fiddling around with my new RaspberryPi lately and I installed on it the transmission web client and daemon.
Because of reasons I've been doing all the setup using windows machines for testing, and everything was fine: from all my windows (XP, 7, 8) machines I can access the transmission address (*[http://raspberrypi:1234/torrent/web/](http://raspberrypi:1234/torrent/web/)*) with no problems at all from any browser.

If I try accessing it from my ubuntu (10.04, 12.04) machines I just get a "page not found" error.
I figured the problem is related to the fact I'm using the machine name (*raspberrypi*) instead the IP address: if I use the direct IP address (e.g.: *192.168.1.234:1234/torrent/web/*) it works flawlessly.
I'd obviously prefer to use the hostname!

So, how can I have ubuntu properly resolving the hostname of the raspberry (or any other host on the same local network for what matters)?

Thanks for your attention \(^__^)/

PS: strangely enough samba works fine with the hostname: *smb://raspberrypi/pishare* works just fine!

EDIT:
I solved the problem adding *wins *in my */etc/nsswitch.conf* file and installing *winbind *as reported on a random website.
I have absolutely no clue about what it does but, so far, it is working on my 12.04 machine :D

---

### Post by El Tito on 2013-03-23
You could try editing /etc/hosts. There are a couple examples in the following link. Good luck!
[http://community.linuxmint.com/tutorial/view/159](http://community.linuxmint.com/tutorial/view/159)

---

### Post by balta on 2013-03-23
Hi, thanks for your reply.

Unfortunately editing the /etc/hosts file wouldn't solve the problem as the resolution hostname-address should be "hardcoded" and a change of local address (caused, for example, by a reboot) would force me to change the /etc/hosts on all the machines.
Isn't there a way to have ubuntu discover the machines on the same network and map the hostname and the address automatically?

Thanks again

---

### Post by axismann on 2013-06-13
Seems to me that if you can't use the /etc/hosts file to resolve host  names, then you got to use either a wins server or a DNS server.  I  don't know how to use DNS to resolve host names but I had some luck with  a wins server recently for a small peer to peer network consisting of  two ubuntu 12.04 machines, a Windows XP machine, and a fourth machine  running a different flavor of linux on a raspberry pi computer.  Samba  is exceedingly simple to set up as a wins server. Read the WINS server  instructions in the Samba manual.  I installed Samba on the two ubuntu  12.04 machines too.  On those, I used the /etc/samba/smb.conf file to  point to the wins server ip address with the wins server =  192.168.xxx.xxx parm (the ip address of the raspberry pi machine on my  local network). I also changed the name resolve order to "name resolve  order = wins hosts lmhosts bcast."  The raspberrypi ip address must  always be the same as recorded in the other machines smb.conf file or  the other machines can't find it.  I then had to make changes to the  /etc/nsswitch.conf file and install the winbind package to get the name  resolution to work.  In the nsswitch.conf file, I had to change the  hosts: statement to "files mdns4_minimal [NOTFOUND=return] wins  [!NOTFOUND=return] dns mdns4" but the [!NOTFOUND=return] is optional.  A  successful WINS lookup is suppose to return to caller by default but  there seemed to be a significant delay.  I tried [SUCCESS=return] but  that didn't seem to make a difference so I went with Not NotFound  instead.  You can google for MAN NSSWITCH.CONF to read about those  status and action options.  I don't know if the other machines have to  have a static IP address since they all register with the WINS server  when you turn them on but I have my router assign the same IP address to  a computer every time I turn it on.  You can't ping the computer by  host name until you get winbind installed and the nsswitch.conf file  updated.  However, once you get the wins server installed, you should be  able to see all the computers on the network if you got Samba set up  correctly and have all computers in the same workgroup.  If at anytime  you put information in the /etc/hosts file, be sure and remove the  entries for the computers (like 192.168.2.2  Hostname  for example)  since if they are different from what they appear to be to the WINS  server, you could have problems with host name resolution.    I use  security = share to access my shares because I don't need user level  security.  How you access your shares is additional effort not covered in  my description.  I was just describing how I effected name resolution  using Samba with a WINS server.

---

### Post by balta on 2013-06-13
Hi, thanks for your very detailed reply.
Eventually I end up setting a static IP address on my RaspberryPI.
If I were to reconfigure it I'll give your guide a try, thanks a lot!

---

