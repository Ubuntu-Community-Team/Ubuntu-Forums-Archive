---
title: "Dhcp"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by ub007 on 2008-06-20
Hiya,

'sudo apt-get install dhcp3-server'
will this code install dhcp and dns as well?or should i use code
'sudo apt-get install bind9' to install the DNS packages...?

I got confused when i found this bit in the documentation on ubuntu sevrer:The most common settings provided by a DHCP server to DHCP clients include: 

IP-Address and Netmask
DNS
WINS

To add to it,if i have my DNS,DHCP and apache2 configured,will I be able to access the webserver from another PC?

Cheers,
David

---

### Post by iaculallad on 2008-06-20
This will install your DHCP and DNS:

```
sudo apt-get install bind9 dnsutils
```

---

### Post by Dedoimedo on 2008-06-20
Hello,

The DHCP server can be used to deliver a variety of information to clients, including:

IP address, subnet, default gateway, NIS server address, DNS server address, and more.

While this configures clients, it does not provide the DNS functionality in itself.

You will have to configure the DNS server as well. If you need help, feel free to ask. DNS server is not the simplest to setup and takes quite a few steps.

Dedoimedo

---

### Post by ub007 on 2008-06-20
thank you....

btw,how do i test my dhcp server after installing it?

---

### Post by Dedoimedo on 2008-06-20
Hello,

After installing, you need to configure it. Do you know how to do that?

Now, assuming you do know ... but if not, ASK!!! Here's how you test it.

1. Start the server (/etc/init.d/dhcpd start).
2. Open a terminal and then type:

tail -f /var/lib/dhcpd/dhcpd.leases

This will open a file dhcpd.lease and keep it open, showing you any changes that take place inside it.

3. Now, start a client machine. On a client, run:

dhclient

This is the DHCP client, it will contact the server and ask for information.

4. If you configured everything as needed, including the routing and firewall rules, the dhcpd.leases file should fill up with the first lease.

This is the database the DHCP server uses to keep tab on the IP addresses it leases to clients.

You should see the first assignment leased.

5. On the client, check with ifconfig to see everything fits and matches configurations in the DHCP main configuration file - /etc/dhcp.conf.

6. Furthermore, on the client, run:

route

To see if the route is ok (if updated by the DHCP server).

gedit /etc/resolv.conf

To see if the domain info and DNS server have been updated, again if configured to be delivered by the DHCP server.

Ask if you need anything.

Regards,
Dedoimedo

---

### Post by phoenixrosebud on 2008-06-22
> **Dedoimedo said:**
> Hello,

After installing, you need to configure it. Do you know how to do that?

Now, assuming you do know ... but if not, ASK!!! Here's how you test it.



How do I configure it? Thanks!

---

### Post by ub007 on 2008-06-23
I tried configuring DHCP and finally got it to start(used random IPs and subnets),but its not yet functional.I've got 4 PCs(installed ubuntu server on one of them) and a switch.I'vent configured DNS yet.How do i set up this network?I wish to give a static IP to the server and other PCs to get their IPs via dhcp.could anyone help me with the condiguration....?
What steps to follow,what IPs to put and so on....

Cheers,
Davis

---

### Post by Dedoimedo on 2008-06-23
Hi,

Here's how to configure a DHCP server:

Client-side configuration: make sure your network adapters lease addresses via DHCP.

File /etc/network/interfaces

For each interface (assume eth0, for example), make sure the following stanza is declared:

iface eth0 inet dhcp

Server side configuration:

/etc/dhcpd.conf

1. Add directive "authoritative" to the beginning of the file.

2. Change this entry to meet your requirements:

subnet x.x.x.x netmask x.x.x.x

Example: subnet 192.168.1.0 netmask 255.255.255.0

3. In the block defined by { } below subnet, define following options:

option routers x.x.x.x ---> define the gateway (e.g. 192.168.1.1)

options subnet-mask x.x.x.x ---> netmask for client interfaces (e.g. 255.255.255.0)

option domain-name-servers x.x.x.x ---> define DNS server (e.g. 192.168.1.2)

range 192.168.1.3 192.168.1.50

This line defines the IP addresses for client machines; the two IPs are just an example, use anything you want, but WITHIN the subnet you defined above!

Optionally, if you want to support the old bootp protocol, change the line to:

range dynamic-bootp 192.168.1.3 192.168.1.50

default-lease-time xxxxx ---> time the IP lease will last, in seconds, e.g 86400


Optionally, you can also define the domain name, netbios server, time server etc ... ask if you need ... consult the man page for details.

Last, below the subnet {} block, you can add "host" directive to define IP address for each client separately. If you need, tell me, I'll add ...

3. Check if file exists /var/lib/dhcpd.leases

If not, create it:

touch /var/lib/dhcpd.leases

This is the database where the server will keep the list of IP leases.

4. Start server

/etc/init.d/dhcpd start

5. Check it's working:

Firewall rules (make sure nothing is blocked)
Check the ports (nmap the local port, look for port 67 udp)

6. On client machines, reboot or run "dhclient"

This will make the clients contact the server and lease the addresses. If everything works out:

You'll get IPs on the clients.

Check te file dhcpd.leases; it should not be empty and should contain a list of leases given to the clients.

Check the file /etc/resolv.conf to see if the DNS server info has been updated.

Run "route" to see if the gateway has been updated.

That's it ...

Cheers,
Dedoimedo


P.S. Hope you get this today, cause I won't be near comp for the next week or so ... max. PM me, I'll give you help when I get back.

---

### Post by ub007 on 2008-06-23
Thanks a ton....

Do i need to configure DNS as well?
My purpose is to setup an intranet,it wont be connected to the internet,atleast for now.....
Will i need to configure a simple LAN DNS,if so ,how?
I found these when i googled dns configs-
search yourisp.com
nameserver 172.25.188.66
nameserver 172.25.188.77 .....since isp aint involved in the scenario,how do i go about it?

Cheers,
David

---

### Post by Dedoimedo on 2008-06-23
Hi,

Do you need DNS? You tell?

Do you intend to resolve names for machines within the LAN? Are the LAN machines going to use the server for name resolution (and basically internet access)?

Dedoimedo

---

### Post by ub007 on 2008-06-27
thank you so much...i've got dhcp up and running,didnt bother bout dns for the time being.aint connected to the internet,...so not of much use...cheers

---

