---
title: "Using Hostnames with ssh"
date: 2013-10-24
forum: New to Ubuntu
---

### Post by newb85 on 2013-10-24
So I finally got around to setting my machines up so that they can ssh into each other.  UFW is enabled, and a rule allowing ssh has been added.  I edited sshd_config to prevent root login.  At least I feel like I have some level of security now.  (I don't really know that the firewall is doing anything, though, since the only port my machine is listening to is 22, and UFW is set to allow ssh on that port, but I digress...)

To the point:  The basic syntax for ssh is:
```
ssh [user]@hostname
```

Now I can get this to work if I enter the target machine's local IP address.  It works, but that seems a sub-optimal approach.  Right now I don't have my router set up to bind IP and MAC addresses.  Even if I do that, I don't know that I want to have to recall the machine address each time I ssh.  I would have thought I could make it work with something like this:
```
ssh aaron@aaron-OptiPlex-745
```
but when I issue that command, nothing happens.  The terminal just sits there like it's looking for something.  (I guess it's unsuccessfully trying to find the target machine.)  Am I missing something?

[s]Side point: Once I've established the ssh connection, my command prompt doesn't change.  I expected it to somehow reflect the ssh login, but instead it still shows the name of the machine I'm sitting at.  Again, am I missing something?[/s]
Either I wasn't seeing straight and this was actually doing what I expected it to, or the behavior changed after I rebooted the target machine.

---

### Post by Lars Noodén on 2013-10-24
You can put shortcuts in [~/.ssh/config](http://manpages.ubuntu.com/manpages/raring/en/man5/ssh_config.5.html)

```

Host op
	User aaron
	HostName aaron-OptiPlex-745

```

With the above, you only have to type *ssh op* and it will start to connect.  Hostname can have a name or an ip number.  But if your machines have dynamically generated ip numbers, such as from DHCP, then some other trick is needed in addition.

---

### Post by newb85 on 2013-10-24
The only file in the ~/.ssh directory is known_hosts.  Should I simply create the config file?

Update: creating the config file worked, but I still have the same problem as before.  If I put the local IP of the target machine in the config file for the HostName everything works great, but if I enter the name of the machine, "aaron-OptiPlex-745", the ssh command just hangs like it can't find the machine.  Yes, I have triple checked that I have the machine name entered correctly.

---

### Post by Lars Noodén on 2013-10-24
How is your machine going to look up the ip address for  "aaron-OptiPlex-745"?  Do you have something in /etc/hosts or do you have some local DNS like dnsmasq running?

If the machines keep the same ip numbers all the time, you can just use those in ~/.ssh/config and connect using your shortcuts.

---

### Post by newb85 on 2013-10-24
> **Lars Noodén said:**
> How is your machine going to look up the ip address for  "aaron-OptiPlex-745"?  Do you have something in /etc/hosts or do you have some local DNS like dnsmasq running?

Don't think so.  I guess that's what I'm missing.  It hadn't occurred to me, but I guess it makes sense that my machine needs to look up the IP address somewhere.

Come to think of it, this might also be why Nautilus gives me the "Failed to retrieve share list from server" messages when I try to browse the network.

Can you give me a little more info on those options?

---

### Post by drmrgd on 2013-10-24
So, this sounds like you are working strictly on a LAN.  Is that right?  If so, then why not just set your computers to get static IP address from the router and use that IP address in your SSH config file?  The "Host" entry acts like a nickname for the connection and is probably easier to type than that long string (although I think autocompletion works with the config file anyway...but I digress :) ).  If you really want to use that long name, then you can set it up like so:

```

Host aaron-OptiPlex-745
HostName 192.168.1.x
User aaron

```

Also, another thing you can do if you like to increase security a bit, is to have SSH listen on a different port than 22.  Set it to something like 10022 and then have the router forward traffic coming in for 22 to 10022.  Looking at /var/log/auth.log on some of my servers, I notice gobs, and gobs of attempts for those on 22.  For those on obscure ports, it's much less traffic.   You can further that by installing DenyHosts, which is pretty easy to setup, and will do things like completely block traffic from IP addresses that have attempted to access the system with too many failed attempts.

---

### Post by bab1 on 2013-10-24
> **newb85 said:**
> Don't think so.  I guess that's what I'm missing.  It hadn't occurred to me, but I guess it makes sense that my machine needs to look up the IP address somewhere.

Come to think of it, this might also be why Nautilus gives me the "Failed to retrieve share list from server" messages when I try to browse the network.

Can you give me a little more info on those options?

The short story is that anytime you refer to a host by name (hostname or alias), that name needs to be resolved to an IP address.  This is usually done by DNS or by setting the hostname to IP mapping in the /etc/hosts file.

The long story is full of variables you need to make configuration decisions about.  Dynamic addressing via DHCP requires that the client provide the hostname while asking for an IP address,  The "Failed to retrieve share list from server" could be a NETBIOS problem, but just as well be a misconfigured DNS setting.  NETBIOS is limited to 15 characters and Samba relies on the /etc/hosts file to convert hostnames into NETBIOS names.  Lots of interconnection here.

SSH also assumes you have set the LAN name services up correctly.  I use this to connect to my remote hosts:  ***ssh <hostname>***,   This assumes that I am connecting as me and the hostname is resolved by the hosts file or DNS.

You need to decide whether you want to rely on DHCP for dynamic IP addresses.  If you do then you need to setup dynamic DNS resolution (BIND9 ???) .  If don't then you will need to take the time to set up immutable (non-changing) IP addresses you can either do that by IP reservations (in the router (DHCP server)) or via static IP addressing (using files (/etc/network/interfaces)).

---

### Post by Lars Noodén on 2013-10-25
Well, one of the options is to store the ip address in the ssh config file as part of the shortcut.  That's been suggested twice above.

If your machines always get the same LAN addresses, you can go around and edit /etc/hosts with the names you want.  Note that this method is a bit of work and does not scale well as it has to be done on each machine.  

Depending on what your modem / router has on it, you might be able to assign names using it.  If you have DD-WRT or OpenWRT on it, dnsmasq should be an option.  That provides DHCP but can also resolve the occasional hostname if configured to do so.

---

### Post by newb85 on 2013-10-25
Thanks! I set static IP addresses fire the machines in question, and added them to the hosts file.

---

