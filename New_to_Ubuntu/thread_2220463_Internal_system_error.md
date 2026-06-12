---
title: "Internal system error"
date: 2014-04-28
forum: New to Ubuntu
---

### Post by davoudi on 2014-04-28
Hi Folk,

So I recently install a Ubuntu 13.10 on my laptop but I face internal system error every other time. I lose internet service and unfortunately restarting the network using command "sudo service networking restart" messes everything up.

 I would be grateful if you could help me with this issue otherwise I have to switch to Ubuntu 12.10 and reinstall everything from scratch.

Best wishes,
Bahman.

---

### Post by ian-weisser on 2014-04-28
Please show us the entire output of the command:
```
ls -l /var/crash/
```
(those are both lowercase Ls)

---

### Post by davoudi on 2014-04-28
Here is the outcome and thanks for your time.

-rw-r----- 1 root     whoopsie  489484 Apr 28 10:53 _opt_cisco_anyconnect_bin_vpnagentd.0.crash
-rw-r--r-- 1 root     whoopsie       0 Apr 28 10:53 _opt_cisco_anyconnect_bin_vpnagentd.0.upload
-rw------- 1 whoopsie whoopsie       0 Apr 28 10:53 _opt_cisco_anyconnect_bin_vpnagentd.0.uploaded
-rw-r----- 1 bahman   whoopsie 5583707 Apr 26 14:30 _usr_lib_chromium-browser_chromium-browser.1000.crash
-rw-r----- 1 bahman   whoopsie  109828 Apr 26 11:40 _usr_share_software-center_software-center.1000.crash
-rw-r--r-- 1 bahman   whoopsie       0 Apr 26 11:40 _usr_share_software-center_software-center.1000.upload
-rw------- 1 whoopsie whoopsie       0 Apr 26 11:40 _usr_share_software-center_software-center.1000.uploaded

---

### Post by ian-weisser on 2014-04-28
Okay, that lists the applications that crashed and when.
Example: Software Center crashed on April 26 11:40

Each of those files is a simple text file. You can open it in any text processor or word processor.
All those crashes are network-related applications.

Next, look at /var/log/syslog.
After a crash, do the command
```
cat /var/log/syslog | grep Network
```
and post the entire output here.

---

### Post by davoudi on 2014-04-28
The output is too big that I cannot copy and paste all.

---

### Post by ian-weisser on 2014-04-28
The just post the few minutes before the crash - the period when your network connection failed.

---

### Post by davoudi on 2014-04-29
Here is the output and thanks for your time.


Apr 29 18:34:34 bahman-Laptop NetworkManager[731]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Apr 29 18:34:34 bahman-Laptop NetworkManager[731]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Apr 29 18:34:34 bahman-Laptop NetworkManager[731]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Apr 29 18:34:34 bahman-Laptop NetworkManager[731]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Apr 29 18:34:34 bahman-Laptop NetworkManager[731]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Apr 29 18:34:34 bahman-Laptop NetworkManager[731]: <info> dhclient started with pid 1494
Apr 29 18:34:34 bahman-Laptop NetworkManager[731]: <info> Activation (eth0) Beginning IP6 addrconf.
Apr 29 18:34:34 bahman-Laptop NetworkManager[731]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Apr 29 18:34:34 bahman-Laptop NetworkManager[731]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Apr 29 18:34:55 bahman-Laptop NetworkManager[731]: <info> (eth0): IP6 addrconf timed out or failed.
Apr 29 18:34:55 bahman-Laptop NetworkManager[731]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Apr 29 18:34:55 bahman-Laptop NetworkManager[731]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Apr 29 18:34:55 bahman-Laptop NetworkManager[731]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Apr 29 18:35:10 bahman-Laptop NetworkManager[731]: <info> (eth0): DHCPv4 state changed preinit -> bound
Apr 29 18:35:10 bahman-Laptop NetworkManager[731]: <info>   address 194.225.69.248
Apr 29 18:35:10 bahman-Laptop NetworkManager[731]: <info>   prefix 25 (255.255.255.128)
Apr 29 18:35:10 bahman-Laptop NetworkManager[731]: <info>   gateway 194.225.69.129
Apr 29 18:35:10 bahman-Laptop NetworkManager[731]: <info>   nameserver '194.225.73.141'
Apr 29 18:35:10 bahman-Laptop NetworkManager[731]: <info>   nameserver '194.225.152.10'
Apr 29 18:35:10 bahman-Laptop NetworkManager[731]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Apr 29 18:35:10 bahman-Laptop NetworkManager[731]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
Apr 29 18:35:11 bahman-Laptop NetworkManager[731]: <info> (eth0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Apr 29 18:35:11 bahman-Laptop NetworkManager[731]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
Apr 29 18:35:11 bahman-Laptop NetworkManager[731]: <info> (eth0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Apr 29 18:35:11 bahman-Laptop NetworkManager[731]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Apr 29 18:35:11 bahman-Laptop NetworkManager[731]: <info> DNS: starting dnsmasq...
Apr 29 18:35:11 bahman-Laptop NetworkManager[731]: <warn> dnsmasq not available on the bus, can't update servers.
Apr 29 18:35:11 bahman-Laptop NetworkManager[731]: <error> [1398780311.785404] [nm-dns-dnsmasq.c:402] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name

---

### Post by JeQhdMD on 2014-04-29
G'day Avoudi,

First,  a general comment based on your possible intent to re-install 12.04.   Considering 14.04 just released, why not get the latest system, including networking setup?

Secondly, have you modified "anything" in your network setup . . are you utilizing IPv4 or IPv6?   IPv6 requires extra config, and is not supported yet by many common websites.

---

### Post by ian-weisser on 2014-04-29
Looks like your wired ethernet connection (eth0) reset. The log you posted seems to show a new connection starting up.
Yeah, restarting the network wouldn't help. Indeed, that seems pretty close to the problem you are already having.

A wired ethernet connection can fail for many possible reasons.
I recommend trying to isolate the fault to one of three possible causes: Your system, the upstream router, or the wiring between,
eliminating one of two of those possible causes will help a lot.

Router: Does anyone else on your network have a similar problem?
Router/wiring: Do you have the exact same problem if you use a different ethernet cable and a different router port?
Do you have a different system you can plug into the connection to see if it's a wiring fault or a problem with your system?

---

