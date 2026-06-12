---
title: "Basic iptables firewall"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by jerremy-tamlin on 2008-11-05
Hi all,

I ran into a wall (or a dark forest rather, there are no walls in linux) trying to open the right ports to connect to my uni's vpn and network.

I tried using firestarter and guarddog but had no joy, the ports the uni told me I needed to open weren't the only ones that I needed. I thought I'd have a go and going down to a more core level and try manipulating the iptables directly. So I hit the tutorials and docs and learnt enough about iptables to setup a basic firewall. In the process I had to uninstall firestarter because it kept fighting with me and changing the iptables it's self, even when I wasn't starting it.

Anyway I managed to setup the following basic iptables firewall, and it WORKS GREAT! I'm just a little concerned that perhaps it's not very secure.

Can anyone tell me if there are huge holes in it?
```
Laptop:~$ sudo iptables -L -v
Chain INPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
 2411 80062 ACCEPT     all  --  lo     any     anywhere             anywhere            
 3664 2980K LOG        all  --  any    any     anywhere             anywhere            state RELATED,ESTABLISHED LOG level debug tcp-sequence tcp-options ip-options uid prefix `iptables-JW ESTABLISHED ' 
 3664 2980K ACCEPT     all  --  any    any     anywhere             anywhere            state RELATED,ESTABLISHED 
  135 17483 LOG        all  --  any    any     anywhere             anywhere            LOG level debug tcp-sequence tcp-options ip-options uid prefix `iptables-JW DROPPED ' 
  135 17483 DROP       all  --  any    any     anywhere             anywhere            

Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 6110 packets, 696K bytes)
 pkts bytes target     prot opt in     out     source               destination         

```

Is there a danger in accepting all outbound traffic or all established/related connections?
This is on a personal laptop that only I use.

Cheers

P.S. if anyone comes across this and wants to learn about iptables this is a [great tutorial]("https://help.ubuntu.com/community/IptablesHowTo") although I had to change one thing in the script given under "Configuration on Startup for NetworkManager"
Something on my system kept overwriting /etc/iptables.rules and making it blank when my system started so I changed the script to load a different file that I created with ```
COMMAND TO MANUALLY CREATE RULES FILE
sudo bash -c 'iptables-save -c > /etc/iptables-my.rules'

SCRIPT LINE:    /sbin/iptables-restore -c < /etc/iptables.rules
CHANGED TO:     /sbin/iptables-restore -c < /etc/iptables-my.rules

```

Please note also that **sudo iptables-save -c > /etc/iptables.rules** doesn't work on later versions of ubuntu. The reason is that sudo gives root privileges only to the command iptables-save but not to the redirection. To work around this one must do **sudo bash -c 'iptables-save -c > /etc/iptables.rules'**

---

### Post by drs305 on 2008-11-05
I can't comment on the security of your setup but will mention for other newbies that firestarter is fairly ancient these days and ufw (uncomplicated firewall) and it's gui-counterpart gufw are available. gufw makes working with iptables relatively easy.

Here is the wiki for ufw (geek warning): [https://wiki.ubuntu.com/UbuntuFirewall]("https://wiki.ubuntu.com/UbuntuFirewall")

Here is a good explanation of how to use gufw: [http://www.howtoforge.com/firewall-management-with-gufw-on-ubuntu-8.04-p2]("http://www.howtoforge.com/firewall-management-with-gufw-on-ubuntu-8.04-p2")

---

### Post by Sava8420 on 2008-11-05
Just a thought, you might want to post this thread under "Security Discussions" in the main support tab.  I think you will have much better luck in getting knowledgable feedback.  As far as I can tell you should be good depending on the network you are on.  I guess it all depends on what level of "secure" you are trying to achieve.  As far as basic security goes Ubuntu out of the box is secure as "most" people could want but judging by your thread I am not thinking you fall into that category.  Good luck.

---

### Post by jerremy-tamlin on 2008-11-18
Cheers, Have posted this to the "Security Discussions" forum. [http://ubuntuforums.org/showthread.php?t=986091](http://ubuntuforums.org/showthread.php?t=986091)

Thanks

---

