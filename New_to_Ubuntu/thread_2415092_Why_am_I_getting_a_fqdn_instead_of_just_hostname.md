---
title: "Why am I getting a fqdn instead of just hostname"
date: 2019-03-19
forum: New to Ubuntu
---

### Post by Axis Mann on 2019-03-19
This is what I get on my ubuntu 14.04 desktop as expected

owner@Pluto$ nslookup 192.168.2.2
Server:      127.0.1.1
Address:    127.0.1.1#53

2.2.168.192.in-addr.arpa    name = Pluto.

but on my new ubuntu 16.06 desktop I get

owner@mimas$ nslookup 192.168.2.3
Server:      127.0.1.1
Address:    127.0.1.1#53

3.2.168.192.in-addr.arpa    name = Mimas.myIPScompany.com.

I was expecting to get the hostname mimas like I get with Pluto and another workstation on my peer to peer network.  Both Pluto and Mimas are configured as WIN clients.  A third machine not shown here is configured as a WINS server. The hosts database in the nsswitch.conf file is configured 

hosts: files,mdns4_minimal [NOTFOUND=return] wins [success=return] dns

Pluto returns the same info for mimas that mimas does.

owner@Pluto$ nslohttps://www.msn.com/okup 192.168.2.3
Server:      127.0.1.1
Address:    127.0.1.1#53

3.2.168.192.in-addr.arpa    name = Mimas.myIPScomany.com.

owner@Pluto$ 

Unexpected, the reverse lookup using hostname. (that's with a dot) works but without dot returns the fqdn.

owner@Pluto$ nslookup mimas.
Server:        127.0.1.1              ^see that dot?
Address:    127.0.1.1#53           

Name:    mimas
Address: 192.168.2.3

owner@Pluto$ 

any ideas?  Where should I be looking for the problem?  On Pluto, Mimas, or somewhere else?

---

### Post by SeijiSensei on 2019-03-20
Do you have a "search" or "domain" parameter in /etc/resolv.conf?  Those will append the domain to unqualified hostnames when doing DNS lookups.

---

### Post by Axis Mann on 2019-03-20
Hi, thanks for your response.

Both machines have search in the /etc/resolv.con file.  The one that is misbehaving and the one that isn't.  They both have

nameserver 127.0.1.1
search myIPScompany.com


itt seems to me that the local name server on the desktop should have resolved the query to just the hostname because of the nameserver 127.0.1.1 entry in the /etc/resolv.conf file. 

 I tried deleting the WINS database to see if there was some additional caching going on behind the scenes.  But that didn't help.  

Now I have two machines that are misbehaving.  It kind of works.  I can use the hostname to access shares but instead of just getting the hostname in the response to some diagnostic tools, I'm now getting a fqdn for some of the machines.  For example, I'm  getting this response for one machine in the peer to peer network

owner@mimas$ ping pluto
64 byte from Pluto (192.168.2.2): imp_seq=1 ttl=64 time=0.294 ms

while I get this response for another machine.

owner @mimas$ ping piServer
64 bytes from piServer.myISPcompany.com (192.168.2.11): imp_seq=1 ttl=64 time=0.294ms

Note that this example is happening on a single machine.  Can you guess which one it is?  Bzzt, you win, it's mimas.

The mimas machine uses the same resolve.conf file for both hostname resolution efforts.  But you can see that myISPcompany.com has been appended to the hostname for piServer but not for hostname Pluto.

It just doesn't seem that the search parameter is the culprit since the same configuration is used for both the resolution of the hostname Pluto and hostname piServer.  

resolv.conf:
nameserver 127.0.1.1
search myIPScompany.com

Claiming that search "will append the domain to unqualified hostnames when doing DNS lookups" belies that fact that when I ping Pluto, a fully qualified domain name **is not returned** from the local name server for hostname Pluto but is returned for the hostname piServer.

Consequently, I just can't believe that the search statement in the resolve.conf file is the culprit.  Certainly, you must agree that to be the case too. There's something else at work here.

The hosts: database configuration in the nsswitch.conf indicates that WINS should handle the name resolution before dns does.

hosts:          files mdns4_minimal [NOTFOUND=return] wins [SUCCESS=return] dns 

I can hardcode an entry in the /etc/host file for piServer and get the expected behavior because of the way nsswitch.conf is configured but I haven't done that for pluto and I get the expected behavior as shown below using nslookup.

owner@mimas$ nslookup pluto
Server:   127.0.1.1
Address: 127.0.1.1#53

Name:    pluto
Address: 192.168.2.2

Or the reverse lookup

owner@mimas$ nslookup 192.168.2.2

Server:   127.0.1.1
Address: 127.0.1.1#53

2.2.168.192.in-addr.arpa           name=Pluto.

There's no search parameter from resolv.conf being appened to the host name.  You can see that, right?  

Look what happens when I repeat exercise on the same machine using a different hostname.

owner@mimas$ nslookup piServer
Server:   127.0.1.1
Address: 127.0.1.1#53
[https://www.msn.com/](https://www.msn.com/)
Name:    piServer.myIPScompany.com
Address: 192.168.2.11

And the reverse lookup

owner@mimas$ nslookup 192.168.2.11
Server:   127.0.1.1
Address: 127.0.1.1#53

11.2.168.192.in-addr.arpa       name=piServer.myISPcompany.com.

Can you see how my.ISPcompany.com is being appended to hostname piServer but not being appended to hostname pluto?  Both the queries are done on mimas with /etc/resolve.conf set to

nameserver 127.0.1.1
search myIPScompany.com

Why would myIPScompany.com be appended to hostname piServer and not hostname pluto?  I don't want the search parameter appended to either, not just one of them. That's what I'm trying to figure out.  Why is it happening?  How can prevent the behavior?  It works for query one but not the other!  How come?

---

### Post by Axis Mann on 2019-03-24
Don't know if this problem is solved.  But the name resolution did stop misbehaving.  The last thing I can remember doing while attempting to diagnose the problem was to turn off both the router and the modem in conjunction with everything else.

 When I rebooted everything, the name resolution process I use was again working.  The ping and nslookup utilities were again all working for a hostname without displaying a fully qualified domain name.

I ultimately put everything back the way it was before I started trying to correct the issuse and it now behaves in a manner I've grown accustom to off an on over the past several years where host name resolution works without an entry in the hosts database /etc/hosts file for each machine.

I don't know much hooey about dns but as anyone can see, name resolution works just fine for hostname without the need to input or display an fqdn (read eff qdn) in the result.

owner@Pluto$ ping piserver
PING piserver (192.168.2.11) 56(84) bytes of data.
64 bytes from piServer (192.168.2.11): icmp_seq=1 ttl=64 time=0.396 ms
64 bytes from piServer (192.168.2.11): icmp_seq=2 ttl=64 time=0.522 ms
64 bytes from piServer (192.168.2.11): icmp_seq=3 ttl=64 time=0.497 ms
64 bytes from piServer (192.168.2.11): icmp_seq=4 ttl=64 time=0.514 ms

--- piserver ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2999ms
rtt min/avg/max/mdev = 0.396/0.482/0.522/0.052 ms

owner@Pluto$ nslookup piserver
Server:        127.0.1.1
Address:    127.0.1.1#53

Name:    piserver
Address: 192.168.2.11

owner@Pluto$ dig piserver

; <<>> DiG 9.9.5-3ubuntu0.19-Ubuntu <<>> piserver
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 26968
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;piserver.            IN    A

;; ANSWER SECTION:
piserver.        0    IN    A    192.168.2.11

;; Query time: 0 msec
;; SERVER: 127.0.1.1#53(127.0.1.1)
;; WHEN: Sun Mar 24 20:41:06 EDT 2019
;; MSG SIZE  rcvd: 42

my /etc/resolv.con file looks like this

owner@Pluto:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search myISPcompany.com

my /etc/hosts file looks like this

127.0.0.1    localhost
127.0.1.1       pluto
# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

my /etc/nsswitch.conf file hosts entry is configured

hosts:          files mdns4_minimal [NOTFOUND=return] wins dns

my /etc/samba/smb.conf file is configured to tell nmbd to be a wins client

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
    wins server = 192.168.2.11

I have the winbind package installed although I don't know if it's really necessary.

owner@Pluto:~$ dpkg -s winbind
Package: winbind
Status: install ok installed

---

### Post by Axis Mann on 2019-03-26
Nope. Back to receiving fqdn in response to ping or nslookup.  Worked fine for just a couple days then after an update to libc, my name resolution regressed back to the problem I was trying to resolve where I get a fqdn when expecting just hostname. 

I tried rebooting the router, the computers, and the modem but that didn't correct the problem this time.  

I haven't figure out yet why I was only temporarily able to get host name resolution working using WINS again.  It use to work as expected.  

Now I'm left clueless and have returned to coding hostnames and ip address in the /etc/hosts file.  nslookup however is again returning a fqdn instead of just the hostname of the associated ip address.

Opps, now dig and nslookup are working at all.  How annoying!

---

### Post by Axis Mann on 2019-03-26
Back to square one.  as you can see from below that nslookup behaviour is again undesirably retuning a fqdn instead of the hostname on my local network.

owner@Pluto:~$ nslookup piserver
Server:        127.0.1.1
Address:    127.0.1.1#53

Name:    piserver.myISP.com
Address: 192.168.2.11

If you look back a few posts, you can see that it was displaying just the hostname.

owner@Pluto$ nslookup piserver
Server:        127.0.1.1
Address:    127.0.1.1#53

Name:    piserver
Address: 192.168.2.11

As you see below, ping has also reverted to displaying a fqdn in the result.

owner@Pluto:~$ ping -c2 piserver
PING piserver (192.168.2.11) 56(84) bytes of data.
64 bytes from piServer.myISP.com (192.168.2.11): icmp_seq=1 ttl=64 time=0.408 ms
64 bytes from piServer.myISP.com (192.168.2.11): icmp_seq=2 ttl=64 time=0.494 ms

--- piserver ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 0.408/0.451/0.494/0.043 ms

I'm clueless.  It went from fqdn to no fqdn back to fqdn in the span of a week. For years, I have had WINS working fine with it resolving hostnames on my local area network.  Now it seems to be out of the loop.  The problem probably isn't wins but instead what ever logic uses nsswitch.conf to figure where to do name resolution.  I just did see libc get updated today after the name resolution started acting out again.  If that's the cause, then I'm guessing that there is nothing else I can do about it.  I guess I'm going to set up a dns server and tell it to use short names.  I'm giving up on WINS name resolution.

---

