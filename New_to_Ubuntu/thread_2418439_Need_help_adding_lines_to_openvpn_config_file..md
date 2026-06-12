---
title: "Need help adding lines to openvpn config file."
date: 2019-05-06
forum: New to Ubuntu
---

### Post by crip720 on 2019-05-06
Have ubuntu 16.04 and having trouble with DNS leaks in VPN.  Was asked by VPN provider to add these lines to opnvpn config file. ```
script-security 2up /etc/openvpn/update-resolv-conf down /etc/openvpn/update-resolv-conf
```
 Provider is windscribe.  I think I need to use sudo nano, but would like if someone can give me the proper file name so I don't mess up.  I have google instructions for nano, but most instructions online require file name or just give /path/to/.  Thank you for anyone willing to hold my hand.

---

### Post by #&amp;thj^% on 2019-05-06
Do us a favor please and copy the instructions here in this thread.
Remind for Code Tags.
EDIT:  Be sure not to post any personal information.

---

### Post by crip720 on 2019-05-06
Thanks, does look better.

---

### Post by #&amp;thj^% on 2019-05-06
Wow they had you figured as a power user, very friendly new user instructions! LOL And this my interpretation of your given info:
BTW You will need to install **"openresolv"** First. **"sudo apt install openresolv"**
In terminal:
```
sudoedit /etc/openvpn/update-resolv-conf
```
now add the line "they" told you to use:
```
script-security 2
up /etc/openvpn/update-resolv-conf.sh
down /etc/openvpn/update-resolv-conf.sh
down-pre
```
Place them just below:
```
# Parses DHCP options from openvpn to update resolv.conf
# To use set as 'up' and 'down' script in your openvpn *.conf:
# up /etc/openvpn/update-resolv-conf
# down /etc/openvpn/update-resolv-conf
#
#Add them here :)
```
Restart your session and check again for leaks!
Good Luck
BTW You will need to install **"openresolv"** First.

---

### Post by crip720 on 2019-05-06
Thank you, will mark as solve if it works.

---

### Post by crip720 on 2019-05-06
Just an update, did not break internet, but does not seem to fix webrtc leak.

---

### Post by #&amp;thj^% on 2019-05-06
I thought as much lets help them along with a few more words, we will add one more line to help then:
```
setenv PATH /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
```
so it now looks:
```
# This updates the resolvconf with dns settings
setenv PATH /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
script-security 2
up /etc/openvpn/update-resolv-conf.sh
down /etc/openvpn/update-resolv-conf.sh
down-pre
```
This is just UN-exceptable hoops to jump through for a client to do, unless it's free and you knew it to be buggy. (Sorry just my 2 cents worth)

---

### Post by crip720 on 2019-05-06
One question 1fallen, you added -pre at the end of first set of code, is that correct?  It is paid, but lifetime use for what most charged for less than a year.

---

### Post by #&amp;thj^% on 2019-05-06
Yes I added "down-pre" to the end.

---

### Post by crip720 on 2019-05-06
New line did not seem to help, added a new dns address plus both of my ISP dns servers, first time I had four servers show, usually only two or three.  Just did about five ipleak tests and leak only showed up for about three of them, other two were good.  I also added openresolv nscd unbound a few days ago, wondering if that helps or hurts what we are doing.

---

### Post by #&amp;thj^% on 2019-05-06
Well lets stop here then, and feel free to link this thread with any correspondence you give them.
Maybe my view on the info you provided by your VPN provider is wonky. IJDK
If you need help un-doing what have done just ask.

---

### Post by crip720 on 2019-05-06
Think maybe solved it, changed Network manager VPN from 'automatic' to 'automatic addresses only'.  When I did this to wired or wireless before, I lost internet till I changed back.  It seems to be working for vpn though.  Just used my other vpn server that is still on automatic and no leaks with that one either.  Maybe the three or four reboots I did, because keyring for vpn does not open when I just stop/start NM, did it.  Had same thing happen a while back when an update knock out my wired, needed a few reboots to get it back.  Thank you for your help 1Fallen, something we did fixed it.

---

### Post by #&amp;thj^% on 2019-05-07
Great, Glad to hear this is sorted out now.:)

---

