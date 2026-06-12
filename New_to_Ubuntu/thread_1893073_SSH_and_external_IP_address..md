---
title: "SSH and external IP address."
date: 2011-12-09
forum: New to Ubuntu
---

### Post by blackseptember on 2011-12-09
Hi all

I´d like to pick your brains a bit regarding the sshd_config file and external IP address. My apologies if im posting this in a wrong forum or the topic has been covered in detail elsewhere - i could not find a satisfying answer, maybe i didnt search long enough in the right places.

Anyways...My issue:

We had an internal ssh server running for a while, this is now upgrade with an additional NIC.
The server will have one NIC that connects to our internal network, the other one connects directly to the internet.
The server is also acting as a router/firewall.

The server works fine, but there is one thing that has come to my attention. Its the ListenAddress keyword. As i gathered one should always tell the server what address(es) it should listen to, but we have a dynamic IP address...

My question here is: what wold be the easiest way to keep the external IP up to date in the sshd_config?  I guess the most likely approach here is scripting the update of the sshd_config.

Im no expert on SSH so i´d like to hear what other solutions is out there.

Our sshd_config looks like this:

Port 22
AddressFamily inet
ListenAddress 192.168.1.11   
ListenAddress ???????????? <---------- External IP
Protocol 2

HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
ServerKeyBits 1024

SyslogFacility AUTH
LogLevel DEBUG

LoginGraceTime 60
PermitRootLogin no
StrictModes yes
MaxAuthTries 5
MaxSessions 5
ClientAliveInterval 1200
ClientAliveCountMax 0
AllowGroups manager biz

RhostsRSAAuthentication no
RSAAuthentication yes
PubkeyAuthentication yes
PasswordAuthentication yes
PermitEmptyPasswords no

Subsystem       sftp    /usr/libexec/sftp-server
Match group secftp
         ChrootDirectory %h
         X11Forwarding no
         AllowTcpForwarding no
         ForceCommand internal-sftp

All suggestions on updating the external IP and improvements of the sshd_config are greatly appreciated.

---

### Post by azmyth on 2011-12-09
I'm just a home user but the way I do it is I setup a forwarding service using no-ip.biz and I just setup a name like blah.no-ip.biz. The no-ip script that checks your IP is in the repo. This will dynamically update your IP in the event it changes. I then just use ssh using my made no-ip name so I just use ssh [email]name@blah.no-ip.biz[/email]

---

### Post by lykwydchykyn on 2011-12-09
If you comment out all "listaddress" directives, the default is to listen on all addresses on all interfaces.  Unless there's an interface you *don't* want to run ssh on, this is probably the simplest solution.

---

### Post by blackseptember on 2011-12-09
Thanks for you reply azmyth

I know of the no-ip setup, which is pretty good. It´s similar to what i eventually will be using, but the no-ip setup dont update the sshd_config´s ListenAddress [ external IP ].

---

### Post by blackseptember on 2011-12-09
I agree with you, lykwydchykyn, that commenting out the ListenAddress, or  using ListenAddress 0.0.0.0, is one way to solve this - but from a security point of view this is usually discouraged.

Does anyone know if sshd_config take FQDN in ListenAddress?

---

### Post by N00b-un-2 on 2011-12-09
I've just done this myself.  you're going to need a DNS because virtually all ISPs do not supply static IP addresses anymore.  Mine charges a good deal of money to lease a static IP.  Just set yourself up with a DNS at no-ip and then install noip2 package on you system to periodically update your DNS with your current external IP.  Beyond that, assuming you are behind a router, you need to assign static local IP addresses in your router's DHCP reservation menu and then forward the port you plan on using.  Also worth noting is that many ISPs will block traffic on lower ports like 22.  set your port to something much higher like 5000.
Works like a charm for me using FTP, SSH and VNC.  Nothing beats being able to grab my homework I forgot to print off my desktop from my Android phone while I'm at school and then emailing it to my instructor.

---

### Post by blackseptember on 2011-12-09
Ooops, totally forgot to add this in my explanation - the ssh server is also used as a router/firewall - so no i cant really put another router infront of it (lack of hardware).

...Adding information to original post now :)

---

### Post by perspectoff on 2011-12-09
You don't specify the external IP as a ListenAddress for SSH.

You specify the port that SSH listens on, and then it is your (hardware or software) router's job to forward that port to the computer on the LAN on which your SSH server is running.

For example, my SSH server is at 192.168.0.133.

My router is then set to forward all port 22 SSH traffic to 192.168.0.133.

The SSH server on 192.168.0.133 listens for port 22 traffic.

End of story. 

If you have multiple computers on a LAN each running a SSH server, each should listen on a different port.

For example, one SSH server could listen on port 22133, and another could listen on port 22134.

The router would direct those ports to the appropriate LAN IP address of each SSH-serving computer on the LAN, and you would select which computer into which to SSH by specifying the correct port.

The you could SSH using your (dynamically maintained) URL address:

to computer 1: ssh mydynamicurl.dyndns.org:22
to computer 2: ssh mydynamicurl.dyndns.org:22133
to computer 3: ssh mydynamicurl.dyndns.org:22134

BTW, there's a good deal of advice on Dynamic DNS at

[http://ubuntuguide.org/wiki/Ubuntu:All#Using_Dynamic_IP_addresses_for_a_webserver](http://ubuntuguide.org/wiki/Ubuntu:All#Using_Dynamic_IP_addresses_for_a_webserver)

or 

[http://ubuntuguide.org/wiki/Dynamic_IP_servers](http://ubuntuguide.org/wiki/Dynamic_IP_servers)

Also, regarding SSH:

[http://ubuntuguide.org/wiki/Ubuntu:All#SSH](http://ubuntuguide.org/wiki/Ubuntu:All#SSH)

---

### Post by lykwydchykyn on 2011-12-09
> **blackseptember said:**
> I agree with you, lykwydchykyn, that commenting out the ListenAddress, or  using ListenAddress 0.0.0.0, is one way to solve this - but from a security point of view this is usually discouraged.

By whom and why?
> 
Does anyone know if sshd_config take FQDN in ListenAddress?

I just tried it.  It appears the answer is no.

---

### Post by blackseptember on 2011-12-09
Thank you for a  good reply perspectoff

Our set up looks like this:
[ Internet ] <-----> [ NIC 1 ]| Firewall/router/ssh |[ NIC 2 ] <-----> [ LAN ]

The ssh server is infact the router/firewall here.

From the explanation you give me, im guessing i could use the firewall to forward the traffic from NIC 1 to it´s internal address:port on NIC 2 and specify the internal address in ListenAddress.

---

### Post by blackseptember on 2011-12-09
Not binding the IP address of a service could, apparently, lead to hijacking of that service, should the box be compromised. 

[Hijacking a service]("http://flylib.com/books/en/3.85.1.7/1/")
[Configure the /etc/ssh/sshd_config file]("http://www.faqs.org/docs/securing/chap15sec122.html")

---

### Post by CharlesA on 2011-12-09
> **lykwydchykyn said:**
> By whom and why?

I don't know, but there really shouldn't be much security problem unless you fail to secure SSH properly.

> **blackseptember said:**
> Not binding the IP address of a service could, apparently, lead to hijacking of that service, should the box be compromised. [/URL]

Perhaps, but if you secure SSH properly (use super strong passwords, or keys) and firewall it with rate limiting/DenyHosts, you should be fine.

---

### Post by blackseptember on 2011-12-09
I hear you, we will be moving away from password and use PKI instead. This narrows down the possible offenders to our base of users, then again most attacks are made by internal users.

---

### Post by lykwydchykyn on 2011-12-09
> **blackseptember said:**
> I hear you, we will be moving away from password and use PKI instead. This narrows down the possible offenders to our base of users, then again most attacks are made by internal users.

This is definitely a good idea, something I've been trying to enforce for outside SSH myself.

If using the firewall to forward ssh connections to the internal connection works, then I think this would be the best bet; but if not, then honestly it's probably less of a risk to let SSH bind to all IPs than to have some custom script constantly modifying sshd_config.

---

### Post by blackseptember on 2011-12-09
Hmmm...Think i´m gonna give scripting a go then.
If you are a good scripter i´d appreciate your feed back on it, will post it in this thread when im done.

---

### Post by azmyth on 2011-12-09
Someone in this thread is trying to right a script to check IP. Instead of mailing, you could have the script change your ssh conf file and resart. It's a bit of a hack.

[http://ubuntuforums.org/showthread.php?t=1892615](http://ubuntuforums.org/showthread.php?t=1892615)

---

### Post by blackseptember on 2011-12-09
The basic idea for the script i´ll be writing:

if [ ListenAddress external IP ] != [ external NIC IP ]
then 
    replace [ ListenAddress IP ] with [ external NIC IP ]
    restart sshd
fi

---

### Post by collisionystm on 2011-12-09
Why are you even modifying SSHD ?

You only need to do this if you have more than 1 internal and external.
If your 192.168.XXX.XXX and your external are the only addresses on the box, you don't need to waste your time with that. It is doing nothing beneficial.

I suggest taking the script that we created in here, go forward a few pages 
[http://ubuntuforums.org/showthread.php?t=1892615](http://ubuntuforums.org/showthread.php?t=1892615)

Have it email you whenever the IP address changes

Either configure your IP tables to filter out ssh requests or
Set your hosts.allow to only accept sshd from certain outside IP's and your hosts.deny to sshd; ALL

---

### Post by blackseptember on 2011-12-09
Binding the external IP address would be beneficial against service hijacking.

Having a script fetch the external NIC IP address from an external site, not sure why one would do that - it can be read straight from the external NIC.

If emailing the IP address one would manually have to change that, thus closing access for the employees.

Only allowing a certain range or list of IP addresses would simply not be possible, people move around all the time and connect from unknown locations.

---

