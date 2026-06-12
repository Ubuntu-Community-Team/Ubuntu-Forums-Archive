---
title: "ethernet bridge communication"
date: 2012-01-01
forum: New to Ubuntu
---

### Post by nmum on 2012-01-01
i had configure an Ethernet bridge on two ubuntu systems both having two Ethernet Cards and both systems are connected with cross cables

 i now want to send a command from one system that should execute on other system using terminal.

can any one help me in this regards
advance thanx

---

### Post by The Cog on 2012-01-01
I assume that the systems can ping each other. If not, fix this first.

The usual thing to do would be to run an SSH server on one of the two systems so that you can log into it from the other system. Ubuntu installs an SSH client by default, but for the one you want to log into, you need to install package openssh-server. This command does that:
> sudo apt-get intstall openssh-server
Now you can ssh to the server using a terminal and execute commands. Assuming the server's address is 1.2.3.4, this command will log you in:
> ssh 1.2.3.4
and you can just do one-off commands by putting the command at the end of the ssh command:
> ssh 1.2.3.4 somecommand
Beware that if the ssh server is open to the internet, you will have bots trying to guess passwords all day, so make sure your passwords are strong. Perhaps look into using keys instead of passwords.

---

### Post by nmum on 2012-01-02
i hv situation like this as in  attachment


i want to add an iptables rule to block an ip on one ridge n send this information to 2nd bridge so that 2nd one need not to do these steps

---

### Post by The Cog on 2012-01-02
I'm not sure if iptables can affect bridged packets. You may need to use brtables instead, but I don't know how easy it is to get brtables to filter by IP address.

Either way, you only need to block the packets in one of the Linux boxes to prevent it from reaching the other side.

---

