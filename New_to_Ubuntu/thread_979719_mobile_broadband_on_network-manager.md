---
title: "mobile broadband on network-manager"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by richaoj on 2008-11-12
I have tethered my palm centro to my laptop ... it works fine with a terminal command line:

sudo pppd /dev/ttyACM0 call ppp-script-treo

HOWEVER, i would like to be able to simply use network manager to connect.  
Is there a way (i know there is, but i don't know how)
to edit the connect script that network-manager uses and force it to use my custom connect script?  What file would i edit?

Here is my connect script:

460800
connect '/usr/sbin/chat -s -v  "" "AT&F0E0V1S0=0"  OK \'AT+CGDCONT=1,"IP","wap.cingular"\'  OK ATD*99#  CONNECT'
debug
updetach
crtscts
noipdefault
novj
lcp-echo-failure 0
nobsdcomp
novjccomp
nopcomp
noaccomp
noauth
user [email]WAP@CINGULARGPRS.COM[/email]
modem
usepeerdns
defaultroute
connect-delay 5000


And i have properly edited /etc/ppp/pap-secrects to work as well.  
Can i have network manager use this script?

OJR

---

### Post by ushills on 2008-11-12
With 8.10 my Palm 500 (windows mobile) was recognised by my laptop as eth1 and no configuration was required.

Are you running 8.10?

---

### Post by richaoj on 2008-11-12
Yes.  8.10, but with a palm os palm-- using a utility called USBModem. 

It did not work just plugged in using any of the default settings in the network manager broadband (ATT) choices.

---

