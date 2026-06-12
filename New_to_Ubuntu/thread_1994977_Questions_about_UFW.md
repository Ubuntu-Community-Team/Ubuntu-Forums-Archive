---
title: "Questions about UFW"
date: 2012-06-03
forum: New to Ubuntu
---

### Post by aRake on 2012-06-03
Hello, I am a very new Ubuntu user (one week).  I have installed Ubuntu 12.04 (64 bit) on my laptop with Windows 7 (dualboot).  I have attempted to configure my iptables by using ufw from the terminal.

As a reference for setting this up, I used [http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)

So far, here is what I have done.
```
Status: active

     To                         Action      From
     --                         ------      ----
[ 1] 20,21,25,80,443/tcp        ALLOW OUT   Anywhere (out)
[ 2] 53/udp                     ALLOW OUT   Anywhere (out)
[ 3] Anywhere                   DENY OUT    Anywhere (out)
[ 4] 20,21,25,80,443/tcp        ALLOW OUT   Anywhere (v6) (out)
[ 5] 53/udp                     ALLOW OUT   Anywhere (v6) (out)
[ 6] Anywhere (v6)              DENY OUT    Anywhere (v6) (out)
```

I am trying to have the very minimal allowance, but I do not know very much about networking.  I am not interested in SSH/VNC or any such thing.  I just want internet access - downloading files, checking my gmail, etc.  

I have a few questions about UFW:
1)  Do I need to have ufw as "enabled" in order for my firewall to function?  I thought it configured iptables, which always runs?  Any explanation?
2)  Am I missing any ports for regular functioning?
3)  Does having Windows 7 as a dualboot affect this in any way?
4)  Why are there two of every rule (a v6 and a not-v6)?

I am very eager to learn more about Linux/Ubuntu, specifically on this topic, but I could not find answers to these questions online.

Thank you very much for your time and help, I very much appreciate it.

---

### Post by ts3 on 2012-06-03
> **aRake said:**
> Hello, I am a very new Ubuntu user (one week).  I have installed Ubuntu 12.04 (64 bit) on my laptop with Windows 7 (dualboot).  I have attempted to configure my iptables by using ufw from the terminal.

As a reference for setting this up, I used [http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)

So far, here is what I have done.
```
Status: active

     To                         Action      From
     --                         ------      ----
[ 1] 20,21,25,80,443/tcp        ALLOW OUT   Anywhere (out)
[ 2] 53/udp                     ALLOW OUT   Anywhere (out)
[ 3] Anywhere                   DENY OUT    Anywhere (out)
[ 4] 20,21,25,80,443/tcp        ALLOW OUT   Anywhere (v6) (out)
[ 5] 53/udp                     ALLOW OUT   Anywhere (v6) (out)
[ 6] Anywhere (v6)              DENY OUT    Anywhere (v6) (out)
```

I am trying to have the very minimal allowance, but I do not know very much about networking.  I am not interested in SSH/VNC or any such thing.  I just want internet access - downloading files, checking my gmail, etc.  

I have a few questions about UFW:
1)  Do I need to have ufw as "enabled" in order for my firewall to function?  I thought it configured iptables, which always runs?  Any explanation?
2)  Am I missing any ports for regular functioning?
3)  Does having Windows 7 as a dualboot affect this in any way?
4)  Why are there two of every rule (a v6 and a not-v6)?

I am very eager to learn more about Linux/Ubuntu, specifically on this topic, but I could not find answers to these questions online.

Thank you very much for your time and help, I very much appreciate it.

I am not an expert by any means so just a few thoughts rather than specific advice:

1) My understanding is that iptables always runs and you can manipulate it directly but if you want to use ufw for that purpose you need to enable it (in the same way that you need to install gufw if you want a gui frontend); the default iptables settings are probably fairly restrictive anyway (I assume it drops all unsolicited incoming traffic etc.) but many people want a bit more control and ufw is one way to achieve that.  Check this post for more details on doing the same thing using iptables, ufw or gufw [http://ubuntuforums.org/showthread.php?t=1876124](http://ubuntuforums.org/showthread.php?t=1876124)

2) I assume you want ftp since you'are allowing ports 20 & 21?  You might want to look into allowing ouy ports 67 and 68 both tcp and udp (that's DHCP); for using thunderbird with gmail one would need 143, 465 and 993 for imap access.  Generally, it's probably a good idea to enable logging (sudo ufw logging on) and if you try to do something and it doesn't work (like setting up thunderbird) check the logs and see which ports were blocked.  For example, on some distros (not ubuntu in my experience) one might need to enable 11371 for accessing pgp key servers.

3) No connection between Windows and linux firewalls in any way as far as I know.

4) I've always thought it's related to IPv6 but it might not be :)

From the way your rules are set up if you want to allow any other ports out you'd need to add them before the sweeping "deny everything else out" rule.

Cheers

---

### Post by aRake on 2012-06-04
> **ts3 said:**
> I am not an expert by any means so just a few thoughts rather than specific advice:

1) My understanding is that iptables always runs and you can manipulate it directly but if you want to use ufw for that purpose you need to enable it (in the same way that you need to install gufw if you want a gui frontend); the default iptables settings are probably fairly restrictive anyway (I assume it drops all unsolicited incoming traffic etc.) but many people want a bit more control and ufw is one way to achieve that.  Check this post for more details on doing the same thing using iptables, ufw or gufw [http://ubuntuforums.org/showthread.php?t=1876124](http://ubuntuforums.org/showthread.php?t=1876124)Thank you very much, I have indeed read that post.

> **ts3 said:**
> 2) I assume you want ftp since you'are allowing ports 20 & 21?  You might want to look into allowing ouy ports 67 and 68 both tcp and udp (that's DHCP); for using thunderbird with gmail one would need 143, 465 and 993 for imap access.  Generally, it's probably a good idea to enable logging (sudo ufw logging on) and if you try to do something and it doesn't work (like setting up thunderbird) check the logs and see which ports were blocked.  For example, on some distros (not ubuntu in my experience) one might need to enable 11371 for accessing pgp key servers.
To tell you the truth, I am not sure exactly what FTP or DHCP are used for.  I have read about them, but the articles I have read have only been about the protocols, not about their applications, so I do not know if I use these, haha.

> **ts3 said:**
> 3) No connection between Windows and linux firewalls in any way as far as I know.

4) I've always thought it's related to IPv6 but it might not be :)

From the way your rules are set up if you want to allow any other ports out you'd need to add them before the sweeping "deny everything else out" rule.

Cheers
Again, thanks for all the help!

---

