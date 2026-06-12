---
title: "Using hostnames"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by markbusu on 2008-05-30
Hi guys...

One thing i noticed in linux other then M$ is that you cannot reach a machine by using its hostname... you always need to specify the ip address...

When i try using ssh user@machine i get unknown host...
When i use ssh user@ip it works...

These machines are within the same local lan...

Any way around this?

Note the IP address for the host might change... so i dont want to alias the IP address with a machine name...

Thanks!

---

### Post by quelx on 2008-05-30
The quick and dirty way is to edit **/etc/hosts** and add a line for each computer

```
sudo gedit -w /etc/hosts
```
```
10.0.0.10	somecomputername
```

---

### Post by markbusu on 2008-05-30
However what happens when the IP of the Machine would change? It has got quite an overhead....

In M$ ARPA is used to query hostname to IP... however this doesn't to be the case in Linux Networking... (However i thought that ARPA was a standard for Etherenet... has got nothing to do with OS)

---

### Post by Zafrusteria on 2008-05-30
The simple way (not what you want you say you want :-) Is to create  a **/etc/hosts** file for each of your machines and use static IP addresses.

```
sudo gedit **/etc/hosts**

127.0.0.1  localhost
192.168.0.1 somehost
192.168.0.3 someotherhost
192.168.0.2 andson
```

Or you could use DHCP and NDS to sort out the problem but that is a little over the top. 

AND then there is DNSmasq which should sort you out with its simple DNS and DHCP server.

Below is what I do, it is taken from a post I could not find today (would have saves a lot of typing :-) ) and the Ubuntu documentation

[DNSmasq Home page]("http://www.thekelleys.org.uk/dnsmasq/doc.html")
[Ubuntu Wireless router]("https://help.ubuntu.com/community/UbuntuWirelessRouter")
[Ubuntu Docs DNSmassq]("https://help.ubuntu.com/community/Dnsmasq")

1. Installation.
1.1. Install Using The 'apt-get' Software

Use the command line below . You will need the universe repository in your software sources list.

Install command

```
sudo apt-get install dnsmasq dnsmasq-base
```

2. Initialization and Configuration.
2.1. The example system used.

The server where dnsmasq is running its DNS and DHCP services is called "server" (192.168.0.7), The Router/default gateway is IP 192.168.0.1. There are a mixture of real and virtual machines all using these services. All machines are in the local domain example.com. The client machines will have names like "workstation" or kvmubuntu.

3.2. Setting up the server
3.2.1. Make backup copies of 'conf' files.

Start by making a copy of the files we will be changing so you can always go back to a know starting point.

Copy original configuration files:

```

mkdir ~/mybackups 
cd /etc
cp dnsmasq.conf hosts resolve.conf  ~/mybackups

```

2.2.2. Setting up **/etc/dnsmasq.conf**

Looking at the file **/etc/dnsmasq.con**f first. Below is a good starting point to get things up and running. The lines are listed in the same order as they appear in the default file. Just uncomment and amend them as necessary. (Remove the '#' from the beginning of the line)

Example **/etc/dnsmasq.conf**:
```
domain-needed
bogus-priv
expand-hosts
domain=example.com
dhcp-range=192.168.0.20,192.168.0.50,24h
```

What these lines will do for you.

    * domain-needed This tells dnsmasq to never pass short names to the upstream DNS servers. If the name is not in the local /etc/hosts file then "not found" will be returned.
    * bogus-priv All reverse IP (192.168.x.x) lookups that are not found in /etc/hosts will be returned as "no such domain" and not forwarded to the upstream servers.
    * expand_hostsSo we can see our local hosts via our home domain without having to repeatedly specify the domain in our /etc/hosts file.
    * domain This is your local domain name. It will tell the DHCP server which host to give out IP addresses for.
    * dhcp-range This is the range of IPs that DHCP will serve: 192.168.0.20 to 192.168.0.50, with a lease time of 24 hours. The lease time is how long that IP will be linked to a host.

Dnsmasq will, set or find out automatically, lots of common networking and connection values. These do not need to be set unless you are paranoid or like to specifically set these things. Which is rather nice of dnsmasq, don't you agree? :)

    * broadcast address
    * network mask
    * router parameters
    * interface (eth0) and IP address to listen on

2.2.3. Setting the server **/etc/hosts** file

The /etc/hosts file on the example server will look like this. Leave the IPv6 stuff as it was.

Example **/etc/hosts:**
```
127.0.0.1 localhost
192.168.0.7 server

```

2.2.4. Setting the server **/etc/resolve.conf** file

One last thing to do it set the localhost or loop device on the server as a nameserver so it can use the DNS service that it is running. Add the nameserver line below to the top of the list in **/etc/resolv.conf**.

Example **/etc/resolve.conf**:
```
nameserver  127.0.0.1
```

2.3. Setting up the clients
2.3.1. Make backup copies of 'conf' files.

Start by making a copy of the files we will be changing so you can always go back to a know starting point.

Copy original configuration files:
```
cd /etc
cp dhcp3/dhclient.conf hosts resolve.conf  ~/mybackups


```The /etc/hosts file on the client machines should look similar to this. Leave the IPv6 stuff alone.

Example /etc/hosts:
```
127.0.0.1 localhost
127.0.1.1 workstation

```

Note: There should be no need to change the hosts file from the default one created by Ubuntu.

2.3.2. Clients for DNS.

In the example setup our server is server or 192.168.0.7 it is the only machine with a static IP address. This is necessary as we need to tell the other machine were to look for the DNS service. So we need to tell the other machines were to get their DNS service from to take advantage of our shiny new server. We do this by adding a line to **/etc/resolv.con**f. I put it as the first nameserver in the file.

Example **/etc/resolve.conf**:
```
nameserver  192.168.0.7
```

2.3.3. Clients for DHCP.

**This is the bit everyone misses off!!!** :confused:

The only change here that we need to do is to make sure that when the host requests an IP address it passes its own hostname to the DHCP server. So the other machines can use its name to look up the IP address it was just given. So for example if we are setting up our workstation called workstation that is in our fictitious domain example.com we would add the following line to /etc/dhcp3/dhclient.conf

Example **/etc/dhcp3/dhclient.conf**:
```
send host-name "workstation.example.com";
```

You can now reboot workstation. During which time it will talk to our new DHCP server request a new IP address. The server will remember which IP address it gave out to workstation and it and other machines on the network will be able to ping workstation. No more needing to know which machine has which IP address.

4. Testing & Troubleshooting
4.1. Testing the DNS server
4.1.1. Locally on the server and on remote hosts

The simplest way to test that your DNS is up and running it to use the dig utility. When you look at the output from dig the part we are interested in is the third and forth line from the end. Just use dig <domain name> to see the output.

```
 dig bbc.co.uk
; <<>> DiG 9.4.2 <<>> bbc.co.uk
;; global options:  printcmd
;; Got answer:
;; ->>HEADER <<- opcode: QUERY, status: NOERROR, id: 57582
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0
;; QUESTION SECTION:
;bbc.co.uk.                     IN      A
;; ANSWER SECTION:
bbc.co.uk.              159     IN      A       212.58.224.131
;; Query time: 21 msec                        # <<==== This line and the one below
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Sun May 11 09:38:21 2008
;; MSG SIZE  rcvd: 43

```

From the test on the domain bbc.co.uk you can see it took all of 21 mseconds to look up. That is around around 1/50 of a second and we used the server 127.0.0.1 (local host) as the DNS.

Now the magic bit, when you do the same dig command again a few minutes later it is much quicker as the previous lookup was cached. So we see this

```
 dig bbc.co.uk
; <<>> DiG 9.4.2 <<>> bbc.co.uk
;; global options:  printcmd
...
...
;; Query time: 0 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)

```

This time it took 0 msec, the DNS is working locally.now try the same command on one of the workstations and you should see the same result. The first time you request a domain it will take some time. the second time will be much quicker. Once the domain as been lookup up it will remain in the cache for some time.

4.2. Testing DHCP.

Assuming your dnsmasq server is already setup and working. Start up one of the other hosts. After it has booted look at the output from ifconfig looking at the second line for the network interface and the inet addr should be within the DHCP range you set on the server.

```
inet addr:192.168.0.7  Bcast:192.168.0.255  Mask:255.255.255.0
```

From the dnsmasq server you should be able to ping the machine you just booted by name and vice-versa.

Make sure you have turned off all other DHCP servers on your system. (E.g The one in your ADSL/Router)

You can test that you are using the dnsmasq DHCP server by making a range one just one IP address in **/etc/dnsmasq.conf**, restarting the dnsmasq server and rebooting the client machine. It should now be using that one IP address.

---

### Post by quelx on 2008-05-30
> **markbusu said:**
> However what happens when the IP of the Machine would change? It has got quite an overhead....

In M$ ARPA is used to query hostname to IP... however this doesn't to be the case in Linux Networking... (However i thought that ARPA was a standard for Etherenet... has got nothing to do with OS)

I think Microsoft is using some NetBIOS/WINS combination with DNS, so windows computers on the same subnet can see names of others even if DNS is not setup for workstations.

---

