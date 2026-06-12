---
title: "Transmission not working after upgrade to 12.04"
date: 2012-05-17
forum: New to Ubuntu
---

### Post by Moriarty123456 on 2012-05-17
Hi Folks,

I've recently upgraded from 11.10 to 12.04 and Transmission is now no longer working. Used to work just fine in 11.10. I've re-installed Transmission - no change. I've checked in the Preferences>Network tab of Transmission and it says "Port used for incoming connections: 56275". Hitting the "test port" button says "Port is closed". I then entered into the terminal:
```
sudo ufw allow 56275/tcp
```Output:
```
WARN: uid is 0 but '/etc/default/ufw' is owned by 1000
WARN: uid is 0 but '/etc/default' is owned by 1000
Rule added
Rule added (v6)
```and tried again. Port still closed according to Transmission. Tried Reboot - the same result. No idea what it means by the WARN messages.

If it helps the output of 
```
sudo iptables -L
```is...
```
Chain INPUT (policy DROP)
target     prot opt source               destination         
ufw-before-logging-input  all  --  anywhere             anywhere            
ufw-before-input  all  --  anywhere             anywhere            
ufw-after-input  all  --  anywhere             anywhere            
ufw-after-logging-input  all  --  anywhere             anywhere            
ufw-reject-input  all  --  anywhere             anywhere            
ufw-track-input  all  --  anywhere             anywhere            

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ufw-before-logging-forward  all  --  anywhere             anywhere            
ufw-before-forward  all  --  anywhere             anywhere            
ufw-after-forward  all  --  anywhere             anywhere            
ufw-after-logging-forward  all  --  anywhere             anywhere            
ufw-reject-forward  all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-output  all  --  anywhere             anywhere            
ufw-before-output  all  --  anywhere             anywhere            
ufw-after-output  all  --  anywhere             anywhere            
ufw-after-logging-output  all  --  anywhere             anywhere            
ufw-reject-output  all  --  anywhere             anywhere            
ufw-track-output  all  --  anywhere             anywhere            

Chain ufw-after-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-input (1 references)
target     prot opt source               destination         
ufw-skip-to-policy-input  udp  --  anywhere             anywhere             udp dpt:netbios-ns
ufw-skip-to-policy-input  udp  --  anywhere             anywhere             udp dpt:netbios-dgm
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere             tcp dpt:netbios-ssn
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere             tcp dpt:microsoft-ds
ufw-skip-to-policy-input  udp  --  anywhere             anywhere             udp dpt:bootps
ufw-skip-to-policy-input  udp  --  anywhere             anywhere             udp dpt:bootpc
ufw-skip-to-policy-input  all  --  anywhere             anywhere             ADDRTYPE match dst-type BROADCAST

Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW BLOCK] "

Chain ufw-after-logging-input (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW BLOCK] "

Chain ufw-after-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-after-output (1 references)
target     prot opt source               destination         

Chain ufw-before-forward (1 references)
target     prot opt source               destination         
ufw-user-forward  all  --  anywhere             anywhere            

Chain ufw-before-input (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere             state RELATED,ESTABLISHED
ufw-logging-deny  all  --  anywhere             anywhere             state INVALID
DROP       all  --  anywhere             anywhere             state INVALID
ACCEPT     icmp --  anywhere             anywhere             icmp destination-unreachable
ACCEPT     icmp --  anywhere             anywhere             icmp source-quench
ACCEPT     icmp --  anywhere             anywhere             icmp time-exceeded
ACCEPT     icmp --  anywhere             anywhere             icmp parameter-problem
ACCEPT     icmp --  anywhere             anywhere             icmp echo-request
ACCEPT     udp  --  anywhere             anywhere             udp spt:bootps dpt:bootpc
ufw-not-local  all  --  anywhere             anywhere            
ACCEPT     udp  --  anywhere             224.0.0.251          udp dpt:mdns
ACCEPT     udp  --  anywhere             239.255.255.250      udp dpt:1900
ufw-user-input  all  --  anywhere             anywhere            

Chain ufw-before-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-before-output (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere             state RELATED,ESTABLISHED
ufw-user-output  all  --  anywhere             anywhere            

Chain ufw-logging-allow (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW ALLOW] "

Chain ufw-logging-deny (2 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere             state INVALID limit: avg 3/min burst 10
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW BLOCK] "

Chain ufw-not-local (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere             ADDRTYPE match dst-type LOCAL
RETURN     all  --  anywhere             anywhere             ADDRTYPE match dst-type MULTICAST
RETURN     all  --  anywhere             anywhere             ADDRTYPE match dst-type BROADCAST
ufw-logging-deny  all  --  anywhere             anywhere             limit: avg 3/min burst 10
DROP       all  --  anywhere             anywhere            

Chain ufw-reject-forward (1 references)
target     prot opt source               destination         

Chain ufw-reject-input (1 references)
target     prot opt source               destination         

Chain ufw-reject-output (1 references)
target     prot opt source               destination         

Chain ufw-skip-to-policy-forward (0 references)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            

Chain ufw-skip-to-policy-input (7 references)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            

Chain ufw-skip-to-policy-output (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain ufw-track-input (1 references)
target     prot opt source               destination         

Chain ufw-track-output (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere             state NEW
ACCEPT     udp  --  anywhere             anywhere             state NEW

Chain ufw-user-forward (1 references)
target     prot opt source               destination         

Chain ufw-user-input (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:56275

Chain ufw-user-limit (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 5 LOG level warning prefix "[UFW LIMIT BLOCK] "
REJECT     all  --  anywhere             anywhere             reject-with icmp-port-unreachable

Chain ufw-user-limit-accept (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain ufw-user-logging-forward (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-input (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-output (0 references)
target     prot opt source               destination         

Chain ufw-user-output (1 references)
target     prot opt source               destination         
```(Sorry for the long cut and paste, but I figure it may be useful to someone who knows..!)
AFAIK, I haven't changed anything with iPtables. 

Hope someone can point me in the right direction... Thanking you...

---

### Post by prshah on 2012-05-17
> **Moriarty123456 said:**
> ```
sudo ufw allow 56275/tcp
```Output:
```
WARN: uid is 0 but '/etc/default/ufw' is owned by 1000
WARN: uid is 0 but '/etc/default' is owned by 1000
Rule added
Rule added (v6)
```

The warning are just that; warnings. It does not affect the ufw command that you have issued.

However, (though this is not the cause of your primary problem) it does mean that there are some permissions issues with the /etc/default and /etc/default/ufw directory.

Normally, these directories and files within are owned and grouped as "root" (UID: 0), however, someone (or something) has changed ownership to these directories ( and possibly files therein) to primary user (UID: 1000, your login name). 

That's a no-no, but it is not causing your problem.

I suspect your problem has nothing to do with ufw. The port is being blocked at your router. You can check this by turning off ufw altogether and checking if the port is enabled (it shouldn't be). dont forget to re-enable ufw!```
sudo [s]service[/s] ufw disable
#now launch and check if port available
#then renable ufw
sudo service ufw restart
```

If the port is still unavailable inspite of ufw being disabled, then you need to check if you have port forwarding on the router enabled, or disable the firewall IN THE ROUTER (NOT RECOMMENDED, except as a quick test!). Please visit [www.portforward.com](www.portforward.com) to look up specific steps to enable port forwarding in your router model.

Please post back with results, or if you need further assistance.

---

### Post by Moriarty123456 on 2012-05-17
Many Thanks prshah!

I disabled UFW with your command. Output is:
```

Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service ufw disable

The script you are attempting to invoke has been converted to an Upstart
job, but disable is not supported for Upstart jobs.
```

However, the port is still disabled in Transmission.  I tried...

```
sudo ufw disable
``` Output...
```
WARN: uid is 0 but '/etc/default/ufw' is owned by 1000
WARN: uid is 0 but '/etc/default' is owned by 1000
Firewall stopped and disabled on system startup
``` Port still blocked. 

Looks like it's my router (which is strange as the settings won't have changed just because of my upgrade to 12.04 I would have thought...) so I'll try  [www.portforward.com]("http://www.portforward.com") for more help. 

Another thought... have I been rooted by someone..?

Thanks again prshah.

---

### Post by prshah on 2012-05-17
> **Moriarty123456 said:**
> 
```
sudo ufw disable
``` Output...
```
WARN: uid is 0 but '/etc/default/ufw' is owned by 1000
WARN: uid is 0 but '/etc/default' is owned by 1000
Firewall stopped and disabled on system startup
``` Port still blocked. 

Another thought... have I been rooted by someone..?


I don't think you have been rooted or compromised, but that is just a top-of-my-head guess. As a starting point, you can check logins to your system at /var/log/auth.log for anything suspicious looking.

Sorry, the command I gave was slightly wrong; corrected now. What you had done was correct. I hope you remembered to restart the service.

Port forwarding depends on the (LAN) ip address of your system. Maybe the upgrade may have removed a customized (static IP) or changed how the router recognizes your system.

If you do not want to fool around with port forwarding, simply (TEMPORARILY) disable the firewall on your ROUTER, and check if the port is visible. DONT FORGET TO RE-ENABLE THE FIREWALL on the router.

Please post back with results.

---

### Post by therisod on 2012-05-17
I have the same (similar) problem.
After upgrading to Ubuntu 12.04 Transmission isn't working any more.

I did fool around with my router port forwarding but without success. (transmission still doesn't work.)

The process freezes and I need to kill it. :cry:

---

### Post by Haneef Mubarak on 2012-05-25
Out of curiosity, have you tried:

```
sudo apt-get update; sudo apt-get upgrade -f
```

---

### Post by ptn107 on 2012-05-25
Did you try closing transmission, removing the following folders, and starting it up again?

rm -r .cache/transmission .config/transmission

This will reset its configuration like it was just installed.  There could be 'artifacts' left over from the upgrade.

---

### Post by theone964 on 2012-05-28
> **ptn107 said:**
> Did you try closing transmission, removing the following folders, and starting it up again?

rm -r .cache/transmission .config/transmission

This will reset its configuration like it was just installed.  There could be 'artifacts' left over from the upgrade.

tried that, it reset the configuration but still wont connect to peers or download.

---

### Post by Francisco6x on 2012-06-14
With Transmission on Ubuntu 12.04.
After downloaded a video, I have a folder with 56 items. 
But not a avi file.
How can I get my avi file?

---

