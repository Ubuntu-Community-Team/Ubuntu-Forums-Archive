---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2018-07-02
forum: Philippine Team
---

### Post by zubae on 2018-07-02
Hello,

I am testing out Zentyal 5.1 commercial version, but when I install packages (DC, DNS, DHCP) I get the following error code Sub-process /usr/bin/dpkg returned an error code (1).

I will post an output of sudo dpkg --configure -a

```
[B]Setting up zentyal-firewall (5.1) ...


service zentyal_webadmin does not exist.dpkg:error processing package zentyal-firewall (--configure):
 
subprocess installed post-installation script returned error exit status 1




dpkg: dependency problems prevent configuration of zentyal-dhcp:
 
zentyal-dhcp depends on zentyal-firewall; however:
  
Package zentyal-firewall is not configured yet.






dpkg: error processing package zentyal-dhcp (--configure):
 
dependency problems - leaving unconfigured


dpkg: dependency problems prevent configuration of zentyal-ntp:
 
zentyal-ntp depends on zentyal-firewall; however:
  
Package zentyal-firewall is not configured yet.






dpkg: error processing package zentyal-ntp (--configure):
 
dependency problems - leaving unconfigured


dpkg: dependency problems prevent configuration of zentyal-samba:
 
zentyal-samba depends on zentyal-firewall; however:
  
Package zentyal-firewall is not configured yet.
 
zentyal-samba depends on zentyal-ntp; however:
  
Package zentyal-ntp is not configured yet.






dpkg: error processing package zentyal-samba (--configure):
 
dependency problems - leaving unconfigured


dpkg: dependency problems prevent configuration of zentyal-dns:
 
zentyal-dns depends on zentyal-firewall; however:
  
Package zentyal-firewall is not configured yet.






dpkg: error processing package zentyal-dns (--configure):
 
dependency problems - leaving unconfigured


dpkg: dependency problems prevent configuration of zentyal-mail:
 
zentyal-mail depends on zentyal-samba; however:
  
Package zentyal-samba is not configured yet.






dpkg: error processing package zentyal-mail (--configure):
 
dependency problems - leaving unconfigured


dpkg: dependency problems prevent configuration of zentyal-openvpn:
 
zentyal-openvpn depends on zentyal-firewall; however:
  
Package zentyal-firewall is not configured yet.






dpkg: error processing package zentyal-openvpn (--configure):
 
dependency problems - leaving unconfigured


dpkg: dependency problems prevent configuration of zentyal-groupware:
 
zentyal-groupware depends on zentyal-mail; however:
  
Package zentyal-mail is not configured yet.






dpkg: error processing package zentyal-groupware (--configure):
 
dependency problems - leaving unconfigured


dpkg: dependency problems prevent configuration of zentyal-sogo:
 
zentyal-sogo depends on zentyal-mail; however:
  
Package zentyal-mail is not configured yet.






dpkg: error processing package zentyal-sogo (--configure):
 
dependency problems - leaving unconfigured


Errors were encountered while processing:
 
zentyal-firewall
 zentyal-dhcp
 zentyal-ntp
 zentyal-samba
 zentyal-dns
 zentyal-mail
 
zentyal-openvpn
 zentyal-groupware
 zentyal-sogo
[/B]


```[B][COLOR=#222222][FONT=Verdana]

Tried configuring the firewall, still smae error. Need help thank you.[/FONT][/COLOR]
[/B]

---

### Post by TheFu on 2018-07-02
Is the system fully up-to date?
```
sudo apt update
sudo apt full-upgrade
```

Do those work without any errors?  You may need to reboot after the 2nd cmd, but only if it completes without errors and creates a file called /var/run/reboot-needed

If that is all working, then we can try an tackle other issues.

---

### Post by mIk3_08 on 2018-07-11
Bump

---

