---
title: "get hostname from ipaddress"
date: 2013-04-25
forum: Programming Talk
---

### Post by IAMTubby on 2013-04-25
Hello,
Is there a way programmatically/linux command to get the hostname/computer name given an ip address.
The ip address I'm giving is that of a system running Windows.
I am looking for something like

$(a-linux-command) 10.94.9.18
Output:WN7-COMPUTERNAME

Note:10.94.9.18 is the ip address of a windows system and WN7-COMPUTERNAME is the name of that system. I'm able to ping the computer name from linux and that also gives me the ip address - but I'm looking for the exact opposite.

[B]
_Tried the following_
1.nslookup, but don't get the desired o/p/
$ nslookup 10.94.9.18
Server:         10.94.165.80
Address:        10.94.165.80#53


** server can't find 18.9.94.10.in-addr.arpa.: NXDOMAIN

2.dig -x 10.94.9.18, but doesn't work.

3.nbtstat works on windows, but I want it in linux[/B]

---

### Post by Lars Noodén on 2013-04-25
Here is one way using host, tail and sed.

```

host *xx.yy.zz.aa* | tail -n 1 | sed -e "s/^.* //;s/[[:punct:]]*$//"

```

You can then put that inside $()

---

### Post by SeijiSensei on 2013-04-25
Is there a nameserver on your network that is authoritative for the 9.94.10.in-addr.arpa domain?  From the reply to your nslookup request, the answer seems to be no.

You can send an nmblookup request against a Windows host to get its Netbios name like this:

```
nmblookup -A 10.94.9.18
```

Here is an example:
```

[root@localhost ~]# nmblookup -A 192.168.100.102
Looking up status of 192.168.100.102
        FUZZFACE        <00> -         M <ACTIVE>
        WORKGROUP       <00> - <GROUP> M <ACTIVE>
        FUZZFACE        <20> -         M <ACTIVE>

        MAC Address = 8C-A9-82-B0-3A-F2

```

The computer's Netbios name is "fuzzface".  To return just the hostname use:

```
 nmblookup -A 192.168.100.102 | grep '<00' | grep -v GROUP | awk '{print $1}'
```

nmblookup is included in the **samba-common-bin** package.

---

### Post by TheFu on 2013-04-25
Windows uses proprietary networking techniques to find proprietary systems.  If the remote computer is in DNS (the standard) properly, then forward and reverse lookups work regardless of OS.  nslookup, dig both query DNS servers. Microsoft often doesn't populate DNS with Windows system names unless the Windows Administrator has a real desire to make life easier for everyone on the network. Most do not.

What is nbtstat?  It is a proprietary tool from Microsoft that speaks a proprietary Netbios protocol.  I don't know the tool, but there must be one that does this for Linux and will return the information you want.  My initial thought is to use **nmap**.  Something like **sudo nmap -sT -PN 10.94.9.18** should work.  nmap is a network scanning tool and is against corporate policy if used by anyone outside the IT security team in most companies. Be careful using it. You might be fired.  It has lots of options, the man page explains everything.

If that tool doesn't work, I'd look in the suite of tools around samba. Samba speaks CIFS, which is what Netbios has morphed into over the years.  A tool like smbtree might be helpful, I didn't read the man page recently.  smbclient may also help. Read the man page for each to see.

After writing this, I did a google for "nbtstat for linux" which returned very useful results that I'm sure you've already seen.  Did those tools not work for you?

---

### Post by IAMTubby on 2013-04-25
> **SeijiSensei said:**
> 
```
nmblookup -A 10.94.9.18
```

SeijiSensei, wow that was fantastic :D
Can I be a bit greedy and ask you if there is something that can give me the name of the logged in user as well ?

---

### Post by IAMTubby on 2013-04-25
> **Lars Noodén said:**
> Here is one way using host, tail and sed.

```

host *xx.yy.zz.aa* | tail -n 1 | sed -e "s/^.* //;s/[[:punct:]]*$//"

```

You can then put that inside $()
Lars, I wasn't able to get that. This is the output
$ host 10.16.97.89  | tail -n 1Host 89.97.16.10.in-addr.arpa. not found: 3(NXDOMAIN)

I got the desired output(computer name) using nmblookup though. Now seeing if I can get the name of the logged in user using the same.

---

### Post by IAMTubby on 2013-04-25
> **TheFu said:**
> Something like **sudo nmap -sT -PN 10.94.9.18** should work.
Sorry TheFu, couldn't get that to work.

---

### Post by Lars Noodén on 2013-04-26
> **IAMTubby said:**
> Lars, I wasn't able to get that. This is the output
$ host 10.16.97.89  | tail -n 1Host 89.97.16.10.in-addr.arpa. not found: 3(NXDOMAIN)


That only works with the standard way (DNS) of doing things.  I thought you were using DNS, but  SeijiSensei found the way for the proprietary product you are using instead and TheFu gave a good explanation.  The short answer is that MS products, in their defaults, do not play well with others.  

About nmap, there is a graphical front end for it called zenmap, you might find that easier.  nmap can be a little complicated at first, but it is quite flexible and powerful.  You have to run it with root privileges 'gksudo zenmap'

---

### Post by schragge on 2013-04-26
> **IAMTubby said:**
> Now seeing if I can get the name of the logged in user using the same.Perhaps this could be done with [smbclient]("http://manpages.ubuntu.com/manpages/raring/en/man1/smbclient.1.html"), but it depends on what services are provided by Windows machine.

---

### Post by SeijiSensei on 2013-04-27
> **IAMTubby said:**
> Can I be a bit greedy and ask you if there is something that can give me the name of the logged in user as well ?

You'd have to look in the log file for the connecting client.  In /var/log/samba you should see logs with either hostnames or IP addresses.  In the log for 10.94.9.18, you should see entries like this:

```
[2013/04/26 17:46:03, 1] smbd/service.c:make_connection_snum(1085)
  black-beauty (192.168.100.104) connect to service joe initially as user joe (uid=1000, gid=1000) (pid 15783)
```

You'll notice that this entry has all the information you seek.  It gives the IP address and Netbios name of the client along with the username and share being accessed.

---

### Post by IAMTubby on 2013-04-28
> **SeijiSensei said:**
> You'd have to look in the log file for the connecting client.  In /var/log/samba you should see logs with either hostnames or IP addresses.  In the log for 10.94.9.18, you should see entries like this:

```
[2013/04/26 17:46:03, 1] smbd/service.c:make_connection_snum(1085)
  black-beauty (192.168.100.104) connect to service joe initially as user joe (uid=1000, gid=1000) (pid 15783)
```

You'll notice that this entry has all the information you seek.  It gives the IP address and Netbios name of the client along with the username and share being accessed.
SeijiSensei, that was fantastic :D
Got it, I had logs like cores  nmbd.log  nmbd.log.1  nmbd.log.2  nmbd.log.3  nmbd.log.4  smbd.log  smbd.log.1  smbd.log.2  smbd.log.3  smbd.log.4, with the smbd logs giving me the required data.
Thanks once again, would have marked thread as solved but don't see the option in ThreadTools
Thanks also to Lars Nooden,TheFu and schragge.

---

### Post by SeijiSensei on 2013-04-28
I use [CentOS]("http://www.centos.org/") for servers, and that implementation creates separate logs for each client IP address.  Apparently Ubuntu puts all that information in the standard smbd and nmbd logs.

---

