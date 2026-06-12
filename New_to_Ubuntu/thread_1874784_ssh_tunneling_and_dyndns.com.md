---
title: "ssh tunneling and dyndns.com?"
date: 2011-11-03
forum: New to Ubuntu
---

### Post by lance bermudez on 2011-11-03
user@computer:~$ ssh -vvv -p 9455 -X -C [email]user@computername.dyndns.org[/email]
OpenSSH_5.8p1 Debian-1ubuntu3, OpenSSL 0.9.8o 01 Jun 2010
debug1: Reading configuration data /home/user/.ssh/config
debug1: Applying options for *
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to computername.dyndns.org [217.128.61.112] port 9455.
debug1: connect to address 217.128.61.112 port 9455: Connection timed out
ssh: connect to host computername.dyndns.org port 9455: Connection timed out

how do i get this to work? Want to tunnel from work to home. have port fording turn on for the port and also have firewall turned off for the text. I'm doing the text from home be for at try it else ware. The dyndns.org right now is the free account to see if it works. Have installed ddclient
output from
sudo ddclient -daemon=0 -debug -verbose -noquiet > ddclient-output
is in attached file ddclient-output

---

