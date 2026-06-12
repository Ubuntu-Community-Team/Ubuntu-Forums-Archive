---
title: "Firewall Scripts For Newbies"
date: 2006-12-13
forum: Outdated Tutorials &amp; Tips
---

### Post by SuperMike on 2006-12-13
Tested: All current and previous Ubuntu versions up until Dapper. May work on Edgy or Feisty or may not.

I. ROCKET FAST FIREWALL PRIMER

Let's get to the point. You have a new Linux or Unix PC, and you want a firewall on it without something that confuses you nor sprays files all over your hard drive in unknown places. You don't want to use something third-party, and you want to improve it meticulously as you learn how to do so. SuperMike is going to hook you up!

First, however, for your own benefit, if you don't know what the terms Linux kernel, firewall, TCP, UDP, or TCP/UDP ports are, then you need to start there before even coming to this doc. Try an acronym site or wikipedia. Oh, and if in an office environment, I also recommend that you don't use this doc to lock down a production server while it's running -- always test on a staging system and get it right before coming back to the production server. Then, make a late-night outage window after a full backup, and let everyone know, in order to install this into production to see if it can work.

So how does a firewall work with Unix and Linux? On these operating systems after about the year 2000, there's a kernel module, NetFilter, which provides the firewall. It was created by an Australian IBM developer, Rusty Russell, and a team of other developers on the web. It is interfaced with the iptables command. It was an improvement on the ipchains command that was previously used. Each iptables command interfaces either with 1 of 3 different interfaces in NetFilter: INPUT, OUTPUT, and FORWARD. INPUT and OUTPUT deal with something like doorways in and out of your operating system. The path that network traffic would take, if it was meant for you, would only come in through the INPUT doorway. Traffic that your system wants to send goes through the OUTPUT doorway. FORWARD is like a mail chute to another operating system and is often used in something called "IP Masquerading", where other people who interface with you consider your IP address to be the same as your proxy or router, or that your proxy or router appears to use your IP address. The FORWARD "chute" discussion is another discussion thread, another day. You can still use this firewall tutorial to get started without it.

The path the network traffic takes through these doorways and chutes are caled rules. The iptables commands that you write change those rules. The rules concentrate primarily on the protocol, TCP or UDP, and the ports for that protocol, which are in the range of 0-65535. When you surf the web, you are using TCP port 80, whether you know it or not. That's the standard for web surfing and web servers usually have that enabled. Since it's the standard, you never had to type it and it's always used. Most applications or daemons/services on your operating system, if they are network-aware, interface with the TCP protocol. TCP is for a solid connection. UDP, however, is like a telegram -- it's for a risky, unstable connection but sometimes is the only way to ensure traffic gets through. (A bit of history. Both were invented to be combined and used in the event of an atomic blast so that network traffic could route through a city in the event a city was eliminated. However, nowadays, we use both to route traffic efficiently through routers.) Applications are written to either use TCP or UDP exclusively, or both. If you were writing an application, wouldn't you want to use both so that you could have one do a heartbeat and ensure everything was running smoothly, or have a failover protocol in case the other protocol was blocked or stopped? Some developers feel the same way. Sometimes it's not always clear what they use, so you have to experiment, read docs, post forum messages, or ask a mentor. To see what ports are usually used for applications, find a keyword (like "pop" for mail hosting) in your /etc/services file with a command like

```
sudo cat /etc/services | grep -i "pop"
```

For starting out, I'm going to demonstrate an INPUT-based firewall because it's fairly secure and easier. Some people like using both INPUT and OUTPUT rules. They like OUTPUT rules because these are the kind that can prevent something like a trojan horse, that may have unknowningly already invaded your system, from calling home and doing more carnage. The problem with using OUTPUT rules are that they require a lot of testing and skill so as not to mess up applications. The combination of INPUT and OUTPUT rules, however, make a firewall stronger. That, I'm afraid, is another thread, another day.

II. GET STARTED FAST!

Start by saving this script in /etc as "firewall.sh" and following the instructions at the bottom of it.

```
#!/bin/bash
# /etc/firewall.sh
#
# When the script runs, it flushes the firewall rules with "iptables -F",
# pokes holes, permits a hole for DNS queries, rejects everything else,
# and shows you what the rules are so that you know it's working.
#
iptables -F
iptables -A INPUT -i lo -j ACCEPT
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -p tcp -m tcp --dport XXX --syn -j ACCEPT
iptables -A INPUT -p udp -m udp --dport XXX -j ACCEPT
iptables -A INPUT -p udp -m udp -s ZZ.ZZ.ZZ.ZZ1 --sport 53 -d 0/0 -j ACCEPT
iptables -A INPUT -p udp -m udp -s ZZ.ZZ.ZZ.ZZ2 --sport 53 -d 0/0 -j ACCEPT
iptables -A INPUT -p tcp -m tcp --syn -j REJECT
iptables -A INPUT -p udp -m udp -j REJECT
iptables -L
#
# After saving, do "sudo chmod u+x /etc/firewall.sh" on me.
# To run or test me, call me with "sudo sh /etc/firewall.sh".

```
III. CONFIGURING - POKING HOLES FOR PORTS

On the lines with XXX, the XXX's are to be replaced with a port number that you want to open up so that your network-aware application or daemon/service can send or receive requests on that port. Later on, we're going to decide whether we need TCP, UDP, or both for your application or daemon/service. For now, though, I strongly encourage you to enable both TCP and UDP and attempt to eliminate one of these later in another step. I would also strongly recommend only focusing on one application or service/daemon at a time, getting it right, and then repeating with other ports for other applications or service/daemons. You will be less frustrated that way.

IV. CONFIGURING - HOLES FOR DNS ARE IMPORTANT

The lines with ZZ are for your DNS lookups, such as when you type "google.com" in your browser and it goes to your DNS server, translates this to an IP address, and then tells your browser to go there. Note I have two lines -- one is for your primary DNS, the other for your secondary DNS. To find out what these are on your system, use your network control panel if you have one, or do 

```
sudo cat /etc/resolv.conf
```

to see if that returns a result. Note you'll want to use the IP addresess if you can, rather than the names, because this speeds up your network activity. Replace the ZZ.ZZ.ZZ.ZZ1 and 2 with those IP addresses.

V. TESTING - CALLING THE SCRIPT

Now start testing your firewall by calling it with:

```
sudo sh /etc/firewall.sh
```

Remember that I recommend you only test one set of ports for one application or service/daemon at a time, growing this script as you work ou the kinks. To get this thing to run all the time on reboots, you can either put it in /etc/init.d as a service/daemon (which is another discussion thread entirely), or do the simple thing of having your GDM, XDM, or KDM call it when that thing loads, such as, for Ubuntu Linux, editing the file "/etc/X11/gdm/Init/Default" and putting the line "/etc/firewall.sh" right after the PATH variable is set at the top. (For the noobs, a GDM is the Gnome Desktop Manager, and this loads after X loads least on my favorite distro, Ubuntu Linux. It starts by showing you a login screen. The KDM is for the KDE desktop, and XDM for someone who wants another kind of desktop.)

VI. TESTING - FIXING PROBLEMS

As you test the firewall, you may find that it doesn't work. Don't give up. The most obvious conclusion is that you either have the wrong ports, or need more than just one port poked through. If you want to disable your firewall while you think about this, do

```
iptables -F
```

Perhaps you were testing too many ports at once and it's frustrating you -- try to pair it down to just the ports you want to test in a given moment. You may also find that the "--dport" parameter on an iptables line does not work for all applications or daemons/services. That was my case when I used the NTP protocol from the clock synchronization within my clock control panel. In those cases, switch "--dport" with "--sport" and see if that doesn't help. I would, however, recommend using "--sport" unless you absolutely have to use this. Last, you could have a syntax error -- remember that Linux and Unix are case-sensitive, a double-dash "--" means a double-dash, a backslash and foreslash are different, a pipe character is different than a slash, and a space really does mean a space.

VII. TESTING - ELIMINATING WHAT YOU DON'T REALLY NEED

Once you get a certain application and/or service/daemon working, now eliminate the UDP option by commenting that iptables line out with a "#" as the first character on the line in your /etc/firewall.sh, bounce or relaunch your appication or service/daemon and see if it still works. If it does, then you probably don't need UDP enabled for that particular use. If it breaks, then switch to enabling just the UDP, commenting out the TCP line with "#". If that breaks even still, then switch to enabling both.

Now you may have more ports enabled than you think you need for an application or daemon/service. For instance, if you enabled all the POP ports on a system that hosts a mail server, including the ones for secure SSL email when you don't use that feature, then you should comment these extra ports out and test to see if the thing still works.

If the applications are currently running, sometimes you can use the

```
lsof -i
```

and

```
netstat -nlp
```

commands as an aid (but not the definitive source) to determine what ports are necessary, as long as you ask more intermediate users what the output of those commands are saying. I mean, I wouldn't want you to be misled by this output, to open a port that you don't necessarily need open.

VIII. CONCLUSION AND SUGGESTIONS FOR IMPROVEMENT

You're done for now. You should have a working firewall script that you can reuse in most cases, you can also expand it. This is not the safest firewall script in the world, but is ideal if you're already behind a NAT router or existing company firewall. This is a good starting point and I highly recommend you stick with this starting point for a couple months to ensure everything is working right. Then, move to enhancing this with more features. To do that, google on topics that have the keywords that at least include "iptables" and may include other keywords like "honeypot", "masquerade", "spoof", "of death" (in quotes), "logging", "drop", "reject", "intermediate", etc. These can show you how to avoid common things like IP spoofing and the "ping of death", where a malformed packet on your subnet or even your PC can be created to bring your applications and services/daemons down or cause you to authenticate a bogus user or permit the bogus user to extract secure information.

---

### Post by frodon on 2006-12-14
Hi and thanks for your guide.

Users interested by iptables may find detailed informations in a similar guide i wrote :
[http://ubuntuforums.org/showthread.php?t=159661](http://ubuntuforums.org/showthread.php?t=159661)

---

### Post by SuperMike on 2006-12-16
I have some more to add:

To block hosts coming to your system, they say use hosts.deny, but then I read that some services don't respect that. Therefore, do it in your iptables firewall script right before the **iptables -A INPUT -i lo -j ACCEPT** with:
```

iptables -A INPUT -s <address goes here> -j DROP
```
You should find out the IP address and don't use a hostname because the 'man' for iptables tells you that DNS lookups are a really bad idea for iptables -- don't make it do that. Ping it to find the IP and then use that instead.

Repeat this command multiple times for each host you want to block.

Oh, and if you haven't installed **jnettop**, I highly recommend it in order to see what kind of traffic you have and where it's going.

P.S., I think you might be able to block a whole subnet if you add /24 on the end, like this example. If you want to block 192.167.4.x, you would do it like:

```

iptables -A INPUT -s 192.167.4.0/24 -j DROP
```

---

