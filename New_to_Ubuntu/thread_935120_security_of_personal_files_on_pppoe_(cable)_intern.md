---
title: "security of personal files on pppoe (cable) internet connection"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by fourthofjuly on 2008-10-01
i have a cable internet connection which i can connect using pon dsl-provider (configured through pppoeconf)...

while browsing through the network, i accidentally noticed that i could access and copy / delete all files from some other users computer running windows...!!! (who might also be subscriber to my internet service provider)... can anyone suggest how this is possible?

now, my question is... how safe are my files in ubuntu's home folder? can they also be accessed elsewhere and tampered with?

if so, how can i ensure security of my data if my ISP has overlooked this?

how about my files on my windows partition since the partitions are mounted?

please guide me...

---

### Post by sydbat on 2008-10-01
I doubt that you accessed someone else's computer. Some websites have no fancy page to look at, just a list of files for download.

As far as I know, Ubuntu has no open ports by default, so someone else should not be able to access your computer remotely. If you are worried, you can use Firestarter (from the repositories System > Administration > Synaptic Package Manager then search for Firestarter) or [ufw]("https://wiki.ubuntu.com/UbuntuFirewall") to configure the built in firewall.

---

### Post by LowSky on 2008-10-01
> **fourthofjuly said:**
> 
while browsing through the network, i accidentally noticed that i could access and copy / delete all files from some other users computer running windows...!!! (who might also be subscriber to my internet service provider)... can anyone suggest how this is possible?

First off you couldn't access someones Windows files without first installing Samba which would allow Network access to a Windows workgroup from a Linux machine, second you would need access to the network, which would mean you were all connected to the same router or you had access to their local connection by knowing the network address or even passwords.

---

### Post by superprash2003 on 2008-10-01
some ISP's share modems with many subscribers.so then two or more subscribers would be on a LAN.. its possible.. as mentioned above, since you are on ubuntu with sharing disabled by default you shouldnt worry... just ensure you have a good firewall. and incase you enable file sharing ensure its password protected..

---

### Post by fourthofjuly on 2008-10-01
> I doubt that you accessed someone else's computer.

yes, there were c and d drives from where i could copy files... for sure...

what exactly are open ports? please explain... does windows have open ports, i didn't know that... 

i have zonealarm firewall running in  windows... how does that help?

---

### Post by fourthofjuly on 2008-10-01
> **LowSky said:**
> First off you couldn't access someones Windows files without first installing Samba which would allow Network access to a Windows workgroup from a Linux machine, second you would need access to the network, which would mean you were all connected to the same router or you had access to their local connection by knowing the network address or even passwords.
well, my ISP has given a cable for internet access that's plugged in my lan card...

not sure if i have samba activated, but drives of some users asked for a password and were not accessible, others i could easily open AND EDIT..., which is really shocking...

---

### Post by fourthofjuly on 2008-10-01
> **superprash2003 said:**
> some ISP's share modems with many subscribers.so then two or more subscribers would be on a LAN.. its possible.. as mentioned above, since you are on ubuntu with sharing disabled by default you shouldnt worry... just ensure you have a good firewall. and incase you enable file sharing ensure its password protected..
if i understand this correctly, 

1) no one has access to my files unless i explicitly share them, right?

2) there is a firewall by default in ubuntu, and firestarter can also be used as an additional security measure

there is this selinux in fedora... can it be installed in ubuntu and will it help me with my problem?

---

### Post by nowshining on 2008-10-01
> **fourthofjuly said:**
> if i understand this correctly, 

1) no one has access to my files unless i explicitly share them, right?

2) there is a firewall by default in ubuntu, and firestarter can also be used as an additional security measure

there is this selinux in fedora... can it be installed in ubuntu and will it help me with my problem?

1: should be unless someone hacks into ur computer - 

2. the firewall in  linux is iptables u can either use a gui to set it up or a bash script, or may i suggest arno-iptables-firewall found in the repos :) much more customizable and easier to setup, and u can add custom iptables rules into the custom-rules file of which arno-iptables will read, alas there are plugins, etc.. the config file can be found in /etc/arno-iptables-firewall/firewall.conf as well as the custom rules file...

---

