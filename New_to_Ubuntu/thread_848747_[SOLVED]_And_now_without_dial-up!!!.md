---
title: "[SOLVED] And now without dial-up!!!"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by iption on 2008-07-03
I reinstalled ubuntu, and when I tried to startup gnome-ppp it couldn't connect. I tried to check it and everything was ok, I even tried wvdial. Please help...

Gnome-ppp log:
```
--> WvDial: Internet dialer version 1.60
--> Initializing modem.
--> Sending: ATX3
ATX3
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: at+cgdcont=1, "ip", "carnet.vip.hr"
at+cgdcont=1, "ip", "carnet.vip.hr"
OK
--> Modem initialized.
--> Sending: ATM1L3DT*99#
--> Waiting for carrier.
ATM1L3DT*99#
CONNECT
~[7f]}#@!}!} } }2}#}$@#}!}$}%\}"}&} }*} } g}%~
--> Carrier detected.  Waiting for prompt.
~[7f]}#@!}!} } }2}#}$@#}!}$}%\}"}&} }*} } g}%~
--> PPP negotiation detected.
--> Starting pppd at Fri Jul  4 01:23:43 2008
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 6621
--> Using interface ppp0
--> Disconnecting at Fri Jul  4 01:23:54 2008
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
```

Obviously my isp doesn't give me my ip.

---

### Post by unutbu on 2008-07-03
Go to System>Administration>Users and Groups.
Click on your username, and the Properties button. Click on the "User Privileges" tab.
Do you have "Connect to internet using modem" enabled?

---

### Post by iaculallad on 2008-07-03
On your terminal:

```
sudo chmod a+rw /etc/ppp/pap-secrets
```

then Re-dial to your ISP. If successful, restore the original security attributes of pap-secrets file w/c will save your current authorized settings.

```
sudo chmod a-rw /etc/ppp/pap-secrets
sudo chmod u+rw /etc/ppp/pap-secrets
```

---

### Post by iption on 2008-07-03
> **iaculallad said:**
> On your terminal:

```
sudo chmod a+rw /etc/ppp/pap-secrets
```

then Re-dial to your ISP. If successful, restore the original security attributes of pap-secrets file w/c will save your current authorized settings.

```
sudo chmod a-rw /etc/ppp/pap-secrets
sudo chmod u+rw /etc/ppp/pap-secrets
```

Tnx this worked.

---

### Post by romainclair on 2009-01-22
Hi I need help for ubuntu7.1 and reliance datacard ec325.
I had net but suddenly he has cuted. it seems permissions problem in wvdial. exit code=16, a modem hung up the phone. Anyone can help me with wvdial, ppp config, or anything else. My pppconfig doesn't work too, ... disconnected. 
[email]romainc@lycos.com[/email]

---

